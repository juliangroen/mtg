---
name: mtg-commander-deck-builder
description: Build, audit, and upgrade Magic: The Gathering Commander (EDH) decks using an 8x8 categorization framework, mana-source ratios, color-scaled mana bases, curve optimization, and archetype-specific ratio bends. Use when the user wants to build a new Commander deck, audit or upgrade an existing EDH decklist, evaluate mana bases, or apply archetype strategy. For archetype-specific tuning, also consult the matching mtg-archetype-* skill.
---

# SKILL: MTG Commander Deck Builder & Upgrader

### Description
An agentic AI instruction set for building, auditing, and upgrading Magic: The Gathering (MTG) Commander (EDH) decks. It uses systematic 8x8 categorization, core infrastructure ratios, color-scaled mana base construction, mana curve optimization, and archetype-specific adjustments.

> **Archetype sub-skills**: When a deck has a clear archetype, pull the matching companion skill for ratio overrides, recommended 8x8 categories, and strategic traps. Available: `mtg-archetype-aggro`, `-control`, `-combo`, `-midrange`, `-voltron`, `-tribal`, `-spellslinger`, `-aristocrats`, `-tokens`, `-blink`, `-enchantress`, `-wheels`, `-reanimator`, `-stax`, `-pillowfort`, `-group-hug`, `-storm`, `-mill`, `-landfall`, `-chaos`, `-superfriends`.

---

## 1. Core Frameworks & Rules

### A. The 8x8 Categorization Framework
* **Core Math**: A standard Commander deck consists of **1 Commander + 35 Lands + 64 Spells** organized into 8 distinct categories of 8 cards each [1].
* **The Core Four (Essential Infrastructure - 32 Cards)**:
  1. **Ramp (8 cards)**: Mana acceleration (rocks, dorks, land ramp, signets) [6].
  2. **Card Draw (8 cards)**: Sustained draw engines and burst refills [6].
  3. **Removal (8 cards)**: Spot removal and board wipes [6].
  4. **Commander Synergy (8 cards)**: Cards directly supporting the commander's core ability [6].
* **Strategy-Specific Categories (32 Cards)**: Select 4 custom categories of 8 cards tailored to the deck's archetype (e.g., Win Conditions/Finishers, Protection, Recursion, Tokens, Tribal Synergy, Tutors, Evasion, or Enablers) [6-8].
* **Categorization Grid Variants**: Shift to 7x9 (9 categories of 7 cards), 9x7 (7 categories of 9 cards), or asymmetrical splits (e.g., 10-8-8-6-6-6-6-6-8) as dictated by deck goals [9].

### B. Baseline Ratios & Infrastructure Requirements
* **Total Mana Sources**: Lands plus Ramp MUST equal **47–50 total mana sources** [10, 11].
  * *Standard baseline*: **37 Lands + 10 Ramp** = 47 mana sources [2, 10, 11].
  * *Heavy ramp package*: **35 Lands + 12+ Ramp** [3, 10, 11].
  * *High-curve / 6+ CMC commander*: **38–39 Lands + 10 Ramp** [3, 11].
* **Infrastructure Floor Metrics**:
  * **Card Draw Floor**: Minimum **8 cards** [2, 12]. Decks with fewer than 8 run out of gas by turn 6 [12].
  * **Ramp Floor**: Minimum **10 cards** [2, 13].
  * **Targeted Removal**: **8–12 cards** (instant-speed preferred) [2].
  * **Board Wipes**: **3–4 cards** (minimum 2) [2].
  * **Win Conditions**: **7–10 dedicated slots** [2, 12]. The deck must include at least 5 distinct cards or clear lethal paths that close out games [12].
  * **Protection**: **2–4 cards** (boots, counterspells, indestructible effects) [2].
  * **Recursion**: **2–4 cards** [2].
  * **Flex / Synergy**: **~10–20 slots** [2].
* **Multi-Role Cards**: Multi-purpose spells (e.g., *Beast Within*, *Ravenous Chupacabra*, *Skullclamp*) should be assigned to whichever core category is currently weakest in the deck structure [10, 14, 15].

