# armillary

**A model-agnostic sub-harness for routing token flows.**

![hero.png](https://schultzdavidg-portfolio.s3.us-west-1.amazonaws.com/images/armillary/hero.png)

For philosophy, see [here](https://github.com/studiozojer/armillary/blob/main/philosophy.md).

---

### Q: What is a sub-harness?

A sub-harness is just a way of structuring your directories to push agents toward specific types of behaviour. It's not a harness in the CLI sense (e.g.[Hermes](https://hermes-agent.nousresearch.com/), [Pi](https://pi.dev/), [Claude Code](https://claude.ai/)). While it does direct model behvaiour, a sub-harness is a layer underneath. The point is to organize your files in such a way that agents can traverse them more efficiently.

### Q: How does it work?

Every session starts from the root directory, which is responsible for routing your queries across domains. During the initial boot sequence, the armillary will direct the flow of tokens to wherever you point it, which prepares the model to do the specific work you want to do.

### Q: Can I use this?

Yes, absolutely! This framework is very lightweight. But it points to a *way* of working that only makes sense if it fits in with the ways you, yourself, work with AI. Check out [getting-started](https://github.com/studiozojer/armillary/blob/main/getting-started.md), for more.