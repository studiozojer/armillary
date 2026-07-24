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
the engine. Legacy `[[models]]`/`[[agents]]` manifest sections and `models/` paths
remain accepted by tooling during migration.)*
