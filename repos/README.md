# repos — the code slot

Compose your product and project repos here. Each is its own independent git repo,
dropped into this folder as `repos/<repo>/`. Everything in here is **gitignored**
except this README — the router never tracks its guests.

These are the codebases your agents act on. The router gives access to them; it
**assumes none by default**. Declare what you compose in `modules.toml`.
