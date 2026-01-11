---
layout: chapter
title: "The Loop"
chapter: 2
part: 1
part_title: "Foundations"
part_url: "/part-1-foundations/"
prev: "/part-1-foundations/01-core"
prev_title: "The Core Partnership"
next: "/part-1-foundations/03-operations"
next_title: "Six Operations"
---

This is how every coding session with AI actually works. Memorize this loop.

![The Loop](/code-with-ai/assets/images/diagrams/02-1-the-loop.png)
{: .chapter-diagram}
*Figure 2.1: The Loop — Describe, Get, Run, Evaluate, Repeat*
{: .diagram-caption}

**DESCRIBE** — You tell AI what you want. "Create a function that calculates bolt stress from force and area."

**GET** — AI gives you code. It might be perfect. It probably won't be.

**RUN** — You actually run the code. Not just look at it. Run it. See what happens.

**EVALUATE** — Does it work? Does it do what you wanted? This is where your engineering judgment matters. AI doesn't know if the output makes sense for your application — you do.

Then you make a decision: **Done or Refine?**

If it works, you're done. Move on.

If it doesn't work, you go back to DESCRIBE with more information. "The function works but it's returning negative values when force is negative. Add validation to reject negative inputs."

This loop might run once. It might run ten times. That's normal. Every professional developer works this way — the only difference is they've done more loops.

<div class="key-insight">
<strong>Key Insight:</strong> Every problem is solvable through iteration. You don't need to get it right the first time. You need to keep going until it's right.
</div>

---

## The Draft Mindset

Here's what most beginners get wrong: they expect perfection on the first try.

![The Draft](/code-with-ai/assets/images/diagrams/02-2-the-draft.png)
{: .chapter-diagram}
*Figure 2.2: The Draft — Progress through iteration*
{: .diagram-caption}

Look at this progression. Version 1 is maybe 10% of what you want. It's rough. It might not even run.

That's fine. That's the *draft*.

Version 2 gets you to 40%. Now the basic structure works. Maybe the output format is wrong.

Version 3 is at 75%. It's doing the right calculation but doesn't handle edge cases.

Version 4 is at 100%. It works. Ship it.

<div class="key-insight">
<strong>Key Insight:</strong> Treat AI output like a first draft, not a final answer.
</div>

When you write an engineering report, do you expect the first draft to be perfect? No. You write, review, revise, repeat.

Code works the same way. The first output from AI is a starting point. Your job is to test it, identify what's wrong, and guide the refinement.

This mindset shift is crucial. Stop asking "why didn't AI give me perfect code?" and start asking "what do I need to tell AI to make this better?"
