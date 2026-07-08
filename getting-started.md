# Getting started

Whenever you start a session from a directory, the first thing your harness does is load a set of tokens. Usually this takes form as a CLAUDE.md file—but I've found that we can go further, with protocols to boot things like:
- Project specs
- Roadmaps
- Philosophy
- Shared workspaces
- Worldmodels

 **The armillary** is a system dedicated to this pattern, and primarily uses file structure as a way to delineate those boot protocols.

![armillary-and-commons](https://schultzdavidg-portfolio.s3.us-west-1.amazonaws.com/images/armillary/armillary-and-commons.png)
 
 It organizes all your work into three directories; the idea is, when you add a .gitignored folder into one of these directories, it allows you to interact with it alongside your other work—all from a single access point.
## repos/
Contains your codebases, similar to a monorepo—except everything in here is .gitignored. The benefit of this system is it allows you to separate big-picture context away from the code. More to the point, it gives you access to all your different repositories from the same access point. 
## commons/
This is a repository pattern designed to hold shared knowledge bases—bespoke protocols, wikis, documents, specs, etc. Commons are designed to be extremely agnostic; I have a base template [here](https://github.com/studiozojer/commons/tree/main), but you can structure these however you want. The point of this category is to delineate your shared workspaces with people.

The one thing commons do that they contain your personal ways of working. For example, you might store bespoke, self-improving skills here. These interface with modules.toml (a top-level index that makes sure the harness knows where to find these skills, practices, and protocols).
## models/
Contains your agents, which I lovingly refer to as 'worldmodels'. These folders contain the map to a specific identity's brain. For example:

``` Prompt
> @tycho, can you orient and tell me about how you look at the world?
```

With this prompt, the armillary will route to `armillary/models/tycho/`, which itself contains a CLAUDE.md, a journal, and a unique worldview. To learn more, check out [this guide](https://github.com/studiozojer/commons/blob/main/grow-your-own-model.md).


