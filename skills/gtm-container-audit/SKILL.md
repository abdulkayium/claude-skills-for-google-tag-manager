---
name: gtm-container-audit
description: Reviews an exported GTM container JSON (web or server) for duplicates, risky triggers, leftovers, naming problems and consent gaps, then ranks the fixes. Use when someone says "audit my GTM", "review this container", "clean up GTM", or "check the container export".
---

# GTM Container Audit

A read-only review of the container file. Findings are ranked by risk.

## Use this when
- Taking over a container from someone else.
- Before a migration (for example the Google tag change inside GTM).
- Numbers look inflated or tags fire on the wrong pages.

## Inputs to ask for
1. The container export (JSON). In GTM: Admin, Export Container.
2. The goal of the audit (cleanup, migration, double counting, handover).
3. The list of platforms that should be tracked.

## Workflow
1. Read the JSON. Count tags, triggers, variables, folders. Note paused tags.
2. **Duplicates.** Look for two tags that send the same event or conversion to the same destination.
3. **Triggers.** Flag conversion tags on All Pages. Flag custom event triggers that use a wildcard (`.*`). Since Google began pushing `gtag.config` events to the dataLayer in October 2026, wildcard triggers can fire an extra time per page. Check this one with care.
4. **Config.** Flag old Google tag, GA4 Configuration or Conversion Linker items that need review after Google's tagging update. Do not delete based on assumption. Note the item and the question.
5. **Hard-coded IDs.** List measurement IDs, conversion IDs and pixel IDs. Check they match what the business owns.
6. **Consent.** Check each tag for consent settings. List tags with none.
7. **Leftovers.** Test tags, old vendors, unused variables, empty triggers.
8. **Naming and notes.** Check names are clear. Suggest a simple pattern if not.
9. **Versions.** Check recent version notes for unexplained changes.

## Output format
- Summary in 3 lines.
- A table: finding, risk (high, medium, low), evidence (tag or trigger name), fix, effort.
- A "looks fine" list, so the owner knows what was checked.

## Decision rules
- High: anything that can double count, miss revenue events, or send data without consent.
- Medium: confusing structure that causes future mistakes.
- Low: naming and tidy-up.
- When unsure whether an item is used, say "needs confirmation" and name who can confirm.

## Guardrails
- Read-only. Do not edit, delete or publish anything.
- Do not guess what a custom HTML tag does if the code is not shown. Ask for it.
- Do not include client names in the output unless the user gave them for the report.
