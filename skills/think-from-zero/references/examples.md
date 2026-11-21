# Worked examples (light path)

Use these as shape references, not scripts to copy verbatim. Always gather real
evidence for the user's case.

---

## 1. Engineering — vector DB for RAG

**User:** "We should add a vector database for our RAG app, right? Everyone uses Pinecone."

**Goal:** answer questions over our docs with good retrieval at under 300 ms, at low cost.
**Assumptions:**
- [GUESS] We have a lot of data -> checked: 40k chunks.
- [CONVENTION] RAG needs a dedicated vector DB -> dropped, see below.
- [FACT] Postgres is already in production; the team knows it.
**Fundamental truths:**
- 40k vectors x 1,536 dims x 4 bytes is about 250 MB. Fits in RAM.
- Exact search over 40k vectors is ~60M multiply-adds: milliseconds on one CPU.
- Every new service adds cost, ops work and a failure point.
**Rebuild:** (a) pgvector in the existing Postgres; (b) in-memory NumPy/FAISS index; (c) managed vector DB.
**Sanity check:** inversion: what makes (a) fail? 100x data growth or heavy filtering at scale. Not true for 12+ months.
**vs convention:** skips a new vendor, a sync pipeline and a bill; costs a migration later if data grows 100x.
**Answer:** use pgvector now. Confidence: high.
**Would change my mind:** data passing ~5M vectors or p95 latency over budget. **Cheapest test:** load the 40k chunks into pgvector and measure p95 today.

---

## 2. Product — paid plan before product-market fit

**User:** "Should we launch a $49/mo Pro tier? Competitors all have one."

**Goal:** learn whether enough users will pay, without slowing activation of free users, in the next 8 weeks.
**Assumptions:**
- [CONVENTION] SaaS needs a Pro tier early -> dropped until willingness-to-pay is known.
- [GUESS] Free users would upgrade for "advanced analytics" -> untested.
- [FACT] ~200 weekly actives; 12 people asked about billing in support.
**Fundamental truths:**
- Price is a hypothesis about value; a public Pro page is a costly commitment (support, entitlements, refunds).
- The scarce resource is signal: who pays, for what, at what price.
- Base rate: many early products add paid tiers and learn mostly that free users ignore them.
**Rebuild:** (a) manual "founding member" invoice to the 12 askers; (b) waitlist + price survey; (c) full self-serve Pro.
**Sanity check:** inversion: (c) fails if entitlements aren't clear or checkout friction kills the few willing buyers — both likely at this size.
**vs convention:** competitors' Pro pages don't prove *your* users will pay *now*.
**Answer:** (a) sell manually to warm demand first. Confidence: medium.
**Would change my mind:** ≥30 unpaid waitlist signups at a stated price, or support volume that needs self-serve. **Cheapest test:** email the 12 askers a one-page offer this week and count paid converts.

---

## 3. Career — jump to a hot stack

**User:** "Everyone's hiring for AI agents. Should I quit my backend job and go all-in on agents for 6 months?"

**Goal:** increase expected career optionality and income over 2–3 years, with runway and skill compounding.
**Assumptions:**
- [CONVENTION] You must go full-time on the hot thing to catch up -> dropped.
- [GUESS] Agent roles will stay scarce and premium for years -> uncertain; treat as volatile.
- [FACT] Stable income, solid distributed-systems experience, ~4 months expenses saved.
**Fundamental truths:**
- Hiring follows budgets and hype cycles; skills that transfer (systems, product sense, reliability) outlast labels.
- Opportunity cost of quitting: lost income, weaker negotiating position, resume gap risk.
- Learning compounds with real problems and feedback, not only tutorials.
**Rebuild:** (a) keep the job; ship 1–2 agent projects in public on nights/weekends; (b) internal transfer / AI-adjacent work at current company; (c) quit and study full-time.
**Sanity check:** counterexample: people who layered new skills onto a strong base often outcompete pure bootcamp pivots when the label cools.
**vs convention:** "quit and go all-in" maximises focus but burns the cheapest path to paid practice.
**Answer:** (a) or (b), not (c), unless runway is >12 months and a concrete offer path exists. Confidence: medium-high.
**Would change my mind:** a written offer in the new domain, or a funded runway ≥12 months plus a portfolio already getting interviews. **Cheapest test:** apply to 5 roles *now* with current skills + one small agent demo; measure response rate before quitting.
