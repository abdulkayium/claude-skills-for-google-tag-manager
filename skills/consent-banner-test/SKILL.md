---
name: consent-banner-test
description: Runs a repeatable test of a cookie banner against tracking: default state, reject, accept, partial choice, and what fires in each case. Use when someone says "test my cookie banner", "does tracking respect consent", "check consent states", or after any banner or GTM change.
---

# Consent Banner Test

A short test matrix with expected results. Takes about 10 minutes.

## Use this when
- A banner was added, replaced or updated.
- Conversions changed after a banner change.
- Before a launch or an audit.

## Inputs to ask for
1. The site URL and the banner tool.
2. Which regions need consent.
3. The expected behavior for each choice (from the company's policy).
4. Access to GTM Preview or Tag Assistant, or screenshots from the tester.

## Workflow
1. Open the site in a fresh private window. Do not click anything.
   - Record the consent state (Tag Assistant, Consent tab).
   - Record which tags fire before any choice.
2. **Reject all.** Record the consent state, tags that fire, cookies set, and the `gcs` value on Google requests.
3. **Accept all.** Record the same four items. Expect `G111` when both ad and analytics storage are granted.
4. **Partial choice** (for example only statistics). Record the same items. Check each signal changed as the policy says.
5. **Change choice later** through the banner link. Check the state updates again.
6. **Another region** (use a different location test if possible). Check the default state differs as designed.
7. Compare results with the expected table.

## Output format
A matrix: scenario, consent state, tags that fired, cookies set, `gcs`, expected, pass or fail.
Then the fixes in order.

## Decision rules
- Tags that need consent firing before any choice is a fail. Fix this first.
- A state that never updates after a choice is a fail. Check the banner to GTM link.
- A pass on states but zero data after Accept means a different problem. Hand over to `gtm-preview-debugger`.

## Guardrails
- Read-only. Do not change banner or tag settings.
- Do not give legal advice. Report what happens and compare it with the written policy.
- Use test sessions only. Do not record or share real visitor data.
