# Wave 2, Agent A — Review platform mining

## Objective

Extract customer sentiment patterns from structured review platforms. The goal is not to summarize reviews but to find recurring patterns — what customers consistently praise, consistently complain about, and consistently ask for.

## Input required

This agent receives the **competitor list from Wave 1** before starting. Do not research competitors outside this list unless a new name emerges prominently during research.

## Sources

Search these platforms for reviews of each competitor:
1. **G2** — Largest B2B review site. Search "[competitor name] G2 reviews"
2. **Capterra** — Strong for SMB tools. Search "[competitor name] Capterra reviews"
3. **TrustRadius** — Tends to have more detailed, enterprise-focused reviews
4. **Product Hunt** — Launch reception and early adopter sentiment
5. **App Store / Google Play** — If the product has a mobile app
6. **Gartner Peer Insights** — If the market is enterprise-grade

## Per-competitor extraction

For each competitor, extract and synthesize:

### Review volume and distribution
- Approximate total review count across platforms
- Average star rating per platform
- Rating trend (improving, stable, declining — look at recent vs older reviews)
- Review freshness (are most reviews from the last year, or mostly old?)

### Praise patterns (what customers love)
Identify the top 3-5 things customers consistently praise. For each:
- What they praise
- How frequently it appears (rough: "mentioned in nearly every review" vs "occasional mention")
- Representative language customers use (paraphrase — don't copy exact quotes)
- Who tends to praise this (small teams? Enterprise users? A specific role?)

### Complaint patterns (what customers hate)
Identify the top 3-5 recurring complaints. For each:
- What they complain about
- Frequency and intensity (mild annoyance vs deal-breaker frustration)
- Is the complaint about the core product, onboarding, support, pricing, or something else?
- Has the company responded or fixed it? (Check if recent reviews still mention it)
- Does this complaint correlate with a specific customer segment?

### Feature requests
What features do reviewers wish the product had? Look for:
- Features mentioned in "cons" or "what could be improved" sections
- Features that are listed as reasons people considered switching
- Integration requests
- UI/UX improvement requests

### Onboarding sentiment
- How do customers describe the setup experience?
- Is onboarding praised, tolerated, or a major pain point?
- Do they mention needing help from support to get started?
- How long does it take to see value? (time-to-value signals)

### Support quality
- How do customers rate support responsiveness?
- Is support quality different by tier? (e.g., "enterprise support is great but free tier gets no help")
- Common support complaints (slow response, unhelpful, no phone support)

### Pricing sentiment
- Do customers feel the price is fair for the value?
- Are there complaints about surprise charges, aggressive upselling, or price increases?
- Does pricing come up in "cons" sections?

### Churn signals
Look for indicators of customers leaving or considering leaving:
- Reviews from former customers explaining why they left
- Reviews mentioning evaluating alternatives
- Reviews where the tone shifted from positive to frustrated over time
- "I would switch if [X alternative] had [Y feature]" statements

## Cross-competitor patterns

After analyzing individual competitors, identify market-level patterns:

- **Universal complaints**: What problem do customers complain about regardless of which tool they use? (This is potential whitespace)
- **Universal praise**: What does every tool in this market do well? (This is table stakes — you must have it)
- **Segment-specific needs**: Do enterprise users want different things than SMB users? Do specific roles have specific needs?
- **Satisfaction gaps**: Which competitor has the largest gap between what customers want and what they deliver?

## Output format

```
## Review sentiment: [Competitor Name]

**Review volume**: ~[number] across [platforms] | **Avg rating**: [X.X/5]
**Trend**: [Improving / Stable / Declining] | **Freshness**: [Most reviews from last X months]

### What customers love
1. **[Theme]** — [description, frequency, who says this]
2. **[Theme]** — [description, frequency, who says this]
3. **[Theme]** — [description, frequency, who says this]

### What customers hate
1. **[Theme]** — [description, frequency, severity, still current?]
2. **[Theme]** — [description, frequency, severity, still current?]
3. **[Theme]** — [description, frequency, severity, still current?]

### Top feature requests
- [Request 1]
- [Request 2]
- [Request 3]

### Onboarding: [Positive / Mixed / Negative]
[Key observations]

### Support: [Positive / Mixed / Negative]
[Key observations]

### Pricing sentiment: [Fair / Mixed / Negative]
[Key observations]

### Churn signals
[Any evidence of customers leaving or wanting to leave, and why]

### Data quality note
[How many reviews this is based on, any caveats about sample bias]
```

After all competitors:

```
## Market-wide sentiment patterns

### Universal complaints (whitespace opportunities)
- [Pattern 1]
- [Pattern 2]

### Table stakes (must-have features)
- [Feature 1]
- [Feature 2]

### Segment-specific insights
[Differences between customer segments]
```

## Important notes

- Review data is inherently biased. Customers with strong opinions (positive or negative) write reviews; satisfied-but-not-thrilled customers don't. Acknowledge this.
- If a competitor has fewer than 10 reviews total, flag it: "LOW REVIEW VOLUME — patterns may not be reliable."
- Recent reviews matter more than old ones. Weight observations from the last 12 months more heavily.
- Don't treat a single scathing review as a pattern. Look for repetition across multiple reviewers.
