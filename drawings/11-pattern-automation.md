# 11: Pattern — Automation

```
╔══════════════════════════════════════════════════════════════════════════════╗
║                                                                              ║
║                         PATTERN: AUTOMATION                                  ║
║                                                                              ║
║   Use this pattern when: Eliminating repetitive manual tasks                 ║
║                                                                              ║
║  ┌──────────────────────────────────────────────────────────────────────┐    ║
║  │                                                                      │    ║
║  │   ┌─────────────┐         ┌─────────────┐         ┌─────────────┐    │    ║
║  │   │             │         │             │         │             │    │    ║
║  │   │   TRIGGER   │────────►│   ACTION    │────────►│   OUTPUT    │    │    ║
║  │   │             │         │             │         │             │    │    ║
║  │   └─────────────┘         └─────────────┘         └─────────────┘    │    ║
║  │                                                                      │    ║
║  │   When X happens          Do Y                    Produce Z          │    ║
║  │                                                                      │    ║
║  └──────────────────────────────────────────────────────────────────────┘    ║
║                                                                              ║
║  ═══════════════════════════════════════════════════════════════════════     ║
║                                                                              ║
║   TRIGGER TYPES:                                                             ║
║                                                                              ║
║   ┌─────────────────────────────────────────────────────────────────────┐    ║
║   │                                                                     │    ║
║   │   ┌───────────┐    ┌───────────┐    ┌───────────┐    ┌───────────┐ │    ║
║   │   │   TIME    │    │   FILE    │    │   EVENT   │    │  MANUAL   │ │    ║
║   │   │           │    │           │    │           │    │           │ │    ║
║   │   │ "Every    │    │ "When new │    │ "When     │    │ "When I   │ │    ║
║   │   │  hour"    │    │  file     │    │  email    │    │  run the  │ │    ║
║   │   │ "Daily    │    │  appears" │    │  arrives" │    │  script"  │ │    ║
║   │   │  at 9am"  │    │ "When     │    │ "When API │    │           │ │    ║
║   │   │ "Every    │    │  modified"│    │  called"  │    │           │ │    ║
║   │   │  Monday"  │    │           │    │           │    │           │ │    ║
║   │   └───────────┘    └───────────┘    └───────────┘    └───────────┘ │    ║
║   │                                                                     │    ║
║   └─────────────────────────────────────────────────────────────────────┘    ║
║                                                                              ║
║  ═══════════════════════════════════════════════════════════════════════     ║
║                                                                              ║
║   COMMON AUTOMATION SHAPES:                                                  ║
║                                                                              ║
║   ┌─────────────┐    ┌─────────────────────────────────────────────────┐     ║
║   │ File Watch  │    │                                                 │     ║
║   │             │    │  ┌───────┐    ┌─────────┐    ┌────────┐         │     ║
║   │             │    │  │ Watch │───►│ Process │───►│ Move/  │         │     ║
║   │             │    │  │Folder │    │  File   │    │ Archive│         │     ║
║   │             │    │  └───────┘    └─────────┘    └────────┘         │     ║
║   └─────────────┘    └─────────────────────────────────────────────────┘     ║
║                                                                              ║
║   ┌─────────────┐    ┌─────────────────────────────────────────────────┐     ║
║   │ Scheduled   │    │                                                 │     ║
║   │ Report      │    │  ┌───────┐    ┌─────────┐    ┌────────┐         │     ║
║   │             │    │  │ Timer │───►│ Gather  │───►│ Email  │         │     ║
║   │             │    │  │ Daily │    │  Data   │    │ Report │         │     ║
║   │             │    │  └───────┘    └─────────┘    └────────┘         │     ║
║   └─────────────┘    └─────────────────────────────────────────────────┘     ║
║                                                                              ║
║   ┌─────────────┐    ┌─────────────────────────────────────────────────┐     ║
║   │ Data Sync   │    │                                                 │     ║
║   │             │    │  ┌───────┐    ┌─────────┐    ┌────────┐         │     ║
║   │             │    │  │ Timer │───►│ Fetch   │───►│ Update │         │     ║
║   │             │    │  │Hourly │    │ Source  │    │ Local  │         │     ║
║   │             │    │  └───────┘    └─────────┘    └────────┘         │     ║
║   └─────────────┘    └─────────────────────────────────────────────────┘     ║
║                                                                              ║
║  ═══════════════════════════════════════════════════════════════════════     ║
║                                                                              ║
║   BUILD SEQUENCE:                                                            ║
║                                                                              ║
║   ┌─────────────────────────────────────────────────────────────────────┐    ║
║   │                                                                     │    ║
║   │   1. ACTION FIRST (without trigger)                                 │    ║
║   │      "Create script that processes all CSVs in /input folder"       │    ║
║   │                                          ↓                          │    ║
║   │   2. TEST MANUALLY                     Run it, verify it works      │    ║
║   │                                          ↓                          │    ║
║   │   3. ADD TRIGGER                                                    │    ║
║   │      "Make it watch for new files" or "Run every hour"              │    ║
║   │                                          ↓                          │    ║
║   │   4. ADD LOGGING                                                    │    ║
║   │      "Log each run to automation.log with timestamp"                │    ║
║   │                                          ↓                          │    ║
║   │   5. ADD ERROR HANDLING                                             │    ║
║   │      "If processing fails, move file to /failed and notify me"      │    ║
║   │                                                                     │    ║
║   └─────────────────────────────────────────────────────────────────────┘    ║
║                                                                              ║
║   ┌─────────────────────────────────────────────────────────────────────┐    ║
║   │  KEY RULE: Always build and test the action before adding trigger.  │    ║
║   └─────────────────────────────────────────────────────────────────────┘    ║
║                                                                              ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

## Reading This Drawing

**The Core Structure (Top):** Three boxes in a row:
- **TRIGGER:** What starts the automation. "When X happens..."
- **ACTION:** What the automation does. "Do Y..."
- **OUTPUT:** What results. "Produce Z..."

Every automation follows this shape. The trigger fires, the action runs, the output appears.

**Trigger Types (Four Boxes):** The four ways automations can start:
- **TIME:** Schedule-based. "Every hour," "Daily at 9am," "Every Monday"
- **FILE:** Filesystem events. "When new file appears," "When file modified"
- **EVENT:** External signals. "When email arrives," "When API called"
- **MANUAL:** You run it. "When I run the script" (still automation—you just trigger it yourself)

**Common Automation Shapes:** Three practical examples:

**File Watch:** Watch folder → Process file → Move/Archive
Use case: New CSVs dropped into a folder get processed automatically and moved to an archive folder.

**Scheduled Report:** Timer daily → Gather data → Email report
Use case: Every morning at 8am, pull yesterday's data and send a summary email.

**Data Sync:** Timer hourly → Fetch source → Update local
Use case: Every hour, check the external API and update the local database.

**The Build Sequence:** How to construct an automation:
1. **ACTION FIRST:** Build the core logic without any trigger. "Create script that processes all CSVs in /input folder"
2. **TEST MANUALLY:** Run it yourself. Does it work?
3. **ADD TRIGGER:** Now add the automatic part. "Make it watch for new files"
4. **ADD LOGGING:** Make it traceable. "Log each run to automation.log with timestamp"
5. **ADD ERROR HANDLING:** Make it robust. "If processing fails, move file to /failed and notify me"

**The Key Rule (Bottom Box):** "Always build and test the action before adding trigger." An automation that runs on a timer but doesn't work is worse than no automation—it runs broken code repeatedly.

## What This Shows

Automation = Trigger + Action + Output. Triggers start the work (time, file change, event). Actions do the work. Build the action first and test it manually, then add the trigger.

## Key Insight

If you do something more than twice, automate it. Build the action, verify it works, then set it to run automatically.

## What This Means In Practice

To automate a task:
1. Identify the manual steps you do
2. Write a script that does those steps (the action)
3. Test the script manually until it works
4. Add the trigger (time, file watch, etc.)
5. Monitor the first few automatic runs

Start simple. A script that you run manually is already a huge improvement over doing work by hand. Automatic triggers come second.

---

[← Build Incrementally](10-build-incrementally.md) | [Next: API Pattern →](12-pattern-api.md)
