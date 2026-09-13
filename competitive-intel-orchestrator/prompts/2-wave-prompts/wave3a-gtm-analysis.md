# Wave 3, Agent A — Go-to-market analysis

## Objective

Analyze how each competitor acquires and retains customers. This reveals where they invest, how they think about growth, and where there are channel gaps a new entrant could exploit.

## Input required

This agent receives:
- **Competitor list from Wave 1**
- **Pricing data from Wave 1** (pricing model affects sales motion)
- **Notable patterns from Wave 2** (sentiment signals that affect GTM effectiveness)

## Per-competitor GTM analysis

### Acquisition channels

Research and assess each channel. For each, note whether the competitor appears to invest heavily, lightly, or not at all:

**Organic search (SEO)**
- What keywords do they rank for? (Search their domain on competitor name + "site:" or check visible content themes)
- Blog presence: publishing frequency, content quality, topic focus
- Do they rank for problem-aware queries ("how to manage X") or product-aware queries ("best X software")?
- Estimated organic traffic level (high, medium, low based on content volume and ranking signals)

**Paid acquisition**
- Google Ads: search for their brand name — do competitors bid on it? Do they bid on generic keywords?
- Social media ads: check Facebook Ad Library, LinkedIn ad presence
- Retargeting: after visiting their site, do you see their ads elsewhere?
- Sponsorships: podcast sponsors, newsletter sponsors, event sponsors in the space

**Product-led growth (PLG)**
- Free tier designed to drive organic adoption?
- Viral mechanics (invite teammates, share outputs, "powered by [brand]" watermarks)
- Community edition or open-source component?
- Template galleries, marketplaces, or public-facing content that drives discovery

**Sales-led motion**
- SDR/BDR presence (check LinkedIn for sales roles)
- Demo-request or "Contact Sales" as primary CTA?
- Enterprise-specific landing pages or case studies
- Channel partners or reseller program

**Community and word-of-mouth**
- Active community (Slack, Discord, forum, subreddit)?
- User conference or events?
- Ambassador/advocate program?
- Referral program details

**Partnerships and integrations**
- Listed in partner marketplaces (Salesforce AppExchange, HubSpot Marketplace, Shopify App Store, etc.)
- Co-marketing with complementary products
- API ecosystem that drives discovery

### Sales motion classification

Classify each competitor's primary motion:
- **Self-serve**: Customer signs up, configures, pays with credit card. No sales team needed.
- **Sales-assisted**: Customer tries the product, sales reaches out to convert/upsell.
- **Enterprise sales**: RFP process, custom contracts, long sales cycle.
- **Hybrid**: Different motions for different segments.

Note the entry point: where does a potential customer first encounter this product? (Google search, peer recommendation, marketplace listing, outbound sales email, conference)

### Content strategy

Analyze their content approach:
- **Blog**: Topics covered, publishing frequency, depth and quality
- **Resources**: Whitepapers, ebooks, guides, templates, calculators
- **Video**: YouTube presence, webinar program, product videos
- **Social**: LinkedIn company page activity, Twitter engagement, other platforms
- **Email**: Newsletter presence, nurture sequences (sign up for their free tier to see)
- **Community content**: User-generated content, case studies featuring customers

What stage of the funnel does their content target?
- Top of funnel (awareness): "What is [category]?" educational content
- Middle of funnel (consideration): Comparison pages, use case pages, ROI calculators
- Bottom of funnel (decision): Case studies, demos, pricing transparency

### Channel assessment

For each competitor, answer:
- Where are they investing most? (Follow the job postings and content volume)
- Where are they underinvesting? (Visible gaps in their strategy)
- What's their customer acquisition cost likely to be? (High = enterprise sales; Low = PLG/SEO)
- Are they diversified or dependent on one channel?

## Market-level GTM patterns

After analyzing individual competitors:

### Dominant acquisition channel
- What channel works best in this market? (If every competitor invests heavily in SEO, content works here)
- Is there a channel no one is using well? (Potential first-mover advantage)

### Sales motion distribution
- How many competitors are self-serve vs. sales-led?
- Is the market trending toward one motion? (PLG replacing sales-led, or enterprise sales becoming more common)

### Content saturation
- How competitive is content in this space?
- What topics are over-covered? (Every competitor has a "What is [X]?" post)
- What topics are under-covered? (Genuine content gaps)

### Channel vulnerability
- Are any competitors over-indexed on a single channel? (Vulnerable to algorithm changes, ad cost increases)
- Who has the most diversified acquisition?

## Output format

```
## GTM analysis: [Competitor Name]

**Primary motion**: [Self-serve / Sales-assisted / Enterprise / Hybrid]
**Primary channel**: [SEO / Paid / PLG / Sales / Community]

### Channel breakdown
| Channel | Investment level | Effectiveness signals |
|---------|-----------------|----------------------|
| SEO/Content | [Heavy/Moderate/Light/None] | [what suggests this] |
| Paid ads | [same] | [same] |
| PLG | [same] | [same] |
| Sales team | [same] | [same] |
| Community | [same] | [same] |
| Partnerships | [same] | [same] |

### Content strategy
[What they publish, where, how often, what funnel stage]

### Notable GTM tactics
[Anything interesting or distinctive about how they acquire customers]

### GTM vulnerability
[Where their acquisition is fragile or underdeveloped]
[confidence tags]
```

After all competitors:

```
## Market GTM landscape

### Dominant channels
[What works in this market, what's saturated]

### Channel gaps
[Underused channels where a new entrant could gain traction]

### Motion trend
[Is the market moving toward self-serve, PLG, enterprise, or something else?]

### Content opportunity
[Under-covered topics and formats]
```
