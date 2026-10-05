# SKILL: MTG Oathbreaker Deck Builder & Upgrader (v5)

### Description

An agentic AI instruction set for building, auditing, and upgrading Magic: The Gathering (MTG) Oathbreaker decks. It adapts the Commander 8x8 framework into a systematic **6x6 categorization method** (1 Oathbreaker + 1 Signature Spell + 22 Lands + 36 Maindeck Spells in 6 categories of 6 cards), incorporating Oathbreaker-specific mana curve targets, color-scaled mana base construction, strict **Mandatory Card Verification & Anti-Hallucination Protocols**, automated dual-source retrieval (EDHrec JSON + Scryfall recency & keyword queries), and exportable plaintext decklist generation.

---

## 1. Core Architectural Framework

### A. The 6x6 Categorization Method

- **Core Math**: An Oathbreaker deck consists of **1 Oathbreaker (Planeswalker) + 1 Signature Spell (Instant/Sorcery) + 22 Lands + 36 Maindeck Spells** organized into 6 distinct categories of 6 cards each (60 cards total).
- **Command Zone (2 Cards)**:
  1. **Oathbreaker**: 1 Planeswalker card that defines color identity and deck strategy.
  2. **Signature Spell**: 1 Instant or Sorcery card within the Oathbreaker's color identity. Castable from the Command Zone only while the Oathbreaker is on the battlefield (command zone tax applies).
- **The Core Three Infrastructure Categories (18 Cards)**:
  1. **Ramp & Acceleration (6 cards)**: Low-cost mana acceleration (1-2 CMC rocks, dorks, land ramp, cost reducers) ensuring reliable turn 2-3 Planeswalker casting.
  2. **Card Draw & Selection (6 cards)**: Low-cost draw engines, cantrips, or refills tailored to a fast 60-card format.
  3. **Removal & Interaction (6 cards)**: Cheap spot removal, counterspells, or asymmetric board wipes to protect your Planeswalker and disrupt opponents.
- **Strategy-Specific Categories (18 Cards)**: 3 custom categories of 6 cards tailored to the deck's primary archetype and command zone synergies (e.g., Planeswalker Protection/Loyalty Synergies, Signature Spell Synergies, Win Conditions/Finishers, Tribal Synergies, or Evasion/Enablers).

### B. Baseline Ratios & Infrastructure Requirements

- **Total Mana Sources**: Lands (22) + Ramp (6) = **28 total mana sources** (~46.7% of deck).
  - *Standard baseline*: **22 Lands + 6 Ramp**.
  - *High-curve / 5+ CMC Oathbreaker*: **23-24 Lands + 7-8 Ramp**.
  - *Ultra-lean / 2-3 CMC Oathbreaker*: **20-21 Lands + 5-6 Ramp**.
- **Infrastructure Floors**:
  - **Card Draw Floor**: Minimum **6 cards**.
  - **Ramp Floor**: Minimum **6 cards** (1-2 CMC preferred).
  - **Targeted Removal Floor**: **6-8 cards** (instant-speed preferred).
  - **Board Wipes Floor**: **2 cards** (asymmetric or low-CMC preferred).
  - **Planeswalker Protection Floor**: **4-6 cards** (chump blockers, pillowfort, counterspells, hexproof).
  - **Win Conditions Floor**: **4-6 dedicated slots** or clear lethal paths (including Signature Spell combos).

### C. Mana Base & Color Scaling Rules (22-Land Baseline)

