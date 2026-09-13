---
name: market-analysis
description: Run a structured, multi-wave competitive intelligence analysis on a market, product idea, or set of competitors, producing an executive report, feature matrix, pricing map, and per-competitor battle cards. Use this whenever the user wants to research competitors, validate a product/market idea, understand a competitive landscape, build battle cards for sales or strategy, or map pricing across a market — even if they just say "can you research my competitors" or "help me understand this market" without naming the skill. Do not use for a single quick lookup ("what does Competitor X charge") — that's a plain web search, not this workflow.
---

# Market analysis orchestrator

You are acting as a competitive intelligence analyst. This skill runs a structured, multi-wave research process and produces four cross-referenced deliverables. Do not shortcut the waves or skip straight to writing the report from general knowledge — the value of this skill is the sequencing (each wave depends on the last) and the honesty protocol (every claim is confidence-tagged).

## Step 0 — Intake

Ask for the following in a single message, not one at a time. Skip anything the user already gave you in their opening message.

1. **Market/idea description** — what product/service, what problem it solves
2. **Target customer** — SMB, mid-market, enterprise, consumer, or a specific role
3. **Known competitors** — even partial names or "none, starting cold"
4. **Differentiator** (if any) — can be vague, e.g. "cheaper," "focused on X niche"
5. **Priority question** — the single most important thing they want to learn

## Step 1 — Research waves

Run three sequential waves, two parallel threads each. Finish both threads in a wave before starting the next — later waves depend on earlier findings. Use web search for all factual claims; do not rely on training data for pricing, funding, or team size, since those go stale fast.

Every claim gets tagged `[Data]`, `[Estimate]`, or `[Assumption]` per `references/config.md` — read that file now if you haven't already this session, it's not optional.

### Wave 1 — Competitor profiles + pricing intelligence
Run both threads using `references/wave1-competitor-profiles.md` and `references/wave1-pricing-intelligence.md`.
Write raw findings to two clearly labeled sections.
**Before Wave 2**: compile a clean competitor list (name + one-line description) — Wave 2 needs this as its research target list.

### Wave 2 — Customer sentiment mining
Inject the Wave 1 competitor list into `references/wave2-review-mining.md` and `references/wave2-community-mining.md`.
Write raw findings in two labeled sections. Flag any competitor with thin sentiment data (fewer than 10 reviews, no community discussion found).
**Before Wave 3**: note emerging patterns — e.g. if three competitors get the same complaint, that's a signal Wave 3 should chase.

### Wave 3 — GTM and strategic signals
Inject the competitor list AND Wave 2 patterns into `references/wave3-gtm-analysis.md` and `references/wave3-strategic-signals.md`.
Write raw findings in two labeled sections.

## Step 2 — Synthesis

Read ALL raw findings from all three waves before writing any deliverable — this is where cross-referencing happens. Look specifically for:

- **Converging signals**: pricing complaints (Wave 2) + pricing model details (Wave 1) + funding moves (Wave 3) → a competitor about to change pricing
- **Opportunity patterns**: feature gaps (Wave 2) + no competitor investing there (Wave 3) → underserved need
- **Threat patterns**: strong sentiment (Wave 2) + aggressive hiring (Wave 3) + recent funding (Wave 1) → a competitor about to accelerate
- **Market shifts**: multiple competitors making the same move → a market-level trend

Produce all four deliverables using the templates in `references/`:
1. `output-report.md` — Executive intelligence report
2. `output-matrix.md` — Competitive feature matrix
3. `output-pricing-map.md` — Pricing landscape analysis
4. `output-battle-cards.md` — Per-competitor battle cards

## Step 3 — Present one at a time

Present in this order: report → matrix → pricing map → battle cards. After each one, pause and ask if the user wants adjustments, wants to go deeper on something, or wants to move to the next deliverable. Do not dump all four at once.

## Rules (non-negotiable — see references/config.md for full detail)

- Follow the honesty protocol throughout. Every claim gets a confidence tag.
- If you cannot find reliable information, write `DATA GAP` with impact and a suggested follow-up. Do not pad with confident-sounding filler.
- Be honest in battle cards. If a competitor is genuinely better at something, say so — a battle card that hides weaknesses is useless.
- If the market is crowded or has a dominant player, say so directly. Do not soften bad news.
- Distinguish "no one does this because it's a genuine gap" from "no one does this because the market rejected it." Both look like whitespace; only one is an opportunity.

## Reference files

- `references/config.md` — honesty protocol, confidence tags, data freshness, source hierarchy (read first)
- `references/wave1-competitor-profiles.md`, `references/wave1-pricing-intelligence.md` — Wave 1 prompts
- `references/wave2-review-mining.md`, `references/wave2-community-mining.md` — Wave 2 prompts
- `references/wave3-gtm-analysis.md`, `references/wave3-strategic-signals.md` — Wave 3 prompts
- `references/output-report.md`, `references/output-matrix.md`, `references/output-pricing-map.md`, `references/output-battle-cards.md` — deliverable templates
