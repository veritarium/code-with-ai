---
layout: chapter
title: "Context"
chapter: 7
part: 2
part_title: "Skills"
part_url: "/part-2-skills/"
prev: "/part-2-skills/06-feedback"
prev_title: "Feedback"
next: "/part-2-skills/08-restart"
next_title: "When to Restart"
---

This concept will change how you work with AI.

![The Window](/code-with-ai/assets/images/diagrams/07-1-the-window.png)
{: .chapter-diagram}
*Figure 7.1: The Window — AI only sees what's in the prompt*
{: .diagram-caption}

Look at this diagram. The large box is YOUR WORLD — everything you know about your project, your history, your requirements, your preferences.

The small box inside is AI'S WINDOW — what AI can actually see.

<div class="key-insight">
<strong>Key Insight:</strong> AI only sees what's in the prompt.
</div>

AI cannot see your screen. It cannot access your files. It doesn't remember your past conversations. It doesn't know your project. It cannot read your mind.

Unless you tell it.

All that stuff floating outside the window — your project history, other files, business requirements, team coding standards, past conversations, your preferences, why you're doing this — AI has no access to any of it.

This is why vague prompts fail. You're assuming AI has context it doesn't have.

**SO YOU MUST:**
- Paste relevant code
- Share error messages
- Explain constraints
- Give context
- State requirements

Make the window bigger. The more context you share, the better AI understands. It's that simple.

---

## What to Share

There are five types of context that dramatically improve AI results.

![What to Share](/code-with-ai/assets/images/diagrams/07-2-what-to-share.png)
{: .chapter-diagram}
*Figure 7.2: What to Share — Five types of context*
{: .diagram-caption}

**1. CONSTRAINTS** — Limitations and requirements.
- "Must work in Python 3.8"
- "No external libraries"
- "Max 100 lines of code"

**2. PREFERENCES** — Style and approach choices.
- "Use descriptive variable names"
- "Add comments for complex logic"
- "Prefer simple over clever"

**3. HISTORY** — What led to this point.
- "We tried X but it failed because..."
- "This is part of a larger system"
- "Previous version had this bug..."

**4. ERRORS** — Exact error messages and symptoms.
- "TypeError: 'NoneType' has no len()"
- "Happens when input is empty list"
- "Line 42 in process_data function"

**5. FILES** — Relevant code and data.
- "Here's the current function: [code]"
- "Sample input data: [data]"
- "Related config file: [config]"

### Before Sending a Prompt

Run through this checklist:
- Did I share relevant constraints?
- Did I mention my preferences?
- Did I explain the history/context?
- Did I include error messages?
- Did I paste the relevant code/files?

<div class="key-insight">
<strong>Key Insight:</strong> More context = Fewer iterations = Better results.
</div>
