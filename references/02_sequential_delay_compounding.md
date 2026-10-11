# Reference 02: Sequential Delay Compounding (The Pipeline Stacking Law)

*Source: Edward Sturm's architectural analysis of the Illyes Oct 2026 benchmarks (Ep. E1192).*

## 2.1 The Pipeline Is Strictly Sequential

Google's organic ingestion pipeline has a fixed order:

```
Discovery -> Crawling -> Rendering -> Quality Evaluation -> Indexing -> Serving
```

No stage begins until the prior stage completes for a given URL. This is the Pipeline Stacking Law: **delays in upstream stages compound multiplicatively into every downstream stage.** If discovery stalls for two weeks, indexing cannot even trigger — a URL cannot be "fast at indexing" while it is slow at discovery.

## 2.2 The Compounding Model

For any change you want reflected in Search (new page, title edit, canonical switch, migration), compute the total expected latency as the sum of the sequential stages it must traverse:

| Change type | Stages traversed | Expected typical latency |
|---|---|---|
| New page appears in Search | Discovery + Crawl + Index | ~20h + pipeline (~1.5h index path) ≈ ~1 day; do not promise faster |
| Title/meta edit on indexed page | Recrawl + Reindex + Serve | ~30d recrawl gate + 1–2d SERP refresh |
| Canonical switch | Recrawl + Re-consolidation | ~30d recrawl gate + 1–3wk canonical convergence |
| Site migration | Full pipeline per URL + signal transfer | 1–3 months typical (row 8) |

**Rules of use:**
1. Never quote a downstream figure (e.g., "titles refresh in 1–2 days") without first checking the upstream gate (recrawl at ~30 days for an average page). The Matrix's title/snippet row assumes the page is already being recrawled on a hot cadence.
2. Crawl-budget bottlenecks shift everything downstream: a site whose crawl capacity is saturated converts routine 1–2 day title changes into multi-month waits. If a trivial change is taking months, audit crawl capacity **before** blaming quality — but run the audit as *diagnosis only* (per `03_quality_vs_technical_diagnosis.md` §3.1–§3.2); never run infrastructure fixes and content remediation on the same asset concurrently.
3. When forecasting, present ranges as **stage sums**, not single numbers, so the client sees where time actually goes.

## 2.3 Upstream Crawl Debt: Identification

Symptoms that the true bottleneck is upstream (discovery/recrawl) rather than content quality:
- GSC "Discovered - currently not indexed" accumulating (discovery succeeded; crawl scheduling has not) — wait benchmark: weeks; escalate per `../../kirby-seo-telemetry/SKILL.md` Module 12 thresholds.
- GSC "Crawled - currently not indexed" (crawl succeeded; quality evaluation is the gate) — this is usually *not* crawl debt; route to `03_quality_vs_technical_diagnosis.md` §3.3.
- Log-file evidence of declining Googlebot hit rate on sections you just updated.
- Sitemap last-discovered dates lagging publication dates by more than the row 4 window (14 days).

## 2.4 Forecast Construction Protocol

1. Identify the change type and its stage chain (§2.2 table).
2. For each stage, look up typical and slowest-case values in `01_google_timing_matrix.md`.
3. Apply environment modifiers (crawl budget saturation, site authority tier, index bloat, log-reported crawl rate).
4. Sum stages for the forecast; quote the **typical sum** as the planning number and the **slowest-case sum** as the risk envelope, per the SLA rules in `04_client_sla_and_expectation_management.md` §4.2.
5. Never subtract from the sum without an explicit acceleration lever from `05_velocity_acceleration_playbook.md` — optimism is not a lever.
