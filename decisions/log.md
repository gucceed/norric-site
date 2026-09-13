# norric-site · decisions log

Append-only. Newest entry at top. Each entry: decision · reversibility · review trigger.

---

## 2026-09-13 — September 2026 trim: half-built surfaces cut, public claims aligned to live state

**Decision.** Edgar: "Trim goes ahead to have the site current and professional. It's a poor reflection on me to keep half baked products up." Applied on branch `trim-sep-2026`, pending his PR review and merge:

- **Pulse cut.** Banner, nav link, indices framework section, Water Rights callout, and all copy references removed. No issue has ever shipped and `/pulse` 404s.
- **Vattendom cut.** Homepage card removed; `vattendom/` page and the `vattendom.norric.io` host rewrite deleted. No data, no API, no domain; "first data Q3 2026" was about to expire unmet.
- **`developer-docs.html` deleted.** Stale v1.0 docs (19 tools, `nk_prod_` keys, Denmark/Norway 2027) and exposed internal strategy: pricing logic, LTV math, named target banks, valuation roadmap. `/api-keys` pricing links retargeted to `/docs#pricing`.
- **`norric-architecture.html` deleted.** Public internal GTM strategy (Fortnox marketplace, Konsult pricing and client counts, named branschorg partners).
- **Build priorities queue and brand-system sections cut** from the homepage; internal roadmap does not belong on the public site. "IP holding structure" and "Institutional cadence" moat cells cut (tax/exit internals; Pulse cadence claim was false).
- **Claims aligned to verified live state** (checked 2026-09-13 against `mcp.norric.io/health` and the norric-mcp source): Kreditvakt "Live · ingestion operational" is true again (2,685 companies tracked, pipelines fresh); Sigvik 33,710 BRFs verified; SIGNAL relabelled "Building · MCP tools live" (data activation pending, munisignal.polsia.app link removed - it shows a US municipal product); MCP endpoint canonicalised to `mcp.norric.io`; API key format unified to `nrk_` (per `issuance/key_gen.py`); Kreditvakt score documented as 0-20 (per `kreditvakt/api.py` `"scale": "0-20"`), docs example fixed.
- **Specific prices removed site-wide** (299/499 kr in docs, SEK 990/2,990 in api-keys, "outcome-based" on the homepage) pending Edgar's canonical pricing decision and the unresolved KuL licensing question. Paid tiers now read "on request".
- **False mechanics fixed:** "keys issued immediately/automatically" claims removed (the api-keys form is a mailto); "issued within 24 hours" applies to all tiers.
- **Org.nr placeholder `[Norric AB]` removed** per Edgar's standing decision (no number until funding); dates refreshed May to September 2026; holding-company internals stripped.

**Reversibility.** High. Everything sits on branch `trim-sep-2026`; nothing deploys until Edgar merges. `git revert` of the merge commit restores the exact prior site. Deleted files remain in git history.

**Review trigger.** Edgar's merge decision is the review. After merge: re-add Vattendom only when first real ingestion exists; restore pricing only after Edgar picks the canonical table and settles KuL.

**Open items at decision time.**
- Canonical pricing table still Edgar's call.
- The api-keys form is a mailto to a personal Gmail; consider `hej@norric.io` (used in the kreditvakt API) once that mailbox is confirmed monitored.
- SIGNAL/Sigvik tool scores in docs still say 0-100; unverified against the server (only Kreditvakt's 0-20 was code-verified).

---

## 2026-05-16 — May 2026 pivot: norric.io repositioned as "private statistical authority for commercial Sweden"

**Decision.** Replaced pre-pivot marketing surface with the May 2026 positioning. Mission updated, indices framework introduced, Pulse banner surfaced. Portfolio rationalised: Jarvis, SiteLoop, Norric Vigil, LeadFlow AI, Betalningskollen all removed from marketing surface (Vigil sensors migrated into Kreditvakt's early-warning tier; the other four killed or out of scope for norric.io). Norric Vattendom added to portfolio at "Building · ingestion in flight" status. SIGNAL retained on munisignal.polsia.app pending rebrand. Pulse routed to `/pulse` page (not subdomain).

**Files changed.** `index.html`, `docs.html`, `developer-docs.html`, `norric-architecture.html`. CSS preserved verbatim; no dependency or design-token changes.

**Reversibility.** Medium. `git revert` to pre-pivot HEAD `3a03224` restores the prior site exactly. Reversible without data migration or third-party coordination.

**Review trigger.** 90 days from today (2026-08-14), or any of: (a) inbound buyer signal requiring repositioning, (b) major regulatory shift in any sensor's source authority, (c) Vattendom reaches Pilot status (requires portfolio card update).

**Open items at decision time.**
- PR pending manual open at `github.com/gucceed/norric-site/pull/new/pivot-may-2026` (`gh` CLI auth broken at deploy time).
- Lighthouse + 380px mobile verification deferred until post-deploy.
- §11 numerical accuracy (33,710 BRFs · 289/290 kommuner · 29,206 rows · 03:15 Europe/Stockholm · 21 MCP tools) needs production cross-check.
