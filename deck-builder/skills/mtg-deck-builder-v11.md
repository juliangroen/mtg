# SKILL: MTG Commander Deck Builder & Upgrader (v11)

### Description
An agentic AI instruction set for building, auditing, and upgrading Magic: The Gathering (MTG) Commander (EDH) decks. It uses systematic 8x8 categorization, core infrastructure ratios, color-scaled mana base construction, mana curve optimization, archetype-specific subskill routing, strict **Card Verification & Anti-Hallucination Protocols**, automated dual-source web data retrieval (EDHrec JSON + Scryfall recency/set queries), and exportable plaintext decklist generation.

---

## 1. Core Architectural Framework

### A. The 8x8 Categorization Method
- **Core Math**: A standard Commander deck consists of **1 Commander + 35 Lands + 64 Spells** organized into 8 distinct categories of 8 cards each.
- **The Core Four Infrastructure Categories (32 Cards)**:
  1. **Ramp (8 cards)**: Mana acceleration (rocks, dorks, land ramp, signets).
  2. **Card Draw (8 cards)**: Sustained draw engines and burst refills.
  3. **Removal (8 cards)**: Spot removal and board wipes.
  4. **Commander Synergy (8 cards)**: Cards directly supporting or scaling the commander's ability.
- **Strategy-Specific Categories (32 Cards)**: 4 custom categories of 8 cards tailored to the deck's primary archetype (e.g., Win Conditions/Finishers, Protection, Recursion, Tokens, Tribal Synergy, Tutors, Evasion, or Enablers).
- **Grid Variants**: Adjust to 7x9 (9 categories of 7 cards), 9x7 (7 categories of 9 cards), or asymmetrical splits (e.g., 10-8-8-6-6-6-6-6-8) as dictated by specific deck needs.

### B. Baseline Ratios & Infrastructure Requirements
- **Total Mana Sources**: Lands + Ramp MUST equal **47-50 total mana sources**.
  - *Standard baseline*: **37 Lands + 10 Ramp** = 47 mana sources.
  - *Heavy ramp package*: **35 Lands + 12 Ramp**.
  - *High-curve / 6+ CMC commander*: **38-39 Lands + 10 Ramp**.
- **Infrastructure Floors**:
  - **Card Draw Floor**: Minimum **8 cards**. Decks with fewer than 8 run out of gas by turn 6.
  - **Ramp Floor**: Minimum **10 cards**.
  - **Targeted Removal Floor**: **8-12 cards** (instant-speed preferred).
  - **Board Wipes Floor**: **3-4 cards** (minimum 2; asymmetric preferred).
  - **Win Conditions Floor**: **7-10 dedicated slots**. The deck must include at least 5 distinct cards or clear lethal paths that close out games.
  - **Protection Floor**: **2-4 cards** (boots, counterspells, indestructible effects).
  - **Recursion Floor**: **2-4 cards**.
- **Multi-Role Spells**: Multi-purpose spells (e.g., *Beast Within*, *Ravenous Chupacabra*, *Skullclamp*) should be assigned to whichever core category is currently weakest in the deck structure.

