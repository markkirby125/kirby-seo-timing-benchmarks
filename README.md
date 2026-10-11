# SEO Timing Benchmarks (Kirby)

[![Kirby Skills Collection](https://img.shields.io/badge/Kirby_Skills-Collection-blue?style=flat-square&logo=github)](https://github.com/markkirby125/kirby-skills-collection)

"How long does SEO take?" For twenty years the honest answer was "it depends." On October 2, 2026, Google Search Central's Gary Illyes ended the ambiguity at Search Central Live Deep Dive Europe (Barcelona), presenting internal benchmark data for indicative typical timeframes and slowest-case upper bounds across Google's entire organic processing pipeline — discovery, recrawl, indexing, sitemaps, titles/snippets, canonicals, migrations, core update recovery, manual actions.

**The problem:** without empirical anchors, SEO forecasting is guesswork, stalled assets get misdiagnosed as "Google being slow" when they are quality-rejected, migration contracts quote fantasy timelines, and client expectations collapse at week 6 of a 3-month consolidation window that is behaving exactly on schedule.

**The solution:** the `kirby-seo-timing-benchmarks` skill digitizes the official timing matrix with confidence tiers, models sequential delay compounding so forecasts are stage-sums instead of vibes, separates technical delays from algorithmic quality verdicts with a deterministic triage protocol, converts the numbers into client SLA and migration governance frameworks, and catalogs the sanctioned levers (internal link velocity, IndexNow's real scope, sitemap hygiene, authority signals) that compress windows — with the anti-patterns that convert timing problems into penalty problems.

Source: Gary Illyes (Google), Oct 2, 2026; analyzed by Edward Sturm (The Edward Show E1192); headline figures corroborated by Search Engine Journal, PPC Land, and Search Engine Roundtable coverage.

## 🪄 The Magic Prompt

Copy and paste this directly to your AI (Cursor, Windsurf, Claude Code, Antigravity):

```markdown
@agent Please install the kirby-seo-timing-benchmarks skill into this workspace.
1. Read the `SKILL.md` file and `references/` directory from this repository: https://github.com/markkirby125/kirby-seo-timing-benchmarks
2. Identify the correct rules system for our current environment (e.g., `.cursor/rules/` for Cursor, `.windsurfrules` for Windsurf, `.clinerules` for Cline, or `~/.agents/skills/` for Antigravity).
3. Save the contents appropriately. If our environment supports multi-file dispatcher skills, clone the directory structure exactly.
4. Confirm when the installation is complete.
```

## Manual Installation

- **Cursor**: Save `SKILL.md` to `.cursor/rules/kirby-seo-timing-benchmarks.mdc` and copy `references/` alongside it.
- **Windsurf**: Append `SKILL.md` to `.windsurfrules`; copy `references/` into the project.
- **Claude Code / Antigravity**: Clone into `~/.agents/skills/kirby-seo-timing-benchmarks/`.
- **Any AI app**: Keep `SKILL.md` and `references/` together; the skill instructs the agent to read the dispatcher before acting.

## What's Inside

| Reference | Purpose |
|---|---|
| `references/00_dispatcher.md` | Master routing: timing lookups & forecasts, stall triage, migration schedules, recovery roadmaps, SLA governance |
| `references/01_google_timing_matrix.md` | The 11-process benchmark table with confidence tiers and quick-lookup |
| `references/02_sequential_delay_compounding.md` | Pipeline stacking law; stage-sum forecasting |
| `references/03_quality_vs_technical_diagnosis.md` | Stall triage: infrastructure delay vs. algorithmic quality verdict |
| `references/04_client_sla_and_expectation_management.md` | Contract SLA templates, migration schedule framework, recovery projections |
| `references/05_velocity_acceleration_playbook.md` | Sanctioned acceleration levers + anti-patterns |
