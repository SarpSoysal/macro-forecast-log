# Macro Forecast Log

Public, timestamped probability forecasts on UK and euro area rates and inflation, plus
conditional cross-asset calls attached to each event. Every forecast is committed before
the event resolves. Nothing is edited or deleted after the fact.

Maintained by [NAME]. Started [DATE].

---

## Why this exists

[2-3 sentences in your own words. What you are trying to find out about your own
judgment, not a pitch. Write this once and leave it.]

---

## Rules

These were fixed on day one and are not changed retroactively.

1. **Rationale before pricing.** Probabilities and reasoning are written and committed
   before looking up what the market or consensus is pricing. The benchmark is captured
   in a second commit.
2. **Resolution source named in advance.** Each call file names the exact source and URL
   that will settle it.
3. **Buckets fixed in advance.** For data prints, the outcome categories are defined
   before the forecast. Probabilities sum to 1.
4. **Nothing deleted.** Wrong calls stay up. Commit history is the audit trail.
5. **Missed weeks are gaps, not late entries.** If a call is not committed before the
   event, it is not made at all.
6. **Conditional calls are made for every event**, whatever the eventual surprise size.
   Surprise size is recorded at resolution and scored in two buckets.

---

## What gets forecast

### Tier 1: event forecasts

| Family | Frequency | Resolution source |
|---|---|---|
| UK CPI, headline and core | Monthly | ONS consumer price inflation bulletin |
| BoE Bank Rate decision | 8 per year | BoE Monetary Policy Summary |
| BoE MPC vote split | 8 per year | BoE Monetary Policy Summary |
| ECB policy decision | 8 per year | ECB monetary policy statement |
| Euro area flash HICP | Monthly | Eurostat flash estimate |
| Spain flash CPI | Monthly | INE indicador adelantado |

### Tier 2: conditional transmission calls

Attached to each Tier 1 event. Form: *given* a surprise of a stated size and direction,
the probability that each asset moves in a stated direction, close to close.

Asset set, fixed at six:

| Asset | What it is reading | Source |
|---|---|---|
| 2y gilt yield | Near-term policy expectations | Bank of England daily yield curve data |
| 10y gilt yield | Term premium and growth | Bank of England daily yield curve data |
| 2s10s gilt gap | Policy story vs growth story | Derived from the two above |
| GBP/USD | Currency reaction | [SOURCE] |
| FTSE 250 | UK domestic equity | [SOURCE] |
| 10y Bund yield | Euro area rates | Deutsche Bundesbank daily yields |
| Euro IG spread (OAS) | Credit and growth risk, euro area calls only | FRED, ICE BofA series [ID] |

No free daily sterling investment grade spread series has been identified, so UK
conditionals use the 2s10s gilt gap in place of a credit leg.

### Tier 3: quarterly cross-asset note

One page per quarter in `/notes`. Three positioning views, rationale, and explicit
falsification criteria for each. Reviewed at the following quarter end. No performance
figures are reported, only whether the reasoning held.

---

## Method

### Price window

Close to close on the release day: the previous session's close against the release day's
close, using official central bank data where available.

Limitation, stated plainly: a close to close move contains the reaction to the release
plus a full day of unrelated news. A tighter window around the release time would isolate
the reaction better but requires intraday data not available here. Where pre and post
release prices were noted manually, they appear as an extra column and are not used in
scoring.

### Scoring

**Tier 1, multi-category Brier score.** Sum over all outcome categories of
(probability assigned minus outcome)², where outcome is 1 for the category that occurred
and 0 for all others. Range 0 to 2. Lower is better.

**Tier 2, binary Brier score.** (probability assigned minus outcome)², where outcome is
1 or 0. Range 0 to 1. Lower is better.

The two scales are different and are never averaged together.

**Reference rows.** Every scoreboard carries two comparison rows:
- the market or consensus benchmark captured before the event
- the naive base rate, meaning the historical frequency of each outcome with no judgment
  applied

Beating the base rate is the minimum bar. Beating the market benchmark is unlikely and is
not claimed.

All scoring is done by hand in a spreadsheet. The arithmetic is deliberately simple
enough to reproduce on paper.

---

## Scoreboard

Sample sizes here are small. A Brier score over fewer than roughly 30 calls carries wide
uncertainty and should not be read as evidence of skill.

### Tier 1

| Calls resolved | My mean Brier | Benchmark | Base rate |
|---|---|---|---|
| 0 | - | - | - |

### Tier 2

| Surprise size | Calls resolved | My mean Brier | Base rate |
|---|---|---|---|
| Large (>= 0.2pp, or decision differs from modal market pricing) | 0 | - | - |
| Small | 0 | - | - |

### Call index

| Date | Event | Tier 1 calls | Tier 2 calls | Status | File |
|---|---|---|---|---|---|
| 2026-10-29 | ECB decision | | | Open | [link] |
| 2026-10-30 | EA flash HICP, Spain flash CPI | | | Open | [link] |
| 2026-11-05 | BoE decision and vote split | | | Open | [link] |
| 2026-11-18 | UK CPI, October data | | | Open | [link] |
| 2026-11-30 | EA flash HICP, Spain flash CPI | | | Open | [link] |
| 2026-12-16 | UK CPI, November data | | | Open | [link] |
| 2026-12-17 | BoE decision, ECB decision | | | Open | [link] |
| 2026-12-30 | EA flash HICP, Spain flash CPI | | | Open | [link] |
| 2027-01-TBC | UK CPI, December data | | | Open | [link] |
| 2027-02-04 | BoE decision and vote split | | | Open | [link] |

All dates to be confirmed against the official release calendars before each call is
committed.

---

## Error review

Written after every fifth resolved Tier 1 call. 100 words on what has been systematically
wrong, not what has been right.

### Review 1, after 5 calls
[blank]

### Review 2, after 10 calls
[blank]

---

## Repo structure

```
README.md                    this file
calls/YYYY-MM-DD-event.md    one file per event, Tier 1 and Tier 2 together
notes/YYYY-QN.md             quarterly cross-asset notes
scores-events.csv            Tier 1 results
scores-transmission.csv      Tier 2 results
benchmarks/                  dated screenshots of captured market pricing
```

## Sources

- Bank of England, Monetary Policy Summary and daily yield curve data
- Office for National Statistics, consumer price inflation bulletin
- European Central Bank, monetary policy statements
- Eurostat, flash HICP estimate
- Instituto Nacional de Estadistica, indicador adelantado del IPC
- Deutsche Bundesbank, daily yields
- FRED, ICE BofA index option-adjusted spreads
