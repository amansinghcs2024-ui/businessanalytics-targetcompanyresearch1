# Part B — Sourcing Strategy + Scale-Up Proposal
### Ahmedabad / Basket A (Specialty & Performance Chemicals) — DeepThought Business Analytics Internship

---

## Question 1: Sourcing Methods (beyond Google search)

| # | Method | Why it works for this ICP | Limitation |
|---|--------|---------------------------|------------|
| 1 | **DSIR (Dept. of Scientific & Industrial Research) recognised in-house R&D units list** | Public list of ~3,000+ companies nationally with government-recognised R&D units. Direct signal for C3 (differentiation) and C7/C4 (someone had to set up and run a formal R&D function). Filterable by state/city and NIC industry code. | Skews toward older, established firms; misses younger unlisted specialty players that haven't applied yet. |
| 2 | **GIDC (Gujarat Industrial Development Corporation) estate-wise member directories** — Vatva, Naroda, Odhav, Sanand, Changodar | These are Ahmedabad's actual chemical manufacturing estates. GIDC and estate-level industrial associations maintain member/allottee lists with plot numbers, which is the fastest way to find real, physically-present manufacturers (satisfies E1/E2) rather than trading offices. | Lists are often not digitized/downloadable — may need manual compilation or a local visit/RTI-style request. |
| 3 | **GCCI (Gujarat Chamber of Commerce & Industry) and GACL/Chemical industry association member directories** | Active association membership signals an operating, engaged company. GCCI has sector-specific committees (chemicals, pharma) with member lists including size/contact info. | Overlaps with GIDC and DSIR lists — heavy deduplication needed. |
| 4 | **USFDA / EU-GMP / WHO-GMP approved facility lists** (for the pharma-adjacent slice of Basket A/B) | Regulatory approval is public, globally searchable (fda.gov), and directly evidences E1 (must have a real facility), C3 (commodity players rarely pursue international approval), and C5 (export tailwind). | Heavy pharma bias; irrelevant for pure pigment/dye/polymer companies. |
| 5 | **BSE SME / NSE Emerge + Screener.in sector filters** | Listed small-caps have public financials (instant revenue-band check), annual reports (leadership bios), and shareholding disclosures (promoter % — directly filters out PE-controlled companies like Fairchem Organics in this batch). | Only captures listed companies — the majority of true ICP fits are unlisted MSMEs. |
| 6 | **Industry expo exhibitor lists** — Chemspec India, CPHI India, Vibrant Gujarat Chemical sector pavilions, GESIA/Chemexcil trade events | Paying for a booth signals active growth intent (C6) and self-selects for companies proud enough of their product to exhibit — segments map directly to the industry baskets. | Biased toward companies that can afford a booth; misses bootstrapped smaller MSMEs. |
| 7 | **MCA (Ministry of Corporate Affairs) filings, via Tofler/Zauba Corp or direct MCA search** | Every registered company has public NIC industry code, director names, paid-up capital, and registered address. Lets you filter Ahmedabad-registered "Chemicals & Chemical Products" (NIC 20xx) companies by capital range as a rough size proxy, and pulls the actual decision-maker's name (C4/C8). | Very noisy — NIC codes are self-reported and often wrong; no website/product data; requires heavy manual filtering. |
| 8 | **LinkedIn Sales Navigator — inverted search** | Instead of finding companies and checking if the decision-maker is technical, search for Founders/MDs/CEOs in Ahmedabad with technical degrees (B.Tech/PhD/Chemical Engineering) at companies sized 50-500 employees, then check if their company is a genuine manufacturer. Strong direct signal for C4. | LinkedIn data (headcount, industry tag) is frequently wrong or stale for Indian MSMEs. |
| 9 | **Export/import shipment data (e.g. Exim/Volza-type trade data)** | Companies that appear as consistent exporters of specialty chemical HS codes (not commodity ones) are self-verifying producers with real export tailwind (C5) — and trade data usually lists the actual manufacturer, filtering out traders. | Paid data sources; HS codes group specialty and commodity chemicals together, so still needs manual review. |
| 10 | **"Unconventional" method — GPCB (Gujarat Pollution Control Board) Zero Liquid Discharge / consent-to-operate filings** | Every operating chemical unit above a certain scale needs GPCB clearance, which is public. A company that has recently invested in ZLD/ETP upgrades (mandatory since ~2020) has demonstrably survived consolidation and is still actively operating at real scale — a strong E1 + going-concern signal, and a good proxy for filtering out the ~120 SME units that have shut down in Vatva since 2020. | Regulatory filings are compliance-focused, not product/differentiation-focused — still needs a follow-up website/LinkedIn check. |

---

## Question 2: The 1000-Company Proposal — Ahmedabad-style scaled to all of India

## Goal
Build a verified list of 1000 Federer-fit companies across the target cities and Basket A/B/C segments within 30 calendar days, using AI + scraping + database access.

## Key constraint
At the ~30% yield observed even in this small batch (1 borderline pass + 4 well-evidenced fails out of 5 deep-dived), the sourcing universe needs to be **~3,500-4,000 companies** to responsibly reach 1,000 verified passes.

## The funnel

```
Universe (3,500-4,000 companies)
    ↓ Hard pre-filters (auto-disqualify: no website, trader/distributor keywords,
      revenue >Rs.500Cr where known, PE-controlled where known)
Screened pool (2,000-2,500)
    ↓ Automated E1/E2 gate + C3-C8 AI scoring (Claude Haiku first pass)
First-pass qualified (1,200-1,400)
    ↓ Sonnet re-score on borderline (40-59 band) + human QA on low-confidence flags
Final verified list (1,000)
```

