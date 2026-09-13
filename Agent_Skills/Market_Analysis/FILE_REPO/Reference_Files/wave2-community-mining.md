# Wave 2, Agent B — Community discussion mining

## Objective

Extract unfiltered customer and market sentiment from community discussions. Unlike structured review platforms, community discussions reveal how people actually talk about the problem, what they're building as workarounds, and what they recommend to each other when no vendor is watching.

## Input required

This agent receives the **competitor list from Wave 1** before starting.

## Sources

Search these communities for discussions about the market, the problem space, and specific competitors:

1. **Reddit** — Search relevant subreddits and r/SaaS, r/startups, r/smallbusiness, r/Entrepreneur, plus niche subs for the specific market. Search for competitor names AND for the problem description.
2. **Hacker News** — Search via hn.algolia.com for competitor names, product launches, and "Ask HN" threads about the problem space.
3. **Indie Hackers** — Discussions about building and using tools in the space.
4. **Twitter/X** — Search for competitor names, complaints, and praise. Look at what power users and industry voices say.
5. **LinkedIn** — Posts and discussions about the problem space (tend to be more enterprise-focused).
6. **Niche forums and communities** — Slack groups, Discord servers, Facebook groups, industry-specific forums relevant to the target market. Search for "[industry] community" or "[problem] forum."
7. **Stack Overflow / Stack Exchange** — If the product has a technical component, look for questions about integrations, workarounds, and limitations.
8. **Quora** — "What is the best tool for [X]" threads.

## What to extract

### "What do you use for X?" threads

These are gold. When someone asks "what do you use for [problem]?", the responses reveal:
- Which competitors get recommended most and why
- Which competitors get actively warned against and why
- What alternatives people suggest that aren't on the competitor list (flag these as potential additions)
- What criteria people use to make their choice (price? Features? Ease of use? Integration with their stack?)

Document:
- Thread URL or description
- What was asked
- Top recommended tools and the reasons given
- Any warnings or anti-recommendations
- The decision criteria people mentioned

### Migration stories

When someone describes switching from one tool to another:
- What they switched from and to
- Why they switched (the trigger — a price increase? Missing feature? Bad support experience?)
- How painful was the migration?
- Are they happier now?
- What do they miss about the old tool?

These stories reveal the actual switching triggers and switching costs experienced by real users.

### Workaround discussions

When people describe building their own solution or cobbling together multiple tools:
- What problem are they trying to solve?
- What tools are they combining? (e.g., "I use Notion + Zapier + Google Sheets because no single tool does X")
- Why isn't an existing solution good enough?
- How much effort is the workaround? (If it's complex, the pain is high — there's demand for a better solution)

### Language map

This is a specific deliverable: build a map of the exact words and phrases real people use to describe:
- The problem ("I spend hours every week on...", "The worst part of my job is...", "I'm drowning in...")
- What they want ("I just wish there was a tool that...", "All I need is...", "If someone built a...")
- Their frustration with current tools ("It's so clunky", "the UI feels like it was designed in 2005", "I can't believe they charge X for...")
- The value they get when something works ("It saves me X hours a week", "Game changer for our team", "Finally something that just works")

This language map is valuable for marketing copy, positioning, and feature naming — it tells you how the market talks about itself.

### Unmet needs

Explicit statements of needs that no current solution addresses:
- "I wish [tool] could do X" where X isn't available in any competitor
- "There's no good solution for Y" declarations
- Feature combinations that don't exist in one product
- Workflow patterns that current tools don't support

Distinguish between:
- **Genuine gaps**: Needs that no tool addresses and multiple people express
- **Niche requests**: One person's very specific workflow need
- **Already solved**: Needs that are actually addressed by a tool the person doesn't know about

### Community sentiment per competitor

For each competitor on the list, summarize:
- Overall community perception (loved / respected / tolerated / disliked)
- Are they seen as the "default" choice? The "enterprise" choice? The "budget" choice? The "cool new" choice?
- Do power users and beginners have different opinions?
- Any recent sentiment shifts (a product update that made people angry, a viral complaint, a competitor gaining fans)

## Output format

```
## Community intelligence: [Market name]

### Recommendation patterns
[What gets recommended in "what do you use for X" threads, and why]

### Migration stories
[Key switching stories: from → to, trigger, outcome]

### Workaround patterns
[What people are building themselves because no tool does it well enough]

### Language map

**How people describe the problem:**
- "[Exact phrasing people use]"
- "[Another common phrasing]"

**What they want:**
- "[Exact phrasing]"
- "[Another common phrasing]"

**Frustration language:**
- "[Exact phrasing]"
- "[Another common phrasing]"

**Value language (when something works):**
- "[Exact phrasing]"
- "[Another common phrasing]"

### Unmet needs
1. **[Need]** — [Who expressed it, how many, genuine gap vs niche request] [confidence tag]
2. **[Need]** — [same format]

### Per-competitor community sentiment

**[Competitor A]**: [How the community sees them — one paragraph]
**[Competitor B]**: [same]
[etc.]

### Newly discovered alternatives
[Any tools or solutions mentioned in community discussions that weren't on the Wave 1 competitor list. Include name, what they do, and why they came up.]

### Data quality notes
[How many threads/discussions this is based on, recency of discussions, any subreddits or communities that were particularly rich or barren]
```

## Important notes

- Community discussions are unfiltered and unverified. People exaggerate, have personal grudges, and sometimes work for competitors. Look for patterns across multiple sources, not individual hot takes.
- Recency matters. A complaint from 3 years ago may have been fixed. Weight recent discussions more heavily.
- Some communities have strong biases (Hacker News leans toward open-source and self-hosted; Reddit startup subs lean toward free/cheap tools). Note the source context.
- If a competitor has almost no community discussion, that itself is a signal — they may have low awareness, a very niche audience, or a quiet user base.
- Capture the language EXACTLY as people use it (paraphrased for copyright, but preserving the vocabulary and emotional register). "This tool is a game-changer" and "this tool is adequate for our needs" tell very different stories.
