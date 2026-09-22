---
name: signal-clustering
description: >
  Turn a pile of collected signals — a horizon-scanning log, a weekly signal-monitor file, a folder of bookmarks, workshop notes — into a small set of named emerging patterns, each scored for momentum, spread, novelty and evidence strength, checked against counter-signals, and compared with the team's own assumptions. Re-run later and it tracks which patterns are growing, fading or new. Triggers on: "cluster these signals", "make sense of my signals", "what patterns are in this", "what's emerging from my horizon scan", "sensemaking", "signal clustering", "affinity map these", "synthesise the signals log", "what are the trends in this list", "weak signals analysis", "which signals matter", "review the signals file", "what's changed since last time", "update the pattern map". Use whenever someone has collected signals and needs to know what they add up to. Different from trend-signal-monitor (which collects signals), trend-report (a deep dive on one topic) and scenario-builder (futures built from drivers) — this is the step in between.
---

# Signal Clustering

Collecting signals is easy; knowing what they add up to is the hard part. Most signal logs become a scroll of interesting links that nobody reads twice. This skill does the sensemaking: it groups signals by the **change underneath them**, not by topic label, scores each group honestly, looks for evidence against it, and holds it up against what the team currently believes.

The output is a short set of **pattern cards** — each a named shift ("From X to Y") with its signals, scores, counter-signals and a recommended next step — plus an interactive **pattern map**, and a state file so the next run can say what's changed.

## Modes

- **First run** — cluster a log from scratch.
- **Update** — the user has run this before (a `patterns.json` exists in the working folder, or they say "update the pattern map"). Cluster only the new signals, attach them to existing patterns where they fit, and report what's **growing, fading, new or merged**. Keep pattern IDs stable across runs.

## Inputs

| Input | Notes | Default |
|---|---|---|
| **Signals** | Any mix: a trend-signal-monitor `signals.md`, CSV, pasted links, bookmarks export, workshop notes | Ask for the file or folder |
| **Focus** | What the patterns are *for* — the organisation, its mission, a decision coming up | Ask once, briefly; a sentence is enough |
| **Current assumptions** | What the team believes about how the area is changing | If not given, draft 5–8 from their strategy or earlier reports, and ask the user to correct them. If there's nothing to go on, skip the assumption check and say so |
| **Time window** | Which signals count | Everything in the file |

## Process

### Step 1 — Ingest and normalise

Parse every signal into a record: `id`, `date`, `title`, `summary`, `source`, `url`, `strength` (if the log rates it), `geography`, `original topic`. The trend-signal-monitor format is:

```
**[Title]** | [Source](URL) | [Date] | Strength: [weak/medium/strong]
[One sentence: why this matters.]
```

Keep original ratings, but don't trust them blindly — Step 4 re-scores at the pattern level.

**Deduplicate**: the same event reported by several outlets is one signal with several sources. Note the extra sources; they count towards evidence strength, not momentum.

### Step 2 — Screen

Mark each record as one of:

- **Signal** — evidence of a change: an event, decision, launch, data point, study, behaviour shift, or unusual experiment
- **Context** — useful background but not evidence of change (explainers, restated old facts)
- **Noise** — off-focus, promotional, or opinion with no event behind it

Keep context and noise out of the clustering, but list them in the appendix with a reason. Never silently drop anything; a reader should be able to see what was set aside and why.

Also tag each signal with: **STEEP+ category** (Social, Technological, Economic, Environmental, Political, Legal, Values) and **type** (policy · market move · product/tech · data point · research · civic/community action · behaviour · counter-signal · wild card).

### Step 3 — Cluster by the change underneath

This is the core step. Work in two passes.

**Pass 1 — draft clusters.** For each signal, ask: *what is shifting, that this is evidence of?* Group signals that are evidence of the same shift, even if they look different on the surface — a council budget line, a retailer's rental launch and a survey result can all be evidence of one change. Do **not** group by topic label, source or category; "Policy signals" is a filing system, not a pattern.

Name each cluster as a **change statement**: *From [what was true] to [what is becoming true]*. If you can't write the "from" half, you haven't found a change yet — you've found a topic.

**Pass 2 — challenge the clusters.** Then critique your own draft:

- **Split grab-bags.** If a cluster needs "and" to describe it, it's probably two.
- **Merge near-duplicates.** Two clusters with the same "to" half are one.
- **Minimum size.** A cluster needs at least 3 signals, from at least 2 independent sources. Anything smaller stays an **outlier**.
- **Protect outliers.** Outliers are where weak signals live. Keep up to 5 of the most intriguing as named outliers with one line on what would have to be true for them to matter. Don't force them into a cluster to tidy up.
- **Check the count.** 5–10 patterns is usually right for a log of 30–150 signals. Fewer suggests clusters that are too broad; more suggests you're relabelling individual signals.

