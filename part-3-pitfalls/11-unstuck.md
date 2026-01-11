---
layout: chapter
title: "Getting Unstuck"
chapter: 11
part: 3
part_title: "Problems"
part_url: "/part-3-pitfalls/"
prev: "/part-3-pitfalls/10-debugging"
prev_title: "Debugging"
next: "/part-4-literacy/12-reading"
next_title: "Reading Code"
---

Getting stuck is normal. Recognizing it early saves time.

![Getting Stuck](/code-with-ai/assets/images/diagrams/11-1-the-stuck.png)
{: .chapter-diagram}
*Figure 11.1: The Stuck Loop — Recognize it early*
{: .diagram-caption}

The warning signs are clear: the same error keeps coming back, fixing one thing breaks another, AI gives the same answer repeatedly, you've made more than five attempts without progress, and you're feeling frustrated or confused. These aren't random problems—they're symptoms of being stuck.

What's actually happening underneath varies. You might have the wrong mental model of the problem. You might be missing crucial information. The task might be too complex for a single prompt. You might be solving the wrong problem entirely. Or the AI's context window might be exhausted with too much back-and-forth.

The stuck loop looks like this: TRY → FAIL → TRY AGAIN → SAME FAIL → back to TRY. You're going in circles. Each attempt looks slightly different but you're not actually making progress. The key is recognizing this pattern early instead of grinding through it.

<div class="key-insight">
<strong>Key Insight:</strong> Being stuck is information. It's telling you that your approach needs to change—not your code, your approach.
</div>

---

## Escape Routes

There are six ways to get unstuck. Pick one based on your situation.

![Escape Routes](/code-with-ai/assets/images/diagrams/11-2-escape-routes.png)
{: .chapter-diagram}
*Figure 11.2: Escape Routes — Six ways out*
{: .diagram-caption}

Starting fresh means beginning a new conversation with a new prompt. This clears context clutter and gives you a fresh perspective. Use this when the same error keeps repeating despite multiple fix attempts.

Breaking smaller means splitting the task into smaller pieces. If the task seems impossible, maybe it's actually several tasks pretending to be one. Solve each piece independently, then combine them when they work.

Adding context means sharing more information with AI. Include full error messages, related files, and examples of expected behavior. Use this when AI seems confused about your situation or keeps giving irrelevant suggestions.

Rephrasing means explaining your problem differently. Use different words or focus on a different aspect of the problem. Sometimes AI misunderstands your first explanation and a new way of saying it clicks immediately.

Asking why means getting AI to explain the error instead of just fixing it. Questions like "why is this happening?" and "what causes this?" can reveal understanding you're missing. Use this when you don't understand the error yourself.

Simplifying means making a minimal example that reproduces the problem. Strip the problem to its core—remove everything that isn't essential. If the minimal version works, add complexity back piece by piece until you find what's breaking.

<div class="key-insight">
<strong>Key Insight:</strong> Every problem has an escape route. Stuck doesn't mean defeated—it means you need a different approach.
</div>

---

## Try It Yourself

This example demonstrates getting unstuck by simplifying a complex problem, then rebuilding piece by piece.

Create a file called `getting_unstuck.py`:

