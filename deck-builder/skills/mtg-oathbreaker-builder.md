# SKILL: MTG Oathbreaker Deck Builder & Upgrader

### Description
An agentic AI instruction set for building, auditing, and upgrading Magic: The Gathering (MTG) **Oathbreaker** decks. Oathbreaker is a 60-card singleton multiplayer format built around a Planeswalker (the "Oathbreaker") and a paired instant/sorcery (the "Signature Spell"), both of which live in the command zone. This skill rescales the Commander 8x8 methodology to Oathbreaker's smaller 58-card maindeck, applies command-zone-aware tax math, and calibrates ratios and curve for a 20-life, 3–5 player free-for-all.

---

## 0. Format Rules (Authoritative — do not violate)

* **Deck Composition**: Exactly **60 total cards**:
  * **1 Oathbreaker** — a Planeswalker card (in command zone).
  * **1 Signature Spell** — an instant OR sorcery card (in command zone).
  * **58 maindeck cards**.
* **Singleton**: Only one copy of any card except basic lands.
* **Color Identity**: Defined by the mana symbols in the Oathbreaker's cost AND rules text. Every card in the deck (including the Signature Spell) may only use mana symbols present on the Oathbreaker. Colorless cards are always allowed. The Signature Spell must match this identity.
* **Life & Players**: Start at **20 life**; typically **3–5 player free-for-all**. There is **no commander damage**.
* **Command Zone Mechanics**:
  * **Oathbreaker Tax**: Cast from command zone for its normal cost **+2 mana for each previous time** it was cast from the command zone this game. If it would leave the battlefield to library/hand/graveyard/exile, you may return it to the command zone instead.
  * **Signature Spell Access**: You may cast your Signature Spell **only while your Oathbreaker is on the battlefield under your control**.
  * **Signature Spell Tax**: Cast from command zone for its normal cost **+2 mana for each previous time** it was cast from the command zone this game. On resolution (or anywhere it would otherwise go), it returns to the command zone instead of the graveyard.
* **Banned List**: Oathbreaker maintains its own banned list (oathbreakermtg.org/banned-list). When legality matters, flag that the user should verify against the current banned list rather than assuming.

---

## 1. Core Frameworks & Rules

### A. The Rescaled Categorization Framework (6x6 Core)
Oathbreaker's 58-card maindeck is ~59% the size of Commander's 99. The 8x8 grid does not fit; use a **6-category baseline** instead.

* **Core Math**: `58 maindeck = 24 Lands + 34 Spells` (baseline). Organize spells into **6 categories of ~5–6 cards**, scaling with archetype.
* **The Core Four (Essential Infrastructure — ~20 cards)**:
  1. **Ramp (5–6 cards)**: Mana acceleration (rocks, dorks, signets, Talismans). Low rocks matter more because they also help pay command-zone tax.
  2. **Card Draw (5–6 cards)**: Sustained engines and burst refills.
  3. **Removal (5–7 cards)**: Spot removal (instant-speed preferred) + 1–2 board wipes.
  4. **Oathbreaker/Signature Synergy (6–8 cards)**: Cards that directly protect, enable, or amplify the Oathbreaker and recur/discount the Signature Spell.
* **Strategy-Specific Categories (~12–16 cards)**: 2–3 custom categories tailored to the archetype (Win Conditions, Protection, Proliferate, Evasion, Enablers, Tutors).
* **Grid Variants**: Treat the layout as flexible — a common split is `6-6-6-6-5-5` or a lean `5-5-5-5-5-5` with more land/ramp. Do not force rigid 8-card bins.

### B. Baseline Ratios & Infrastructure Requirements
Scaled down from Commander. The command zone guarantees access to the Oathbreaker + Signature Spell, so dedicated "finisher" slots can be fewer — but tax escalation punishes over-reliance on recasting.

* **Total Mana Sources**: Lands plus Ramp should equal **~28–32 total mana sources** (vs 47–50 in Commander).
  * *Standard baseline*: **24 Lands + 6 Ramp** = 30 mana sources.
  * *Low-curve / aggressive*: **22–23 Lands + 5–6 Ramp**.
  * *High-curve / 5+ CMC Oathbreaker or recast-heavy*: **25–26 Lands + 7–8 Ramp**.
* **Infrastructure Floor Metrics (58-card scale)**:
  * **Card Draw Floor**: Minimum **5 cards** (6+ preferred). Smaller decks dig faster but still flood/stall without draw.
  * **Ramp Floor**: Minimum **5 cards**. Prioritize 1–2 CMC rocks so they double as tax payment.
  * **Targeted Removal**: **5–7 cards** (instant-speed preferred).
  * **Board Wipes**: **1–2 cards** (lower than Commander — your Oathbreaker is a loyalty asset vulnerable to your own wipes; prefer asymmetric or planeswalker-sparing wipes).
  * **Win Conditions**: **3–5 dedicated slots or clear lethal lines**. The Oathbreaker + Signature Spell often ARE a win condition engine, reducing dedicated finisher count.
  * **Protection**: **3–5 cards** (critical — losing the Oathbreaker to removal taxes every recast by +2 and resets ultimates).
  * **Flex / Synergy**: **~8–14 slots**.
