# Wave 3, Agent B — Strategic signals

## Objective

Read the tea leaves. This agent looks at leading indicators — the signals that predict where a competitor is heading before they announce it. Hiring patterns, funding moves, product velocity, and strategic shifts all telegraph future moves if you know how to read them.

## Input required

This agent receives:
- **Competitor profiles from Wave 1** (company basics, funding history)
- **Sentiment patterns from Wave 2** (what customers are feeling — this adds context to strategic moves)

## Per-competitor strategic analysis

### Hiring signals

Search "[competitor name] careers" and their LinkedIn jobs page:

**What roles are they hiring for?**
- Engineering roles: What type? (Frontend, backend, ML/AI, infrastructure, security, mobile). Engineering hires signal what they're building next.
- Sales roles: SDRs, AEs, enterprise reps, sales engineers. Sales hires signal scaling revenue.
- Marketing roles: Content, demand gen, product marketing, brand. Marketing hires signal a push for awareness or repositioning.
- Customer success/support: Growing CS means they have retention work to do — either scaling with new customers or fighting churn.
- Product/design: Product managers, UX designers. Signals investment in product quality and new feature development.
- Executive hires: New CRO (revenue push), new CPO (product pivot), new CTO (technical rebuild).

**Reading the pattern:**
- Mostly engineers, few salespeople → building phase, product not yet fully baked
- Mostly salespeople, few engineers → scaling phase, product is "done enough" to sell hard
- Hiring enterprise sales + security engineers → moving upmarket
- Hiring PLG/growth engineers + marketing → going downmarket or adding self-serve
- Cutting across the board → trouble, or being acquired, or pivoting
- Hiring in a new geo → market expansion
- Hiring ML/AI roles → adding AI features (or caught up in the hype)

**Volume signals:**
- How many open roles total? (Compare to team size from Wave 1 — if they have 50 people and 30 open roles, they're growing aggressively)
- Has the hiring volume changed recently? (Lots of roles added or removed in the last month)

### Funding trajectory

- What stage are they at? (Seed → early, Series A → growth, Series B+ → scaling or pre-IPO)
- Runway estimate: When was their last raise? How much? Typical burn rate for a company their size?
- Investor quality: Are their investors generalist VCs, industry-specific, strategic (from a potential acquirer)?
- Is the funding trend accelerating or slowing? (Each round bigger than the last, or longer gaps between rounds?)
- Any signals of profitability or path to profitability? (Press mentions, leader statements)
- Acquisition risk: Are they likely to be acquired? By whom? (Check if strategic investors are on their cap table)

### Product velocity

Check their changelog, release notes, blog, or product updates:
- **Ship frequency**: How often do they release updates? (Weekly = fast iteration, quarterly = more deliberate, nothing in 6 months = concerning)
- **Release type**: Bug fixes (maintenance mode) vs. new features (building) vs. major product changes (pivoting)
- **Recent launches**: What have they shipped in the last 3-6 months? What does this reveal about priorities?
- **AI integration**: Are they adding AI features? How substantive (core product integration vs. bolt-on chatbot)?
- **Platform expansion**: New integrations, API improvements, marketplace additions
- **Mobile**: Have they launched or significantly updated mobile apps recently?

### SEO footprint

- Domain authority or traffic estimates (check via search result positioning for key terms)
- How many pages are indexed? (A rough proxy for content investment)
- Are they ranking for bottom-of-funnel terms (high intent) or mostly top-of-funnel (awareness)?
- Recent content velocity: have they ramped up publishing?

### Public roadmap and direction signals

- Does the company have a public roadmap? What's on it?
- CEO/founder public statements (blog posts, podcast appearances, conference talks) — what are they talking about?
- Job descriptions often leak strategy: a job posting for a "Marketplace Product Manager" reveals marketplace plans before any announcement
- Patent filings (for larger companies)

### Market positioning shifts

Based on all available signals, assess whether this competitor is:
- **Moving upmarket**: Enterprise features, enterprise hiring, higher prices, SOC2/HIPAA, custom contracts
- **Moving downmarket**: Free tier launch, self-serve focus, lower prices, PLG investment
- **Expanding horizontally**: Adding features outside their core (a CRM adding project management, an email tool adding a CMS)
- **Deepening vertically**: Specializing in specific industries (healthcare, fintech, e-commerce)
- **Pivoting**: Significant strategic direction change
- **Steady state**: No major directional changes, optimizing what they have

### Risk indicators

Red flags that a competitor may be weakening:
- Leadership departures (check LinkedIn for recent C-suite exits)
- Layoffs (news, LinkedIn activity, Glassdoor reviews mentioning cuts)
- Negative press (lawsuits, data breaches, customer complaints going viral)
- Declining review sentiment (Wave 2 data)
- Long gaps between product updates
- Glassdoor rating below 3.5 or declining
- Sudden silence on social media or content

## Cross-competitor strategic synthesis

After analyzing individual competitors, identify market-level strategic patterns:

### Market momentum
- Is the overall market growing, mature, or declining? What signals support this?
- Are new entrants arriving? (Recent launches, VC investment in the category)
- Are incumbents consolidating? (Acquisitions, mergers, feature absorption)

### Directional convergence
- Are multiple competitors making the same strategic move? (All adding AI, all moving upmarket, all launching free tiers)
- What does this convergence signal about where the market is heading?
- Is anyone going against the trend? Why?

### Vulnerability map
- Which competitors have the most risk indicators?
- Which competitors are best positioned for the next 12-18 months?
- Where is a new entrant most likely to find an opening?

## Output format

```
## Strategic signals: [Competitor Name]

### Hiring signals
- Open roles: [number] | Team size: [number] | Growth rate: [%]
- Hiring focus: [Engineering / Sales / Both / Other]
- Signal reading: [What the hiring pattern suggests about their direction]
[confidence tag]

### Funding position
- Last round: [type, amount, date]
- Estimated runway: [X months]
- Trajectory: [Accelerating / Steady / Slowing]
[confidence tag]

### Product velocity
- Ship frequency: [Weekly / Monthly / Quarterly / Slow]
- Recent focus: [New features / Maintenance / Platform / AI]
- Notable recent releases: [What they've shipped]
[confidence tag]

### Strategic direction
- Current move: [Upmarket / Downmarket / Horizontal / Vertical / Steady]
- Evidence: [What supports this reading]
[confidence tag]

### Risk indicators
- [List any red flags, or "None detected"]
[confidence tag]
```

After all competitors:

```
## Market strategic landscape

### Market momentum
[Growing, mature, or declining — with evidence]

### Directional trends
[Where competitors are collectively heading]

### Vulnerability map
[Who's strongest, who's weakest, where the openings are]

### Key unknowns
[What we couldn't determine and why it matters]
```
