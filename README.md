# Signal Clustering

A skill for [Claude Code](https://docs.anthropic.com/en/docs/agents-and-tools/claude-code/overview) and [Cowork](https://claude.ai) that turns a pile of collected signals into a small set of named emerging patterns. The pile can be a horizon-scanning log, a weekly signal-monitor file, bookmarks or workshop notes. Each pattern is scored, checked against evidence that cuts the other way, and compared with what your team currently assumes. Run it again later and it tells you which patterns are growing, fading or new.

## What it does

1. **Reads and tidies the log**: parses each signal and merges duplicate reports of the same event.
2. **Screens**: separates real signals of change from background and noise, listing what it set aside and why.
3. **Clusters by the change underneath**, not by topic. Each pattern is named as a shift, "From X to Y". A second pass splits grab-bags, merges near-duplicates, enforces a minimum of three signals from two sources, and protects intriguing outliers rather than forcing them into a cluster.
4. **Scores each pattern on four separate dimensions**: momentum, spread, novelty and evidence, with a reason for every score.
5. **Looks for counter-signals**, and flags patterns where it found none, because that's suspicious.
6. **Checks your assumptions**, marking each as supported, challenged or untested. Challenged assumptions lead the report.
7. **Checks the scan itself**: category balance, over-relied-on sources and geography, plus new search queries to fill the gaps.
8. **Recommends a next step** for each pattern (act, research or watch) and says what would change that recommendation.

It outputs a Markdown report, an interactive pattern map and a `patterns.json` state file. The state file is what lets the next run report changes over time.

See [`examples/`](signal-clustering/examples/) for a complete worked example. It's a real 54-entry log on repair, reuse and sharing in the UK and Europe, with every signal a real, linked item, clustered into patterns. It includes the report, the pattern map (GitHub shows HTML as code, so download it and open it in a browser) and the state file.

## Installation

**Ask Claude to set it up for you.** If you're using Claude Code or Claude Cowork, you can just say something like *"install the signal-clustering skill from github.com/greencat667/signal-clustering-skill-claude"* and Claude will clone the repo and put it in the right place. You don't need to do this by hand.

Or do it yourself: copy the `signal-clustering/` folder into your project's `.claude/skills/` directory:

```bash
git clone https://github.com/greencat667/signal-clustering-skill-claude.git
cp -r signal-clustering-skill-claude/signal-clustering/ your-project/.claude/skills/signal-clustering/
```

Claude will pick it up automatically the next time you start a session.

## Example prompts

Once installed, just ask Claude something like:

> "Cluster the signals in `horizon/signals.md` into emerging patterns. We're a housing charity; our working assumptions are that councils will keep cutting homelessness prevention and that private renting keeps shrinking."

And a month later:

> "Update the pattern map with this month's signals. What's growing and what's fading?"

## A note on what this is

The patterns are only as broad as the log. A scan that only searches the places a team already looks will mostly confirm what the team already believes. That's why the skill reports on the scan's own blind spots and treats "no assumption challenged" as a warning, not a clean bill of health. The clustering is an AI-assisted judgement; discuss it as a team before acting on it.

## Pairs well with

- [trend-signal-monitor](https://github.com/greencat667/trend-signal-monitor-skill-claude) — collects the signals this clusters, in a format it reads directly
- [trend-report](https://github.com/greencat667/trend-report-skill-claude) — a deep dive on the strongest pattern
- [scenario-builder](https://github.com/greencat667/scenario-builder-skill-claude) — use high-novelty patterns as driving forces
- [foresight](https://github.com/greencat667/foresight-skill-claude) — turn "what would change this" into forecast questions

## Repository structure

```
signal-clustering-skill-claude/
├── signal-clustering/
│   ├── SKILL.md                       # Copy this folder to .claude/skills/
│   ├── references/
│   │   ├── scoring-rubric.md          # Momentum, spread, novelty, evidence
│   │   └── output-template.md         # Report template and patterns.json schema
│   ├── assets/
│   │   └── pattern-map.html           # Interactive map template
│   └── examples/
│       ├── repair-reuse-signals.md    # The input: a real signals log
│       ├── patterns-repair-reuse.md   # The report
│       ├── patterns-repair-reuse.html # The pattern map
│       └── patterns.json              # The state file for the next run
├── README.md
├── CONTRIBUTING.md
└── LICENSE
```

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md). Note that this repo isn't actively maintained, so responses to issues and PRs will be slow or may never come.

## License

MIT — see [LICENSE](LICENSE).
