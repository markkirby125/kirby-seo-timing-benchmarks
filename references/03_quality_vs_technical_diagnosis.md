# Reference 03: Quality vs. Technical Diagnosis (Stall Triage Protocol)

*Source: Edward Sturm's analysis (Ep. E1192) of the Illyes benchmarks. Core insight: when a URL experiences "months or never" for indexing, recrawling, or sitemaps, it is rarely a technical queue failure — it is an algorithmic quality rejection.*

## 3.1 The Two Failure Classes

| Class | Mechanism | Evidence pattern | Remedy owner |
|---|---|---|---|
| **Technical delay** | Pipeline stage slow or blocked: robots/WAF blocks, noindex tags, canonical conflicts, redirect chains, crawl-budget saturation, orphaned URLs | Failure is *uniform* across a section or template; log files show missing/deferred crawls; GSC reports a concrete blocker | Dev / infrastructure |
| **Quality rejection** | Google's scheduler actively deprioritizes low-utility, duplicate, or unverified content; the URL sits past its benchmark window with no technical blocker | Failure is *selective* (same template, some URLs indexed, some not); no blocker in GSC; age far exceeds Matrix row 1–4 slowest cases | Content / strategy |

**Do not run both remediation tracks at once.** Misdiagnosis is expensive: quality problems are never fixed by infrastructure work, and technical problems are never fixed by rewriting content.

## 3.2 Triage Protocol (run in order)

1. **Benchmark clock check.** Has the asset actually exceeded its Matrix window? (New URL: >14 days since publication with sitemap submitted and still zero discovery signals → continue; else wait. Title change: check the ~30d recrawl gate first.)
2. **Blocker scan (technical pass).** robots.txt / meta robots / X-Robots-Tag, WAF/CDN rules throttling Googlebot (see `../../kirby-aiseo-skill/SKILL.md` Module 1 WAF/CDN AI-crawler audit), noindex inherited from template, canonical pointing elsewhere, redirect chains, orphan status (no internal links), sitemap presence and validity.
3. **Uniformity test.** Compare fate of URLs sharing the template/folder. Uniform failure → technical or template-level quality issue. Mixed failure → page-level quality rejection on the failing subset.
4. **Crawl-budget audit.** Log files: is Googlebot visiting the section at all? Saturated capacity → raise priority via internal-link weight, prune index bloat (execution guidance: `../../kirby-aiseo-skill/SKILL.md` Module 1).
5. **Quality verdict.** All technical checks clean, benchmarks exceeded, crawl visits observed, still not indexed → classify as **algorithmic quality rejection**. Proceed to §3.3.

## 3.3 "Months or Never" Is a Verdict, Not a Delay

- The slow tail of Matrix rows 1–4 terminates in **never**. Google's scheduler does not hold low-quality URLs in an infinitely long queue — it deprioritizes them out of the pipeline entirely.
- The correct response is not more waiting and not more submission (resubmitting a sitemap does not override a quality verdict). The correct response is to **change the asset**: consolidate, differentiate, add verifiable utility, or cut it (410/404 doctrine: `../../kirby-seo-deployment/SKILL.md` §7.7 — 410 drops dead URLs ~2x faster than passive 404s).
- For location/template pages specifically, `Crawled - currently not indexed` is classified as a **differentiation deficit** — route to `../../kirby-local-seo/SKILL.md` Module 7 (Gate 0 + 10-rule framework), and audit per `../../kirby-seo-telemetry/SKILL.md` Module 11.
- For undifferentiated scaled content generally, the Scaled Content Abuse demotion ladder (Module 1, 3–9 month post-purge recovery baseline) and the Grokipedia 97% collapse quarantine protocol (Module 17) are in `../../kirby-aiseo-skill/SKILL.md`.

## 3.4 Escalation Table

| Observation | Elapsed vs. Matrix | Classification | Route |
|---|---|---|---|
| URL undiscovered, no GSC record, sitemap clean | > 14 days | Discovery stall | Technical pass (§3.2 step 2–4) → if clean, quality |
| Discovered - not indexed, uniform across folder | > 14–21 days | Crawl-scheduling debt or template quality | §3.2 steps 3–4 |
| Crawled - not indexed, selective | Any | Page-level quality rejection | §3.3; location pages → `../../kirby-local-seo/SKILL.md` M7 |
| Title/snippet unchanged in SERPs | > 60 days (past 30d recrawl + 1–2d refresh) | Crawl deprioritization | Crawl-budget audit (§3.2 step 4); if capacity is fine → quality |
| Canonical still unresolved | > 8 weeks | Signal conflict | Audit internal links / sitemap / 301 conflicts (Matrix row 7) |
| Post-migration traffic flat | > 6 months | Migration quality failure | `04_client_sla_and_expectation_management.md` §4.4 escalation |

## 3.5 Interaction with Telemetry Thresholds

Stall detection instrumentation (GSC exports, threshold alerts at the Matrix boundaries) is implemented in `../../kirby-seo-telemetry/SKILL.md` Module 12. This reference defines *what* the thresholds mean and *which class* of failure they indicate; telemetry defines *how* they are monitored and alerted.
