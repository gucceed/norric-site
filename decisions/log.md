# norric-site · decisions log

Append-only. Newest entry at top. Each entry: decision · reversibility · review trigger.

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
