# Tesla UK Cost-of-Ownership Analysis

An interactive comparison of four UK Tesla models, built around finance terms read
directly off Tesla's own configurator rather than estimated.

**Live site:** https://arindamr.github.io/tesla/

## What's here

| Page | Purpose |
|---|---|
| `index.html` | Decision hub — guided chooser, comparison tables, narratives, money traps |
| `model3-tco-calculator.html` | Model 3 RWD — full interactive calculator |
| `model3-LR-tco-calculator.html` | Model 3 Premium Long Range RWD |
| `modelY-tco-calculator.html` | Model Y RWD |
| `modelY-LR-tco-calculator.html` | Model Y Premium Long Range RWD |
| `*-market-tracker.html` | Per-model market trackers with current inputs and change log |

## The four cars

| Car | OTR | Range | 48-mo APR | 4-year cost |
|---|---|---|---|---|
| Model 3 RWD | £37,990 | 332 mi | 0% | £25,014 |
| Model 3 Premium LR RWD | £44,990 | 466 mi | 0% | £29,028 |
| Model Y RWD | £41,990 | 314 mi | 0% | £27,548 |
| Model Y Premium LR RWD | £48,990 | 378 mi | **2.90%** | £35,407 |

## Method

Costs are **economic cost**, not cash out of pocket: every payment is compounded
forward to the end of the horizon at a 5% opportunity rate, minus whatever the car —
or your equity in it — is worth at that point. Financed routes are amortised from
principal, APR and balloon. The Optional Final Payment is modelled as a put option on
the residual: at month 48 you settle only if the car is worth more than the OFP, and
hand it back if it is not.

Each calculator reproduces Tesla's own quoted monthly payments exactly across all five
mileage options. Annual cost breakdowns reconcile to their horizon totals to the penny,
verified against an independent Python implementation.

## Assumptions

10,000 miles/year · home charging at 7p/kWh off-peak (90% home, 10% public) ·
personal post-tax money · 5% opportunity cost · residuals −22% year one, −11%/yr after.
All adjustable in each calculator.

## Caveats

Finance figures were captured on **30 July 2026** and the promotional terms require an
order by **30 September 2026**. Prices and offers change — re-quote before relying on
any of it. Insurance, real-world efficiency, tyre costs and the depreciation curve are
estimates. **Not financial advice.**

## Technical notes

Every page is a single self-contained HTML file with no external dependencies —
no frameworks, no CDN, no build step. A shared light/dark theme toggle persists
across pages via `localStorage`, falling back to a `?theme=` query parameter so it
works when opened as local files too.
