# armillary

**A model-agnostic sub-harness for routing token flows.** For philosophy, see [here](https://github.com/studiozojer/armillary/blob/main/philosophy.md).

![hero.png](https://schultzdavidg-portfolio.s3.us-west-1.amazonaws.com/images/armillary/hero.png)

## Q: What is a sub-harness?

A sub-harness is just a way of structuring your directories that pushes agents toward specific types of behaviour. 

While it is a harness in the sense that it directs AI behaviour, it is really only a layer underneath the actual CLI. You can use [Hermes](https://hermes-agent.nousresearch.com/), [Pi](https://pi.dev/), [Claude Code](https://claude.ai/)—whatever you like—with a sub-harness.

The point of a sub-harness is to organize your file system to enable more efficient knowledge traversal.

### Q: How does it work?

In the armillary, there are three types of top-level directories:
1. Agents, a.k.a. worldmodels
2. Repos, a.k.a. your code bases
3. Commons, a.k.a. shared, persistent, graph-structured knowledge

Whenever you start a session from the root directory, the first thing your context window does is load up a set of tokens. This might mean:
- Project specs
- Changelogs
- Philosophy
- Worldmodels

By doing this at the beginning, we shape downstream model behaviour, to be more aligned with our personal ways of working.

### Q: Can I use this?

Yes, absolutely! This framework is very lightweight. But it points to a *way* of working that only makes sense if it fits in with the ways you, yourself, work with AI.

I recommend checking out [the commons](https://github.com/studiozojer/commons), for more.