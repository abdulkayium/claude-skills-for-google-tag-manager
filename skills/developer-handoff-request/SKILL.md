---
name: developer-handoff-request
description: Writes a clear request for a website developer to add or fix tracking code (dataLayer events, hidden fields, redirects, parameters), with exact code, acceptance tests and a rollback note. Use when someone says "ask the dev", "implementation request", "developer needs to add dataLayer", or "write a ticket for tracking".
---

# Developer Handoff Request

A ticket a developer can finish without questions.

## Use this when
- Tracking needs a code change on the site or the backend.
- A previous request was unclear and came back wrong.

## Inputs to ask for
1. The goal in one line.
2. The page or flow and the platform or framework.
3. The exact data needed (event name, fields, example values).
4. Where the code should run (page load, after submit, after payment).
5. The deadline and who tests.

## Workflow
1. Write the **goal** in one sentence and the **why** in one sentence.
2. Write the **scope**: where the change is needed. Say what is not in scope.
3. Give the **exact code or payload** in a code block, with real field names.
4. Give **rules**: fire once, only after success, number types, no personal data unless approved.
5. Write **acceptance tests** as steps the developer can follow, with the expected result.
6. Add **how to verify**: open the page, run the action, check the dataLayer in the console or in GTM Preview.
7. Add **rollback**: how to undo the change if it breaks something.
8. Add **questions** that need an answer before work starts.

## Output format
```
Title: [short]
Goal:
Why:
Where:
What to add (code):
Rules:
Acceptance tests:
How to verify:
Rollback:
Open questions:
```

## Decision rules
- Give one clear way to do it. Do not give five options.
- Use their stack's words (for example Blade, React, Liquid) if known.
- If the data does not exist on the page, ask where the backend can supply it.

## Guardrails
- Writing only. Do not send the ticket or change any code. Give the text for the user to send.
- Do not ask the developer to send raw personal data into the dataLayer unless the owner approved it and consent is handled.
- Do not include secrets or access keys.
- Be polite and specific. No blame.
