# armillary

**A model-agnostic sub-harness that routes token flows**

The core idea is that the context window is a design surface. Every token influences model behaviour — so the theory is, if we are intentional about what tokens get loaded, we can shape more efficient model behaviour.

---

### Efficiency?

When I talk about efficiency, I mean it in the way that the whole point of a hashmap is O(1) lookup. Currently, models are terribly inefficient at gathering the resources they need to do a task.

My thesis revolves around building low-entropy token pathways using graph theory. The armillary is the sub-harness I use to figure out how to create those pathways.

### Q: Can I use this?

A: Yes, absolutely! This framework is very lightweight. But it points to a *way* of working that only makes sense if it fits in with the ways you, yourself, work with AI.

### Q: How does it work?

The first thing you have to understand is the idea that: the first batch of tokens in the context window are, arguably, the most instrumental. They are the easiest to access (due to solidified content-addresses via DISOT), and dictate the flow of every downstream interaction in the window.

What the armillary does is, it **primes** your context window with a specific mindset. A worldview, if you will.

When you start a session (in whatever harness of your choosing) at this root directory, the armillary does a few things. First, it finds its boot protocols.  to gather whatever context will be useful for the work session.