### C. Mana Base & Color Scaling Rules
- **Baseline**: Begin with ~37 lands and scale based on color count and curve.
- **Color Count Scaling**:
  - **Mono-Color**: 28-32 Basics + 5-8 colorless Utility Lands (e.g., *Rogue's Passage*, *War Room*).
  - **Two-Color**: Basics + dual lands, with ~4 utility lands.
  - **Three-Color**: 37-38 Lands total, heavy dual/tri-land fixing, 8-12 basics, max 2-3 utility lands.
  - **Four / Five-Color**: Almost all lands must produce multiple colors; 2-3 basics per color max (for fetch targets); 0-1 colorless utility lands.
- **Land Tiers & Quality Priorities**:
  - *Tier 1*: Fetch Lands, Original Duals.
  - *Tier 2*: Shock Lands, Bond Lands (top tier in multiplayer).
  - *Tier 3*: Pain Lands (cheap, always untapped), Check Lands, Slow Lands.
  - *Tier 4*: Filter Lands, Triomes.
  - *Tier 5*: Tap Lands (budget fallback).
  - *Budget Mana Base Rule*: Prioritize untapped pain lands, Command Tower, Exotic Orchard, and Evolving Wilds / Terramorphic Expanse over always-tapped lands.

### D. Mana Curve & Casting Cost Calibration
- **Average Mana Value Target**: Aim for **2.8 to 3.5** across non-land spells.
  - *Avg CMC < 2.8*: Hyper-aggressive or combo decks.
  - *Avg CMC > 3.5*: High-curve decks requiring extra land/ramp support.
- **Curve Distribution Rules**:
  - At least **50% of non-land spells MUST cost 3 or less**.
  - The bulk of utility and infrastructure spells must sit at **2-4 mana**.
  - Spells costing 5+ must provide high multi-opponent impact.
- **Commander CMC Adjustments**:
  - *Cheap Commander (1-3 CMC)*: Enables a low, lean curve.
  - *Mid-Range Commander (4-5 CMC)*: Uses the standard curve profile.
  - *Expensive Commander (6+ CMC)*: Requires a **bimodal curve**—a heavy concentration of 1-3 CMC ramp/interaction and a smaller set of high-impact endgame plays.
- **Practical Mana Costs**: Evaluate cards by true casting cost rather than printed cost (e.g., *Blasphemous Act* as 1-2 CMC, *Treasure Cruise* as 1-2 CMC, Convoke/Delve).

---

## 2. Archetype Subskill Routing Rule

When building or auditing a deck with a specific playstyle, load the corresponding archetype subskill (e.g., `skills/archetypes/{archetype}.md`) to apply ratio overrides and custom categories:
1. **Identify Deck Archetype**: Aggro, Control, Combo, Aristocrats, Spellslinger, Voltron, Tokens, Reanimator, Stax, Enchantress, Landfall, Tribal, Mill, Superfriends, Blink, Wheels, Group Hug, Pillowfort, Midrange, Storm, or Chaos.
2. **Apply Subskill Overrides**: Adjust baseline creature count, interaction suite, wipe density, and target average CMC according to subskill parameters.
3. **Fill Custom 8x8 Categories**: Use the 4 custom strategy categories defined in the subskill to complete the 32 strategy slots in the 8x8 matrix.

---

## 3. Verification & Dual-Source Data Retrieval Protocol

### A. MANDATORY Anti-Hallucination & Card Verification Gate
**Rule**: The AI agent MUST NEVER rely on unverified memory, state card abilities from memory without double-checking, or guess card types/effects.
1. **Oracle Text & Card Type Verification**: Before declaring what a card does or assigning it to a functional category (e.g., verifying if a spell is a tutor, bounce, draw, or removal), the agent MUST verify its exact Oracle text, card type, and CMC via Scryfall or EDHrec JSON endpoints.
2. **Color Identity Check**: Confirm every card strictly matches the Commander's color identity before adding it to a decklist.
3. **Format Legality Check**: Confirm the card is legal in Commander (`f:commander`).

### B. Flexible New-Card Discovery Protocol (Scryfall)
EDHrec historical deck counts lag behind new set releases (Universes Beyond sets like TMNT, Marvel, Final Fantasy, recent expansion blocks, or newly printed mechanics). To ensure new cards are evaluated fairly alongside established staples:
1. **Targeted Scryfall Queries**: Execute parallel Scryfall searches for recent sets and relevant keywords:
   - `https://scryfall.com/search?q=f:commander+ci:{color_identity}+(year>=2024+or+s:{set_code})&order=edhrec`
   - `https://scryfall.com/search?q=f:commander+ci:{color_identity}+(o:"{mechanic_clause}"+or+kw:{keyword}+or+t:{type})&order=edhrec`
2. **Flexible Integration Policy**: Actively evaluate newly released or set-specific cards and integrate synergistic options naturally across existing functional categories rather than forcing a rigid dedicated category.

### C. EDHrec Priority for Commander Discovery & Staples
1. **Master Tag Indexes**:
   - Theme Index: `https://json.edhrec.com/pages/tags/themes.json`
   - Typal Index: `https://json.edhrec.com/pages/tags/typal.json`
2. **Commander & Synergy Endpoints**:
   - `https://json.edhrec.com/pages/commanders/{commander-slug}.json`
3. **Extract Established Staples**: Use EDHrec JSON to capture top-ranked staple infrastructure, high-synergy cards, and consensus choices.

### D. Notebook Source Persistence Policy
When running within a notebook environment:
- **EDHrec JSON Endpoints**: Fetch raw JSON content and save as text sources (`add_sources` with `type: 'text'`).
- **Scryfall Search URLs (HTML)**: Add directly as web URL sources (`add_sources` with `type: 'web_url'`).

---

## 4. Exportable Plaintext Decklist Artifact Standard

When a deck build or overhaul is finalized, the agent MUST generate a clean, unformatted `.txt` file artifact in `/workspace/out/{commander-slug}-decklist.txt`.

### Format Requirements:
- Standard Quantity-First Syntax (`1 Card Name` or `12 Island`).
- Optional Section Headers (`// Commander`, `// Ramp`, `// Creatures`, `// Lands`).
- **No Markdown, HTML, bullets, or extra commentary** inside the `.txt` file.
- Total maindeck card count MUST equal **99** (+ 1 Commander = 100 total cards).

---

## 5. Agentic Workflow Instructions

### Workflow A: Building a New Deck from Scratch
1. **Commander Discovery & Recommendation**:
   - Identify canonical tag using `themes.json` or `typal.json`.
   - Fetch theme/typal JSON page (`themes/{theme}.json` or `tribes/{tribe}.json`).
   - Present top commanders ranked by EDHrec deck count.
2. **Define Context**: Confirm Commander, printed/practical CMC, color count, and strategy archetype.
3. **Dual-Source Retrieval & Verification**:
   - Fetch EDHrec commander JSON (`commanders/{commander-slug}.json`).
   - Execute targeted Scryfall recency/set/keyword query (`year>=2024`, `s:{relevant_set}`, `o:"{keyword}"`, `t:{creature_type}`).
   - **Verification Gate**: Check exact Oracle text, color identity, and card type for every candidate card before slotting.
4. **Establish Mana Foundation**:
   - Calculate Lands (35-38) + Ramp (10-12) to hit **47-50 total mana sources**.
   - Select utility land allowance based on color count.
5. **Build the 8x8 Non-Land Matrix**:
   - Allocate Core 4 categories: Ramp (8), Draw (8), Removal (8), Commander Synergy (8).
   - Allocate 4 custom strategy categories, integrating synergistic new set releases alongside established EDHrec staples.
6. **Curve & Win Condition Audit**:
   - Verify Average Mana Value is between **2.8 and 3.5**.
   - Confirm at least **50% of non-land spells cost 3 or less**.
   - Ensure at least **5 clear win condition cards/combos** exist.
7. **Generate Exportable Decklist Artifact**:
   - Write plaintext decklist to `/workspace/out/{commander-slug}-decklist.txt`.

---

## 6. Output Format Standard
Present deck builds in four distinct sections:
1. **Deck Architecture Summary**: Commander, Archetype, Lands/Ramp total, and Average CMC.
2. **Categorized Card List (8x8 Grid)**: Grouped by category with multi-role annotations.
3. **Mana Base Breakdown**: Color distribution, untapped duals, and utility lands.
4. **Ratio & Curve Audit Table**: Showing current stats vs. baseline targets (Draw, Ramp, Removal, <=3 CMC %, Win Cons).
