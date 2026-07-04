# armillary

Minimal, **agent-agnostic router** root. Composes whatever a workspace declares in `modules.toml` — agents, a commons, repos, and the **protocols** they bring — loading each into the session at its declared time (with a gitignored `modules.local.toml` for private, per-machine bindings). **Assumes no agents by default**, and treats a **commons** as standard practice, offering to connect one if absent. A bare clone is still a working host with no modules, and that is fine. See `README.md` for the idea, `modules.toml` for the schema.

## Dispatcher protocol

When launched from the router root (not from inside a composed module):

1. **Read `modules.toml`.** It declares what's composed — agents, a commons, repos — and the **protocols** each brings (see § Protocols), with private/per-machine bindings layered in from `modules.local.toml` / `CLAUDE.local.md`. A bare clone declares nothing; that is the default, not an error.
   - **Commons are standard practice (agents are not).** Agents are genuinely optional — assume none. A commons carries the workspace's shared knowledge, board, and protocols, so a working deployment normally composes one. If none is declared, the router still boots and works bare — but surface a one-line offer: *"no commons is composed — clone or connect one to attach this workspace's shared knowledge and protocols?"* Don't block on it; just make the absence visible.
2. **Boot-load** every protocol declared `load = "boot"` — read its body now. These compose the session's starting context (e.g. a board surfaces; a metrics protocol offers consolidation past a threshold).
3. **Register** every `load = "on-demand"` protocol as a pointer — note its `name` and `when`, but **do not read the body** (lazy by design; see § Protocols).
4. **Surface** briefly, at the top of the session, whatever boot-load produced (a board, an offer). With nothing composed, there is nothing to surface — proceed.
5. **Route the opening message:**
   - Names a composed module (agent or repo), or clearly describes work in its domain → dispatch to it; follow its own boot protocol as if launched there. An explicit `@<agent>` summon is boot-gated where a `summon-boot` hook is composed: the summoned model's own boot runs first — before any repo/skill/tool touch except this dispatcher — even when the same message also names a destination (the destination is material to orient *through*, not a reason to skip orienting).
   - Matches a registered `on-demand` protocol's `when` → read that protocol's body now, then proceed.
   - Meta/structural — about the router or the workspace itself → stay at dispatcher; load `self.md` before responding.
   - Nothing composed → everything is dispatcher-layer.
   - Ambiguous → ask.
6. **At session close**, run any `load = "session-end"` protocol (best-effort — see § Protocols).

If launched directly inside a composed module, skip this protocol. `self.md` and boot-surfaced protocols are dispatcher-layer surfaces, not part of any module's own boot.

## Protocols

The dispatcher's real work is **composing what loads, and when.** A **protocol** is a discipline — a "how to do X" — that a composed module brings (an agent, the commons, a repo) and declares in `modules.toml`:

```toml
[[protocols]]
name   = "board"
source = "commons/practices/board/practice.md"
load   = "boot"
```

**Declarative, not discovered.** The router knows a protocol exists because `modules.toml` *names* it — it does not scan. That keeps the manifest legible: open `modules.toml` and you see exactly what loads, and when. (A module may organize its protocol bodies however it likes — a commons often groups them under `practices/` — but each is wired in by a declaration.)

**Load timings** (`load =`):

- **`boot`** — read at session start; composes the starting context. Run at dispatcher step 2.
- **`on-demand`** — a pointer; the body is read only when its `when` matches the work (step 5). Lazy by design: anything auto-loaded at boot becomes a *write-attractor* — a sink for whatever an agent wants guaranteed-seen — so the router reads on-demand bodies only when the work actually calls for them.
- **`session-end`** — run at close (step 6). **Best-effort, not guaranteed:** a clean session close isn't promised (context fills, the window just ends), so don't rely on it for anything that *must* persist.

Honor a protocol's declared `requires:` — a missing dependency means skip it, not error. Presence-gated throughout: a bare clone declares no protocols, and the router loads nothing.

## Routing

Routing is the generic algorithm in § Dispatcher protocol, step 5: a message that names or clearly describes a composed module's domain dispatches to that module (and follows its own boot protocol); work that matches a registered `on-demand` protocol loads it then; meta/structural work stays at the dispatcher (load `self.md`); with nothing composed, everything is dispatcher-layer; ambiguous → ask.

**A workspace's concrete module mappings** — which agent or repo owns which domain, and where each resolves on a given machine — live in `CLAUDE.local.md` (and `modules.local.toml`), so the published router stays agnostic to who occupies it. A bare clone has no mappings and routes everything to the dispatcher.
