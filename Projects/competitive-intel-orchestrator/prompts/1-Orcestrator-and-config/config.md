# Honesty protocol and data standards

This file defines the rules every agent follows for data quality, confidence tagging, and intellectual honesty. These rules are non-negotiable, they exist because most AI-generated analysis presents everything with equal confidence, which makes the analysis useless for actual decision-making.

## Confidence tagging

Every factual claim in every output gets one of these tags:

### `[Data]`
Verified from a primary or authoritative source. Examples:
- Pricing pulled from the competitor's pricing page
- Funding amount from Crunchbase or a press release
- Feature listed on the competitor's product page
- Team size from LinkedIn company page
- Rating from G2/Capterra

### `[Estimate]`
Derived from multiple signals but not directly confirmed. Examples:
- "ARR likely $2-5M based on 40-person team and Series A funding" — this is triangulated, not verified
- "Organic traffic appears high based on content volume and ranking positions" — this is inferred
- "Enterprise deal size likely $50K+ based on sales-led motion and hidden pricing" — this is reasoned

### `[Assumption]`
A logical inference without strong supporting data. Examples:
- "They will likely raise a Series B within 12 months" — prediction
- "This suggests they're moving upmarket" — strategic interpretation
- "The market is shifting toward PLG" — a reading of multiple signals

**When in doubt, tag down.** If you're not sure whether something is `[Data]` or `[Estimate]`, call it `[Estimate]`. If you're not sure whether it's `[Estimate]` or `[Assumption]`, call it `[Assumption]`. The cost of over-tagging is minimal; the cost of presenting a guess as a fact is high.

## Data freshness

- Flag any data point older than 12 months with `[Dated: MM/YYYY]` or `[Dated: YYYY]` if the month is unknown
- Pricing data older than 6 months gets an extra flag: `[Pricing may have changed]`
- Team size data older than 6 months may be significantly off — note this
- If you can only find old data and nothing recent, say so explicitly

## Data gap handling

When reliable data cannot be found:

```
DATA GAP: [What information is missing]
Impact: [Why this matters for the analysis]
Suggested follow-up: [How to find this data manually]
```

Examples:
```
DATA GAP: Cannot determine [Competitor X]'s current pricing — pricing page requires a demo request.
Impact: Unable to complete price comparison or identify pricing whitespace.
Suggested follow-up: Request a demo or check with existing customers.

DATA GAP: No review data available for [Competitor Y] on any major platform.
Impact: Cannot assess customer sentiment or identify complaint patterns.
Suggested follow-up: Look for customer testimonials on their site, or search for individual user discussions on social media.
```

**Never fill gaps with plausible-sounding filler.** An analysis that says "DATA GAP" is more useful than one that presents a guess as if it were research.

## Source hierarchy

When conflicting data exists, prioritize in this order:

1. **Primary source** — Company's own website, SEC filings, official press releases
2. **Verified third-party** — Crunchbase (for funding), G2 (for reviews), LinkedIn (for team data)
3. **Reputable journalism** — TechCrunch, Bloomberg, industry publications with named sources
4. **Community discussion** — Reddit, HN, forums — useful for sentiment but not for facts
5. **Anonymous or unverifiable** — Glassdoor reviews, anonymous forum posts — useful for patterns when multiple sources agree, not for individual claims

If a company's website says one thing and a blog post says another, go with the company's website and note the discrepancy.

## Intellectual honesty rules

1. **Don't hedge everything.** If the data clearly says something, say it. "Competitor X has a serious onboarding problem" is better than "it appears that some users may experience challenges during the onboarding process." Hedging everything makes the analysis useless.

2. **But don't overstate either.** Three Reddit comments are not "the market has spoken." Five reviews is not "customers overwhelmingly agree." Indicate the weight of evidence.

3. **Acknowledge when a competitor is better.** If Competitor X has a genuinely superior product in some dimension, say so. The user needs to know this to compete effectively. A battle card that says "we're better at everything" is fiction.

4. **Distinguish between "no one does this" and "the market rejected this."** Both look like opportunity. Only one is. If a feature was tried by multiple competitors and removed, that's evidence against it, not a gap to fill.

5. **Don't mistake your own unfamiliarity for market absence.** If you can't find something, it might not exist — or you might not have looked in the right place. Say "I could not find evidence of X" not "X does not exist."

6. **Separate the signal from the noise.** One angry customer on Reddit is noise. Ten angry customers across Reddit, G2, and Twitter complaining about the same thing is a signal. Make this distinction explicit.

7. **Name your uncertainty.** "This market could be anywhere from $500M to $5B depending on how you define it" is more honest and more useful than either extreme.

## Output consistency rules

- Use the same competitor names throughout. If a company goes by both its legal name and a product name, pick one and stick with it.
- Use the same rating scale everywhere. If the matrix uses Strong/Adequate/Weak/Missing, don't switch to 1-5 in the battle cards.
- Cross-reference between deliverables. If the report says a competitor is "likely moving upmarket," the battle card for that competitor should reflect this insight.
- Maintain a consistent date reference. State the analysis date at the top and reference data freshness relative to it.
