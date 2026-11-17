# Decision Memo: Where the Premium Is Calculated

**Date:** Nov 17, 2026
**Author:** Ricky Cotton
**Decision area:** Day 2 design tradeoff

## Context

A first-time shopper types in their details and expects an instant premium estimate. Today the premium is calculated in two places: the web app calculates an estimate as the shopper types, and the quote service calculates the premium that gets saved. We have aligned the two sets of rates to the sponsor's launch values, but the calculation is still in two places, so the two could drift apart again.

## Options considered

1. **Keep the estimate in the app, with matching rates.** The estimate appears instantly as the shopper types, and it works even if the service is slow. The cost is that the rates live in two places and must be kept in sync by hand.
2. **Ask the service for every estimate.** There is one source of truth for the premium, so the estimate and the saved number always match. But every keystroke waits on a network call, and the estimate fails whenever the service or its database is down, which is the same dependency we already flagged as a demo risk.
3. **Share one rates file between the app and the service.** This gives one source of truth without a network delay. It is not realistic this week, because the app and the service are written in different languages and would need a shared build step first.

## Recommendation

Option 1 for launch: keep the instant estimate in the app and align its rates to the sponsor's values. The saved premium is the service's number. Before each demo, we compare the two on several sample inputs. We schedule Option 3 for the next round.

## Why

Customers judge the product in the first few seconds, and a slow or failing estimate costs us the shopper. The number they save is the number the service stores, so the record they rely on is correct. A two-place calculation with a sample check before each demo is an acceptable risk for launch.

## What would change my mind

If the sponsor changes rates more than once a month, or a spot-check finds any mismatch after launch, I would move to Option 2 for the saved premium at minimum, and plan Option 3 for the next round.
