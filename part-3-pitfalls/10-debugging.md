---
layout: chapter
title: "Debugging"
chapter: 10
part: 3
part_title: "Problems"
part_url: "/part-3-pitfalls/"
prev: "/part-3-pitfalls/09-traps"
prev_title: "Common Pitfalls"
next: "/part-3-pitfalls/11-unstuck"
next_title: "Getting Unstuck"
---

Your code doesn't work. Here's the systematic approach to fixing it.

![The Debugging Flow](/code-with-ai/assets/images/diagrams/10-1-the-debugging.png)
{: .chapter-diagram}
*Figure 10.1: The Debugging Flow — A systematic approach*
{: .diagram-caption}

**Step 1: CAPTURE** — Copy the exact error message. All of it. Not a summary, the actual text.

**Step 2: LOCATE** — Find the problem line. Error messages usually tell you where.

**Step 3: CONTEXT** — Include the surrounding code. AI needs to see what's happening around the error.

**Step 4: ASK** — Send to AI with all this context.

**Step 5: APPLY** — Make the fix.

**Step 6: TEST** — Run it again. Verify it's actually fixed.

## Bad vs Good Debug Requests

**BAD:** "My code doesn't work, fix it"
- Missing: error message
- Missing: which line fails
- Missing: relevant code
- Missing: what it should do
- Result: AI will guess wrong

**GOOD:** "Error: TypeError on line 15. Here's lines 10-20: [code]. Input was: [1, 2, None]. Expected: sum of numbers. Should skip None values."
- Has: exact error
- Has: location
- Has: code context
- Has: input data
- Has: expected behavior
- Result: Precise fix provided

<div class="key-insight">
<strong>Key Insight:</strong> Better information in = Better fix out.
</div>

---

## Error Types

Understanding error types helps you describe them better to AI.

![Error Types](/code-with-ai/assets/images/diagrams/10-2-error-types.png)
{: .chapter-diagram}
*Figure 10.2: Error Types — Know your errors*
{: .diagram-caption}

**SYNTAX ERROR** — Code can't even run.
Examples: Missing brackets, typos, wrong indentation.
Tell AI: "Syntax error on line X: [error message]"
Difficulty: Easiest. Usually one character or line to fix.

**RUNTIME ERROR** — Code runs but crashes midway.
Examples: Division by zero, null access, file not found.
Tell AI: "Crashes at line X with [error]. Input was [data]."
Difficulty: Medium. Need to understand what triggered it.

**LOGIC ERROR** — Code runs but gives wrong result.
Examples: Wrong calculation, off-by-one, wrong condition.
Tell AI: "Got [X], expected [Y]. Here's the code."
Difficulty: Hardest. No error message to guide you.

### What to Include for Each Error Type

| Error Type | Must Include | Also Helpful |
|------------|--------------|--------------|
| Syntax | Error message, line number | Few lines around error |
| Runtime | Error message, traceback, input | Full function, what triggers it |
| Logic | Actual output, expected output, code | Test cases, what it should do |

<div class="key-insight">
<strong>Key Insight:</strong> Name the error type = Faster fix.
</div>
