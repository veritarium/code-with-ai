---
layout: chapter
title: "Feedback"
chapter: 6
part: 2
part_title: "Skills"
part_url: "/part-2-skills/"
prev: "/part-2-skills/05-precision"
prev_title: "Precision"
next: "/part-2-skills/07-context"
next_title: "Context"
---

AI gave you something. It's not quite right. What do you say next?

This is where most beginners fail. They give bad feedback, and then wonder why AI keeps giving them wrong answers.

![Good vs Bad Feedback](/code-with-ai/assets/images/diagrams/06-1-good-vs-bad.png)
{: .chapter-diagram}
*Figure 6.1: Good vs Bad Feedback — What works and what doesn't*
{: .diagram-caption}

## Bad Feedback

**"It doesn't work"** — AI has no idea what's wrong. Doesn't work how? What happened? What did you expect?

**"This is wrong"** — Wrong how? What's the correct behavior?

**"Fix it"** — Fix what? AI will guess, and it will guess wrong.

**"That's not what I wanted"** — Then what DID you want? AI can't read your mind.

## Good Feedback

**"Getting error: TypeError on line 15"** — AI knows exactly where to look.

**"Output is 5, but should be 10"** — AI knows the gap it needs to close.

**"Change the loop to start at 1, not 0"** — AI knows exactly what to change.

**"Add validation: reject negative numbers"** — AI knows the requirement.

See the pattern? Good feedback is specific. It tells AI exactly what's wrong and often suggests what needs to change.

<div class="key-insight">
<strong>Key Insight:</strong> Specific feedback → Specific fixes → Done faster.
</div>

---

## The Feedback Formula

Here's a formula you can use every time AI gives you something that's not quite right:

![The Formula](/code-with-ai/assets/images/diagrams/06-2-the-formula.png)
{: .chapter-diagram}
*Figure 6.2: The Feedback Formula — Got X, Expected Y, Change Z*
{: .diagram-caption}

**"Got [X]. Expected [Y]. Change [Z]."**

Three parts. Complete information. Immediate fix.

**GOT [X]** — What actually happened. The current output, the error message, the current behavior.

**EXPECTED [Y]** — What should happen. The correct output, the desired behavior, the expected result.

**CHANGE [Z]** — What to modify. The specific fix, which part to change. This part is optional but helpful.

### Example

**Got:** "Function returns 15 when given input [1, 2, 3, 4, 5]"

**Expected:** "Should return 120 (the product, not the sum)"

**Change:** "Use multiplication instead of addition in the loop"

Put it together: "The function returns 15 for input [1,2,3,4,5] but should return 120 — it's calculating the sum instead of the product. Change the addition to multiplication in the loop."

AI now has everything it needs. One response, done.

<div class="key-insight">
<strong>Key Insight:</strong> Complete information = One-shot fix.
</div>
