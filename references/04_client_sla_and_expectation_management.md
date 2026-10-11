# Reference 04: Client SLA & Expectation Management

*Application of the Illyes Oct 2026 benchmarks (Ep. E1192 analysis) to governance: contracts, SLAs, migration schedules, and recovery projections. These numbers eliminate guesswork when diagnosing stalled assets, managing client expectations, and planning architectural migrations.*

## 4.1 The SLA Doctrine

1. **Never sell a Google-side timeline as a deliverable.** The Matrix describes Google's pipeline, which you influence but do not control. SLAs cover *your* actions (audit complete in N days, fixes deployed by date X), with Google-side expectations quoted separately as planning ranges.
2. **Quote typical as the plan, slowest-case as the risk envelope**, and always name the gate: "title refreshes typically land in 1–2 days *after recrawl*, and recrawl of an established page runs ~30 days — so our planning window is 4–6 weeks."
3. **Bundling rule:** any client-facing timeline for a change = stage-sum forecast (per `02_sequential_delay_compounding.md` §2.4) + one explicit acceleration lever if used (per `05_velocity_acceleration_playbook.md`), never silent optimism.
4. **The 'never' conversation:** contracts must acknowledge the quality verdict tail (Matrix §1.2). Promising eventual indexation of an asset Google has quality-rejected is the #1 source of failed SEO retainers.

## 4.2 Contract SLA Templates (adapt per engagement)

**Content/refresh retainer:**
- Agency SLA (own actions): audit within 5 business days; fixes staged within 10; deployment per `../../kirby-seo-deployment/SKILL.md` velocity rules.
- Expectation annex (Google-side, non-binding): new-URL discovery ~20h typical / weeks+ slow tail; recrawl ~30d; title & snippet SERP refresh 1–2d post-recrawl / weeks-months slow; client informed that slow tails indicate quality verdicts requiring asset change, not waiting.

**Site migration engagement (see §4.4):**
- Expectation annex: signal consolidation 1–3 months typical; 6 months to 1+ year slow case; traffic parity checkpoints at 30/60/90 days; formal escalation at 6 months.
- Liability carve-out: post-migration ranking variance within the consolidation window is pipeline behavior, not agency error, absent a technical defect on the checklist.

**Core-update recovery engagement:**
- Expectation annex: 3–6 months typical, and *gated on Google's next core update deployment* — remediation quality is necessary but the macro recalculation is Google's schedule (row 9). Set review checkpoints aligned to known core-update cadence, not weekly ranking reports.

## 4.3 Expectation-Setting Scripts

- "How long until we see results?" → Quote row-appropriate stage sums: "New content is typically discoverable in about a day and indexable within hours after that — *if* the site is being crawled healthily. For changes to existing pages, Google refreshes on roughly a 30-day cycle, so we plan on 4–6 weeks to see title and snippet updates land."
- "Our competitor outranked us with a fresh page in minutes." → Explain the authority bypass (`01_google_timing_matrix.md` §1.3): earned priority, not a tactic; the path is authority + real traffic + topical density over time.
- "It's been 3 months, nothing changed." → Run the triage protocol (`03_quality_vs_technical_diagnosis.md` §3.2) before any statement; if classified as quality verdict, present the asset-change options, not a wait-and-see.

## 4.4 Migration Scheduling Framework

Benchmark anchors: **1–3 months typical, 6 months to 1+ year slowest** (Matrix row 8); canonical consolidation adds 1–3 weeks post-cutover (row 7) under clean signals.

1. **Pre-migration (T-minus):** freeze URL taxonomy; map all redirects 1:1; purge conflicting canonical signals (internal links to deprecated URLs, sitemaps listing non-canonicals, chained 301s) — the canonical lag extends to *months* when mixed signals persist.
2. **Cutover:** single-event flip (staging doctrine: `../../kirby-seo-deployment/SKILL.md` Module 7 / Module 20); regenerate and submit XML sitemaps at cutover (processing: ~24h typical, 14d slow); expect the ~20h discovery cadence to re-fire against the new URL space.
3. **Consolidation window (months 1–3):** monitor GSC coverage migration of old→new, canonical resolution, and crawl-rate transfer. Do not layer new architecture changes on top mid-window.
4. **Escalation (month 6+):** traffic materially below pre-migration baseline at 6 months triggers the §3.4 escalation — full technical re-audit plus per-template quality review; beyond 6 months the slow-case window is exhausted and the deficit is yours or the asset's, not Google's queue.

## 4.5 Reporting Cadence Alignment

Report *leading* indicators inside Google's windows, not lagging outcomes outside them: crawl stats and discovery events (daily), coverage transitions (weekly), canonical resolution (weekly), ranking/traffic deltas (monthly, with core-update gating noted on row 9 recoveries). Instrumentation: `../../kirby-seo-telemetry/SKILL.md` Module 12.