- **Baseline**: Begin with 22 lands and scale based on color count and curve.
- **Color Count Scaling**:
  - **Mono-Color**: 16-18 Basic Lands + 4-6 Utility Lands (e.g., *Karn's Bastion*, *War Room*, *Interplanar Beacon*).
  - **Two-Color**: 12-14 Basics + 8-10 dual lands + 2-3 utility lands.
  - **Three-Color**: 6-8 Basics + 14-16 dual/tri-lands + 1-2 utility lands.
- **Land Quality Priorities**:
  - *Untapped Budget Duals*: Pain Lands, Bond Lands, Shock Lands, Fast Lands.
  - *Planeswalker Utility Lands*: *Interplanar Beacon*, *Karn's Bastion*, *Mobilized District*, *Forge of Heroes*.

### D. Mana Curve & Casting Cost Calibration

- **Average Mana Value Target**: Aim for **2.2 to 3.0** across maindeck non-land spells.
  - *Avg CMC < 2.4*: Aggro, Burn, or fast Combo.
  - *Avg CMC 2.4 - 2.8*: Midrange, Spellslinger, or Planeswalker Control.
- **Curve Distribution Rules**:
  - At least **65% of maindeck spells MUST cost 3 or less**.
  - Bulk of spells sit at **1-3 mana** due to 20 starting life and fast gameplay pace.
- **Signature Spell Cost Calibration**:
  - Signature Spells should ideally cost **1 to 3 mana** to allow repeated casting with the command zone tax (+2 mana per recast).
  - Spells costing 4+ mana must serve as game-ending finishers or total board resets.

---

## 2. Archetype Subskill Routing & Signature Spell Selection

### A. Signature Spell Selection & Recommendation Protocol

Because Oathbreaker requires pairing every Planeswalker with an Instant or Sorcery Signature Spell, the AI agent MUST systematically evaluate and recommend the top 3-4 Signature Spell options using a 4-tier functional taxonomy:

1. **The 4 Functional Signature Spell Taxonomy Categories**:
   - **Tier 1: Evasion & Enabler Spells (Low-CMC Aggro/Tempo)**: Spells that make your Oathbreaker or attackers unblockable or grant haste/trample (*Enter the Enigma*, *Slip Through Space*, *Distortion Strike*, *Shadow Rift*).
   - **Tier 2: Engine & Card Selection Spells (Consistency)**: Cheap cantrips and tutors that ensure you never run out of gas or can repeatedly search for combo pieces (*Brainstorm*, *Lim-Dûl's Vault*, *Ponder*, *Demonic Tutor*, *Splinter's Technique*, *Light Up the Stage*).
   - **Tier 3: Protection & Interaction Spells (Control/Defense)**: Instant-speed answers or defensive shields castable on demand to protect your Oathbreaker (*An Offer You Can't Refuse*, *Counterspell*, *Heroic Intervention*, *Silence*, *Infernal Grasp*).
   - **Tier 4: High-Impact Finishers / Board Resets (Late-Game)**: Game-ending spells or asymmetric wipes cast when you have established board control (*Teferi's Protection*, *Exsanguinate*, *Cyclonic Rift*, *Toxic Deluge*).

2. **Data Sourcing for Signature Spell Recommendations**:
   - **Source A (EDHrec Card JSON)**: Fetch `https://json.edhrec.com/pages/cards/{planeswalker-slug}.json` or `/commanders/`. Parse the `cardlists` object for "Instants" and "Sorceries" to see top community inclusions in decks featuring that Planeswalker.
   - **Source B (Scryfall Oathbreaker Filter)**: Execute `https://scryfall.com/search?q=f:oathbreaker+(t:instant+or+t:sorcery)+ci:{color_identity}+cmc<=3&order=edhrec` to find high-synergy low-cost spells in the exact color identity.
   - **Source C (Oathbreaker Command Tax Heuristic)**: Prioritize spells with **CMC 1 to 2** or spells with mechanics like *Flashback*, *Rebound*, *Buyback*, or *Draw a Card* so the spell remains castable even as command tax increases (+2 mana per cast).

---

## 3. Strict Verification & Dual-Source Data Retrieval Protocol

### A. MANDATORY Anti-Hallucination & Card Verification Gate

**Rule**: The AI agent MUST NEVER rely on unverified memory, state card abilities from memory without double-checking, or guess card types/effects.

1. **Oracle Text & Card Type Verification**: Before declaring what a card does or assigning it to a functional category (e.g. verifying if a spell is a tutor, bounce, draw, or removal), the agent MUST verify its exact Oracle text, card type, and CMC via Scryfall or EDHrec JSON endpoints.
2. **Color Identity Check**: Confirm every card strictly matches the Oathbreaker's color identity before adding it to a decklist.
3. **Format Legality Check**: Verify the card is legal in Oathbreaker (`f:oathbreaker`).

### B. Flexible New-Card Discovery Protocol (Scryfall)

EDHrec historical deck counts lag behind new card releases (Universes Beyond sets like TMNT, Marvel, Final Fantasy, recent expansion blocks, or niche archetype mechanics). To ensure new cards are evaluated fairly alongside established staples:

1. **Targeted Scryfall Queries**: Execute parallel Scryfall searches for recent sets and relevant keywords:
   - `https://scryfall.com/search?q=f:oathbreaker+ci:{color_identity}+(year>=2024+or+s:{set_code})&order=edhrec`
   - `https://scryfall.com/search?q=f:oathbreaker+ci:{color_identity}+(o:"{mechanic_clause}"+or+kw:{keyword}+or+t:{type})&order=edhrec`
2. **Flexible Integration Policy**: Actively evaluate newly released or set-specific cards and integrate synergistic options naturally across existing functional categories rather than forcing a rigid dedicated category.

### C. EDHrec JSON Priority Protocol

Fetch EDHrec data using dual endpoints:

1. `https://json.edhrec.com/pages/commanders/{planeswalker-slug}.json` (if EDH-legal commander)
2. `https://json.edhrec.com/pages/cards/{planeswalker-slug}.json` (fallback for planeswalkers legal only in Oathbreaker)

### D. Notebook Source Persistence Policy

When running within a notebook environment:

- **EDHrec JSON Endpoints**: Fetch raw JSON content and save as text sources (`add_sources` with `type: 'text'`).
- **Scryfall Search URLs (HTML)**: Add directly as web URL sources (`add_sources` with `type: 'web_url'`).

---

## 4. Exportable Plaintext Decklist Artifact Standard

When an Oathbreaker build is finalized, the agent MUST generate a clean, unformatted `.txt` file artifact in `/workspace/out/{oathbreaker-slug}-oathbreaker-decklist.txt`.

### Format Requirements

```text
// Oathbreaker
1 {Planeswalker Name}

// Signature Spell
1 {Instant or Sorcery Name}

// Deck
1 {Card Name}
...
10 {Basic Land Name}
```

- Total maindeck card count MUST equal **58** (+ 1 Oathbreaker + 1 Signature Spell = 60 total cards).

---

## 5. Agentic Workflow Instructions

### Workflow A: Building or Auditing an Oathbreaker Deck

1. **Oathbreaker & Signature Spell Selection**:
   - Identify Oathbreaker (Planeswalker) and Signature Spell (Instant/Sorcery) pairing.
   - Run Signature Spell recommendation protocol to select optimal 1-3 CMC spell.
2. **Dual-Source Retrieval & Verification**:
   - Query EDHrec JSON for Planeswalker synergies (`/cards/{slug}.json` or `/commanders/`).
   - Execute mandatory Scryfall recency & keyword queries (`year>=2024`, `s:{set_code}`, `o:"{mechanic}"`).
   - **Verification Gate**: Check Oracle text, color identity, and card type for every candidate card before slotting.
3. **Establish Mana Foundation**:
   - Calculate Lands (22) + Ramp (6) = 28 total mana sources.
4. **Build the 6x6 Non-Land Matrix**:
   - Allocate Core 3 categories (18 cards): Ramp (6), Draw (6), Removal (6).
   - Allocate 3 Custom Strategy categories (18 cards), integrating synergistic new set releases alongside established staples.
5. **Curve & Ratio Audit**:
   - Target Average CMC: **2.2 to 3.0**.
   - Verify **>=65% of maindeck spells cost 3 or less**.
6. **Generate Exportable Decklist Artifact**:
   - Write plaintext decklist to `/workspace/out/{oathbreaker-slug}-oathbreaker-decklist.txt`.

---

## 7. Output Format Standard

Present Oathbreaker builds in four distinct sections:

1. **Oathbreaker Architecture Summary**: Oathbreaker, Signature Spell, Archetype, Lands/Ramp total, and Average CMC.
2. **Categorized Card List (6x6 Grid)**: Grouped by category with multi-role annotations.
3. **Mana Base Breakdown**: Color distribution, utility lands (*Karn's Bastion*, *Interplanar Beacon*), and budget duals.
4. **Ratio & Curve Audit Table**: Showing current stats vs. baseline targets.
