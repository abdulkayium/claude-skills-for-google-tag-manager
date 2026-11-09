---
name: delivery-message
description: Writes a short, clear delivery message after a tracking setup or fix: what was done, how it was checked, what to watch, and what is next. Use when someone says "write the delivery message", "project complete message", "tracking setup done", or "send update to client".
---

# Delivery Message

A message a client can read in 30 seconds and trust.

## Use this when
- A tracking setup or fix is finished.
- Screenshots of tags, conversions or tests need a message around them.

## Inputs to ask for
1. What was set up or fixed.
2. How it was tested and the result.
3. Anything the client must do (publish, approve, test, give access).
4. What to watch in the next days.
5. The tone and channel (email, Slack, chat).

## Workflow
1. Open with the result in one line.
2. List what was done in short arrow lines (→), 3 to 6 items.
3. Say how it was checked, in one or two lines.
4. Say what to expect: when data will show up and where.
5. Add a "what to watch" line with one clear thing.
6. Close with the next step or a friendly offer to help.

## Output format
```
Hi [Name],

[Result in one line.]

What was done:
→ item
→ item
→ item

How I checked it:
[One or two lines.]

What to expect:
[One or two lines.]

[Next step or offer.]
```

## Decision rules
- If something is not finished, say it plainly and give a date or a condition.
- If a number is shown, say where it comes from.
- Keep it under 150 words unless the user asks for more.

## Guardrails
- Writing only. Do not send the message or change any system. Give the text for the user to send.
- Do not claim things were tested if they were not.
- Do not blame people. State the fact and the fix.
- Do not include logins, keys or private data.
