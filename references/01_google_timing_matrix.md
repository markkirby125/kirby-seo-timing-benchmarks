# Reference 01: The Official Google Timing Matrix

*Source: Gary Illyes (Google Search Central), "How long does SEO take?" presentation, Search Central Live Deep Dive Europe, Barcelona, October 2, 2026. Digitized from Edward Sturm's analysis (The Edward Show, Ep. E1192, 8:50). These numbers ended two decades of "it depends" as the industry's standard answer.*

## 1.0 Confidence Tiers & Usage Rules

- **Tier 1 (press-corroborated):** rows independently reported by Search Engine Journal ("Google Shows How Long Crawling, Indexing & Recovery Take"), PPC Land (Oct 3, 2026), and Search Engine Roundtable recap tables. These may be quoted externally with source attribution.
- **Tier 2 (single-source):** rows digitized from the video dossier only. Treat as directional; corroborate before external citation.
- All figures are **indicative typical timeframes and slowest-case upper bounds** Google uses internally — not guarantees, not SLAs. Google's scheduler dynamically reprioritizes by quality, authority, and demand.
- **Never** quote a slowest-case figure as an expectation, and never quote a typical figure as a promise. Client-facing projections use the SLA framework in `04_client_sla_and_expectation_management.md`.

## 1.1 The Matrix (pipeline stages + adjacent processes)

Rows 1–7 track the sequential ingestion pipeline of Reference 02: rows 1–3 are its stages, and rows 4–7 are pipeline-gated processes that inherit the discovery/recrawl clock and may appear as downstream add-on terms in a stage-sum forecast. Rows 8–11 are adjacent processes with independent administrative clocks — never feed rows 8–11 into a stage-sum (Reference 02 §2.4).

| # | Process | Typical | Slowest Case | Tier | Notes |
|---|---|---|---|---|---|
| 1 | New URL discovery | ~20 hours | Weeks to never | 1 | Sitemap submission does not bypass discovery; low-quality URLs may never be discovered. |
| 2 | Recrawl of known URL | ~30 days (1 month) | Weeks to never | 1 | Googlebot's default refresh cadence for content it already holds. |
| 3 | Indexing pipeline latency (post-crawl) | from ~1.5 hours | Months to never | 1 | Press corroboration phrases this as "**from** 1.5 hours" — a floor/start latency, not a mean duration. The pipeline is fast by construction; "months or never" signals quality failure, not queue backlog (see `03_quality_vs_technical_diagnosis.md`). |
| 4 | XML sitemap processing | ~24 hours (1 day) | Up to 14 days or never | 2 | Stale, error-ridden, or low-trust sitemaps fall to the slow tail. |
| 5 | Page title changes in SERPs | 1–2 days | Several weeks to months | 2 | Constrained by the recrawl cadence of row 2. |
| 6 | Search snippet changes | 1–2 days | Several weeks to months | 2 | Same recrawl dependency as row 5. |
| 7 | Canonical changes | 1–3 weeks | Months | 2 | Extends when conflicting signals persist: internal links to deprecated URLs, sitemaps listing non-canonicals, conflicting 301s. |
| 8 | Site migrations | 1–3 months | 6 months to 1+ year | 1 | Full consolidation including signal transfer; see `04_client_sla_and_expectation_management.md` §4.4. |
| 9 | Core update recovery | 3–6 months | 6–12 months | 1 | Macro site-quality recalculations generally do not update until Google deploys the **next** core update. |
| 10 | Manual action removals | 1–2 weeks | 4–6 weeks+ | 2 | Dormant/low-activity sites suffer the slow tail. |
| 11 | GSC URL removals | ~2 hours | Up to 24 hours | 2 | The only near-real-time process in the Matrix. |

## 1.2 The Two Asymmetries That Matter

1. **Pipeline speed vs. queue speed.** The indexing pipeline itself (from ~1.5 hours) is roughly 13x faster than new-URL discovery (~20 hours) and ~480x faster than recrawl (~30 days). When diagnosing delays, the bottleneck is almost never the pipeline — it is discovery or recrawl scheduling upstream of it (see `02_sequential_delay_compounding.md`).
2. **Typical vs. never.** Every row's slowest case terminates in "never" or "1+ year." The slow tail is not a longer queue; it is a different mechanism — quality-based deprioritization. This is the single most consequential insight of the Illyes disclosure: **"months or never" is a verdict, not a delay** (`03_quality_vs_technical_diagnosis.md` §3.3).

## 1.3 The Authority Bypass

Authoritative websites with real user traffic and topical relevance can bypass these timelines entirely — Sturm demonstrates fresh URLs ranking #1 above legacy news publications in under 5 minutes. The scheduler operates a real-time priority lane keyed on domain authority, clickstream traffic, fresh contextual backlinks, and topical density. This bypass is a *earned state*, not a tactic: the levers that build it are in `05_velocity_acceleration_playbook.md`, and the ceiling is governed by off-site authority (execution: `../../kirby-off-page-seo/SKILL.md`).

## 1.4 Quick Lookup: Common Questions → Row

| Question | Answer row |
|---|---|
| "I published hours ago and the page isn't in Google" | Row 1 (~20h typical) — wait before escalating |
| "I fixed my titles but SERPs show the old ones" | Rows 5–6, gated by row 2 (~30d recrawl) |
| "My sitemap has been 'processing' for days" | Row 4 (up to 14 days) |
| "301s are in place but canonicals haven't switched" | Row 7 (1–3 weeks; check for signal conflicts) |
| "We migrated and traffic hasn't recovered" | Row 8 (1–3 months typical; escalate past 6) |
| "We improved the site after the core update — when?" | Row 9 (3–6 months, likely gated on next core update) |
| "Reconsideration request accepted — when do rankings return?" | Row 10 (1–2 weeks) |

## 1.5 Source Manifest

| Source | Type | Date | Confirms |
|---|---|---|---|
| Gary Illyes presentation, Search Central Live Deep Dive Europe (Barcelona) — event announcement: `developers.google.com/search/blog/2026/07/search-central-live-deep-dive-europe-2026` | Primary (presentation, not published proceedings) | Oct 2, 2026 | The disclosure event itself |
| Edward Sturm, The Edward Show Ep. E1192 — `youtu.be/sRZizu5mi_c` | Full-matrix analysis (digitization source for all 11 rows) | Oct 2026 | Rows 1–11 incl. Tier 2 rows |
| Search Engine Journal, "Google Shows How Long Crawling, Indexing & Recovery Take" | Press recap | ~Oct 4, 2026 | Rows 1, 2, 8, 9 (headline ranges) |
| PPC Land, "Google says new pages take about 20 hours to be found, some never are" | Press recap | Oct 3, 2026 | Rows 1, 9 (and 1–3 month other-recovery framing) |
| Search Engine Roundtable, "Google Search Data On Crawling, Indexing & Serving" (recap table) | Press recap | ~Oct 5, 2026 | Rows 1–2 typical + slow ranges |
| Palai Media, "How Long Google Indexing Takes: Internal Benchmarks" | Press recap | ~Oct 5, 2026 | Row 3 as "**from** 1.5 hours" (start-latency framing) |
| Google Search Central docs, "Google Search's Core Updates" — `developers.google.com/search/docs/appearance/core-updates` | Standing documentation | current | Row 9 consistency ("could take several months") |

**Provenance note:** press recaps corroborate the headline rows; rows 3–7, 10–11 rest on the video analysis as digitized here. The 13x/480x arithmetic in §1.2 is this skill's derivation, not Google's. When quoting externally, attribute the primary presentation and the tier per this manifest.
