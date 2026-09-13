# Market Analysis Skill

A structured, four-wave competitive intelligence workflow for AI assistants. Give it a market or product idea, and it researches competitors, pricing, customer sentiment, and go-to-market signals in sequence, then produces four cross-referenced deliverables: an executive report, a feature matrix, a pricing map, and per-competitor battle cards.

Built for product managers who want rigorous competitive research without writing code.

## Who this is for

You're a PM (or founder, or strategist) who wants real competitive intelligence, not a five-bullet ChatGPT summary, but you don't want to spin up Claude Code, write API scripts, or build a multi-step autonomous agent to get it.

This is a **prompt package**, not a piece of software. It's a set of instructions that tells your AI assistant *what to research, in what order, and how to be honest about what it doesn't know*. You stay in the loop the whole time: you kick off each research phase, review what comes back, and approve before moving to the next one. Nothing runs in the background unsupervised.

If you're comfortable with Claude Code or the Anthropic API, you could turn this into a fully autonomous pipeline that runs without you. This isn't that. This is the version you can install in an afternoon and run from a normal chat window.

## Why it's more than "just a good prompt"

Two things make this different from asking your AI assistant to "research my competitors":

1. **It's sequenced.** Later research phases (customer sentiment, GTM signals) are built using what earlier phases (competitor list, pricing) found. A single prompt can't do this: it has to research in order.
2. **It tags every claim.** Every fact gets marked `[Data]` (verified from a source), `[Estimate]` (triangulated), or `[Assumption]` (an inference or prediction). If it can't find something, it says `DATA GAP` instead of guessing. This is the difference between analysis you can act on and analysis that just sounds confident.

## What's inside

```
market-analysis/
├── SKILL.md                              ← the orchestrator: what to do, in what order
└── references/
    ├── config.md                         ← the honesty protocol (confidence tags, data gaps)
    ├── wave1-competitor-profiles.md      ← Wave 1: who the competitors are
    ├── wave1-pricing-intelligence.md     ← Wave 1: what they charge
    ├── wave2-review-mining.md            ← Wave 2: what customers say (G2, Capterra, etc.)
    ├── wave2-community-mining.md         ← Wave 2: what customers say (Reddit, forums)
    ├── wave3-gtm-analysis.md             ← Wave 3: how competitors sell and market
    ├── wave3-strategic-signals.md        ← Wave 3: funding, hiring, product direction
    ├── output-report.md                  ← template: executive report
    ├── output-matrix.md                  ← template: feature matrix
    ├── output-pricing-map.md             ← template: pricing landscape
    └── output-battle-cards.md            ← template: per-competitor battle cards
```

## Install

This uses a format called **Agent Skills** (`SKILL.md` plus a `references/` folder), an open convention now supported by several AI coding tools. Support varies by platform; here's the honest breakdown.

### Claude (claude.ai, Claude Code, or Cowork)

Claude has native support for this format.

- **claude.ai (web/desktop app):** Settings → Capabilities → Skills → upload the `market-analysis` folder (or a zipped `.skill` file if you've packaged one).
- **Claude Code / Cowork:** copy the folder into `.claude/skills/market-analysis/` in your project (or `~/.claude/skills/market-analysis/` to make it available everywhere).

Once installed, just describe your market or product idea in a new conversation. No need to name the skill; it should trigger automatically. If it doesn't, say "use the market analysis skill" explicitly.

### GitHub Copilot (VS Code agent mode, Copilot CLI, or coding agent)

Copilot added native Agent Skills support in December 2025, using the exact same `SKILL.md` format.

- **Project-level:** copy the folder into `.github/skills/market-analysis/` in your repo.
- **Global (all your repos):** copy it into `~/.copilot/skills/market-analysis/`.

Copilot loads skills automatically when it decides your prompt is relevant, using the same trigger behavior as Claude. Note: this skill was written and tested against Claude. Copilot should follow it, but if you notice it skipping steps or under-tagging confidence, that's worth flagging as a difference in how the two models follow multi-step instructions, not a bug in the file.

### ChatGPT

**Straight talk: ChatGPT does not support this file format natively.** There's no folder to drop this into. You have two options, and both require a bit of manual setup:

**Option A: ChatGPT Project (easiest, private to you)**
1. Create a new Project in ChatGPT.
2. Open `market-analysis/SKILL.md` and paste its contents into the Project's custom instructions.
3. Upload every file in `references/` to the Project's files.
4. Start a new chat inside the Project and describe your market. ChatGPT will use the instructions and files as context.

**Option B: Custom GPT (if you want to share it with others)**
1. Create a new GPT in the GPT Builder.
2. Paste `SKILL.md` into the GPT's instructions field.
3. Upload the `references/` files as Knowledge.
4. Publish or share the link.

Both options work, but they're a weaker version of what Claude/Copilot do: ChatGPT won't automatically decide when to "load" a reference file the way a real Skill does, so it may need reminders mid-conversation ("check the config.md rules on confidence tagging") if it starts drifting from the honesty protocol.

## How to run it

However you installed it, the process is the same:

1. Start a new conversation and describe your market: what you're building, who the customer is, any competitors you already know, your differentiator, and what you most want to learn.
2. The assistant runs three research waves in order (competitors + pricing → customer sentiment → GTM signals), pausing between them.
3. It synthesizes everything into four deliverables, presented one at a time: report, matrix, pricing map, battle cards. You review and can ask for changes between each one.

## Limitations (read this before you trust the output)

- **This is not automated.** You need to be present for each wave. If you want a "kick it off and come back to finished reports" experience, this isn't it; that requires an actual API-driven pipeline.
- **Web search quality varies by platform.** The research is only as good as the assistant's ability to search the web and read what it finds. Results will differ across Claude, Copilot, and ChatGPT depending on their search tools.
- **The honesty protocol depends on the model actually following it.** Confidence tags (`[Data]` / `[Estimate]` / `[Assumption]`) and `DATA GAP` flags are instructions, not guarantees. Spot-check a few claims yourself, especially anything you're about to base a real decision on.
- **It was built and tested on Claude.** It should port reasonably well to Copilot since they share the Skills format, and less predictably to ChatGPT since it's a manual workaround there. Treat any behavior differences as expected, not broken.

## Customizing

Everything is plain markdown. Edit the wave files to change what gets researched, edit `output-*.md` to change deliverable formats, or edit `config.md` to loosen or tighten the honesty rules. No code required.

## License

Add a license of your choice before publishing (MIT is a reasonable default for a prompt/instructions repo like this).
