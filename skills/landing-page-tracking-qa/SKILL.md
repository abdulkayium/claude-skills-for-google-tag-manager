---
name: landing-page-tracking-qa
description: A step-by-step QA for a new or changed landing page: container load, each call to action, tag firing, one real test conversion, and delivery to ad platforms and CRM. Use when someone says "new landing page", "validate tracking on this page", "QA this page", or "page changed, is tracking still working".
---

# Landing Page Tracking QA

Checks one page from first load to the final record in the CRM.

## Use this when
- A landing page is new, rebuilt or moved.
- A marketer asks "is tracking working on this page?"
- A site update happened and nobody tested tracking.

## Inputs to ask for
1. The page URL.
2. The key actions on the page (form, call button, chat, booking, download).
3. The conversion actions that should count each action.
4. Access to GTM Preview, or screenshots.
5. Where the lead should appear (CRM, email, sheet).

## Workflow
1. **Load check.** The container loads once. No second container. No missing container.
2. **List the actions.** Classify each: form on page, form in popup, form in iframe, phone click, chat, booking, outbound click.
3. **Match each action to a tag.** Name the tag and trigger that should handle it.
4. **Check the trigger logic** for each action (event, conditions, page or selector).
5. **Run a test.** Do one real test conversion with the user's approval. Use a clear test name and a test email.
6. **Watch Preview.** The right tag fires once. Values are correct. Consent is respected.
7. **Check the destinations.** The conversion appears in the ad platform diagnostics or test view. The lead appears in the CRM with source fields.
8. **Check mobile.** Run the key action on a phone.
9. Record pass or fail per action.

## Output format
- A table: action, expected tag, result, evidence, status.
- A list of fixes in priority order.
- A short message for the marketer and a short request for the developer, if needed.

## Decision rules
- A tag that fires on page view when it should fire on submit is a fail.
- No CRM record after a pass in Preview means the problem is in the form to CRM link.
- If an action cannot be tracked in the browser (cross-domain iframe), say so and give the next best signal.

## Guardrails
- Read-only. Do not edit tags or publish.
- Test leads must be clearly marked and deleted by the owner afterward.
- Do not claim "tracking works" without a real test result.
