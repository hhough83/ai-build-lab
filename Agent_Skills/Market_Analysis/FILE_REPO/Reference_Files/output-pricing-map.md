# Output template: Pricing landscape analysis

Use this structure to produce the pricing landscape deliverable. This goes beyond a price comparison table — it analyzes how competitors think about pricing, what psychology they use, and where pricing opportunities exist.

---

## Structure

```
# Pricing landscape: [Market name]
**Analysis date**: [Date]
**Pricing data freshness**: [When each competitor's pricing was last verified]
```

### 1. Pricing comparison table

A clean, scannable table showing every competitor's pricing side by side.

```
## Tier-by-tier comparison

| | [Comp A] | [Comp B] | [Comp C] | [Comp D] |
|--|----------|----------|----------|----------|
| **Model** | Per seat | Usage-based | Flat rate | Freemium + per seat |
| **Value metric** | Users | API calls | — | Users |
| **Free tier** | 14-day trial | 1,000 calls/mo | No | Free for 3 users |
| **Entry price** | $29/seat/mo | $49/mo | $99/mo | $15/seat/mo |
| **Mid tier** | $59/seat/mo | $149/mo | $249/mo | $35/seat/mo |
| **Top tier** | $99/seat/mo | $499/mo | $499/mo | $65/seat/mo |
| **Enterprise** | Custom | Custom | Custom | Custom |
| **Annual discount** | 20% | 15% | 10% | 20% |
| **Billing** | Monthly/Annual | Monthly/Annual | Annual only | Monthly/Annual |
```

Add a row for key feature gates — what features are locked behind higher tiers:

```
| **Key feature gates** | Analytics at $59+, API at $99+ | Higher rate limits | SSO at $249+, API at $499+ | SSO at $35+, Automations at $65+ |
```

Tag each price with confidence: `[Data]` if from pricing page, `[Estimate]` if inferred.

### 2. Value metric analysis

Analyze what each competitor chose as their value metric and why it matters:

```
## Value metric analysis

### How competitors charge

**Per-seat pricing** ([Comp A], [Comp D])
- Pros for the vendor: Predictable, scales with organization size
- Cons for the customer: Penalizes large teams with light users, creates "seat hoarding" where admins limit access
- Customer sentiment: [What Wave 2 data says about pricing satisfaction]

**Usage-based pricing** ([Comp B])
- Pros: Aligns cost with value, low barrier to start
- Cons: Unpredictable bills, customers may self-limit usage to control costs
- Customer sentiment: [What Wave 2 data says]

**Flat rate** ([Comp C])
- Pros: Simple, predictable, no per-user friction
- Cons: Doesn't scale value with company size, may underprice for enterprise
- Customer sentiment: [What Wave 2 data says]

### Value metric alignment
- Does each competitor's value metric align with how their customers actually get value?
- Example: If the product's value is in automation (saving time), but pricing is per seat (penalizing team size), there's a misalignment that creates customer friction.
- Flag any misalignments and note the customer complaints that result (from Wave 2 data)
```

### 3. Pricing psychology breakdown

Analyze the deliberate pricing psychology each competitor uses:

```
## Pricing psychology

### [Comp A]
- **Anchoring**: Enterprise tier at $99/seat makes $59 feel reasonable [Data/Estimate]
- **Most Popular badge**: Applied to mid-tier, steering buyers away from cheapest option [Data]
- **Charm pricing**: $29, not $30 — classic psychological pricing [Data]
- **Annual lock-in incentive**: 20% discount for annual commitment [Data]
- **Feature gating strategy**: Core features available at entry tier; analytics and API access reserved for higher tiers to drive upgrades [Data]

### [Comp B]
[Same analysis]

### Market-wide patterns
- What pricing psychology tactics are universal in this market?
- Are any tactics notably absent? (An opportunity to use them — or evidence that they don't work here)
```

### 4. Positioning map

Create a qualitative positioning map based on two axes. Choose the two most meaningful axes for this market. Common options:

- **Price vs. Feature richness** (most common: shows who's expensive for what they offer)
- **Price vs. Ease of use** (useful for markets where simplicity is a selling point)
- **SMB focus vs. Enterprise focus** (shows market segment positioning)
- **Specialized vs. General-purpose** (shows breadth of positioning)

```
## Positioning map

Axes: [X-axis label] vs [Y-axis label]

         High [Y-axis]
              |
   [Comp C]   |   [Comp A]
              |
  ———————————+———————————  
              |
   [Comp D]   |   [Comp B]
              |
         Low [Y-axis]

   Low [X]              High [X]

### What the positioning reveals
- [Quadrant analysis — which quadrants are crowded, which are empty]
- [Where the user's product could position]
- [What positioning would be most defensible]
```

### 5. Whitespace analysis

This is the most valuable section — where are the pricing opportunities?

```
## Pricing whitespace and opportunities

### Price point gaps
- [Is there a price range no one occupies? e.g., nothing between $50/mo and $200/mo]
- [Is there a missing "starter" tier for very small teams or individuals?]
- [Is there a missing mid-market option between self-serve and enterprise?]

### Model gaps
- [Is there a pricing model no one uses that would work? e.g., everyone charges per seat but a flat rate per-project model would better match how customers get value]
- [Could usage-based pricing work where everyone currently charges per seat?]
- [Is there an outcome-based pricing opportunity?]

### Psychology gaps
- [Are competitors leaving money on the table? e.g., no annual discounts, no tiering psychology]
- [Are customers asking for pricing structures that don't exist? (Wave 2 data)]

### Strategic pricing opportunities
Based on the full analysis, here are the pricing strategies most likely to work for a new entrant:

1. **[Strategy name]**: [Description, rationale, evidence from research, risks]
2. **[Strategy name]**: [Description, rationale, evidence from research, risks]
3. **[Strategy name]**: [Description, rationale, evidence from research, risks]

### Pricing traps to avoid
- [Traps specific to this market — e.g., "Don't compete on price with [Comp D] — they're funded and willing to undercut. Compete on value."]
- [Model traps — e.g., "Per-seat pricing is the norm but customers hate it — a new entrant using per-seat will inherit the same complaints"]
```

### 6. Switching cost summary

```
## Switching cost landscape

| Competitor | Data export | Integration depth | Contract lock-in | Migration effort | Overall |
|-----------|------------|-------------------|-----------------|-----------------|---------|
| [Comp A] | Easy | Deep | Annual | High | High switching cost |
| [Comp B] | Moderate | Shallow | Monthly | Low | Low switching cost |

### What this means for a new entrant
- [Which competitors' customers are most "captive" and hardest to win?]
- [Which competitors' customers are most "free" and easiest to win?]
- [What would you need to build to make switching easier? (Migration tools, import features, concierge onboarding)]
```

## Important notes

- Pricing pages change frequently. Note the exact date each competitor's pricing was checked.
- Enterprise pricing is almost always hidden. If you can't find it, flag it as a DATA GAP and estimate based on signals (sales team size, customer logos, market positioning).
- Don't treat listed pricing as real pricing. Enterprise customers negotiate. Startups offer discounts. The sticker price is a starting point.
- Pricing strategy recommendations should acknowledge that the user may not know their cost structure yet. Frame suggestions as "worth testing" rather than "you should charge X."
