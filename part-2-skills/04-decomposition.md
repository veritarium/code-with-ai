---
layout: chapter
title: "Decomposition"
chapter: 4
part: 2
part_title: "Skills"
part_url: "/part-2-skills/"
prev: "/part-1-foundations/03-operations"
prev_title: "Six Operations"
next: "/part-2-skills/05-precision"
next_title: "Precision"
---

This is the single most important skill for coding with AI: breaking big things into small things.

![Decomposition](/code-with-ai/assets/images/diagrams/04-1-decomposition.png)
{: .chapter-diagram}
*Figure 4.1: Decomposition — Breaking big tasks into AI-sized pieces*
{: .diagram-caption}

Look at this tree. At the top, you have a big task: "Build a bolt calculator app."

If you give that to AI, you'll get something. But it probably won't be what you want. The task is too big, too vague, too open to interpretation.

Now look what happens when we decompose it.

That big task breaks into medium tasks:
- Input section
- Calculation engine
- Results display
- File handling

Each of those breaks into small tasks:
- Input section → Get force value, Get area value, Validate inputs
- Calculation engine → Calculate stress, Check against limits, Determine pass/fail

These small tasks are *perfect* for AI. They're specific. They're contained. They have clear inputs and outputs.

<div class="key-insight">
<strong>Key Insight:</strong> Big tasks confuse AI. Small tasks get perfect results.
</div>

Think of it like engineering drawings. You don't hand someone a napkin sketch and say "build this building." You provide detailed drawings of each component. AI needs the same thing.

---

## The One-Sentence Rule

Here's a simple test to know if your task is the right size.

![The Rule](/code-with-ai/assets/images/diagrams/04-2-the-rule.png)
{: .chapter-diagram}
*Figure 4.2: The One-Sentence Rule — The test for right-sized tasks*
{: .diagram-caption}

Ask yourself: **"Can I explain this task in ONE sentence?"**

If NO — the task is too big. Break it down further.

If YES — the task is just right. Give it to AI.

**TOO BIG:** "Build me an app that handles all our bolt calculations with a UI and database and reports"

That's not one sentence describing one task. That's a paragraph describing a project.

**JUST RIGHT:** "Create a function that calculates tensile stress from force and area"

One sentence. One task. One clear outcome.

More examples of right-sized tasks:
- "Write a function that reads a CSV file and returns a list of values"
- "Add error handling to reject negative numbers"
- "Create a loop that processes each row in the data"

Each of these can be explained in one sentence. Each will get you good results from AI.

<div class="key-insight">
<strong>Key Insight:</strong> When you find yourself writing a paragraph to describe what you want, stop. That's a sign you need to decompose first.
</div>
