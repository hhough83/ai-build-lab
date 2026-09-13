---
name: home-affordability-calculator
description: Builds a personalized, interactive HTML home-affordability calculator for a specific location — researches that area's property tax rate and typical utility costs, then generates a self-contained webpage the user can open in any browser to adjust home price, down payment, property tax, and home size and see monthly cost and % of income update live. Use this whenever the user asks "can I afford a house in X", wants a home affordability or mortgage calculator for a specific city/county, wants to compare home sizes or down payment scenarios for a real estate decision, or asks to turn a home-buying analysis into an interactive tool. Trigger even if they don't say "HTML" or "calculator" explicitly — phrases like "help me figure out what I can afford in [place]" or "build me something to play with the numbers for this house" both qualify.
---

# Home Affordability Calculator

Generates a single self-contained HTML file: a location-aware home affordability
calculator with live sliders for home price, down payment, property tax, and home
size. No server, no database — everything runs client-side in the browser.

The whole point of this skill is that it's *personalized*: default values, tax
rate, utility costs, and even the visual theme should reflect the specific place
the user is buying in, not generic national averages. Research is not optional —
it's the reason this skill exists instead of just handing over a static template.

## Step 1: Collect inputs

Ask the user for (use `ask_user_input_v0` if available, otherwise ask in prose):

1. **Location** — city/county + state. This drives the property tax and utility
   research, so push for specificity ("Lehigh County, PA" is far more useful than
   "Pennsylvania").
2. **Down payment** — a dollar amount they're planning to put down.
3. **Home size(s)** — one or more square footage values they want to compare
   (e.g., "2,000 and 3,200 sqft", or just one number if they only care about one
   size). Support 2–4 sizes as tiers/buttons in the tool.
4. **Home price (or price range)** — needed to compute the mortgage and property
   tax dollar amount. If they haven't given one, ask, or infer a reasonable
   starting point from typical home prices in that location (say what you
   assumed and why).
5. **Gross annual income** — used (not net/take-home) because it's what lenders
   actually underwrite against, and it's a number people can state without
   digging up a paystub.
6. **Average monthly debt payments** — credit cards, auto loans, student loans,
   and any other recurring debt obligations *outside* utilities, the mortgage
   itself, and general household bills. This is what turns the calculator into
   a real debt-to-income (DTI) check instead of a loose affordability guess.

Don't over-ask. Six questions is the ceiling — if the user already gave some of
this in their message, don't re-ask it. If someone truly doesn't know their
monthly debt off-hand, $0 is an acceptable default, but say that's what you
assumed — it changes the DTI number meaningfully.

## Step 2: Research the location

Use web search for each of these. This is the step that makes the output actually
useful instead of a generic template — don't skip it or fall back to national
averages without trying local sources first.

**Property tax rate:**
- Search for "[county] property tax rate" or "[county] effective tax rate" —
  county assessor sites, SmartAsset, and Tax-Rates.org tend to have current
  effective rates (tax paid ÷ assessed value, expressed as a %).
- Compute the annual dollar amount as `home price × effective rate`. Use this as
  the slider default, but keep the slider range wide (roughly 0.3× to 3× the
  computed default) so the user can still explore scenarios.

**Utility costs, by home size:**
- Search for the area's electricity rate (¢/kWh) — EIA state/utility data is
  the most reliable source.
- Determine the dominant heating fuel for that region (natural gas, electric,
  heating oil, or propane) — this varies a lot by state and even by county
  (rural areas without gas lines often run oil or propane, which cost more).
  Search "[county] heating fuel type common" or check EIA's residential energy
  consumption survey data for the region.
- Search for typical water/sewer costs in that municipality if it's on a public
  system, or note that well/septic means minimal recurring water cost.
- Combine electricity + heating + water/sewer + internet (~$120–150/mo is a fine
  assumption almost anywhere) + trash into **one blended monthly total per home
  size** — this skill does NOT show utilities itemized, just a single combined
  number per size tier. Scale the total up with square footage (a 5,000 sqft
  home might run 60-80% more than a 2,000 sqft home in the same area, mostly
  from heating and cooling load).