```python
# getting_unstuck.py
# Demonstrating escape routes when you're stuck

# ============================================================
# SCENARIO: You're trying to build a data processor that:
# 1. Reads a CSV file
# 2. Filters rows by condition
# 3. Calculates statistics
# 4. Formats output
#
# After 5 attempts, nothing works. Time to apply escape routes!
# ============================================================

def demonstrate_stuck_loop():
    """Show what being stuck looks like"""
    print("=" * 60)
    print("THE STUCK LOOP")
    print("=" * 60)

    print("""
You asked AI to build a data processor.

Attempt 1: "Build a data processor that reads CSV, filters,
           calculates stats, and formats output."
Result: Complex code with multiple bugs.

Attempt 2: "Fix the bugs."
Result: Fixed one bug, created two more.

Attempt 3: "The filter isn't working."
Result: Filter works, but stats calculation breaks.

Attempt 4: "Now the stats are wrong."
Result: Stats work, but output format is broken.

Attempt 5: "Fix the output."
Result: Back to the original bugs!

YOU ARE STUCK. Time to try an escape route.
""")


def escape_route_simplify():
    """Demonstrate the SIMPLIFY escape route"""
    print("\n" + "=" * 60)
    print("ESCAPE ROUTE: SIMPLIFY")
    print("=" * 60)

    print("""
Strategy: Strip to minimum viable version.
Instead of all 4 features, start with just 1.
""")

    # Step 1: Just read data (forget CSV, use hardcoded data)
    print("STEP 1: Can we process hardcoded data?")
    print("-" * 40)

    data = [
        {"name": "Bolt A", "stress": 150, "limit": 200},
        {"name": "Bolt B", "stress": 250, "limit": 200},
        {"name": "Bolt C", "stress": 180, "limit": 200},
    ]
    print(f"Data: {data}")
    print("SUCCESS! We can work with this structure.\n")

    # Step 2: Add filtering
    print("STEP 2: Can we filter this data?")
    print("-" * 40)

    def filter_over_limit(items):
        return [item for item in items if item["stress"] > item["limit"]]

    over_limit = filter_over_limit(data)
    print(f"Over limit: {over_limit}")
    print("SUCCESS! Filtering works.\n")

    # Step 3: Add statistics
    print("STEP 3: Can we calculate statistics?")
    print("-" * 40)

    def calculate_stats(items):
        if not items:
            return {"count": 0, "avg_stress": 0, "max_stress": 0}
        stresses = [item["stress"] for item in items]
        return {
            "count": len(stresses),
            "avg_stress": sum(stresses) / len(stresses),
            "max_stress": max(stresses)
        }

    stats = calculate_stats(data)
    print(f"Stats: {stats}")
    print("SUCCESS! Stats calculation works.\n")

    # Step 4: Add formatting
    print("STEP 4: Can we format output?")
    print("-" * 40)

    def format_report(items, stats):
        report = "STRESS ANALYSIS REPORT\n"
        report += "=" * 30 + "\n"
        for item in items:
            status = "OVER" if item["stress"] > item["limit"] else "OK"
            report += f"{item['name']}: {item['stress']} MPa [{status}]\n"
        report += "-" * 30 + "\n"
        report += f"Average: {stats['avg_stress']:.1f} MPa\n"
        report += f"Maximum: {stats['max_stress']} MPa\n"
        return report

    report = format_report(data, stats)
    print(report)
    print("SUCCESS! Formatting works.\n")

    # Step 5: Now combine them
    print("STEP 5: Combine all working pieces")
    print("-" * 40)

    def process_data(data):
        """Complete data processor built from working pieces"""
        over = filter_over_limit(data)
        stats = calculate_stats(data)
        return {
            "all_data": data,
            "over_limit": over,
            "stats": stats,
            "report": format_report(data, stats)
        }

    result = process_data(data)
    print("Combined function works!")
    print(f"Found {len(result['over_limit'])} items over limit")
    print(f"Average stress: {result['stats']['avg_stress']:.1f} MPa")


def escape_route_add_context():
    """Demonstrate the ADD CONTEXT escape route"""
    print("\n" + "=" * 60)
    print("ESCAPE ROUTE: ADD CONTEXT")
    print("=" * 60)

    print("""
When AI doesn't understand your data format, show examples.

BAD PROMPT:
"Process my CSV file and find errors."

GOOD PROMPT (with context):
"Process my CSV file. Here's the format:

Sample rows:
bolt_id,material,stress_mpa,yield_strength
B001,steel,150,250
B002,aluminum,95,270
B003,steel,280,250

Find rows where stress_mpa exceeds yield_strength.
Return bolt_id and how much it's over the limit."
""")

    # With full context, AI can write:
    def find_failures(csv_data):
        """Function AI would generate with good context"""
        lines = csv_data.strip().split('\n')
        header = lines[0].split(',')

        failures = []
        for line in lines[1:]:
            values = line.split(',')
            row = dict(zip(header, values))

            stress = float(row['stress_mpa'])
            yield_str = float(row['yield_strength'])

            if stress > yield_str:
                failures.append({
                    'bolt_id': row['bolt_id'],
                    'over_by': round(stress - yield_str, 1)
                })

        return failures

    sample_csv = """bolt_id,material,stress_mpa,yield_strength
B001,steel,150,250
B002,aluminum,95,270
B003,steel,280,250
B004,steel,260,250"""

    print("Result with proper context:")
    failures = find_failures(sample_csv)
    for f in failures:
        print(f"  {f['bolt_id']}: {f['over_by']} MPa over limit")


def escape_route_ask_why():
    """Demonstrate the ASK WHY escape route"""
    print("\n" + "=" * 60)
    print("ESCAPE ROUTE: ASK WHY")
    print("=" * 60)

    print("""
Instead of "Fix this error", ask "Why is this happening?"

ERROR: KeyError: 'stress'

BAD: "Fix the KeyError"
Result: AI adds try/except, hiding the real problem

GOOD: "Why am I getting KeyError: 'stress'? Here's my code
      and sample data."

AI EXPLAINS:
"The KeyError occurs because your CSV has 'stress_mpa' as
the column name, but your code is looking for 'stress'.

The data shows: bolt_id,material,stress_mpa,yield_strength
Your code uses: row['stress']
Should be: row['stress_mpa']"

Now you understand the root cause, not just a band-aid fix!
""")


def demonstrate_decision_guide():
    """Show which escape route to use when"""
    print("\n" + "=" * 60)
    print("ESCAPE ROUTE DECISION GUIDE")
    print("=" * 60)

    guide = [
        ("Same error repeating", "START FRESH", "New conversation clears context"),
        ("Task seems impossible", "BREAK SMALLER", "Solve one piece at a time"),
        ("AI seems confused", "ADD CONTEXT", "Share more details and examples"),
        ("Miscommunication", "REPHRASE", "Explain differently"),
        ("Don't understand error", "ASK WHY", "Get explanation first"),
        ("Too many variables", "SIMPLIFY", "Strip to minimum, rebuild"),
    ]

    print(f"\n{'Situation':<25} {'Escape Route':<15} {'Why It Helps'}")
    print("-" * 70)
    for situation, route, reason in guide:
        print(f"{situation:<25} {route:<15} {reason}")


# ============================================================
# RUN ALL DEMONSTRATIONS
# ============================================================

if __name__ == "__main__":
    demonstrate_stuck_loop()
    escape_route_simplify()
    escape_route_add_context()
    escape_route_ask_why()
    demonstrate_decision_guide()

    print("\n" + "=" * 60)
    print("KEY LESSONS")
    print("=" * 60)
    print("""
1. Recognize when you're stuck (same error repeating, no progress)
2. Stop pushing the same approach harder
3. Pick an escape route based on your situation
4. SIMPLIFY is often the most powerful: strip down, rebuild

Being stuck is not failure - it's information telling you
to change your approach. The best developers get stuck too.
They just recognize it faster and know how to escape.
""")
```

