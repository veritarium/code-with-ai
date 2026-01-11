---
layout: chapter
title: "Common Pitfalls"
chapter: 9
part: 3
part_title: "Problems"
part_url: "/part-3-pitfalls/"
prev: "/part-2-skills/08-restart"
prev_title: "When to Restart"
next: "/part-3-pitfalls/10-debugging"
next_title: "Debugging"
---

Let's talk about mistakes. Every beginner makes these. Now you won't.

![Common Traps](/code-with-ai/assets/images/diagrams/09-1-common-traps.png)
{: .chapter-diagram}
*Figure 9.1: Common Traps — Mistakes everyone makes*
{: .diagram-caption}

**TRAP 1: BLIND TRUST**
Running code without reading it. AI-generated code can have bugs, security issues, or just not do what you think.
*Fix: Always review before running. Ask AI to explain what the code does.*

**TRAP 2: VAGUE PROMPTS**
"Make it better" or "Fix this" — AI will guess what you mean, usually wrong.
*Fix: Be specific about what's wrong. State expected vs actual behavior.*

**TRAP 3: TOO BIG TASKS**
"Build me a whole app" — Too much at once. AI loses focus, you lose control.
*Fix: Break into small tasks. One feature at a time.*

**TRAP 4: NO CONTEXT**
Not sharing error messages or relevant code. AI is working blind.
*Fix: Paste errors, include code, share the context.*

**TRAP 5: GIVING UP TOO FAST**
First attempt didn't work, quit. But you were maybe one iteration away.
*Fix: Give 3-5 attempts. Iterate and refine.*

**TRAP 6: NOT LEARNING**
Copy-paste without understanding. You never build skills this way.
*Fix: Ask AI to explain. Learn from each solution.*

<div class="key-insight">
<strong>Key Insight:</strong> Most traps come from treating AI like magic instead of a tool. Stay engaged, stay specific, stay curious.
</div>

---

## Trust Levels

How much should you trust AI's output? It depends on the consequences of failure.

![Trust Levels](/code-with-ai/assets/images/diagrams/09-2-trust-levels.png)
{: .chapter-diagram}
*Figure 9.2: Trust Levels — How much verification is needed*
{: .diagram-caption}

**LOW TRUST — Verify Everything**

When: Security-related code, financial calculations, safety-critical systems, data deletion operations.

Action: Read every line. Test thoroughly. Get a second opinion. Understand fully.

**MEDIUM TRUST — Review and Test**

When: Standard features, business logic, API integrations, database operations.

Action: Skim the code. Run basic tests. Check edge cases. Verify behavior.

**HIGH TRUST — Quick Check**

When: Simple utilities, formatting code, text manipulation, documentation.

Action: Glance at output. Run once. Check it works. Move on.

<div class="key-insight">
<strong>Key Insight:</strong> Trust level depends on consequences of failure, not AI confidence.
</div>

AI might be very confident about code that deletes your database. That doesn't mean you should trust it blindly.

For a bolt stress calculator in a real engineering application? Low trust. Verify everything.

For a script that renames files in a folder? Higher trust. Quick check.

**Higher stakes = More verification needed.**
