---
layout: chapter
title: "When to Restart"
chapter: 8
part: 2
part_title: "Skills"
part_url: "/part-2-skills/"
prev: "/part-2-skills/07-context"
prev_title: "Context"
next: "/part-3-pitfalls/09-traps"
next_title: "Common Pitfalls"
---

Sometimes you need to know when to stop refining and start fresh.

![The Decision](/code-with-ai/assets/images/diagrams/08-1-the-decision.png)
{: .chapter-diagram}
*Figure 8.1: The Decision — Refine or restart?*
{: .diagram-caption}

Here's a simple decision tree. AI gave you output that isn't right. Ask yourself: "Is it close to what I want?"

If yes, **REFINE**. Give feedback, iterate, build on what you have. The structure is correct but there are small bugs or typos. Maybe it's missing one feature. Perhaps the style needs adjustment or the logic is correct but incomplete. These problems are worth fixing in place.

If no, **RESTART**. New conversation, new prompt, fresh start. The approach is wrong entirely. AI missed the point of your request. There are multiple fundamental problems that would need a complete rewrite. You're going in circles with the same errors repeating.

The sunk cost fallacy is strong here. You've invested time in this conversation, and it feels wasteful to abandon it. But sometimes the fastest path to working code is to start over with everything you've learned.

<div class="key-insight">
<strong>Key Insight:</strong> Starting fresh isn't failure. It's efficiency.
</div>

---

## The 5-Attempt Rule

Here's a practical rule: five attempts maximum, then restart.

![The 5-Attempt Rule](/code-with-ai/assets/images/diagrams/08-2-the-5-attempt-rule.png)
{: .chapter-diagram}
*Figure 8.2: The 5-Attempt Rule — Know when to cut losses*
{: .diagram-caption}

Attempt 1 is your initial prompt—just try and see what happens. Attempt 2 refines by adding more specifics and clarifying what's wrong. Attempt 3 adjusts by fixing errors and trying different wording. Attempt 4 rephrases with a different approach or new angle on the problem. Attempt 5 is your last try, incorporating everything you've learned.

If you're still not there after five attempts, restart. New conversation, better prompt, fresh context.

Why five? Too few attempts (1-2) means giving up too early—you might be one piece of information away from the solution. Just right (3-5) gives enough attempts to find solutions without wasting time. Too many attempts (6+) hit diminishing returns—context gets cluttered and you start going in circles.

The beautiful thing about restarting is you're not starting from zero. You now know what doesn't work. Your second attempt will be better because your first attempt taught you something.

<div class="key-insight">
<strong>Key Insight:</strong> 5 attempts max, then start fresh with what you learned.
</div>

---

## Try It Yourself

Practice knowing when to restart:

- After 3 failed attempts: "Let me try a completely different approach. Instead of X, let's try Y."
- "Forget the previous code. Here's what I actually need: [clearer description]"
- "The loop approach isn't working. Can you solve this using list comprehension instead?"
- "Start fresh: I need a function that does X. Here's an example of input and expected output."
- "New approach: instead of processing all at once, let's do it in batches of 100"

---

## Key Takeaway

Don't let sunk cost keep you stuck. If you've made five attempts and you're still not close, restart. Take what you learned—what the data looks like, what doesn't work, what edge cases exist—and write a better prompt from scratch. A fresh start with knowledge beats endless iteration on a broken foundation.

In Part 3, we'll look at the common pitfalls that trip up beginners and how to avoid them.

