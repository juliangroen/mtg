# SUB-SKILL: Budget Commander Deck Building (\$50-\$100 Starting Baseline)

### Description
An agentic sub-skill instruction set for building functional, competitive, and scalable Magic: The Gathering (MTG) Commander decks on a strict **\$50-\$100 starting budget**, structured for modular future upgrades and fully aligned with the 8x8 framework and Dual-Source Data Retrieval Protocol in `mtg-deck-builder-v9.md`.

---

## 1. Budget Spending Priority Breakdown (\$100 Allocation)

When building under a \$100 price cap, allocate resources in order of gameplay impact:

| Category | Budget Target | Strategy & Selection Rules |
| :--- | :--- | :--- |
| **Mana Base** | **\$20 - \$30** | **Highest Priority.** A deck that can't cast spells loses. Skip \$10-\$40 fetches, shocks, triomes, and surveil lands. |
| **Ramp Package** | **\$10 - \$15** | Accelerated mana wins games. Use \$0.50-\$2 2-mana rocks and green land ramp spells. |
| **Commander Synergy** | **\$20 - \$30** | Dedicated budget engine cards that directly enable the commander's primary ability. |
| **Win Conditions / Finishers** | **\$10 - \$20** | High-impact budget game-enders that close out games without high price tags. |
| **Removal & Card Draw** | **\$10 - \$15** | Keep interaction cheap (\$0.50-\$2). Save expensive staple slots for budget equivalents. |

---

## 2. Category-by-Category Budget Guidelines

### A. The \$20 Mana Base Blueprint
- **Basics Foundation**: 15-25 basic lands (\$0.00).
- **Core Budget Rainbow Lands**: *Command Tower* (\$1), *Exotic Orchard* (\$1), *Path of Ancestry* (\$1).
- **Color-Specific Budget Cycles**:
  - *Tainted Lands* cycle (\$1-\$3 each, 2-color black decks).
  - *Bounce Lands* (Ravnica Guildgates/Aqueducts, \$0.25 each).
  - *Pain Lands* (\$1-\$2 each - cheap and always enter untapped).
- **Cards to Skip**: Fetch Lands (\$12-\$40), Shock Lands (\$8-\$20), Triomes (\$12-\$30), Check Lands (\$5-\$10).

### B. The \$15 Budget Ramp Suite (10-12 Accelerators)
- **Universal Budget Artifact Ramp**: *Sol Ring* (\$1), *Arcane Signet* (\$1-\$2), *Fellwar Stone* (\$1), *Mind Stone* (\$0.50), *Thought Vessel* (\$1), *Coldsteel Heart* (\$1).
- **Green Budget Land Ramp**: *Cultivate* (\$1), *Kodama's Reach* (\$1), *Rampant Growth* (\$0.50), *Farseek* (\$2).
- **Cards to Skip**: *Mana Crypt* (\$150), *Jeweled Lotus* (\$80), *Mana Vault* (\$25), *Chrome Mox* (\$40).

### C. The \$15 Budget Card Draw Engine (8-10 Draw Spells)
- **Budget Draw Engines**: *Skullclamp* (\$1-\$2), *Bident of Thassa* (\$1), *Harmonize* (\$0.50), *Slate of Ancestry* (\$2), *Mind's Eye* (\$2), *Mystic Remora* (\$4).
- **Cards to Skip**: *Rhystic Study* (\$20-\$40), *Sylvan Library* (\$50-\$100), *Necropotence* (\$30), *Consecrated Sphinx* (\$20).

### D. The \$15 Budget Removal & Interaction Suite
- **Spot Removal**: *Swords to Plowshares* (\$2), *Path to Exile* (\$2), *Beast Within* (\$2), *Generous Gift* (\$2).
- **Board Wipes**: *Crux of Fate* (\$2), *Austere Command* (\$2-\$3), *Mutilate* (\$1), *Cleansing Nova* (\$1).
- **Cards to Skip**: *Cyclonic Rift* (\$20+), *Damnation* (\$40+), *Force of Will* (\$100+).

