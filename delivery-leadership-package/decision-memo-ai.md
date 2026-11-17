# Decision Memo: Using AI to Draft Seed Data

**Date:** Nov 18, 2026
**Author:** Ricky Cotton
**Decision area:** AI-assisted data and launch readiness

## Context

For the launch demo, we needed more sample quotes so the quote list shows a wider range of customers. We asked Copilot to add two quotes, q7 and q8. Copilot wrote the records, including their premiums, and the seed ran successfully. The premium is the number a shopper sees, so it has to match what the service calculates. The seed values looked plausible, but Copilot did not calculate them.

## Options considered

1. **Accept the AI-written records as they are.** This is the fastest route. But the premiums look right without being checked, and that is the risk.
2. **Reject the AI records and enter the quotes by hand.** This avoids relying on AI, but it adds a manual step where errors can creep in too.
3. **Use the AI records only after checking each premium against the rate formula, and correct any that don't match.** This keeps the speed and gives a check that doesn't depend on Copilot's judgment.

## Recommendation

Option 3. Replace Copilot's premiums with the values the rate formula produces, then confirm the service returns the same numbers.

## Why

The demo depends on the numbers being right. A premium that looks plausible but doesn't match the service would undermine the whole showcase, and the audience would have no way to tell. The check took minutes and gives us evidence we can show.

## Results

- **q7** (life, age 45, coverage 200,000): Copilot's premium was 168. The rate formula gives 70 × 1.0 × 20 = **1,400**. Corrected.
- **q8** (home, age 44, coverage 300,000): Copilot's premium was 420. The rate formula gives 135 × 1.0 × 30 = **4,050**. Corrected.
- **Rates and logic:** The client and API calculate the same premium for the same inputs, with the same rates.
- **Rounding:** The client doesn't round to the cent, but the API does. For inputs that produce fractions, the client can show more decimals. Routed to the client team.
- **Original six seeds:** Their premiums come from an older rate table, as documented. The showcase will explain this.

## What would change my mind

If the sponsor changes the rate table or the formula, I would recalculate all eight seeded quotes before the demo. If the sponsor says a $4,050 monthly premium for a $300,000 home policy is not intended, I would route that to the sponsor as a launch risk before Friday.
