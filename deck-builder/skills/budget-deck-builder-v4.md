# SUB-SKILL: Budget Deck Building (Commander, Oathbreaker, Pauper EDH)

### Description
An agentic sub-skill instruction set for building functional, competitive, and scalable Magic: The Gathering (MTG) decks on a budget across **Commander (EDH)**, **Oathbreaker**, and **Pauper EDH (pEDH)** formats. It integrates directly with `mtg-deck-builder-v11.md`, `oathbreaker-deck-builder-v5.md`, and `pauper-edh-deck-builder-v2.md`, offering format-specific budget allocation rules, budget swap heuristics, Scryfall price filters, and EDHrec budget endpoint routing.

---

## 1. Multi-Format Budget Targets & Spending Priorities

Budget targets scale proportionally based on deck size and format constraints:

| Format | Standard Budget Target | Ultra-Budget Target | Key Focus Area |
| :--- | :--- | :--- | :--- |
| **Commander (EDH)** | **$50 - $100** | **$25 - $50** | Untapped budget duals, budget ramp, high-synergy engine cards. |
| **Oathbreaker** | **$30 - $60** | **$15 - $30** | Low-CMC 1-2 mana rocks, budget Signature Spells, Planeswalker protection. |
| **Pauper EDH (pEDH)** | **$25 - $50** | **$15 - $25** | Avoiding high-cost common staples, focusing on gates/bridges. |

### Budget Resource Allocation (Standard Baseline)
- **Mana Base (25 - 30%)**: Highest priority. Prioritize untapped budget duals, pain lands, gates, and rainbow lands over expensive shocks/fetches.
- **Ramp & Acceleration (15 - 20%)**: Low-cost 1-2 CMC accelerators ($0.25 - $2.00) that ensure reliable casting.
- **Commander / Strategy Synergies (25 - 30%)**: High-synergy budget engines that scale the leader's core abilities.
- **Card Draw & Removal (15 - 20%)**: High-value interaction and draw spells ($0.25 - $2.00) replacing $20+ staple slots.

---

## 2. Format-Specific Budget Guidelines

### A. Commander (EDH) Budget Baseline ($50-$100)
- **Mana Base**: *Command Tower*, *Exotic Orchard*, Pain Lands ($1-$2), Tainted Lands ($1-$2), Bounce Lands ($0.25). Skip $10-$40 Fetches/Shocks/Triomes.
- **Ramp**: 10-12 accelerators (*Sol Ring*, Signets, Talismans, *Fellwar Stone*, *Cultivate*, *Rampant Growth*).
- **Draw**: 8-10 draw engines (*Skullclamp*, *Bident of Thassa*, *Mind's Eye*, *Harmonize*). Skip $30+ staples like *Sylvan Library*.

### B. Oathbreaker Budget Baseline ($30-$60)
- **Mana Base**: 22 lands total. Untapped pain lands, *Interplanar Beacon*, *War Room*, *Karn's Bastion*, Command Tower.
- **Signature Spell Selection**: Select low-CMC (1-2 mana) budget instants/sorceries (*Enter the Enigma*, *Preordain*, *Lim-Dûl's Vault*, *Distortion Strike*) to minimize command zone recast tax.
- **Ramp**: 6 low-cost accelerators (1-2 CMC rocks/dorks).

### C. Pauper EDH (pEDH) Budget Baseline ($25-$50)
- **Format Constraint**: All 99 maindeck cards MUST be commons (`f:paupercommander r:common`).
- **High-Cost Common Swaps**: While pEDH is inherently budget-friendly, certain tournament common staples carry higher price tags ($5-$25). Apply budget swaps:
  - *High-Cost Common Acceleration* -> *Simian Spirit Guide* / *Elvish Spirit Guide* / *Wayfarer's Bauble* ($0.50-$1).
  - *High-Cost Common Removal* -> *Cast Down* ($0.25) / *Feed the Swarm* ($0.25) / *Counterspell* ($0.50).
  - *High-Cost Common Graveyard Interaction* -> *Tormod's Crypt* ($0.50) / *Nihil Spellbomb* ($0.50).
- **pEDH Land Priorities**: Gates (*Basilisk Gate*, *Citadel Gate*), Bridges (*Goldmire Bridge*), Thriving Lands, Gain Lands, Snow Duals.

---

## 3. Commander / Leader Selection Strategy

To maintain strict budget limits across any format, selection of the Commander / Oathbreaker / Uncommon Creature is critical:

- **Avoid $20+ Leaders**: High leader costs force severe cuts across the remaining maindeck slots.
- **Avoid Signature-Card Traps**: Skip commanders that *require* specific $20+ cards to function properly.
- **Target High-Value / Self-Contained Leaders**:
  - *Commander*: *Splinter, Radical Rat* (~$1.50), *Krenko, Mob Boss* (~$5), *Marwyn, the Nurturer* (~$2), *Toski, Bearer of Secrets* (~$4).
  - *Oathbreaker*: *Kaito, Bane of Nightmares* (~$3), *Chandra, Torch of Defiance* (~$3), *Vraska, Golgari Queen* (~$2.50).
  - *Pauper EDH*: *Gut, True Soul Zealot* (~$0.25), *Loyal Apprentice* (~$0.25), *Slimefoot, the Stowaway* (~$0.25), *Mayhem Devil* (~$0.50).

---

## 4. Automated Dual-Source Retrieval for Budget Decks (EDHrec + Scryfall)

When building budget decks under any main skill, combine EDHrec budget endpoints with Scryfall price filters:

### A. EDHrec Budget Endpoint Protocol
- **Legendary Leaders**: Fetch budget JSON payload from EDHrec commanders budget endpoint.
- **Non-Legendary / Planeswalker Leaders**: Fetch budget JSON payload from EDHrec cards budget endpoint.

### B. Scryfall Price Filters
When querying Scryfall for budget candidates, append explicit USD price filters (`usd<=2` or `usd<=1`):
- **Budget Search Parameter**: Add USD price caps to Scryfall search queries and sort by EDHrec rank.
- **Targeted Functional Budget Swaps**:
  - *High-Cost Finishers* ($25+) -> *Overwhelming Stampede* ($2) or *End-Raze Forerunners* ($0.50).
  - *High-Cost Protection* ($10+) -> *Wrap in Vigor* ($1) or *Unbreakable Formation* ($1).

---

## 5. Exportable Plaintext Decklist Artifact Standard

When finalizing a budget deck build, generate a clean, unformatted `.txt` file artifact following the card quantity requirements of the target format:
- **Commander & Pauper EDH**: 99 Maindeck Cards + 1 Commander = **100 Total Cards** (`/workspace/out/{commander-slug}-decklist.txt`).
- **Oathbreaker**: 58 Maindeck Cards + 1 Oathbreaker + 1 Signature Spell = **60 Total Cards** (`/workspace/out/{oathbreaker-slug}-oathbreaker-decklist.txt`).

---

## 6. Iterative Upgrade Pathway (75% Power Scaling)

A budget starting deck allows players to achieve ~75% table competitiveness immediately while establishing a modular upgrade pathway:

1. **Phase 1 (Budget Baseline)**: Build a lean, low-curve framework using budget untapped lands and high-synergy low-cost spells.
2. **Phase 2 (Targeted Slot Upgrades)**: Replace underperforming budget cards in this order:
   - *Step 1*: Tapped budget duals -> Shock lands, Pain lands, Bond lands.
   - *Step 2*: High-cost conditional removal -> Universal cheap interaction.
   - *Step 3*: Budget card draw -> Sustained engine staples.
