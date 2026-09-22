# Output templates

## Report: `patterns-[slug].md`

```markdown
---
title: "[Topic]: Emerging Patterns"
subtitle: "Signal clustering of [N] signals, [start date] to [end date]"
author: "[Organisation or team]"
date: "[Date]"
---

# Summary

[2–3 sentences: what the log covered, how many signals, how many patterns.]

## Assumptions this challenges

- **[Assumption]** — challenged by [Pattern name]: [one line why]

## The patterns at a glance

| # | Pattern | Signals | Momentum | Spread | Novelty | Evidence | Next step |
|---|---|---|---|---|---|---|---|
| P1 | [Name] | [n] | [1–5] | [1–5] | [1–5] | [1–5] | Act / Research / Watch |

[Since last time — update mode only: growing, fading, new, merged/split, assumption changes]

# Patterns

## P1 — [Name]

**From** [what was true] **to** [what is becoming true].

[2–4 sentences: what's shifting, and why it matters for the focus.]

**Scores:** Momentum [n] — [reason] · Spread [n] — [reason] · Novelty [n] — [reason] · Evidence [n] — [reason]

**Signals**

- [Date] — [Title] ([Source](URL))
- ...

**Counter-signals**

- [Date] — [Title] ([Source](URL)): [why it cuts against the pattern]
- *(or: "None found in the log or in a quick search. The log's sources may be one-sided on this.")*

**Next step: [Act / Research / Watch].** [One or two sentences on what to do.]
**What would change this:** [one observable development that would move it up or down]

[Repeat for each pattern]

# Outliers worth keeping

- **[Signal title]** ([Source](URL)) — it would matter if [what would have to be true].

# Assumption check

| Assumption | Status | Patterns |
|---|---|---|
| [Assumption] | Supported / Challenged / Untested | P1, P3 |

# Scan health

- **Categories:** [counts by STEEP+], and what's thin
- **Sources:** [any source over about 15% of signals]
- **Geography:** [spread versus focus]
- **Queries to add:** "[query]" — [what it would find]
- **Queries to drop or rethink:** "[query]" — [why]

# Appendix

## A. All signals by pattern

| ID | Date | Signal | Category | Type | Pattern |
|---|---|---|---|---|---|

## B. Set aside

| ID | Signal | Screened as | Reason |
|---|---|---|---|

## C. How this was produced

[One paragraph: method, AI assistance, human review, and the fact that the patterns are only as broad as the log.]
```

## State file: `patterns.json`

```json
{
  "topic": "string",
  "run_date": "YYYY-MM-DD",
  "previous_run_date": "YYYY-MM-DD or null",
  "window": { "from": "YYYY-MM-DD", "to": "YYYY-MM-DD" },
  "signals": [
    { "id": "S001", "date": "YYYY-MM-DD", "title": "string", "url": "string",
      "category": "Social|Technological|Economic|Environmental|Political|Legal|Values",
      "type": "policy|market|product|data|research|civic|behaviour|counter|wildcard",
      "screen": "signal|context|noise", "pattern": "P1 or null" }
  ],
  "patterns": [
    { "id": "P1", "name": "string", "from": "string", "to": "string",
      "signals": ["S001"], "counter_signals": ["S014"],
      "scores": { "momentum": 1, "spread": 1, "novelty": 1, "evidence": 1 },
      "recommendation": "act|research|watch",
      "challenges": ["A2"], "status": "new|growing|steady|fading|merged",
      "history": [ { "run_date": "YYYY-MM-DD", "signals": 0, "scores": {} } ] }
  ],
  "outliers": ["S020"],
  "assumptions": [
    { "id": "A1", "text": "string", "status": "supported|challenged|untested", "patterns": ["P1"] }
  ]
}
```

In update mode, keep every existing `id`. New signals continue the numbering. A merged pattern keeps the older ID and records the other in `history`.
