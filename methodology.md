# Methodology — Part A: Ahmedabad, Specialty Chemicals (Basket A)

## City and segment choice

**City: Ahmedabad.** Chosen for operational density — the Vatva, Naroda, Odhav, and Sanand GIDC industrial estates, plus the wider Ahmedabad-Vadodara-Bharuch chemical corridor, host one of India's largest concentrations of specialty and performance chemical manufacturers. This gives a large enough universe to realistically find 25 qualified companies within the ~30% yield the assignment describes.

**Segment: Basket A — Custom synthesis & specialty chemicals / Performance chemicals.** This is the strongest-fit basket for Ahmedabad specifically: pigments, dyes, oleochemicals, and chlor-alkali derivatives are the city's dominant manufacturing identity, and many of these companies are promoter-driven with genuine technical differentiation (proprietary processes, imported German/Swiss equipment, DSIR-recognized R&D).

## Process actually followed for this batch

1. **Broad discovery search** — searched general terms ("Ahmedabad specialty chemicals manufacturer," directory/listicle sites) to build an initial name list. This surfaced ~25-30 candidate names from sources like a scraped Ahmedabad chemical-manufacturer contact list, a B2B lead-gen directory (AeroLeads), and stock-screener "top chemical stocks" roundups.
2. **Per-company deep dive** — for each candidate investigated, searched for: company website/about page, Screener.in (for listed companies — gives revenue, promoter holding %, growth trend directly), LinkedIn, and MCA/company-registry aggregators (Tofler, TheCompanyCheck, Tracxn) for unlisted companies.
3. **Evidence-based scoring** against the assignment's E1/E2 gates and C3-C8 criteria, using only what could be verified from public sources — no inference presented as fact.
4. **Honest fail documentation** — where a company failed a gate or hit an auto-disqualify condition, that reasoning is recorded in the CSV rather than the company being silently dropped, per the assignment's instruction to document fails "with clear reasoning, not just 'doesn't fit.'"

## What this batch actually produced (be transparent about scope)

Out of the first ~10 companies deep-dived, this batch surfaced:
- **1 genuine borderline/pass candidate** (Devarsons Industries) with real evidence but an unconfirmed revenue band and systems-maturity picture — flagged for direct verification rather than guessed at.
- **4 well-documented fails**, each illustrating a different failure pattern the assignment specifically warns about:
  - **Fairchem Organics** — strong technical moat, but majority-controlled by an institutional investor (Fairfax India Holdings), the same disqualifying pattern as the assignment's own Suven Pharma example.
  - **Asahi Songwon Colors** and **Epigral (formerly Meghmani Finechem)** — both genuinely differentiated, promoter-driven, technically strong companies that have **scaled past the Rs.500Cr ceiling**. This is an important segment-level finding: Ahmedabad's most visible, easiest-to-find specialty chemical names (the ones that dominate search results and stock-screener lists) are disproportionately the ones that have already grown out of DT's target band. The genuinely ICP-fitting companies are more likely to be smaller, unlisted, harder-to-find firms — which is exactly why the assignment expects a ~70% miss rate.
  - **Panacea Phytoextracts** — a "looks right on paper" trap: correct city, correct segment description, but too small and with no visible systems infrastructure to build on.

## Honest limitation and how the remaining companies should be researched

Reaching the full 25 requires investigating roughly 60-75 more companies at this same level of diligence — cross-checking revenue (Screener.in for listed, Tofler/MCA filings for unlisted), decision-maker background (LinkedIn, company "About" pages), and growth/systems signals (careers pages, press sections, GST/export data) one company at a time. That volume of individual verification is the actual multi-day core of this assignment and cannot be responsibly compressed into a single research session without either (a) fabricating evidence that wasn't actually verified, or (b) presenting low-confidence guesses as confirmed facts — both of which fail the assignment's explicit "we will verify your claims" standard.

**`candidate_universe_to_research.csv`** in this same folder lists ~20 additional real, unlisted-or-smaller Ahmedabad chemical companies surfaced during this research (Matangi Industries, Aksharchem India, ARCL Organics, Arvee Laboratories, and others) that are plausible next candidates precisely because they are *not* the large listed names — continue the same search → verify → score process on this list to build out toward 25.

## Sources used

- Screener.in — revenue, promoter holding %, multi-year growth trend for listed companies
- Company websites — product portfolio, certifications, "About Us" / leadership pages
- LinkedIn company pages — headcount, HQ location
- Tofler / TheCompanyCheck / Tracxn — MCA filing data, directors, incorporation history for unlisted companies
- Aggregated directory/listicle sources (AeroLeads, SalezShark, a scraped Ahmedabad chemical manufacturers list) — used only for initial name discovery, never as evidence for scoring

## What I learned about the segment

- Ahmedabad's specialty chemical scene is bifurcated: a handful of well-known, listed, technically excellent companies that have **outgrown** the Rs.50-500Cr band (Epigral, Asahi Songwon, Fairchem/Fairchem Organics), and a much larger, harder-to-search long tail of unlisted mid-sized manufacturers in GIDC estates that are the actual target zone.
- PE/institutional control (Fairchem Organics via Fairfax) is a real and recurring trap in this segment — several Gujarat specialty chemical companies took foreign PE investment in the 2010s, which silently disqualifies otherwise excellent-looking candidates.
- Public web search alone under-serves the *smaller*, unlisted end of the market that DT actually wants — DSIR's R&D-recognized unit list, GIDC estate-wise member directories, and GCCI (Gujarat Chamber of Commerce) member lists would likely be far more productive than general search for the next batch, and are recommended as primary sources in the sourcing-methods answer (Part B, Question 1).

## Code / tools used

No custom scraping code was used for this batch — research was done via direct web search and page reads (Screener.in, company sites, MCA-data aggregators), which was sufficient at this small scale. For scaling to 25+ and beyond, see the automation approach described in the Part B, Question 2 proposal (`part_b_sourcing_and_1000_proposal.md`).
