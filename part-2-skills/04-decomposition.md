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

Look at this tree. At the top, you have a big task: "Build a bolt calculator app." If you give that to AI as-is, you'll get something. But it probably won't be what you want. The task is too big, too vague, too open to interpretation.

Now look what happens when we decompose it. That big task breaks into medium tasks: input section, calculation engine, results display, and file handling. Each of those breaks into small tasks. The input section becomes "get force value," "get area value," and "validate inputs." The calculation engine becomes "calculate stress," "check against limits," and "determine pass/fail."

These small tasks are perfect for AI. They're specific. They're contained. They have clear inputs and outputs. Each one can be described in a single sentence, and AI can execute each one with near-perfect accuracy.

Think of it like engineering drawings. You don't hand someone a napkin sketch and say "build this building." You provide detailed drawings of each component. AI needs the same level of specificity. The more you break down a problem before asking AI to solve it, the better your results will be.

<div class="key-insight">
<strong>Key Insight:</strong> Big tasks confuse AI. Small tasks get perfect results.
</div>

---

## The One-Sentence Rule

Here's a simple test to know if your task is the right size.

![The Rule](/code-with-ai/assets/images/diagrams/04-2-the-rule.png)
{: .chapter-diagram}
*Figure 4.2: The One-Sentence Rule — The test for right-sized tasks*
{: .diagram-caption}

Ask yourself: "Can I explain this task in ONE sentence?" If you can't, the task is too big—break it down further. If you can, the task is just right—give it to AI.

Consider these two approaches to the same goal. The first says "Build me an app that handles all our bolt calculations with a UI and database and reports." That's not one sentence describing one task—that's a paragraph describing a project. AI will either refuse or produce something unusable.

The second approach says "Create a function that calculates tensile stress from force and area." One sentence. One task. One clear outcome. This is the kind of prompt that gets results.

<div class="key-insight">
<strong>Key Insight:</strong> When you find yourself writing a paragraph to describe what you want, stop. That's a sign you need to decompose first.
</div>

---

## Try It Yourself

Practice breaking down tasks:

- "Create a function that validates an email address" (one task)
- "I want to build a budget tracker" → Break this down: "What are the main parts of a budget tracker?"
- "Create a function that checks if a string contains the @ symbol"
- "Create a function that checks if there's text before and after the @"
- "Combine these checks into a simple email validator"
- "What other checks should a complete email validator have?"

---

## Key Takeaway

Decomposition is the master skill for AI coding. Before you write any prompt, ask yourself: "Is this task small enough?" If you can't describe it in one sentence, break it down. Build your programs from small, single-purpose pieces, and AI will help you assemble them into something powerful.

In the next chapter, we'll focus on making each of those small prompts as precise as possible.