### C. Mana Base & Color Scaling Rules
* **Color Count Scaling**:
  * **Mono-Color**: 28–32 Basics + 5–8 colorless Utility Lands (e.g., *Rogue's Passage*, *War Room*) [11].
  * **Two-Color**: Basics + dual lands, with ~4 utility lands [11, 16].
  * **Three-Color**: 37–38 Lands total, heavy dual/tri-land fixing, 8–12 basics, max 2–3 utility lands [16, 17].
  * **Four / Five-Color**: Almost all lands must produce multiple colors; 2–3 basics per color max (for fetch targets); 0–1 colorless utility lands [16].
* **Land Tiers & Quality Priorities**:
  * *Tier 1*: Original Duals, Fetch Lands [18].
  * *Tier 2*: Shock Lands, Bond Lands (top tier in multiplayer) [18].
  * *Tier 3*: Pain Lands (cheap, always untapped), Check Lands, Slow Lands [18-20].
  * *Tier 4*: Filter Lands, Triomes [19].
  * *Tier 5*: Tap Lands (budget fallback) [19].
  * *Budget Mana Base Rule*: Prioritize untapped pain lands, Command Tower, Exotic Orchard, and Evolving Wilds / Terramorphic Expanse over always-tapped lands [20].

### D. Mana Curve & Casting Cost Calibration
* **Average Mana Value Target**: Aim for **2.8 to 3.5** across non-land spells [4].
  * *Avg CMC < 2.8*: Hyper-aggressive or combo decks [4].
  * *Avg CMC > 3.5*: High-curve decks requiring extra land/ramp support [4].
* **Curve Distribution Rules**:
  * At least **50% of non-land spells MUST cost 3 or less** [21].
  * The bulk of utility and infrastructure spells must sit at **2–4 mana** [21].
  * Spells costing 5+ must provide high multi-opponent impact [21, 22].
* **Commander CMC Adjustments**:
  * *Cheap Commander (1–3 CMC)*: Enables a low, lean curve [23].
  * *Mid-Range Commander (4–5 CMC)*: Uses the standard curve profile [23].
  * *Expensive Commander (6+ CMC)*: Requires a **bimodal curve**—a heavy concentration of 1–3 CMC ramp/interaction and a smaller set of high-impact endgame plays [23].
* **Practical Mana Costs**: Evaluate cards by true casting cost rather than printed cost (e.g., *Blasphemous Act* as 1–2 CMC, *Treasure Cruise* as 1–2 CMC, Convoke/Delve) [24].

### E. Strategic Archetype Ratio Bends
Adjust standard baseline numbers based on the deck's primary archetype [5]:

| Archetype | Creature Count | Removal | Wipes | Card Draw | Lands | Ramp | Key Archetype Slots |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **Baseline** | ~20–25 | 8–12 | 3–4 | 8–10 | 35–38 | 10–12 | ~10–20 Synergy |
| **Aggro** | 26–32 | 5–6 | 1–2 | 8–10 | 34–36 | 10–12 | Threat density over answers [5] |
| **Control** | 10–15 | 12–15 | 5–7 | 10–12 | 37–39 | 10–12 | Answer density & land drops [25] |
| **Combo** | Low/Var | 6–8 | 1–3 | 10–12 | 35–37 | 10–12 | 4–8 Tutors, 4–6 Protection, 6–10 Combo [25] |
| **Voltron** | Low | 6–8 | 1–2 | 8–10 | 35–37 | 10–12 | 12–16 Equip/Auras, 6–8 Protection, 4–6 Evasion [26] |
| **Tribal** | 25–35 | 6–8 | 2–3 | 8–10 | 35–37 | 10–12 | 5–8 Lords / Type Anthems [26] |
| **Spellslinger** | 6–10 | 8–12 | 2–4 | 10–12 | 35–37 | 10–12 | 35–45 Instants/Sorceries, 4–6 Cost Reducers [27] |
| **Aristocrats** | Engine | 6–8 | 2–3 | 6–8 | 35–37 | 10–12 | 5–8 Outlets, 6–10 Death Payoffs, 8–12 Recur/Tokens [27, 28] |

---

## 2. Agentic Workflow Instructions

### Workflow A: Building a New Deck from Scratch
1. **Define Context**: Identify the Commander, its printed/practical CMC, color count, and strategy archetype [5, 23].
2. **Establish Mana Foundation**:
   * Calculate Lands (35–38) + Ramp (10–12) to hit **47–50 total mana sources** [3, 10, 11].
   * Select utility land allowance based on color count (Mono: 5–8, 2-Color: ~4, 3+ Color: 0–3) [11, 16, 17].
3. **Build the 8x8 Non-Land Matrix**:
   * Allocate the Core 4 categories: Ramp (8), Draw (8), Removal (8), Commander Synergy (8) [6].
   * Define 4 custom archetype categories (8 cards each) tailored to the commander [6-8].
4. **Curve & Win Condition Audit**:
   * Verify Average Mana Value is between **2.8 and 3.5** [4].
   * Confirm at least **50% of non-land spells cost <= 3 mana** [21].
   * Ensure at least **5 clear win condition cards/combos** exist [12].

### Workflow B: Auditing & Upgrading an Existing Decklist
1. **Ratio & Infrastructure Audit**:
   * Check total mana sources (Is Lands + Ramp >= 47?) [10, 11].
   * Check Card Draw (Is Draw >= 8?) [2, 12].
   * Check Removal & Wipes (Is Removal >= 8, Wipes >= 2?) [2].
   * Check Win Conditions (Are there >= 5 clear win paths?) [12].
2. **Identify Cut Candidates**:
   * Spells costing **5+ CMC that only affect a single target or opponent** [22].
   * Redundant **4+ CMC spells** that duplicate cheaper effects [22].
   * **"Win-more" cards** that perform poorly when behind on board [22].
   * Excessive synergy cards displacing core infrastructure [13].
3. **Execute Upgrade Recommendations**:
   * Swap single-purpose cards for **multi-role spells** [10, 14, 15].
   * Upgrade mana base with untapped fixing lands [18-20].
   * Replace high-cost cards to drag the average CMC toward the **2.8–3.5 target** [4].

---

## 3. Output Format Standard
When presenting deck builds or upgrades to the user, format responses into four distinct sections:
1. **Deck Architecture Summary**: Commander, Archetype, Lands/Ramp total, and Average CMC [4, 5, 10].
2. **Categorized Card List (8x8 Grid)**: Grouped by category with multi-role annotations [1, 6, 10].
3. **Mana Base Breakdown**: Color distribution, untapped duals, and utility lands [11, 17, 18].
4. **Ratio & Curve Audit Table**: Showing current stats vs. baseline targets (Draw, Ramp, Removal, <=3 CMC %, Win Cons) [2, 4, 12, 21].
