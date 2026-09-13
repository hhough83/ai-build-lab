# Home Affordability Calculator

A reusable AI skill that generates a personalized, interactive home
affordability calculator for any location, delivered as a single
self-contained HTML file you can open in any browser. No installs, no
server, no account.

It's written as a Claude skill (a `SKILL.md` file), but the instructions are
plain markdown, so the same file works as a Custom GPT configuration in
ChatGPT or as repository instructions for GitHub Copilot. Setup steps for
all three are below.

## Why I built this

My husband and I are starting the process of selling our current home and
buying a new one. Partway through, I realized the numbers that actually
determine what we can comfortably afford don't live in any one place:

- A mortgage pre-approval tells you what a bank will lend you, not what your
  monthly budget can actually absorb once utilities, taxes, and existing debt
  are in the picture.
- A home listing gives you square footage and an asking price, not what it
  costs to heat, cool, and run water through that house in that specific
  region.
- Property tax rates vary widely by county and even by township, and pulling
  the effective rate (not just the statutory one) usually means digging
  through county assessor sites or paid tools.

None of that is hard to find individually. But pulling it all together for
every house you're seriously considering, every time, is genuinely tedious,
and it's exactly the kind of research-then-synthesize task an AI agent is
good at. So I built a skill that does the legwork: it asks a few questions,
researches the location, and hands back a calculator with real, current
numbers already loaded in, with every input still adjustable, because no two
houses (or two people's assumptions) are the same.

## What it does

Give it a location, a down payment, one or more home sizes to compare, your
gross annual income, and your average monthly debt payments. It will:

1. Research that area's effective property tax rate and typical utility
   costs (electricity, heating fuel, water/sewer) scaled to each home size.
2. Look up a current mortgage rate rather than relying on a stale default.
3. Generate a calculator with all of that pre-loaded, styled with a visual
   theme that fits the location.
4. Compute both:
   - Back-end DTI (housing + debts divided by gross income), the ratio
     lenders actually use to qualify a mortgage.
   - Percent of gross income including utilities, a fuller real-world
     picture of monthly cash flow, since utilities aren't part of a bank's
     math but they are part of your actual bill.

Every number (home price, down payment, property tax, interest rate, loan
term, home size, income, debt) stays adjustable after the file is generated.
It's meant for playing out scenarios, not just reading one static answer.

## Important: these are averages, not quotes

The research behind this tool pulls area-level averages, not house-specific
facts. Every home is different. A 2,000 sqft house with new windows and a
heat pump will cost less to run than a 2,000 sqft house from 1975 with an
oil furnace, even on the same street. Treat the property tax and utility
figures as a realistic starting point for budgeting, not as a substitute
for:

- The actual tax bill for a specific property (available from the county
  assessor or usually disclosed by the listing agent).
- Real utility bills from the current homeowner (a good question to ask
  during a showing or in an offer contingency).
- A lender's actual pre-approval numbers, which factor in your full credit
  picture.

This tool is for narrowing down what's realistic before you're deep into the
process, not for finalizing a budget the week before closing.

## What's in this repo

```
home-affordability-calculator/
├── SKILL.md              # The instructions an AI assistant follows
├── assets/
│   └── template.html     # The calculator template, with {{PLACEHOLDER}} tokens
└── README.md              # This file
```

`SKILL.md` is the actual skill definition. It spells out what questions to
ask, what to research, and how to fill in the template. `template.html` is
the reusable shell; each time the skill runs, the assistant fills it in with
location-specific numbers and saves a new, complete HTML file.

## Installing and using this skill

### Claude (claude.ai or Claude Code)

1. Download `home-affordability-calculator.skill` (or point Claude at this
   repo's `SKILL.md` directly).
2. In Claude, add it as a custom skill. If you have a packaged `.skill`
   file, Claude's interface will show a "Save skill" button when you share
   it in a conversation.
3. In a new conversation, just ask for what you want, for example:
   > "Can I afford a house in Lehigh County, PA? I'm putting $150K down,
   > comparing 2,000 and 3,200 sqft homes, gross about $130K a year, and pay
   > $450 a month in other debt."
4. Claude will ask for anything missing, research the area, and hand you
   back a ready-to-open HTML file.

### GitHub Copilot

Copilot reads repository-level instructions from a file at
`.github/copilot-instructions.md`, and reads standalone agent instructions
from an `AGENTS.md` file at the repository root.

1. Copy the contents of `home-affordability-calculator/SKILL.md` into a new
   file at `.github/copilot-instructions.md` in the repo where you want to
   use it (or into `AGENTS.md` at the repo root if you're using Copilot's
   coding agent).
2. Keep `assets/template.html` somewhere in the same repo so Copilot can
   find and edit it, and reference its path in your instructions file if
   it's not at the default location.
3. Open Copilot Chat and describe what you want, the same way you would
   with Claude. Copilot will use the instructions file as context and
   should follow the same research-then-fill-in-the-template workflow.
4. Since Copilot is built for coding workflows, it's most reliable when you
   explicitly ask it to "edit `assets/template.html` and save the result as
   a new file" rather than leaving that step implicit.

### ChatGPT

ChatGPT doesn't read a `SKILL.md` file automatically, but you can turn this
into a Custom GPT in a few minutes.

1. Go to the GPT builder (Explore GPTs, then Create) and choose the
   Configure tab.
2. Paste the full contents of `SKILL.md` into the Instructions field.
3. Under Knowledge, upload `assets/template.html` so the GPT has the
   template available to edit.
4. Turn on Code Interpreter/Data Analysis under Capabilities. This lets the
   GPT actually edit the HTML file and hand you back a downloadable result,
   instead of only pasting code into the chat.
5. Save the GPT, then start a conversation the same way you would with
   Claude, describing your location, down payment, home sizes, income, and
   debt.

If you don't want to build a Custom GPT, you can also just start a regular
ChatGPT conversation, paste in the SKILL.md instructions plus your request
in the same message, and attach `template.html` as a file. It works for a
one-off use, but a Custom GPT is worth it if you'll run this more than once.

## Tech notes

- Pure HTML, CSS, and JavaScript. No build step, no dependencies, no
  backend.
- Each generated calculator is fully self-contained. You can email it, host
  it, or just keep it on your desktop.
- The visual theme (colors, background motif) is chosen per location by the
  assistant rather than hardcoded, so a calculator for a mountain town looks
  different from one for a coastal city.

## License

MIT. Use it, fork it, adapt it for your own house hunt.
