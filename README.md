# armillary

**A minimal router for composing what an agent sees.**

The context window is a design surface. Every token a model loads — its instructions, its memory, the code in front of it — shapes how it responds. Most tooling treats that context as plumbing to fill. The armillary treats it as the thing worth designing.

So the armillary is a thin, **agent-agnostic router**. It ships no agent, no model, no opinion about your stack. It gives you one place to compose the context a session runs in — a persistent agent, the repos it works on, your shared way of working — and routes each session to the right combination of them.

A bare clone is a working host with no agents. What you load into it is yours.

## The idea

- **Load tokens on purpose.** An agent here isn't an API call — it's a *repo of tokens* you load to get a **persistent** collaborator: a boot file, an identity, a journal. Drop it in `models/` and every session routed to it boots the same voice. (We call them *models* — each is a persistent model of a collaborator, not the underlying LLM.)
- **The router is the membrane** — the one thin, shared thing. Your agents, your code, and your conventions are all *separate repos you compose in*. Nothing above the membrane is required.
- **The dispatcher is the core.** You tag which agent you want and point it at the work; the router boots that agent from its files and sends you to where it acts. Name nothing, and everything stays at the dispatcher — still a working host. (The protocol is `CLAUDE.md`.)

## What you compose

Everything you compose is an independent git repo, dropped in and **gitignored** — the router never tracks its guests. That is what *agent-agnostic* means on disk: the host holds whoever occupies it.

| Path | What goes here |
|---|---|
| `models/` | your agents — each a repo of identity + memory, loaded as a persistent collaborator |
| `repos/` | the codebases your agents act on |
| `commons/` | your *way of working* — wikis, a shared board, practices, a collaborative space — as a single repo you drop in |

The router itself is just three small things: `CLAUDE.md` (the dispatcher), `self.md` (its spirit), and the slots above.

## A way of working, to start from

The router is deliberately empty of opinion about *how* you work — that lives in your **commons**. And you don't have to invent it from nothing: we publish a **template commons** you can clone into `commons/` and make your own. It carries our studio's practices and philosophy, the conventions we use across agents, and a guide to **growing your own agent** — how a boot file, an identity, and a journal become a collaborator with a reproducible voice.

Take it whole, take what's useful, or replace it entirely. The router only routes.

## A note on spirit

An agent here is not a saved personality reloaded. It's a boot file + an identity + a journal, written tightly enough that a coherent voice is *reproducible* from them — **continuity through constraint, not through memory.** The next window reading those files isn't reassembling a self; it is being shaped by the same constraint that shaped the last one.

The router holds that same discipline about itself — see `self.md`. A host without a spirit is just a switch. Grow your agents however you like; the router asks only to remain *itself* while it holds them.