### Step 4 — Score each pattern

Score each pattern 1–5 on four dimensions using `references/scoring-rubric.md`. Show the reasoning in a phrase for each score, not just the number.

| Dimension | Question |
|---|---|
| **Momentum** | Is evidence arriving faster? Compare signal counts in the earlier and later halves of the window, and weight recent strong signals |
| **Spread** | Is it showing up across different sectors, places and types of actor, or only in one corner? Convergence from different directions is the strongest sign a pattern is real |
| **Novelty** | How far is this from what the team, and the mainstream conversation, already assume? |
| **Evidence** | How solid are the signals: primary sources, data and decisions, or commentary and press releases? |

Don't combine these into a single score. A pattern with high novelty and weak evidence is a different kind of thing — something to investigate — from one with high momentum and strong evidence, which is something to act on.

### Step 5 — Look for counter-signals

For each pattern, search the log — and, if web search is available, briefly search beyond it — for **evidence against it**: reversals, closures, failed pilots, data pointing the other way, credible critiques. Record them on the card.

A pattern with no counter-signals at all is suspicious, not reassuring. Say so if you looked and found none, and note the risk that the log's own sources are one-sided.

### Step 6 — Check against assumptions

Compare each pattern with the team's current assumptions. Label each assumption:

- **Supported** — the patterns back it up
- **Challenged** — one or more patterns cut against it
- **Untested** — the log contains nothing either way

Challenged assumptions are the headline of the whole exercise. Put them first in the summary. Untested assumptions point to gaps in what the scan is looking at.

### Step 7 — Check the scan itself

Signal logs have blind spots that come from how they were collected, not from the world. Report:

- **Category balance** — STEEP+ counts. A log that's 70% policy signals says as much about the search queries as about the world.
- **Source concentration** — any single source supplying more than about 15% of signals.
- **Geography** — where the signals come from, versus where the focus is.
- **Suggested queries** — 3–6 new search queries for the monitor that would fill the gaps or test the most novel patterns, and any queries that only produce noise and could be dropped.

### Step 8 — Recommend a next step for each pattern

Give each pattern one recommendation:

- **Act** — strong evidence, high momentum, clearly relevant: take it into planning now
- **Research** — high novelty or relevance but thin or contested evidence: investigate (a trend report, expert calls, a forecast question)
- **Watch** — plausible but early: add targeted queries to the monitor and revisit next run

For each, write **what would change the recommendation** — one observable development that would move it up or down a level.

### Step 9 — Critique

Before handing over, check:

- Every pattern is a change statement with a real "from", not a topic
- Every pattern has at least 3 signals from at least 2 independent sources
- Scores have reasons; nothing scores 5 without strong evidence behind it
- Counter-signals were looked for, and their absence is noted where relevant
- At least one pattern or outlier challenges a current assumption — if none does, say so plainly and ask whether the log is only collecting what the team already believes
- No signal appears in more than two patterns (if it does, the patterns probably overlap)
- Every link in the output comes from the log or was verified during Step 5

## Outputs

Write these to the user's working folder:

1. **`patterns-[slug].md`** — the report, following `references/output-template.md`: summary (challenged assumptions first), pattern cards, outliers, assumption check, scan health, appendix (all signals with their pattern, set-aside items with reasons).
2. **`patterns-[slug].html`** — the pattern map: copy `assets/pattern-map.html` and replace only the `DATA` object. Momentum on one axis, novelty on the other, dot size by number of signals, colour by recommendation, a ring on patterns that challenge an assumption, with cards and a table below. Open it in a browser to check it renders before handing over.
3. **`patterns.json`** — the state file for the next run (schema in `references/output-template.md`): pattern IDs, change statements, signal IDs, scores and the run date.

### Update mode output

Add a **"Since last time"** section at the top of the report:

- **Growing** — patterns whose momentum rose, with the new signals
- **Fading** — patterns with no new signals, or only counter-signals
- **New** — patterns that didn't exist last run (often a promoted outlier)
- **Merged or split** — with the old and new IDs
- **Assumptions whose status changed**

## Handoffs

If these skills are installed, offer the natural next step:

- **trend-report** — a deep dive on the strongest "Act" or most important "Research" pattern
- **scenario-builder** — use high-novelty, high-uncertainty patterns as driving forces
- **foresight** — turn a pattern's "what would change the recommendation" line into a forecast question
- **trend-signal-monitor** — add the suggested queries to the weekly scan

## Files

| File | Purpose |
|---|---|
| `SKILL.md` | This process |
| `references/scoring-rubric.md` | How to score momentum, spread, novelty and evidence |
| `references/output-template.md` | Report template and `patterns.json` schema |
| `assets/pattern-map.html` | Interactive pattern map; replace the `DATA` object |
| `examples/` | A complete worked example: a real signals log, the report, the map and the state file |
