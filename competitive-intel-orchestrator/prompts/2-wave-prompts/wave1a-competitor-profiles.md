# Wave 1, Agent A — Competitor profiling

## Objective

Build a comprehensive profile of every meaningful competitor in the market. "Meaningful" includes direct competitors, adjacent solutions, and alternatives the target customer might choose instead (including doing nothing, using spreadsheets, or hiring a person).

## Research scope

Identify and profile:
- **5-8 direct competitors**: Same category, same buyer, solving the same core problem
- **2-3 adjacent solutions**: Broader platforms that include this functionality (e.g., a CRM that has a built-in email tool competing with standalone email tools), manual alternatives, or tools from neighboring categories that compete for the same budget line item

For each competitor, research and document:

### Company profile
- Company name
- Year founded
- Headquarters location
- Team size (exact if available, range estimate if not)
- Brief company description (one sentence on what they do)

### Product profile
- Product name (if different from company name)
- One-paragraph product description in plain language
- Core features (bulleted list, 5-10 key capabilities)
- Target customer segment (who they sell to: SMB, mid-market, enterprise, specific verticals)
- Platform/deployment (web app, mobile, desktop, API, on-premise)
- Key integrations (what does it connect to)

### Traction signals
- User/customer count (if publicly available)
- Revenue indicators (ARR if known, or relative signals like "appears to be doing $1-5M ARR based on team size and funding")
- Notable customers or logos
- Growth trajectory (growing fast, steady, stagnating — based on hiring, social signals, review volume trends)
- Market share estimate if available

### Funding and backing
- Total funding raised
- Most recent round (type, amount, date, lead investor)
- Key investors
- What the funding signals about their trajectory

### Strengths
- What they genuinely do well (features, UX, market position, brand, community)
- Where they have defensible advantages
- What their customers love about them (preview — Wave 2 will go deeper)

### Weaknesses
- Known limitations or gaps
- Areas where customers express frustration
- Structural disadvantages (small team vs. well-funded competitors, legacy tech, narrow focus)

## Research sources

Search in this priority order:
1. Company website (product pages, about page, pricing page, careers page)
2. Crunchbase / PitchBook for funding data
3. LinkedIn for team size and hiring signals
4. G2/Capterra for category placement and competitor comparisons
5. Recent news articles and press releases
6. Product Hunt launches
7. App store listings if applicable

## Output format

Use this structure for each competitor. Do not skip sections — if data is unavailable, write `DATA GAP: [what's missing and why it matters]`.

```
## [Competitor Name]

**Type**: Direct competitor | Adjacent solution | Manual alternative
**Founded**: [year] [confidence tag]
**HQ**: [location] [confidence tag]
**Team size**: [number or range] [confidence tag]
**Funding**: [total raised] — last round: [details] [confidence tag]

### What they do
[One paragraph plain-language description]

### Core features
- [Feature 1]
- [Feature 2]
- [etc.]

### Target customer
[Who they sell to and how they position]

### Traction
[User count, revenue signals, notable customers, growth trajectory]
[confidence tag per claim]

### Strengths
- [Strength 1 — why it matters]
- [Strength 2 — why it matters]

### Weaknesses
- [Weakness 1 — what it means for their customers]
- [Weakness 2 — what it means for their customers]

### Confidence notes
[Any caveats about data quality, freshness, or reliability for this competitor]
```

## Tagging rules

Every factual claim gets one tag:
- `[Data]` — Verified from a primary or authoritative source
- `[Estimate]` — Derived from multiple signals but not directly confirmed
- `[Assumption]` — Logical inference, treat with caution

Flag any data point older than 12 months with `[Dated: MM/YYYY]`.