* **Multi-Role Cards**: Assign multi-purpose spells (e.g., *Beast Within*, *Abrade*, *Mystic Confluence*) to whichever core category is currently weakest. In the tighter 58-card build, multi-role density matters MORE than in Commander.

### C. Mana Base & Color Scaling Rules
Land counts are lower (22–26 vs 35–38) and color identity is dictated by the Oathbreaker. Because the Signature Spell and Oathbreaker demand on-color mana early, **fixing speed and untapped sources are prioritized over raw count**.

* **Color Count Scaling**:
  * **Mono-Color**: 23–25 lands = ~18–21 basics + 4–6 colorless utility lands (*Rogue's Passage*, *War Room*, *Castle* lands).
  * **Two-Color**: 23–25 lands, dual lands + ~3 utility lands; keep enough basics for fetch/retrieval.
  * **Three-Color**: 24–26 lands, heavy dual/tri fixing, 4–6 basics, max 2 utility lands.
  * **Four / Five-Color** (rare — requires a WUBRG-ish planeswalker): nearly all lands produce multiple colors; 1 basic per color max; 0–1 colorless utility lands.
* **Land Tiers & Quality Priorities** (same tier logic as Commander, but untapped matters more at 20 life in faster games):
  * *Tier 1*: Original Duals, Fetch Lands.
  * *Tier 2*: Shock Lands, Horizon/Canopy Lands.
  * *Tier 3*: Pain Lands, Check Lands, Fast Lands (great in a low land count), Slow Lands.
  * *Tier 4*: Filter Lands, Triomes, Pathways.
  * *Tier 5*: Tap Lands (budget fallback — minimize; tempo loss is harsher in 60-card multiplayer).
  * *Budget Rule*: Prioritize untapped pain/fast lands, Command Tower, Exotic Orchard, and dual-producing utility over always-tapped lands.

### D. Mana Curve & Casting Cost Calibration
Oathbreaker games skew faster and lower than Commander because the deck is smaller and the command zone provides a reliable engine.

* **Average Mana Value Target**: Aim for **2.3 to 3.0** across non-land spells (lower than Commander's 2.8–3.5).
  * *Avg CMC < 2.3*: Hyper-aggressive, spellslinger, or combo decks.
  * *Avg CMC > 3.0*: High-curve decks needing extra land/ramp support and a bimodal shape.
* **Curve Distribution Rules**:
  * At least **55–60% of non-land spells MUST cost 3 or less** (tighter than Commander because the deck draws through itself faster and must pay escalating command-zone tax).
  * The bulk of infrastructure sits at **1–3 mana**.
  * Reserve open mana to recast the Signature Spell each turn — budget the curve so you can both develop AND pay the Signature Spell tax (+2 per prior cast).
* **Oathbreaker CMC Adjustments**:
  * *Cheap Oathbreaker (2–3 CMC)*: Enables a low, lean, aggressive curve; you redeploy it cheaply after wipes.
  * *Mid Oathbreaker (4–5 CMC)*: Standard curve; prioritize protection so you avoid repeated +2 recast taxes.
  * *Expensive Oathbreaker (6+ CMC)*: Requires a **bimodal curve** — dense 1–3 CMC ramp/protection to land it once and keep it alive, since each recast is brutally taxed.
* **Signature Spell Tax Planning**: Treat the Signature Spell's effective cost as `printed + 2 × (times already cast)`. A spell you intend to cast every turn (e.g., a cheap burn/draw/bounce spell) is far better than an expensive one-shot, because the tax compounds. Favor Signature Spells at **1–3 CMC** with repeatable value.
* **Practical Mana Costs**: Evaluate by true casting cost (Convoke, Delve, cost reduction), e.g., *Treasure Cruise* as 1–2 CMC.

### E. Strategic Archetype Ratio Bends (Oathbreaker scale, 58-card maindeck)
Adjust the baseline based on the deck's primary archetype. Counts are maindeck cards (Oathbreaker + Signature Spell excluded).

| Archetype | Creatures | Removal | Wipes | Card Draw | Lands | Ramp | Key Archetype Slots |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **Baseline** | ~12–16 | 5–7 | 1–2 | 5–6 | 23–25 | 5–7 | ~8–14 Synergy |
| **Aggro** | 18–22 | 3–4 | 0–1 | 4–5 | 21–23 | 5–6 | Threat density; low curve |
| **Control** | 6–10 | 8–10 | 3–4 | 6–8 | 25–26 | 6–7 | Answers + card advantage |
| **Combo** | Low/Var | 4–5 | 0–2 | 6–8 | 23–25 | 6–7 | 2–4 Tutors, 3–4 Protection, 3–5 Combo pieces |
| **Voltron** | Low | 4–5 | 0–1 | 5–6 | 22–24 | 5–7 | 8–10 Equip/Auras, 4–5 Protection, 3–4 Evasion |
| **Spellslinger** | 4–6 | 6–8 | 1–2 | 6–8 | 23–25 | 5–7 | 18–24 Instants/Sorceries, 2–4 Cost Reducers |
| **Superfriends** | 3–6 | 4–6 | 3–5 (asym.) | 5–6 | 24–26 | 6–7 | 6–10 extra Planeswalkers, 3–5 Proliferate |
| **Tokens/Aristocrats** | Engine | 4–6 | 1–2 | 5–6 | 23–25 | 5–7 | 4–6 Payoffs, 6–8 Token/Recur |

---

## 2. Agentic Workflow Instructions

### Workflow A: Building a New Deck from Scratch
1. **Define Context**:
   * Identify the **Oathbreaker (planeswalker)**: its CMC, color identity (cost + rules text symbols), and loyalty abilities.
   * Choose a **Signature Spell** (instant/sorcery) within that color identity. Prefer **1–3 CMC repeatable value** given tax escalation. Confirm it synergizes with the Oathbreaker.
   * Determine the strategy archetype.
2. **Establish Mana Foundation**:
   * Calculate Lands (22–26) + Ramp (5–7) to hit **~28–32 total mana sources**.
   * Weight ramp toward 1–2 CMC rocks so they also pay command-zone tax.
   * Select utility land allowance by color count (Mono: 4–6, 2-Color: ~3, 3+ Color: 0–2).
3. **Build the Non-Land Matrix (~34 spells)**:
   * Allocate Core Four: Ramp, Draw, Removal, Oathbreaker/Signature Synergy.
   * Define 2–3 custom archetype categories.
   * Ensure a **Protection package (3–5 cards)** to keep the Oathbreaker alive and avoid recast tax.
4. **Curve & Win Condition Audit**:
   * Verify Average Mana Value is **2.3–3.0**.
   * Confirm **≥55% of non-land spells cost ≤3 mana**.
   * Confirm the deck has **≥3 clear win lines**, counting the Oathbreaker/Signature engine where applicable.
   * Validate every card is **on-color** per the Oathbreaker's identity and the deck is **singleton**.

### Workflow B: Auditing & Upgrading an Existing Decklist
1. **Legality Audit (do this first)**:
   * Exactly 60 cards: 1 planeswalker Oathbreaker + 1 instant/sorcery Signature Spell + 58 maindeck.
   * Singleton (basics exempt). Flag duplicates.
   * Every card on-color vs the Oathbreaker's identity; flag off-color symbols.
   * Flag any cards the user should check against the current banned list.
2. **Ratio & Infrastructure Audit**:
   * Mana sources: is Lands + Ramp ≥ 28?
   * Card Draw ≥ 5? Removal ≥ 5? Wipes 1–2 (asymmetric preferred)?
   * Protection ≥ 3 to defend the Oathbreaker?
   * ≥3 clear win lines?
3. **Identify Cut Candidates**:
   * 5+ CMC spells that only affect a single target/opponent.
   * Redundant 4+ CMC spells duplicating cheaper effects.
   * Symmetric board wipes that kill your own Oathbreaker's board/loyalty support with no upside.
   * A high-CMC Signature Spell whose tax makes repeat casting impractical — recommend a cheaper repeatable alternative.
   * "Win-more" cards that are dead when behind.
4. **Execute Upgrade Recommendations**:
   * Swap single-purpose cards for multi-role spells (density matters more at 58 cards).
   * Lower the curve toward the 2.3–3.0 target; add 1–2 CMC rocks for tax payment.
   * Add protection (hexproof grants, counters, flicker, phase-out) for the Oathbreaker.
   * Upgrade to untapped fixing lands.

---

## 3. Output Format Standard
When presenting deck builds or upgrades, format responses into these sections:
1. **Deck Architecture Summary**: Oathbreaker (+CMC/colors), Signature Spell (+CMC, effective taxed cost), Archetype, Lands/Ramp total, Average CMC.
2. **Command Zone Plan**: How the Oathbreaker and Signature Spell interact, the intended recast cadence, and tax budgeting.
3. **Categorized Card List (6-Category Grid)**: Grouped by category with multi-role annotations; 58 maindeck cards.
4. **Mana Base Breakdown**: Color distribution, untapped duals, utility lands (22–26 total).
5. **Ratio & Curve Audit Table**: Current stats vs Oathbreaker baseline targets (Draw, Ramp, Removal, Protection, ≤3 CMC %, win lines) plus legality checks (60 cards, singleton, on-color).