### Week 1 — Build the universe
- Pull DSIR R&D-recognised unit list (national, filter to target cities/NIC codes).
- Scrape GIDC/GCCI/industry-association member directories for each target city's chemical/manufacturing estates.
- Pull BSE SME + NSE Emerge + Screener.in sector lists for instant financial pre-filtering.
- Pull USFDA/EU-GMP facility lists for the pharma-adjacent baskets.
- Query MCA data (via a tool like Antigravity, or Tofler/Zauba) by NIC code + city + paid-up-capital range.
- LinkedIn Sales Navigator inverted search for technical founders/MDs in target cities.
- Deduplicate (fuzzy name matching + CIN matching for anything with a company registration number) → target **3,500-4,000 unique companies** with at minimum name, city, rough segment tag, and website where found.

### Week 2 — Scrape + automated scoring
- For each company with a website: scrape homepage, about/leadership, products, news/press, careers, contact (5-8 pages, Playwright to handle JS-rendered sites, ~8K tokens per company).
- Hard pre-filter before any AI call: no website found, single parked page, name contains "Trading/Imports/Distributors," known revenue >Rs.500Cr. This alone should eliminate 500-800 companies cheaply.
- Send remaining scraped content to Claude Haiku with a structured ICP-scoring prompt (mirroring the E1/E2 gates + C3-C8 rubric from this assignment) → return JSON: gate results, 6 criterion scores with evidence quotes, total, band, and a confidence flag per criterion.
- Any company scoring 40-59 (borderline) or with any "low confidence" flag gets automatically queued for Sonnet re-scoring.

### Week 3 — Re-score + human QA
Known LLM failure modes to explicitly guard against (based on patterns already seen in this small batch, e.g. Devarsons scoring borderline because systems/revenue evidence was genuinely thin, not because the model guessed):
- **C3 inflation** — treating baseline certifications (ISO 9001) as differentiation.
- **C4 false positives** — inferring "technical" from any engineering degree regardless of institution tier.
- **Revenue/PE-control false negatives** — as seen with Fairchem Organics and Epigral in this batch, the model needs an explicit instruction to check Screener.in-style promoter-holding data before scoring C4/C8, not just website language.
- **C6 false positives** — reading old press-page dates (2019-2021) as current growth signals.

QA process: auto-flag rules (e.g., total score exactly 40-42 with all-high-confidence tags = likely inflated; any C3 evidence citing only ISO 9001/14001; any C6 evidence citing news older than 2 years) → route to human review (~3-4 min/company). Spot-check 50 random "strong pass" results.

### Week 4 — Final assembly
- Merge clean strong-passes + QA-verified passes; drop remaining borderline/unverified.
- Target: **1,000 verified companies.**
- Add personalization hooks for the top 200 (priority outreach tier).
- Compile master CSV + summary dashboard + methodology doc + source-contribution breakdown (which source contributed how many final companies, to guide future sourcing investment).
- Buffer day for overruns.

## Realistic yield at each stage
| Stage | Count | Yield vs. previous stage |
|---|---|---|
| Raw universe (Week 1) | 3,500-4,000 | — |
| After hard pre-filter | 2,700-3,200 | ~80% survive |
| After AI first-pass scoring | 1,200-1,400 pass | ~40-45% of screened pool |
| After re-score + QA | 1,000 verified | ~75-80% of first-pass survive QA |

## Risk mitigation
- **Yield lower than expected** (a real risk — this batch's first 5 companies alone showed 2 well-known "obvious" candidates disqualified purely on having outgrown the revenue band): expand into more state-level industrial directories (GIDC, MIDC, TSIIC per state) and Google-Maps-based industrial-estate scraping as a fallback.
- **Scraper blocked**: rotate user agents, add delays, fall back to manual research for flagged high-priority companies.
- **AI scoring accuracy below target**: split scoring into a factual pass (E1/E2, C5, revenue) vs. a judgment pass (C3, C4, C8) using different prompts/models, and explicitly require the model to check promoter-holding/ownership data before scoring C4/C8 — the single biggest false-positive risk observed in this batch's research.

## Tools and budget
| Tool | Purpose |
|---|---|
| Claude Haiku API | First-pass ICP scoring at scale |
| Claude Sonnet API | Borderline re-scoring, judgment-heavy criteria |
| Playwright + Python | Website scraping |
| Screener.in / Tofler / Zauba / MCA data | Financial and ownership verification |
| LinkedIn Sales Navigator | Decision-maker discovery |
| Antigravity / GitHub Copilot | MCA data extraction tooling, pipeline code assistance |

---

## The Hand-Drawn Diagram — what to draw (I cannot make this part for you)

The assignment is explicit that a digitally generated diagram will get the application rejected without review, so this has to be drawn by hand and photographed. Here's a content outline you can sketch from — turn each stage above into a box, with arrows showing the funnel narrowing:

1. **Top box:** "Universe: 3,500-4,000 companies" with 6-8 small labelled feeder arrows coming into it — one per source (DSIR list, GIDC directories, BSE/NSE SME, USFDA list, expo lists, MCA data, LinkedIn Sales Nav, GPCB filings).
2. **Arrow down** labelled "hard pre-filters" → box "Screened pool: 2,000-2,500."
3. **Arrow down** labelled "AI scoring (Haiku, E1/E2 + C3-C8)" → box "First-pass qualified: 1,200-1,400."
4. **Arrow down**, split into two paths: "borderline → Sonnet re-score" and "low-confidence → human QA," both feeding into a final box "Verified: 1,000 companies."
5. **Side timeline strip** along the bottom: Week 1 / Week 2 / Week 3 / Week 4 labels under the matching funnel stages.
6. Optionally, mark the two "quality checkpoint" diamonds (hard pre-filter, human QA) distinctly from the process boxes.

Draw it, photograph it, send it in the Internshala chat — that's the one piece of this whole assignment that only you can produce.
