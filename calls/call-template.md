# [EVENT NAME], [DATE]

Forecast committed: [TIMESTAMP, from the commit, not typed by hand]
Resolution source: [EXACT URL]

---

## Tier 1: event forecast

### Question
[Precise wording.]

### Outcome categories
[Fixed before forecasting. Must be exhaustive and non-overlapping.]

| Category | My probability |
|---|---|
| <= [x] | |
| [x] to [y] | |
| [y] to [z] | |
| >= [z] | |
| **Sum** | **1.00** |

### Rationale
[Max 150 words, your words. Cover: the two or three things driving your view,
and the single thing most likely to make you wrong. Written before looking at
any market pricing or consensus. Commit at this point.]

### What would make me wrong
[One or two sentences. Be specific enough that you could check it afterwards.]

---

## Benchmark

Captured: [TIMESTAMP]
Source: [Reuters poll / OIS-implied / CME FedWatch / other, with URL]
Screenshot: [path in /benchmarks]

| Category | Benchmark probability or consensus |
|---|---|
| | |

Base rate used: [what it is and where it comes from]

---

## Tier 2: conditional transmission calls

Close to close, [previous session close] to [release day close].

### If the outcome is [above expectations by the stated margin]

| Asset | Direction | My probability |
|---|---|---|
| 2y gilt yield | rises | |
| 10y gilt yield | rises | |
| 2s10s gilt gap | narrows | |
| GBP/USD | rises | |
| FTSE 250 | falls | |

### If the outcome is [below expectations by the stated margin]

| Asset | Direction | My probability |
|---|---|---|
| | | |

### Reasoning for the transmission
[Max 100 words. Why these directions. This is the part that matters most,
because it is the part that is about understanding rather than forecasting.]

---

## Resolution

Resolved: [DATE]

### Tier 1
Actual outcome: [value and category]
Surprise vs consensus: [x pp]
My Brier: [ ]   Benchmark Brier: [ ]   Base rate Brier: [ ]

### Tier 2
Surprise bucket: [large / small]

| Asset | Predicted direction | Actual move | Correct? | Brier |
|---|---|---|---|---|
| | | | | |

Mean Tier 2 Brier this event: [ ]

---

## What I got wrong

[3 to 5 sentences, your words. Not "I was unlucky". What specifically did you
misunderstand or underweight, and what will you do differently on the next
call of this type. If you were right, say what you think was judgment and what
was luck.]
