# Output template: Competitive intelligence report

Use this structure to produce the executive report. This is the first deliverable the user sees — it sets the strategic context for everything that follows.

---

## Structure

### Header

```
# Competitive intelligence report: [Market name]
**Analysis date**: [Date]
**Analyzed by**: AI-assisted competitive intelligence
**Competitors covered**: [Number] direct, [Number] adjacent
**Data quality**: [Overall assessment — e.g., "Strong for top 5 competitors; limited data on 2 smaller players"]
```

### 1. Executive summary

Half a page maximum. Answer these questions in narrative form (not as a bulleted list):
- What is this market? (One sentence definition)
- How competitive is it? (Crowded, emerging, consolidated, fragmented)
- Where is it heading? (Key directional trend)
- What is the single biggest opportunity for a new entrant?
- What is the single biggest risk for a new entrant?
- What's the confidence level in this analysis? (What's well-supported vs. where data was thin)

This summary should be useful on its own — if someone only reads this section, they should walk away with the essential picture.

### 2. Market landscape

**Market structure**
- Total number of players identified (direct + adjacent + alternatives)
- Market concentration: Is this a winner-take-all market, an oligopoly, or highly fragmented?
- Market maturity: Emerging (lots of startups, no clear leader), Growing (leaders emerging, still room), Mature (established leaders, hard to break in), Declining (consolidation, shrinking demand)
- Total addressable signal: Not a precise TAM — what signals exist about market size and growth? (VC investment in the category, analyst mentions, search volume trends)

**Competitor tier map**
Organize competitors into tiers based on strength of position:
- Tier 1 — Market leaders (strongest product + traction + funding)
- Tier 2 — Strong contenders (competitive product, growing, but haven't reached leader status)
- Tier 3 — Niche players (serving a specific segment well but limited broader appeal)
- Tier 4 — Emerging / early (new entrants, limited traction, but interesting product or approach)
- Adjacent — Tools from other categories that compete for the same budget

For each tier, list the competitors with a one-sentence summary of their position.

### 3. Strategic opportunities

Identify 3-5 opportunities based on cross-referencing all research waves. Each opportunity should cite evidence from multiple waves.

For each opportunity:

```
**Opportunity: [Name it in 5 words or fewer]**

Evidence:
- [Wave 1 signal — e.g., pricing gap between $30/mo and $200/mo tiers]
- [Wave 2 signal — e.g., universal complaint about onboarding complexity]
- [Wave 3 signal — e.g., no competitor investing in community-led growth]

Strength of signal: [Strong / Moderate / Speculative]

What this means: [One paragraph on why this is an opportunity and how to exploit it]

Risk: [What could make this opportunity a trap]
```

### 4. Strategic risks

Identify 3-5 risks. These are reasons entering this market could fail, even with a good product.

For each risk:

```
**Risk: [Name it]**

Evidence:
- [What signals support this risk]

Severity: [High / Medium / Low]
Likelihood: [High / Medium / Low]

What this means: [One paragraph on how this risk could manifest]

Mitigation: [What would reduce this risk]
```

### 5. Moat assessment

What defensibility exists in this market — and what doesn't?

Analyze these moat types for the market:
- **Network effects**: Does the product get more valuable with more users? (Marketplace, collaboration tool, community)
- **Switching costs**: How hard is it to leave once you're using a tool? (Data lock-in, workflow integration, team training)
- **Data advantages**: Does anyone have proprietary data that others can't access?
- **Brand**: Does brand matter in this market, or is it purely feature-driven?
- **Distribution**: Does anyone have a distribution advantage (built-in audience, marketplace presence, partnership network)?
- **Technical**: Is there a genuine technical barrier to entry (complex infrastructure, regulated data, hard-to-build capabilities)?

For each: who has it, how strong is it, and can a new entrant build it?

### 6. Data gaps and recommended follow-up

List every DATA GAP flagged across all research waves. Group by impact:

**High impact gaps** (these could change the strategic picture):
- [Gap and why it matters]
- [Suggested method to close the gap]

**Medium impact gaps** (would improve analysis quality):
- [Gap and why it matters]

**Low impact gaps** (nice to have):
- [Gap]

### Footer

```
---
**Methodology**: This analysis was conducted using web research across company websites, review platforms (G2, Capterra, TrustRadius), community discussions (Reddit, HN, forums), job postings, funding databases, and public product data. All claims are tagged with confidence levels: [Data], [Estimate], or [Assumption]. See individual raw findings for source details.

**Limitations**: This analysis reflects publicly available information as of [date]. Private companies may have undisclosed funding, revenue, or strategic plans. Customer sentiment is sampled, not comprehensive. Pricing may have changed since last verified.
```
