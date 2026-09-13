# Wave 1, Agent B — Pricing intelligence

## Objective

Reverse-engineer the pricing strategy of every competitor identified in this market. Go beyond "it costs $X/mo" — understand the pricing model, the psychology behind it, and what it means for a new entrant.

## Per-competitor pricing analysis

For each competitor, research and document:

### Pricing model
- **Model type**: Per seat, usage-based, flat rate, freemium, hybrid, quote-based enterprise, one-time purchase
- **Value metric**: What scales with price? (users, events, contacts, API calls, storage, projects, messages sent). This is critical — the value metric reveals what the company thinks customers value most.
- **Billing**: Monthly, annual, or both? What's the annual discount (typically 15-20%)?

### Tier breakdown
For each pricing tier:
- Tier name
- Price point
- What's included
- What's gated (features only available at higher tiers)
- Usage limits at this tier
- Who this tier is designed for (persona/company size)

### Free offering
- Free tier (permanent, limited version) vs. free trial (time-limited, full version)?
- Trial duration if applicable
- Free tier limitations (what forces the upgrade?)
- Is the free tier genuinely useful or just a teaser?

### Pricing psychology
Analyze the pricing page for deliberate psychological tactics:
- **Anchoring**: Is there an expensive tier designed to make the middle tier look reasonable?
- **Decoy pricing**: Is any tier deliberately unattractive to push buyers toward another?
- **Charm pricing**: $49 vs $50, $99 vs $100
- **Social proof on tiers**: "Most popular" badges, customer logos on enterprise tier
- **Urgency/scarcity**: Limited-time pricing, "prices going up" messaging
- **Price hiding**: Is enterprise pricing hidden behind "Contact Sales"? This usually signals $50K+/year deals.
- **Reverse trial**: Do they start you on a premium tier and downgrade after the trial?

### Switching costs
- **Data portability**: Can customers export their data? How easily?
- **Integration lock-in**: How deeply does the product embed in the customer's workflow?
- **Contract terms**: Monthly cancellation or annual lock-in? Early termination fees?
- **Migration effort**: How much work is it to switch to an alternative?

### Price-to-value assessment
- Does the pricing feel fair relative to the value delivered? (Check this against Wave 2 sentiment if available)
- Where does the pricing create friction? (e.g., per-seat pricing for a tool where only some team members use it daily)
- What pricing complaints appear in reviews or discussions?

## Market-level pricing analysis

After documenting individual competitors, analyze the pricing landscape:

### Price range
- Lowest entry price across all competitors
- Highest price point (or typical enterprise deal size)
- Where the market clusters (are most competitors at $30-50/seat/mo, or is it spread?)

### Dominant model
- What pricing model is most common? (Per seat tends to dominate B2B SaaS, usage-based is growing)
- Is anyone challenging the dominant model? (e.g., one competitor doing flat-rate while everyone else charges per seat)

### Pricing gaps
- Is there a price point no one occupies? (e.g., a $200/mo gap between SMB plans and enterprise plans)
- Is there a model no one uses? (e.g., everyone charges per seat but the product's value is per-project)
- Is anyone pricing too high for what they deliver? (Potential displacement opportunity)
- Is anyone pricing too low? (May signal a different business model, or a company burning cash for growth)

## Output format

```
## Pricing: [Competitor Name]

**Model**: [type] | **Value metric**: [what scales]
**Billing**: [monthly/annual/both] | **Annual discount**: [%]

### Tiers
| Tier | Price | Key inclusions | Key limits | Target buyer |
|------|-------|---------------|------------|-------------|
| [name] | [price] | [what's in] | [what's capped] | [who it's for] |

### Free offering
[Free tier vs trial, limitations, upgrade triggers]

### Pricing psychology
[Tactics observed on the pricing page]

### Switching costs
- Data portability: [easy/moderate/hard]
- Integration depth: [shallow/moderate/deep]
- Contract lock-in: [monthly/annual/multi-year]
- Migration effort: [low/medium/high]

### Price-to-value notes
[Does the pricing match the value? Where does it create friction?]
[confidence tags]
```

After all individual analyses:

```
## Market pricing landscape

### Price clustering
[Where most competitors land, outliers]

### Dominant model and challengers
[What model dominates, who's doing something different]

### Pricing whitespace
[Gaps in price points, unoccupied models, positioning opportunities]
```

## Tagging rules

Same as all agents:
- `[Data]` — From the competitor's actual pricing page or confirmed source
- `[Estimate]` — Inferred from partial data (e.g., "enterprise pricing likely $50K+ based on sales-led motion")
- `[Assumption]` — Logical guess
- Flag pricing data older than 6 months with `[Dated]` — pricing changes frequently
