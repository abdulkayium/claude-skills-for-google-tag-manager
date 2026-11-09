---
name: weekly-tracking-update
description: Writes a short weekly tracking status update for a client or manager: done, in progress, blocked, risks and next week. Use when someone says "weekly update", "status update for tracking", "what did we do this week", or "write my Friday update".
---

# Weekly Tracking Update

A short, honest update that people actually read.

## Use this when
- A weekly or monthly update is due.
- A manager asks for progress on tracking work.

## Inputs to ask for
1. Notes on what was done this week.
2. What is in progress and what is blocked, and by whom.
3. Any checked numbers or health results.
4. Plans for next week.
5. The audience and channel.

## Workflow
1. Open with one line on the overall status: on track, at risk, or blocked.
2. **Done:** 3 to 5 arrow lines (→), each with the result, not only the task.
3. **In progress:** items with the next step.
4. **Blocked:** what is needed and from whom.
5. **Risks:** one to three items with a plain impact line.
6. **Numbers:** only checked numbers, with the source and date range.
7. **Next week:** top 3 items.

## Output format
```
Status: [on track / at risk / blocked]

Done:
→ ...

In progress:
→ ...

Blocked:
→ ...

Risks:
→ ...

Next week:
→ ...
```

## Decision rules
- Keep it under 200 words unless asked.
- Lead with results. Skip task lists with no outcome.
- If there is bad news, say it early and give the plan.

## Guardrails
- Writing only. Do not send the update or change any system. Give the text for the user to send.
- Do not invent progress or numbers.
- Do not name other clients in an update for one client.
- Do not blame people. State the fact and the next step.
