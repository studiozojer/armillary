# armillary

![hero.png]([https://schultzdavidg-portfolio.s3.us-west-1.amazonaws.com/images/armillary/hero.png](https://schultzdavidg-portfolio.s3.us-west-1.amazonaws.com/images/armillary/hero.png))

**A model-agnostic sub-harness for routing token flows**

Every token in the session influences model behavior — so the theory is, if we are intentional about what tokens get loaded, we can shape more efficient model behavior.

For philosophy, see [here](https://github.com/studiozojer/armillary/blob/main/philosophy.md).

---

## Q: What is a sub-harness?

A sub-harness is just a way of structuring your directories, in order to push agents toward specific types of behaviour.

In the armillary, there are three types of top-level directories:
1. Agents, a.k.a. worldmodels
2. Repos, a.k.a. your code bases
3. Commons, a.k.a. shared, persistent, graph-structured knowledge

It's called a "sub-harness" because while it is a harness in the sense that it directs AI behaviour, it is agnostic towards the actual CLI. You can use [Hermes](https://hermes-agent.nousresearch.com/), [Pi](https://pi.dev/), [Claude Code](https://claude.ai/)—whatever you like—with a sub-harness.

### Q: How does it work?

First, boot your session into the top-level dir.

Then, in your first message, you ask the armillary to route you towards the tokens you need. For example, you might direct it to pick up one of your agents's boot protocols.

``` CLI
> @tycho can you orient? i want to clean up the athanor today
```

After sending this message, the armillary will follow a chain of text files, which illustrate protocols, first principles, historical logs, etc. to prepare the session for the work you want to do.

Everything else you do downstream will follow suit.

### Q: Can I use this?

Yes, absolutely! This framework is very lightweight. But it points to a *way* of working that only makes sense if it fits in with the ways you, yourself, work with AI.

I recommend checking out [the commons](https://github.com/studiozojer/commons), for more.
