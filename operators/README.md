# operators — the occupant slot

Compose your operators here. An **operator** is a composed identity — its files,
graph, and protocols — as distinct from the **model** (the engine that pilots it in
a given session; operators are model-agnostic). Each operator is its own
independent git repo, dropped into this folder as `operators/<operator>/`.
Everything in here is **gitignored** except this README — the router never tracks
its guests.

The router routes a session to whichever operators are present and **assumes none
by default**. A bare clone has this empty slot and a dispatcher that routes
everything to itself — that is a working host, not an error. Declare what you
compose in `modules.toml`.

*(Renamed from `models/` 2026-07-24 — the old name collided with "model" meaning
the engine. Legacy `[[models]]`/`[[agents]]` manifest sections are still parsed, and
a manifest may still declare `path = "models/<name>"`, since the path is read from
the manifest. The `models -> operators` compat symlink is **retired as of
2026-07-28**: a bare `models/...` path written in prose no longer resolves. It was
removed on purpose — a symlink that resolves silently means nothing ever breaks, so
nothing ever gets fixed, and a rename stays permanently unfinished.)*
