# Competitive Intelligence Orchestrator

A structured prompt system for [Claude Projects](https://claude.ai) that turns a market description into actionable competitive intelligence — not surface-level summaries.

You describe a market. The system runs three sequential research waves (competitor profiling → customer sentiment mining → strategic signal detection), cross-references findings across waves, and produces four deliverables: an executive report, feature matrix, pricing landscape, and per-competitor battle cards.

---

## Why I built this

I'm a product leader at a large healthcare tech company. Every time I needed competitive intelligence — for roadmap planning, positioning, or stakeholder conversations — I'd either get a 50-slide deck full of logos and obvious observations, or I'd spend a week doing it myself.

The problem with most competitive analysis isn't the research. It's the synthesis. Individual facts about competitors are easy to find. What's hard is connecting a pricing complaint in a G2 review to a funding announcement to a hiring pattern and recognizing that a competitor is about to reprice — before they announce it.

That cross-referencing is what this system is designed to do.

### Design decisions

**Three waves, not one big prompt.** Each wave builds on the last. Wave 1 maps the landscape. Wave 2 mines customer sentiment using the competitor list Wave 1 produced. Wave 3 reads strategic signals informed by patterns Wave 2 surfaced. A single prompt can't do this — it would either lose context or skip the cross-referencing that produces the best insights.

**Two parallel threads per wave.** Within each wave, two research threads run simultaneously — one quantitative, one qualitative. Wave 1 pairs competitor profiles with pricing intelligence. Wave 2 pairs structured review mining with unfiltered community discussion. Wave 3 pairs go-to-market analysis with strategic signal detection. Each thread has a dedicated prompt with specific instructions, sources, and output formats.

**An honesty protocol, not a style guide.** The `config.md` file defines three confidence tags — `[Data]`, `[Estimate]`, and `[Assumption]` — and requires every factual claim to carry one. It also defines rules for data gaps, source hierarchy, and intellectual honesty (like distinguishing between "no one does this" and "the market rejected this"). This exists because AI-generated analysis tends to present everything with equal confidence, which makes it useless for actual decisions.

**Four distinct deliverables, not one report.** Different stakeholders need different views of the same intelligence. The executive report sets strategic context. The feature matrix shows where competitors are strong or weak across specific capabilities. The pricing map reveals value-metric patterns and pricing whitespace. The battle cards give per-competitor tactical guidance. Each template enforces a structure that prevents the common failure mode of "interesting observations with no clear implication."

### What I learned building it

Prompt architecture is product architecture. The same skills that make a good product spec — clear scope, explicit dependencies, structured outputs, defined quality standards — make good prompt systems. The orchestrator is essentially a product requirements doc for an AI research workflow, and the wave prompts are feature specs.

The hardest part wasn't getting Claude to research. It was getting it to be honest about what it didn't find. The honesty protocol exists because early versions would fill data gaps with plausible-sounding filler that read great and was completely unverifiable. The `DATA GAP` format forces explicit acknowledgment of missing information, which turned out to be one of the most valuable parts of the output.

---

## How to use it

### Setup

1. Go to [claude.ai](https://claude.ai) and create a new Project.
2. Upload everything in the `prompts/` folder as project knowledge.
3. Copy the contents of `prompts/orchestrator.md` and paste it into the Project's custom instructions (system prompt).
4. Start a new conversation inside the Project.

### Running an analysis

Describe the market you want to analyze. The system will ask you for five things (if you don't provide them upfront):

- **Market/idea description** — What product or service? What problem does it solve?
- **Target customer** — Who's the buyer?
- **Known competitors** — Any you're already aware of (or "none")
- **Your differentiator** — What would you do differently? Can be vague.
- **Priority question** — The single most important thing you want to learn

The system then runs three research waves sequentially. Each wave produces raw findings. After all three waves complete, it synthesizes everything into four deliverables, presented one at a time:

1. **Executive intelligence report** — Market structure, competitive tiers, opportunity and threat analysis, moat assessment
2. **Competitive feature matrix** — Side-by-side capability comparison with ratings and confidence levels
3. **Pricing landscape** — Pricing models, tier breakdowns, value metrics, pricing whitespace
4. **Battle cards** — Per-competitor tactical cards with strengths, weaknesses, and evaluation guidance

After each deliverable, you can ask follow-up questions, request deeper analysis on specific competitors, or move to the next one.

### What to expect

- **Time**: A full run takes 20-40 minutes depending on market complexity and how many competitors surface.
- **Quality**: Strongest for markets with established competitors that have public pricing, review presence, and visible hiring/funding activity. Thinner for very early-stage or niche markets where public data is scarce.
- **Honesty**: The system will tell you when data is thin, when a claim is an estimate vs. verified, and when a gap exists. This is by design — an analysis that says "DATA GAP" is more useful than one that guesses.

### Customization

You can modify the system for your needs:

- **Add a wave** — Create a new prompt file following the pattern of the existing waves (objective → input required → per-competitor analysis → cross-competitor patterns → output format → tagging rules). Reference it in `orchestrator.md`.
- **Change output templates** — The four output templates in `prompts/` define the structure of each deliverable. Adjust sections, add new ones, or change the rating scales.
- **Narrow the scope** — If you only care about pricing, you can run Wave 1 alone and skip the rest. The wave prompts work independently, though cross-wave synthesis is where the best insights come from.
- **Adjust the honesty protocol** — The confidence tags and data-gap format in `config.md` can be tuned. Add domain-specific tags (e.g., `[Regulatory]` for compliance-sensitive claims) or adjust the source hierarchy for your industry.

---

## Project structure

```
prompts/
├── orchestrator.md                # System prompt — controls the full workflow
├── config.md                      # Honesty protocol, confidence tags, data standards
│
├── wave1-competitor-profiles.md   # Wave 1A: Company + product + traction profiles
├── wave1-pricing-intelligence.md  # Wave 1B: Pricing models, tiers, psychology
│
├── wave2-review-mining.md         # Wave 2A: G2/Capterra/TrustRadius sentiment
├── wave2-community-mining.md      # Wave 2B: Reddit/HN/Twitter unfiltered discussion
│
├── wave3-gtm-analysis.md          # Wave 3A: Acquisition channels, sales motions, content
├── wave3-strategic-signals.md     # Wave 3B: Hiring, funding, product velocity, risk
│
├── output-report.md               # Template: Executive intelligence report
├── output-matrix.md               # Template: Competitive feature matrix
├── output-pricing-map.md          # Template: Pricing landscape analysis
└── output-battle-cards.md         # Template: Per-competitor battle cards
```

### How the pieces connect

```
orchestrator.md (system prompt — runs the show)
    │
    ├── config.md (loaded by all waves — honesty rules, tagging, source hierarchy)
    │
    ├── Wave 1 ──┬── wave1-competitor-profiles.md ──┐
    │            └── wave1-pricing-intelligence.md ──┤
    │                                                ├─→ Competitor list
    ├── Wave 2 ──┬── wave2-review-mining.md ────────┐     (feeds Wave 2)
    │            └── wave2-community-mining.md ──────┤
    │                                                ├─→ Sentiment patterns
    ├── Wave 3 ──┬── wave3-gtm-analysis.md ─────────┐     (feeds Wave 3)
    │            └── wave3-strategic-signals.md ─────┤
    │                                                │
    └── Synthesis ──→ Cross-references ALL findings
                      │
                      ├── output-report.md
                      ├── output-matrix.md
                      ├── output-pricing-map.md
                      └── output-battle-cards.md
```

---

## Limitations

- **Depends on public data.** Private companies with no review presence, hidden pricing, and minimal public footprint will have thin profiles. The system flags these as `DATA GAP` rather than guessing.
- **Point-in-time snapshot.** Pricing changes, teams grow, companies get acquired. The analysis date matters. Re-run periodically for fast-moving markets.
- **AI research, not primary research.** This doesn't replace talking to customers, attending industry events, or requesting vendor demos. It's a starting layer that tells you where to dig deeper.
- **Single-session context.** Claude's context window means very large markets (20+ competitors with deep profiles) may require prioritization. The system handles this by tiering competitors and going deeper on the most important ones.

---

## License

MIT

---

## About

Built by [Your Name] — Product Leader focused on B2B SaaS and AI/ML platforms.

This project is part of my exploration of AI-assisted product workflows. If you're a PM, strategist, or founder who does competitive analysis regularly, I'd like to hear how it works for your market.

[LinkedIn](https://www.linkedin.com/in/hhough/) 