**Homeowners insurance (nice-to-have, don't block on it):**
- If you find a state or regional average easily, scale it by home size and
  include it. If not, a reasonable placeholder ($100–350/mo depending on size
  and region — higher in coastal/wildfire/severe-weather states) is fine, just
  say it's an estimate.

**Current mortgage rate:**
- A quick search for "current 30 year mortgage rate" is worth doing so the
  default isn't stale — rates move. Don't guess from memory.

Cross-check numbers that seem surprising (e.g., a property tax rate under 0.3%
or over 3% is unusual — verify before using it).

## Step 3: Pick a visual theme for the location

The generated page should feel like it belongs to that place, not like a generic
dashboard. Pick a color palette and a subtle SVG background motif that fits the
location's character:

- Mountain/rural (Poconos, Rockies, Appalachia): deep forest greens, warm amber
  accents, topographic contour-line motif.
- Coastal (New England shore, Pacific Northwest, Gulf Coast): navy/slate blues,
  sandy or coral accent, gentle wave-line motif.
- Desert Southwest: warm terracotta/clay, deep umber background, dune or mesa
  silhouette motif.
- Urban/metro: charcoal or graphite background, a crisp single accent color
  (electric blue, signal orange), fine grid-line motif instead of organic lines.
- If nothing obvious fits, a tasteful neutral (slate background, warm accent) is
  always safe — don't force a theme that doesn't match.

Use your judgment; this list is illustrative; don't mechanically apply it to
places that don't fit the pattern.

Whatever you choose, keep contrast high enough to read comfortably (dark
background + light text, or the reverse — don't do light-on-light or
dark-on-dark) and keep the motif subtle (low opacity, background layer, never
competing with the actual numbers).

## Step 4: Fill in the template

Copy `assets/template.html` to your workspace, then use `str_replace` to fill in
every `{{PLACEHOLDER}}` token. Reference table:

| Placeholder | What goes here |
|---|---|
| `{{PAGE_TITLE}}` | e.g. "Lehigh County Home Affordability Calculator" |
| `{{GOOGLE_FONTS_URL}}` | A Google Fonts `<link>` href with a display serif + body sans + mono (Fraunces/IBM Plex is a safe default; swap for something else if the theme calls for it) |
| `{{FONT_DISPLAY}}`, `{{FONT_BODY}}`, `{{FONT_MONO}}` | The three font-family names from that URL |
| `{{COLOR_BG_DEEP}}`, `{{COLOR_BG_MID}}`, `{{COLOR_BG_PANEL}}` | Background colors, darkest to lightest, per your chosen theme |
| `{{COLOR_PAPER}}`, `{{COLOR_PAPER_DIM}}` | Primary and secondary text colors |
| `{{COLOR_ACCENT}}`, `{{COLOR_ACCENT_BRIGHT}}` | Theme accent color, two shades |
| `{{COLOR_OK}}`, `{{COLOR_WARN}}`, `{{COLOR_BAD}}` | Verdict-band colors — keep these green/amber/red-ish regardless of theme, since that mapping is meaningful, just tune the exact hue to fit |
| `{{COLOR_LINE}}` | A low-opacity border color, e.g. `rgba(255,255,255,0.12)` |
| `{{COLOR_GLOW}}` | A very low-opacity accent color for the header glow, e.g. `rgba(200,140,60,0.08)` |
| `{{MOTIF_SVG}}` | Raw SVG `<path>`/`<g>` markup for the background motif, viewBox 0 0 1200 800, opacity 0.04–0.08 |
| `{{EYEBROW_TEXT}}` | The location, e.g. "Lehigh County, Pennsylvania" |
| `{{H1_TEXT}}` | "Home Affordability Calculator" (customize only if it improves clarity) |
| `{{SUBTITLE_TEXT}}` | One or two sentences on what the tool does |
| `{{PRICE_MIN}}`, `{{PRICE_MAX}}`, `{{PRICE_STEP}}`, `{{PRICE_DEFAULT}}` | Numeric slider bounds and default for home price, sized to the local market |
| `{{PRICE_MIN_LABEL}}`, `{{PRICE_MAX_LABEL}}`, `{{PRICE_DEFAULT_LABEL}}` | Same values, formatted for display (e.g. "$400K", "$675,000") |
| `{{DOWN_MIN}}`, `{{DOWN_MAX}}`, `{{DOWN_STEP}}`, `{{DOWN_DEFAULT}}` + labels | Same pattern, for down payment |
| `{{TAX_MIN}}`, `{{TAX_MAX}}`, `{{TAX_STEP}}`, `{{TAX_DEFAULT}}` + labels | Same pattern, for annual property tax dollar amount |
| `{{SIZE_BUTTONS_HTML}}` | One `<button data-sqft="N">label</button>` per size tier the user asked about, first one with `class="active"` |
| `{{SIZE_DEFAULT_SQFT}}` | The sqft value of that first/active button, as a bare number |
| `{{RATE_DEFAULT}}` | Current researched mortgage rate, e.g. `6.75` |
| `{{GROSS_MIN}}`, `{{GROSS_MAX}}`, `{{GROSS_DEFAULT}}` + labels | Slider bounds and default for gross annual income, from what the user told you |
| `{{DEBT_DEFAULT}}` + label | Default for average monthly debt payments, from what the user told you (or `0` if they didn't know, flagged as an assumption) |
| `{{UTILITY_TOTALS_JS}}` | JS object literal mapping each sqft to its blended monthly utility total, e.g. `{ 2000: 310, 3200: 430 }` |
| `{{INSURANCE_TOTALS_JS}}` | Same shape, for homeowners insurance |
| `{{FOOTER_NOTE}}` | 2–4 sentences: what's included, key assumptions, and an honest reminder that this is a planning tool, not a lender quote or tax bill — verify locally before making an offer |

A few things to get right:
- `{{SIZE_BUTTONS_HTML}}`, `{{UTILITY_TOTALS_JS}}`, and `{{INSURANCE_TOTALS_JS}}`
  must use the exact same sqft numbers as keys/values, or the lookup breaks.
- Keep slider ranges sensible relative to the default (roughly ±40-50% for price
  and down payment, wider for tax since rates vary a lot by scenario).
- Don't leave any `{{...}}` token unreplaced — check with a quick grep before
  finishing.

### How the tool scores affordability

The template computes two different percentages — don't blur them together:

- **Back-end DTI** (`housing costs + monthly debt` ÷ `gross monthly income`) is
  the number lenders actually use to qualify a mortgage. Utilities are *not*
  part of a lender's DTI calculation, so this figure intentionally excludes
  them. The verdict bands are built on this number, using standard conventional
  underwriting guidelines: under 36% is very conservative, 36–43% is the normal
  qualifying range most lenders accept, 43–50% is the tight end most lenders
  will still approve with compensating factors, and 50%+ exceeds what most
  conventional lenders allow.
- The headline **"% of gross income"** figure in the verdict banner includes
  utilities too, since that's a fuller picture of real monthly cash flow even
  though it's not what a bank checks.
- "Left Over / Month" is gross income minus obligations — it is **not**
  spendable cash, since income tax hasn't come out yet. Say this plainly in the
  footer note so the user doesn't mistake it for net.

## Step 5: Save and present

Save the finished file to `/mnt/user-data/outputs/` with a descriptive name
(e.g. `lehigh_county_affordability_calculator.html`), then use `present_files`
so the user can open it. In your reply, briefly state the key researched numbers
(property tax rate used, utility estimate, mortgage rate) so the user can sanity
check them — don't just hand over the file silently.

## Verification before handing off

Quickly grep the filled-in file for any leftover `{{` to catch missed
placeholders, and mentally re-derive one data point (e.g. mortgage payment at
the default price/down/rate) to confirm the math lines up with what's displayed.
