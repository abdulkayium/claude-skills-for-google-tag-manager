---
name: gtm-preview-debugger
description: Finds why a GTM tag does not fire, fires twice, or sends wrong values, using Preview and Tag Assistant evidence. Use when someone says "tag not firing", "trigger not working", "GTM debug", or "tag fires twice".
---

# GTM Preview Debugger

A step-by-step way to find the cause, with proof at each step.

## Use this when
- A tag shows "Not fired" in Preview.
- A tag fires on the wrong page or more than once.
- A variable shows undefined or the wrong value.

## Inputs to ask for
1. The tag name, the trigger name, and what should happen.
2. A screenshot of the Preview summary for the test action.
3. A screenshot of the Variables tab at the event where the tag should fire.
4. Whether the problem is in Preview only, on the live site only, or both.

## Workflow
1. **Is the event there?** Look for the event in the Preview timeline (for example `form_submit_success`, `purchase`). No event means the problem is on the site or dataLayer, not in the tag.
2. **Is the trigger true?** Open the tag's "Why not fired" panel. Read each trigger condition against the real variable values at that event.
3. **Is a variable wrong?** Check data layer variables: name, version, and path. A typo in the key is common. Check that the value exists at that exact event, not later.
4. **Is consent blocking?** Check the Consent tab. A tag with consent checks will not fire if the state is denied.
5. **Is something blocking it?** Look for blocking triggers and tag sequencing.
6. **Is it a timing problem?** Check if the page redirects before the tag finishes. Use "Wait for Tags" where it applies.
7. **Preview works, live fails?** Check that the latest version is published, and look for ad blockers, caching, or a different container ID on the live page.
8. **Fires twice?** Look for two triggers, two tags, two containers, or a single-page app that sends the event on each route change.

## Output format
- The most likely cause, with the exact evidence (event, variable, value).
- A numbered fix.
- A re-test list.

## Decision rules
- Always prove the cause with a screenshot or value. Do not guess.
- If two causes are possible, give the test that separates them.
- If the dataLayer event is missing, write the request for the developer instead of changing the tag.

## Guardrails
- Read-only. Do not edit or publish the container. Give the exact change and let the user apply it.
- Do not ask for passwords or logins. Screenshots and exports are enough.