Run it:

```bash
python getting_unstuck.py
```

**Expected Output:**

```
============================================================
THE STUCK LOOP
============================================================

You asked AI to build a data processor.

Attempt 1: "Build a data processor that reads CSV, filters,
           calculates stats, and formats output."
Result: Complex code with multiple bugs.

...

============================================================
ESCAPE ROUTE: SIMPLIFY
============================================================

Strategy: Strip to minimum viable version.
Instead of all 4 features, start with just 1.

STEP 1: Can we process hardcoded data?
----------------------------------------
Data: [{'name': 'Bolt A', 'stress': 150, 'limit': 200}, ...]
SUCCESS! We can work with this structure.

...

============================================================
ESCAPE ROUTE DECISION GUIDE
============================================================

Situation                 Escape Route    Why It Helps
----------------------------------------------------------------------
Same error repeating      START FRESH     New conversation clears context
Task seems impossible     BREAK SMALLER   Solve one piece at a time
AI seems confused         ADD CONTEXT     Share more details and examples
Miscommunication          REPHRASE        Explain differently
Don't understand error    ASK WHY         Get explanation first
Too many variables        SIMPLIFY        Strip to minimum, rebuild

============================================================
KEY LESSONS
============================================================

1. Recognize when you're stuck (same error repeating, no progress)
2. Stop pushing the same approach harder
3. Pick an escape route based on your situation
4. SIMPLIFY is often the most powerful: strip down, rebuild
...
```

The SIMPLIFY approach is especially powerful. By building each piece independently and verifying it works before adding complexity, you isolate problems instead of chasing them through tangled code.

---

## Key Takeaway

Getting stuck happens to everyone. The skill is recognizing it early and choosing an escape route. If you've tried five times with no progress, stop. Ask yourself: Should I start fresh? Break smaller? Add context? Rephrase? Ask why? Simplify? One of these will get you moving again. Stuck is temporary when you have strategies to escape.

In Part 4, we'll develop your code literacy—the ability to read and understand code even when you didn't write it.

