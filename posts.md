---
title: How I think about system design
tags: programming, thinking
---

System design is less about knowing the right answers and more about knowing which questions to ask first. Most engineers, when given a design problem, jump immediately to solutions. The instinct is understandable — solutions feel productive. But a solution without a well-understood problem is just a guess with extra steps.

The questions that matter most are almost always the boring ones. How many users? How often does the data change? What happens if this part fails? What does "working" actually mean here? These aren't exciting questions. They don't make you sound smart in interviews. But they are the ones that determine whether your system survives contact with reality.

> A system that handles the boring cases well is more valuable than one that handles the interesting cases brilliantly.

**Start with constraints, not components**

The temptation is to start drawing boxes — a load balancer here, a cache there, a message queue just in case. Resist this. Start with constraints. Constraints are the shape of the problem. Components are just tools you pick once you understand the shape.

```
// Wrong starting point
System → Load Balancer → App Servers → Database

// Right starting point
- 10M users, 90% read-heavy
- Data must be consistent within 500ms
- Budget: $X/month
- Team size: 4 engineers
```

The second version tells you which tools are even worth considering. The first is just a diagram that could apply to anything.

**On simplicity**

The best systems I have seen are boring. They use well-understood components, make obvious tradeoffs, and optimise for the team's ability to understand and change them. The worst systems are clever. They use novel approaches, make non-obvious tradeoffs, and optimise for the designer's ego.

Simple systems fail in simple ways. You can reason about them. You can fix them at 3am when something goes wrong. That is worth more than elegance.

---
title: What nobody tells you about learning to program
tags: programming, learning
---

Everyone who learned to program remembers the moment it clicked. What they don't tell you is that the clicking never stops — you just get better at sitting with the not-yet-clicked feeling without panicking.

The first year of programming is mostly learning to read error messages without your heart rate spiking. The second year is learning that the error message is usually lying to you about where the actual problem is. The third year is when you start to find this funny.

**The thing about tutorials**

Tutorials are maps, not territory. They show you a path that someone else took through a problem that has already been solved. This is useful for learning the landscape. It is useless for learning to navigate.

At some point you have to close the tutorial and build something that does not have an answer key. This is uncomfortable. It is also the only way to actually learn.

> You do not really understand something until you have been stuck on it for two hours and figured it out yourself.

**On feeling behind**

Every programmer feels behind. Senior engineers feel behind. People who built the tools you use feel behind. The field moves fast enough that being current is a full-time job on top of your actual full-time job.

The useful reframe: you are not behind. You are at a particular point in a journey that does not have a finish line. The goal is not to catch up. The goal is to keep moving and find the parts that interest you enough to go deep.

```python
# The code you write at year 1
def get_user(id):
    for user in users:
        if user.id == id:
            return user

# The code you write at year 3
def get_user(id):
    return user_map.get(id)  # O(1) vs O(n), built the map once

# What you think at year 5
# Was the map worth the memory? How many users? How often does this run?
```

The questions change more than the code does.

---
title: Notes on writing clearly
tags: writing, thinking
---

The hardest thing about writing clearly is that it requires thinking clearly first. Most writing problems are thinking problems in disguise. When a sentence won't come out right, the usual cause is not a vocabulary problem or a grammar problem — it is that you do not yet know what you are trying to say.

The fix is not to try harder to write the sentence. The fix is to stop and ask: what am I actually trying to say here? Say it out loud if you have to. The spoken version is almost always clearer than the written one, because speaking forces you to commit.

**On the first draft**

The first draft exists to find out what you think. It is not a document, it is a conversation with yourself. Give yourself permission to write badly in it. The only thing the first draft has to do is exist.

Revision is where writing actually happens. The first draft is just thinking out loud with your fingers.

**On clarity vs simplicity**

These are not the same thing. A simple sentence can be unclear. A complex sentence can be perfectly clear. What you are aiming for is *precision* — the sentence says exactly what you mean and nothing else.

> Clear writing is not about short words and short sentences. It is about sentences where every word is doing work.

Cut words that are not doing work. Not because short is better, but because dead weight obscures the words that matter.
