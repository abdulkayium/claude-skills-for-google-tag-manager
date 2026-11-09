---
name: booking-tool-tracking-check
description: Checks and plans conversion tracking for embedded booking tools (Calendly, Cal.com, HubSpot Meetings, and similar), including iframe events and source carry-over. Use when someone says "track Calendly bookings", "booked call conversion", "iframe booking tracking", or "booking source missing".
---

# Booking Tool Tracking Check

Booked calls are often the real goal. Embedded tools hide them from normal triggers. This skill finds a reliable signal.

## Use this when
- A booking widget sits in an iframe or popup.
- Booked calls are not counted, or the thank-you page is a different domain.
- Bookings arrive in the CRM without source data.

## Inputs to ask for
1. The booking tool and how it is embedded (inline, popup, link to a hosted page).
2. The page URL where the widget loads.
3. What happens after booking (message inside the widget, redirect, email only).
4. Whether the CRM receives the booking and from where.

## Workflow
1. **Pick the signal.** Best to worst:
   - the tool's own embed event or message sent to the page
   - a redirect to your own confirmation page after booking
   - a webhook or CRM event sent from the server
   - a click on the "schedule" button (weakest, only counts intent)
2. **Find what the widget sends.** Open the console and log all page messages while a test booking is made:
   `window.addEventListener('message', function (e) { console.log(e.origin, e.data); });`
   Look for a message that appears only when a booking succeeds.
3. **Build the listener.** Push one dataLayer event, for example `booking_success`, when that message appears. Check the origin before trusting the message.
4. **Fire once.** Add a guard so one booking sends one event.
5. **Carry the source.** Pass UTMs and click ID into the booking (URL parameters, hidden fields or tool settings). See `gclid-utm-crm-capture`.
6. **Test.** Make a real test booking, then cancel it. Check Preview, the ad platforms and the CRM.

## Output format
- The chosen signal and why.
- The listener code or the redirect plan.
- A test table: step, expected result.
- A note on source carry-over.

## Decision rules
- If the tool offers an official embed event, use it. Event names change between versions, so confirm them in the tool's current docs and in your own console test.
- If nothing is available in the browser, move to a server-side webhook or CRM-based event.
- Count the booking, not the click on the button, for the main conversion.

## Guardrails
- Read-only. Do not publish tags. Make test bookings only with the user's approval, and cancel them.
- Check the message origin in code. Never trust any message from any site.
- Do not store personal data from the booking in the dataLayer.
