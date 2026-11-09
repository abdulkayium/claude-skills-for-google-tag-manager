---
name: server-side-gtm-launch
description: Helps decide if a business needs server-side GTM and, if yes, plans the launch: hosting, first-party domain, clients, tags, testing and monitoring. Use when someone says "do we need server-side tracking", "set up sGTM", "Stape setup", or "server container plan".
---

# Server-Side GTM Launch Plan

First a clear yes or no. Then a safe rollout plan.

## Use this when
- A client asks "do we need server-side?"
- Planning a new server container (Stape, Google Cloud, or another host).
- Moving Meta CAPI or Google tags to the server.

## Inputs to ask for
1. Monthly ad spend and main platforms.
2. Site platform (Shopify, WordPress, custom) and where DNS is managed.
3. Current problems (blocked tags, short cookie life, missing conversions, slow site, CAPI needs).
4. Who will own hosting cost and monitoring.
5. Consent setup in place.

## Workflow
1. **Feasibility.** List the real reasons to go server-side. Good reasons: Meta CAPI needs, longer first-party cookie life, less browser code, control over data sent to vendors. Weak reasons: "everyone does it".
2. **Cost and effort.** Name the hosting cost type, the DNS work, and the monitoring job. Do not invent prices; tell the user to check the host's current pricing.
3. **Plan the domain.** Use a first-party subdomain for the tagging server. Check with the host how to match the website's IP setup, because Safari may shorten cookie life when the IPs differ. Verify in testing.
4. **Plan the data flow.** Web container sends to the server URL. Server uses a client (for example the GA4 client), then tags for GA4, Google Ads, Meta CAPI and others.
5. **Plan testing.** Use server Preview and web Preview together. Check each tag fires once and values match.
6. **Plan monitoring.** Check server health, request counts and errors weekly. Name an owner.
7. **Plan rollback.** Keep the old browser setup available until numbers match for a set period.

## Output format
- Verdict: yes, not yet, or no, with 3 reasons.
- A phased plan (prepare, build, test, switch, monitor).
- A risk list with owners.

## Decision rules
- Low spend and simple needs: recommend fixing browser tracking first.
- CAPI or cookie life are real problems: recommend server-side, in phases.
- Consent still applies. Server-side does not remove the need for consent.

## Guardrails
- Read-only. Do not create containers, servers or DNS records.
- Never claim a percent of data recovered without measured proof. Say "can improve" and plan a before and after check.
- Do not promise to bypass ad blockers or privacy rules.