### E. Budget Win Conditions & Finishers (\$10-\$20)
- **Budget Mass Finishers**: *Overwhelming Stampede* (\$2 - alt-Craterhoof), *Insurrection* (\$3), *End-Raze Forerunners* (\$0.50), *Finale of Devastation* (\$5 budget printings), *Blood Moon* (\$10 budget lock).

---

## 3. Commander Selection Strategy

To keep total deck costs under \$100, commander selection is critical:

- **Avoid \$20+ Commanders**: High commander prices force extreme budget cuts across the remaining 99 cards.
- **Avoid Signature-Card Traps**: Skip commanders that *require* specific \$20+ engine cards to function (e.g., Urza requiring expensive artifact shells).
- **Target High-Value / Self-Contained Commanders**:
  - *Splinter, Radical Rat* (~\$1.50) - Dimir Ninja/Rat Tribal & Evasion Engine.
  - *Krenko, Mob Boss* (~\$5) - Mono-Red Goblins (cheap tribal synergies).
  - *Marwyn, the Nurturer* (~\$3) - Mono-Green Elves (high ramp/mana engine on a budget).
  - *Ghave, Guru of Spores* (~\$2) - Abzan Counters/Sacrifice (enables cheap multi-card combos).
  - *Muldrotha, the Gravetide* (~\$5) - Sultai Graveyard (recurs budget permanents).
  - *Toski, Bearer of Secrets* (~\$4) - Mono-Green Creature Draw Engine.

---

## 4. Automated Dual-Source Retrieval for Budget Decks (EDHrec + Scryfall)

When building budget decks under `mtg-deck-builder-v9.md`, combine EDHrec budget endpoints with Scryfall price parameters:

### A. EDHrec Budget JSON Endpoint
- Query the dedicated budget JSON endpoint for the selected commander:
  `https://json.edhrec.com/pages/commanders/{commander-slug}/budget.json`
- *Example*: `https://json.edhrec.com/pages/commanders/splinter-radical-rat/budget.json`

### B. Scryfall Price Filters & Functional Budget Swaps
When querying Scryfall, apply explicit USD price caps combined with EDHrec order sorting:
- **Base Query Format**: `https://scryfall.com/search?q={QUERY}+usd<=2&order=edhrec`
- **Targeted Budget Swaps**:
  - Instead of *Craterhoof Behemoth* (\$25+) -> Search *Overwhelming Stampede* (\$2) or *End-Raze Forerunners* (\$0.50).
  - Instead of *Heroic Intervention* (\$10+) -> Search *Wrap in Vigor* (\$1) or *Unbreakable Formation* (\$1).
  - Instead of *Teferi's Protection* (\$30+) -> Search *Clever Concealment* (\$5) or *Flawless Maneuver* (\$5).
  - Instead of *Rhystic Study* (\$30+) -> Search *Bident of Thassa* (\$1) or *Mystic Remora* (\$4).

---

## 5. Exportable Plaintext Decklist Artifact

When finalizing a budget deck build, the agent MUST generate a clean, unformatted `.txt` file artifact in `/workspace/out/{commander-slug}-decklist.txt` following Section 4 of `mtg-deck-builder-v9.md`:
- Quantity-first syntax (`1 Card Name` or `12 Island`).
- Total card count equals **99 maindeck cards + 1 Commander = 100 total cards**.

---

## 6. The Iterative Upgrade Pathway (75% Power Scaling)

A \$100 starting deck allows players to achieve ~75% table competitiveness immediately while laying out a clear upgrade path over time:

1. **Phase 1 (\$50-\$100 Baseline)**: Build a lean, low-curve 8x8 framework using budget untapped lands and high-synergy low-cost spells.
2. **Phase 2 (Targeted Slot Upgrades)**: Play 10-20 games and replace underperforming budget cards in this sequence:
   - *Upgrade Step 1*: Tapped budget duals -> Shock lands, Pain lands, Bond lands.
   - *Upgrade Step 2*: High-cost conditional removal -> Universal cheap interaction (*Farewell*, *Cyclonic Rift*).
   - *Upgrade Step 3*: Budget card draw -> Sustained engine staples (*Rhystic Study*, *Trouble in Pairs*).