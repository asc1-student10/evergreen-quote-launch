# Stakeholder Status Update: Evergreen Quote Launch

**To:** Instructor (project sponsor)
**From:** Ricky Cotton
**Date:** Nov 17, 2026

## What shipped today
- Day 2 complete: client wired to the API through the dev proxy, and the list and save paths read from the database.
- Seam fix applied; the type-check is clean.
- Client rates aligned to the sponsor's launch values, with the same inputs checked in the client and the API.
- Launch title and banner set; landing hero approved as content.
- GraphQL mounted; the explorer query returns the seeded quotes.
- Risk register written (five risks, owners, and escalation triggers), and the board re-prioritized by dependency.
- Renters coverage deferred to a later round, recorded on its board issue.
- Premium-math decision drafted: keep the instant estimate in the app, with the saved premium from the service.

## What slipped (and why)
- Nothing slipped today.

## Open item
- The form-default request (life coverage) is with the front-end team, awaiting their decision before launch.

## What's next (tomorrow)
- Containerize the API as `evergreen-quote-api:2.0` and run it with the client.
- Deploy the stack to the local kind cluster, with three API pods and the database.
- Enable the two-job CI workflow, so every push runs both checks.
- Send the written demo plan.

## What I need from you
- **By Wednesday 12pm, confirm the demo plan** is acceptable for Friday, running locally on the kind cluster.
- **By Wednesday 12pm, confirm the renters deferral** is acceptable for this launch.
