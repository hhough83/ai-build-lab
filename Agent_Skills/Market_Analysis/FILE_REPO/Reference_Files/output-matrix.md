# Output template: Competitive feature matrix

Use this structure to produce the feature comparison matrix. This deliverable gives a scannable view of who does what — and where the gaps are.

---

## Construction rules

### Identify features to compare

Pull features from three sources:
1. **Core features listed on competitor product pages** (Wave 1) — what do they all claim to do?
2. **Features customers praise or complain about** (Wave 2) — what do users actually care about?
3. **Features customers request** (Wave 2) — what's missing from the market?

Organize features into categories. Typical categories (adapt to the specific market):
- Core functionality (the primary job the product does)
- Workflow and automation
- Integrations and ecosystem
- Collaboration and team features
- Reporting and analytics
- Administration and security
- Mobile and accessibility
- AI and smart features
- Support and onboarding

### Rating scale

Rate each competitor on each feature using this scale:
- **Strong** — Best-in-class or notably good implementation. Customers praise it.
- **Adequate** — Functional, gets the job done, no major complaints. Standard implementation.
- **Weak** — Exists but customers complain about it. Limited implementation.
- **Missing** — Feature does not exist in the product.
- **Unknown** — Could not determine from available data. (Mark with DATA GAP)

Do not use numeric scores (1-5). They imply false precision. The four-level scale forces honest categorization.

### Include the user's product

Add a column for the user's product (even if hypothetical). If the product doesn't exist yet, mark features as "Planned," "Possible," or leave blank. This lets the user see exactly where they'd stand relative to the market.

## Structure

```
# Competitive feature matrix: [Market name]
**Last updated**: [Date]

## How to read this matrix
- **Strong**: Best-in-class implementation, customers love it
- **Adequate**: Works fine, standard implementation
- **Weak**: Exists but limited or frustrating
- **Missing**: Not available
- **Unknown**: Could not verify

## Core functionality

| Feature | [Comp A] | [Comp B] | [Comp C] | [Comp D] | [Your product] |
|---------|----------|----------|----------|----------|----------------|
| [Feature 1] | Strong | Adequate | Missing | Weak | Planned |
| [Feature 2] | Adequate | Strong | Adequate | Missing | — |
| [Feature 3] | Strong | Strong | Weak | Adequate | Planned |

## Workflow and automation

| Feature | [Comp A] | [Comp B] | [Comp C] | [Comp D] | [Your product] |
|---------|----------|----------|----------|----------|----------------|
| [Feature 1] | ... | ... | ... | ... | ... |

## [Continue for each category]

```

After the matrix, include:

```
## Matrix insights

### Table stakes (every strong competitor has these)
- [Feature 1]: Required for credibility in this market
- [Feature 2]: Customers expect this

### Differentiators (only 1-2 competitors have these, and customers value them)
- [Feature]: Only [Comp A] has this, and their customers cite it as a key reason they chose the product

### Whitespace (no competitor does this well)
- [Feature/capability]: Rated Weak or Missing across all competitors. [Is this a genuine gap or something the market doesn't want?]

### Feature fatigue (everyone has it but no one cares)
- [Feature]: Every competitor has this but it rarely appears in buying criteria or reviews. Not a differentiator.

### Confidence notes
- [Comp X]'s ratings are based on [N] reviews and product page analysis. Confidence: [High/Medium/Low]
- [Feature Y] was difficult to assess — ratings may not reflect current state.
```

## Important notes

- A feature existing is not the same as a feature being good. "Has reporting" and "has reporting that customers actually use and value" are different. Use the review data from Wave 2 to distinguish between checkbox features and genuinely strong implementations.
- Don't inflate the matrix with micro-features to make one competitor look better. Stick to features that matter to the buying decision.
- If a category has only one feature worth tracking, don't pad it with three more just to fill the table. Keep it tight.
- The matrix should fit on one screen when printed or viewed as a document. If it's more than 25-30 feature rows, you've gone too granular — consolidate related features.
