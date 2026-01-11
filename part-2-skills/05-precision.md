---
layout: chapter
title: "Precision"
chapter: 5
part: 2
part_title: "Skills"
part_url: "/part-2-skills/"
prev: "/part-2-skills/04-decomposition"
prev_title: "Decomposition"
next: "/part-2-skills/06-feedback"
next_title: "Feedback"
---

Not all prompts are equal. There's a spectrum from vague to precise, and where you land on that spectrum determines your success rate.

![The Spectrum](/code-with-ai/assets/images/diagrams/05-1-the-spectrum.png)
{: .chapter-diagram}
*Figure 5.1: The Spectrum — From vague to precise*
{: .diagram-caption}

Look at this gradient bar. On the left, in red: VAGUE. On the right, in blue: PRECISE.

**VAGUE: "Help me with calculations"**
Success rate: maybe 20%. AI has no idea what calculations. What inputs? What outputs? What domain? It will guess, and it will probably guess wrong.

**MEDIUM: "Write a stress calculation function"**
Success rate: around 50%. Better. AI knows the domain now. But what kind of stress? What inputs does the function take? What should it return?

**PRECISE: "Write a Python function called calculate_tensile_stress that takes force in Newtons and area in square millimeters, returns stress in MPa, and raises an error if either input is negative"**
Success rate: 90%+. AI knows exactly what to build. The function name, the inputs, the output, the units, the error handling — it's all specified.

<div class="key-insight">
<strong>Key Insight:</strong> More specific prompts = Fewer iterations = Better results.
</div>

Yes, writing precise prompts takes more time upfront. But it saves enormous time in the loop. Would you rather spend 2 minutes writing a good prompt and get working code, or spend 30 seconds on a vague prompt and then 20 minutes trying to fix what AI gives you?

---

## Five Components of a Good Prompt

Here's a framework for building precise prompts. Five components.

![Five Components](/code-with-ai/assets/images/diagrams/05-2-five-components.png)
{: .chapter-diagram}
*Figure 5.2: Five Components — The framework for precise prompts*
{: .diagram-caption}

**WHAT** — The action you want. "Create a function" or "Fix this error" or "Explain this code"

**WHERE** — The location or context. "In the utils.py file" or "In the calculate function" or "For this data structure"

**HOW** — The method or approach. "Using a for loop" or "With error handling" or "Using the pandas library"

**WHY** — The purpose. "To improve performance" or "For user validation" or "To match the existing code style"

**EXAMPLE** — Show what you expect. "Input: [1,2,3], Output: 6" or "Like this existing function but for temperature"

You don't always need all five. But the more you include, the better your results.

### Building a Complete Prompt

**WHAT:** "Create a function"
**WHERE:** "in utils.py"
**HOW:** "using recursion"
**WHY:** "to calculate factorials for the stats module"
**EXAMPLE:** "factorial(5) should return 120"

Put it together: "Create a function in utils.py using recursion to calculate factorials for the stats module. Example: factorial(5) should return 120."

That's a precise prompt. AI will nail it on the first try.
