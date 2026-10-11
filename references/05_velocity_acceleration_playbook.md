# Reference 05: Velocity Acceleration Playbook

*Source: Edward Sturm's "velocity acceleration protocols" (Ep. E1192). Accelerating past typical queues requires establishing domain authority, real user clickstream traffic, fresh contextual backlinks, and dense topical authority — forcing Google's real-time crawl scheduler to prioritize URL inspection. The authority bypass ceiling is demonstrated at §1.3 of the Matrix: fresh URLs ranking #1 in under 5 minutes on established entities.*

## 5.1 Doctrine: Acceleration Is Earned-State Engineering

The typical benchmarks in the Matrix apply to *average-priority* URLs. The scheduler maintains a real-time priority lane for high-authority, high-traffic, topically dense entities. Every lever below works by moving the asset up that priority ladder. None of them are tricks; all of them are the same signals Google's scheduler already measures, applied deliberately.

**Risk envelope:** acceleration levers compress *typical* windows; they do not repeal quality verdicts. A quality-rejected URL (`03_quality_vs_technical_diagnosis.md` §3.3) gains nothing from this playbook until the asset itself changes.

## 5.2 The Lever Inventory

| Lever | Window compressed | Mechanism | Risk / boundary |
|---|---|---|---|
| **L1. IndexNow (Bing & partners)** | Discovery on participating engines | Push-based submission bypasses crawl-discovery wait. **Google Search is not an IndexNow participant** — do not sell it as Google discovery acceleration. | Low risk; zero Google effect. Use for Bing-ecosystem freshness. |
| **L2. GSC URL Inspection + request indexing** | Google discovery/refresh on single URLs | Manually schedules crawl for the inspected URL; quota-limited (~10–12/day, section-level). | Legitimate for priority pages; not scalable to programmatic rollouts — bulk reliance reads as unnatural. |
| **L3. Internal link velocity** | Recrawl of changed pages | Fresh/re-positioned internal links from crawled-often pages (homepage, hub pages) put target URLs on a hotter recrawl cadence than the ~30d default. | Anchor/spam discipline applies; donors selected via `site:` harvest (`../../kirby-aiseo-skill/SKILL.md` §10.11). |
| **L4. XML sitemap hygiene + lastmod integrity** | Sitemap processing (row 4) | Accurate lastmod, canonical-only URLs, <50k/50MB per file, submitted at publish time. | Fake lastmod inflation erodes trust in the signal — never bump dates without real change. |
| **L5. Fresh contextual backlinks** | Discovery + crawl priority + quality evaluation | New external links from crawled-frequently pages trigger discovery of linked URLs and lift crawl priority. Acquisition execution: `../../kirby-off-page-seo/SKILL.md`. | Link velocity spikes on a cold domain are a footprint, not a lever (guardrails: `../../kirby-seo-deployment/SKILL.md` Module 7 velocity rules). |
| **L6. Real user traffic routing** | Scheduler priority (the bypass lane) | Genuine clickstream activity (email/social/nurture routing to the new asset) signals demand Google's scheduler weighs in real time. | Must be *real* users; traffic-bot inflation is detectable and penalizable. |
| **L7. Topical density completion** | Quality evaluation pass rate | Publishing the missing cluster siblings around the target URL raises the entity's topical authority, lifting per-URL quality evaluation outcomes. | Publish-to-accelerate must still clear per-URL utility bars (Scaled Content Abuse ladder: `../../kirby-aiseo-skill/SKILL.md` Exec Summary). |
| **L8. Crawl-budget decriminalization** | Global recrawl cadence | Prune index bloat, fix crawlable-parameters waste, consolidate duplicates — frees Googlebot capacity for the URLs that matter. | Pure infrastructure win; no downside. Audit: `../../kirby-aiseo-skill/SKILL.md` Module 1. |

## 5.3 Compression Protocol (per scenario)

**Scenario A — new priority page must be visible fast:**
L2 (immediate) + L3 (same-day internal links from hub donors) + L4 (sitemap with true lastmod). Expected: discovery inside hours-to-1-day instead of ~20h-plus-tail. Follow with L6 if the page has a real audience to route.

**Scenario B — title/snippet edits must land before the ~30d recrawl gate:**
L2 per edited URL (within quota) + L3 (link the edited URLs from a hot page). Expected: refresh in days, not the full 30d cycle.

**Scenario C — canonical switch must converge inside 1–3 weeks:**
Pre-clean all conflicting signals first (internal links, sitemap entries, 301 chains) — acceleration cannot outrank signal conflict (Matrix row 7 slow case). Then L2 + L4 on the canonical URL only; ensure the sitemap lists *only* canonicals.

**Scenario D — migration cutover must not stall:**
L4 at cutover (fresh sitemaps, canonical-only) + L3 re-pointing key internal links at cutover + L5 refresh of top external links where feasible. Then stay out of the way for the 1–3 month consolidation window (§4.4).

**Scenario E — quality-verdict rescue (asset not indexed for months):**
No acceleration applies. Change the asset (consolidate/differentiate/410) per `03_quality_vs_technical_diagnosis.md` §3.3, then re-enter via Scenario A.

## 5.4 What Does NOT Work (anti-patterns)

- **Sitemap resubmission spam** against a quality verdict — submission does not override deprioritization.
- **IndexNow as a Google fix** — wrong engine; Google is not a participant.
- **Mass GSC request-indexing on programmatic rollouts** — quota-bound and footprint-risky; bulk visibility is earned via L3/L5/L7, and pre-deploy gates (`../../kirby-seo-deployment/SKILL.md` Module 19) exist to make bulk pages index-worthy first.
- **Traffic inflation / bot clicks** — detectable; converts a timing problem into a penalty problem.
