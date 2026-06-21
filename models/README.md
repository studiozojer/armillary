# models — the agents slot

Compose your agents here. Each agent is its own independent git repo, dropped into
this folder as `models/<agent>/`. Everything in here is **gitignored** except this
README — the router never tracks its guests.

The router routes a session to whichever agents are present and **assumes none by
default**. A bare clone has this empty slot and a dispatcher that routes everything
to itself — that is a working host, not an error. Declare what you compose in
`modules.toml`.
