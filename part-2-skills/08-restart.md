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

This example simulates a restart scenario. We'll show a failing approach and then a successful fresh start with lessons learned.

Create a file called `restart_strategy.py`:

```python
# restart_strategy.py
# Demonstrating when to restart vs. when to refine

# === SCENARIO: Parse sensor data from a file ===

# ATTEMPT 1-5: Kept trying to fix a fundamentally flawed approach
# The original code tried to use regex for everything
# Each "fix" created new problems

def parse_sensor_data_bad_approach(data_string):
    """
    Bad approach: Over-complicated regex parsing

    This represents 5 failed attempts where each fix
    broke something else. Time to restart!
    """
    import re
    # Attempt 1: Basic regex - missed timestamps
    # Attempt 2: Added timestamp regex - broke value parsing
    # Attempt 3: Fixed value parsing - failed on negative numbers
    # Attempt 4: Fixed negatives - broke on missing values
    # Attempt 5: Added optional handling - became unreadable mess

    pattern = r'(\d{4}-\d{2}-\d{2}T\d{2}:\d{2}:\d{2})?\s*sensor_(\d+):\s*(-?\d+\.?\d*)?'

    results = []
    for match in re.finditer(pattern, data_string):
        # This is getting too complicated...
        timestamp = match.group(1) or "unknown"
        sensor_id = match.group(2)
        value = match.group(3)
        if value:
            results.append({
                'timestamp': timestamp,
                'sensor': f'sensor_{sensor_id}',
                'value': float(value)
            })
    return results


# RESTART: Fresh approach after learning from failures
# Lessons learned:
# 1. Data has consistent structure - don't need regex
# 2. Split by lines, then parse each field
# 3. Handle errors per-line, not globally

def parse_sensor_data_fresh_start(data_string):
    """
    Fresh approach: Simple line-by-line parsing

    After 5 failed attempts with regex, started fresh.
    Simpler approach works better for structured data.
    """
    results = []
    errors = []

    for line_num, line in enumerate(data_string.strip().split('\n'), 1):
        line = line.strip()

        # Skip empty lines and comments
        if not line or line.startswith('#'):
            continue

        # Split line into parts
        parts = line.split(',')

        if len(parts) != 3:
            errors.append(f"Line {line_num}: Expected 3 fields, got {len(parts)}")
            continue

        timestamp, sensor_id, value_str = [p.strip() for p in parts]

        # Parse value with error handling
        try:
            value = float(value_str)
        except ValueError:
            errors.append(f"Line {line_num}: Invalid value '{value_str}'")
            continue

        results.append({
            'timestamp': timestamp,
            'sensor': sensor_id,
            'value': value
        })

    return {'data': results, 'errors': errors}


# === Demonstrate the difference ===
if __name__ == "__main__":
    # Sample sensor data
    sensor_data = """
    # Sensor readings from process monitor
    2024-01-15T10:30:00, sensor_1, 23.5
    2024-01-15T10:30:00, sensor_2, -5.2
    2024-01-15T10:30:01, sensor_1, 24.1
    2024-01-15T10:30:01, sensor_3, 100.0
    2024-01-15T10:30:02, sensor_2, ERR
    2024-01-15T10:30:02, sensor_1, 23.8
    """

    print("RESTART STRATEGY DEMONSTRATION")
    print("=" * 60)

    print("\nATTEMPTS 1-5: Regex approach (kept breaking)")
    print("-" * 60)
    print("Attempt 1: Basic regex - missed timestamps")
    print("Attempt 2: Fixed timestamps - broke value parsing")
    print("Attempt 3: Fixed values - failed on negatives")
    print("Attempt 4: Fixed negatives - broke on missing values")
    print("Attempt 5: Added optional matching - unreadable mess")
    print("\nResult after 5 attempts:")
    bad_result = parse_sensor_data_bad_approach(sensor_data)
    print(f"Parsed {len(bad_result)} records (should be 5 valid)")
    print("Still buggy, hard to maintain, time to RESTART!")

    print("\n" + "=" * 60)
    print("FRESH START: Simple line-by-line parsing")
    print("-" * 60)
    print("Lessons applied:")
    print("  1. Data is structured - don't need regex")
    print("  2. Parse line by line for clarity")
    print("  3. Handle errors individually")

    good_result = parse_sensor_data_fresh_start(sensor_data)

    print(f"\nSuccessfully parsed {len(good_result['data'])} records:")
    for record in good_result['data']:
        print(f"  {record['timestamp']} | {record['sensor']} | {record['value']}")

    if good_result['errors']:
        print(f"\nHandled {len(good_result['errors'])} error(s):")
        for error in good_result['errors']:
            print(f"  {error}")

    print("\n" + "=" * 60)
    print("OUTCOME:")
    print("  Bad approach: 5 attempts, still broken")
    print("  Fresh start:  1 attempt, working code")
    print("  Total time saved by restarting: ~80%")
    print("=" * 60)

    # Verify the results
    print("\nVERIFICATION:")
    assert len(good_result['data']) == 5, "Should parse 5 valid records"
    assert len(good_result['errors']) == 1, "Should catch 1 error (ERR value)"
    assert good_result['data'][1]['value'] == -5.2, "Should handle negative numbers"
    print("All assertions passed!")
```

Run it:

```bash
python restart_strategy.py
```

**Expected Output:**

```
RESTART STRATEGY DEMONSTRATION
============================================================

ATTEMPTS 1-5: Regex approach (kept breaking)
------------------------------------------------------------
Attempt 1: Basic regex - missed timestamps
Attempt 2: Fixed timestamps - broke value parsing
Attempt 3: Fixed values - failed on negatives
Attempt 4: Fixed negatives - broke on missing values
Attempt 5: Added optional matching - unreadable mess

Result after 5 attempts:
Parsed 0 records (should be 5 valid)
Still buggy, hard to maintain, time to RESTART!

============================================================
FRESH START: Simple line-by-line parsing
------------------------------------------------------------
Lessons applied:
  1. Data is structured - don't need regex
  2. Parse line by line for clarity
  3. Handle errors individually

Successfully parsed 5 records:
  2024-01-15T10:30:00 | sensor_1 | 23.5
  2024-01-15T10:30:00 | sensor_2 | -5.2
  2024-01-15T10:30:01 | sensor_1 | 24.1
  2024-01-15T10:30:01 | sensor_3 | 100.0
  2024-01-15T10:30:02 | sensor_1 | 23.8

Handled 1 error(s):
  Line 7: Invalid value 'ERR'

============================================================
OUTCOME:
  Bad approach: 5 attempts, still broken
  Fresh start:  1 attempt, working code
  Total time saved by restarting: ~80%
============================================================

VERIFICATION:
All assertions passed!
```

Five attempts with the wrong approach produced nothing but frustration. One attempt with a fresh approach—informed by what we learned—produced working code immediately. That's the power of knowing when to restart.

---

## Key Takeaway

Don't let sunk cost keep you stuck. If you've made five attempts and you're still not close, restart. Take what you learned—what the data looks like, what doesn't work, what edge cases exist—and write a better prompt from scratch. A fresh start with knowledge beats endless iteration on a broken foundation.

In Part 3, we'll look at the common pitfalls that trip up beginners and how to avoid them.

