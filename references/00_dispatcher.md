# Kirby SEO Timing Benchmarks - Dispatcher

This skill handles SEO timeline forecasting, stall triage, and velocity acceleration based on Google's official October 2026 processing-pipeline benchmarks (Gary Illyes, Search Central Live Deep Dive Europe, Barcelona, Oct 2, 2026; digitized from Edward Sturm / The Edward Show Ep. E1192 with independent press corroboration — see `01_google_timing_matrix.md` §1.0).

## 📚 Reference Index
- **01: The Official Google Timing Matrix** -> Read `./01_google_timing_matrix.md` (the 11-process benchmark table, typical vs. slowest-case ranges, corroboration status, and confidence tiers)
- **02: Sequential Delay Compounding** -> Read `./02_sequential_delay_compounding.md` (the pipeline-stacking law; modeling upstream crawl debt that cascades into downstream stalls)
- **03: Quality vs. Technical Diagnosis** -> Read `./03_quality_vs_technical_diagnosis.md` (triage protocol separating infrastructure delays from algorithmic quality rejection)
- **04: Client SLA & Expectation Management** -> Read `./04_client_sla_and_expectation_management.md` (governance frameworks, contract SLA templates, migration schedules, recovery projections)
- **05: Velocity Acceleration Playbook** -> Read `./05_velocity_acceleration_playbook.md` (tactical protocols to compress timeframes: authority signals, internal link velocity, IndexNow, real-traffic routing, and §5.5 Late-Mover Crawl Acceleration for seasonal/promotional resets)

## When to Use
- A stakeholder asks "how long will SEO take?", "why isn't my page indexed yet?", or "when will we recover from the core update?" and you need empirical ranges instead of "it depends" (Matrix: `01_google_timing_matrix.md`).
- You are forecasting a launch, content refresh, or migration schedule and must commit dates or budgets (apply the compounding model in `02_sequential_delay_compounding.md` before quoting anything from the Matrix).
- You are triaging a stalled asset (URL not discovered, not crawled, not indexed, or changes not reflected in SERPs) and must decide: technical fix vs. quality remediation vs. wait (protocol: `03_quality_vs_technical_diagnosis.md`).
- A URL, recrawl, or sitemap has been pending for "months or never" — classify it as a suspected algorithmic quality rejection, not a queue failure (`03_quality_vs_technical_diagnosis.md` §3.3).
- You are drafting or auditing client contracts, SLAs, or expectation-setting documents for SEO deliverables (`04_client_sla_and_expectation_management.md`).
- You are planning a site migration and need the realistic 1–3 month typical / 6 months-to-1+-year slow-case window plus the pre-migration checklist (`04_client_sla_and_expectation_management.md` §4.4; operational migration execution is `../../kirby-seo-deployment/SKILL.md` Module 20).
- You are projecting recovery from a core update (3–6 months typical, gated on the *next* core update) or a manual action (1–2 weeks typical; dormant sites suffer) (`01_google_timing_matrix.md` rows 9–10).
- You need to compress any of these windows and want sanctioned acceleration levers (authority, link velocity, IndexNow, real traffic) with their risk envelopes (`05_velocity_acceleration_playbook.md`).
- You are launching seasonal or promotional landing pages on a compressed timeline (1–2 weeks before peak events) and require the Late-Mover Crawl Acceleration Protocol to force Googlebot discovery and indexing via global navigation and homepage Viewport 1 anchors within 6–12 hours (`05_velocity_acceleration_playbook.md` §5.5).

## Routing Boundaries (do not duplicate sibling skills)
- **Detecting** stalls from GSC telemetry (threshold alerts, coverage deltas) lives in `../../kirby-seo-telemetry/SKILL.md` Module 12. This skill defines the thresholds and the diagnosis; telemetry instruments them.
- **Deploying** migrations under timing benchmarks (staging, cutover, monitoring windows) lives in `../../kirby-seo-deployment/SKILL.md` Module 20. This skill supplies the schedule math.
- **Launch milestone calibration** for a brand-new site (Day 1 discovery spike, sitemap processing, canonical consolidation) lives in `../../kirby-zero-to-100-seo/SKILL.md` Module 2, which consumes this skill's Matrix.
- **Title/snippet refresh expectations** after the 1-Hour SEO Update live in `../../kirby-aiseo-skill/SKILL.md` Module 16, aligned to the Matrix's 1–2 day propagation reality.
- Off-site authority building (the input to velocity acceleration) is executed by `../../kirby-off-page-seo/SKILL.md`; this skill only specifies the timing leverage.

## Confidence Doctrine
All Matrix figures are **indicative typical ranges and upper bounds**, not contractual SLAs from Google. Rows corroborated by independent press coverage are Tier 1; rows resting solely on the video analysis are Tier 2 (single-source, directional). Never quote a figure to a client without its tier (`01_google_timing_matrix.md` §1.0).
