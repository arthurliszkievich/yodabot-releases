# 📖 Yoda Bot v2.0 — Complete Command Reference Manual
### The Definitive CLI & Web GUI Operating Manual for Dokkan Battle Automation

---

## 🧭 The Golden Rule of Navigation: Double Enter (`2x Enter`)

In any interactive prompt, farming loop, or configuration submenu:
- **Press Enter once**: Yoda Bot displays:
  ```text
  [Press Enter again to clear screen & return to menu]
  ```
- **Press Enter again**: The bot immediately clears the terminal screen (`cls` on Windows, `clear` on Linux/Android) and returns to the main interactive menu cleanly without crashing or corrupting your state.

---

## ⚡ Command Syntax & Formatting Rules

- **100% Case-Insensitive**: You can type `INFO`, `info`, `Info`, `OMEGA_FARM`, or `omega_farm`.
- **Standardized `snake_case`**: Multi-word commands use clean underscores (e.g., `omega_farm`, `db_story_all`, `smart_team`, `deck_change`).
- **Flexible Multi-Argument Parsing**: Commands accepting IDs (such as `kagi`) support single or multiple arguments separated by **spaces**, **commas**, or both:
  ```bash
  kagi 101001 101002 101003
  kagi 101001, 101002, 101003
  ```

---

## 👤 1. Account & Session Management

| Command | Arguments | Access Tier | Description |
| :--- | :--- | :---: | :--- |
| **`info`** | *none* | Free / Standard | Displays a comprehensive status card of the active account: User ID, Rank, Dragon Stones, Zeni, Current/Max Stamina, Card Box capacity, and Active Deck team composition. |
| **`help`** | `[command]` | Free / Standard | Displays the interactive help catalog with grouped categories and parameter descriptions. |
| **`new`** | *interactive* | Free / Standard | Guided wizard to initialize a brand-new Dokkan Battle account, automatically completing the intro tutorial and prologue. |
| **`load`** | `<account_name>` | Free / Standard | Switches the active session to a saved profile from the `saves/` folder. Supports tab completion. |
| **`transfer`** | *interactive* | Free / Standard | Transfers an existing account into Yoda Bot via Transfer Code or Google Auto-Login (CDP). |
| **`gui`** | *none* | APEX Exclusive | Spawns the background server and launches the interactive visual Web GUI in your browser (`http://127.0.0.1:8080`). |
| **`exit`** / **`quit`** | *none* | Free / Standard | Gracefully terminates active background workers and exits Yoda Bot. |

---

## 🌾 2. Farming & Quest Automation

| Command | Arguments | Access Tier | Description |
| :--- | :--- | :---: | :--- |
| **`omega_farm`** | *interactive* | Standard / VIP | The master end-to-end farming engine. Runs Quest Mode (Areas 1–35+), Dragon Ball Stories, Story Events, and Dokkan Events with automatic team replenishment and stamina management. |
| **`db_story_all`** | *none* | VIP Tier | Scans and clears every incomplete Dragon Ball Story event and sub-difficulty in one go, claiming hundreds of first-clear Dragon Stones. |
| **`kagi`** | `<stage_id(s)>` | Free / Standard | **Portal of Memories** automated farmer. Uses Story, Challenge, or Z-Battle Keys to farm stages that are currently closed in regular rotation. |
| **`eza_run`** | `<stage_id>` `[target_lv]` | Free / Standard | Auto-climbs Extreme Z-Battle stages sequentially from Level 1 up to Level 30 (or custom target) for Dragon Stones, Grand Kais, and Awakening Medals. |
| **`stage`** | `<stage_id> [times] [diff]` | Free / Standard | Farms a specific stage for `[times]` repetitions (default: 1) with optional difficulty. Example: `stage 575001 5` to run 5 times, displaying progress `Run X/N`. |

### 🗝️ Portal of Memories (`kagi`) Quick Guide

| Key Type | Color Indicator | Typical Stages & Rewards |
| :--- | :---: | :--- |
| **Story Keys** | 🟢 Green | Dragon Ball Story, Prime Battle preparatory drops, farmable SSR cards & support memories. |
| **Challenge Keys** | 🔵 Blue | Dokkan Awakening Medals for retired festival and carnival units. |
| **Z-Battle Keys** | 🟣 Purple | Extreme Z-Awakening (EZA) stages for legacy UR & LR units. |

> **Pro-Tip**: You can queue multiple stages in a single line:
> ```bash
> YODA $ kagi 102001, 102002 102003
> ```

---

## 🏆 3. Mission Automation

| Command | Arguments | Access Tier | Description |
| :--- | :--- | :---: | :--- |
| **`mission`** | *none* | Free / Standard | Interactive categorical mission browser. Lets you inspect and claim rewards by category: Daily, Event, Campaign, Special, King Kai, and Supreme Kai missions. |
| **`auto_mission`** | *none* | VIP Tier | **1-Click Batch Claim**. Automatically checks all completed missions across every category, claims all pending rewards, and prints a consolidated summary of Dragon Stones, Orbs, and Tickets acquired. |

---

## ⚔️ 4. Teams, Deck & Box Management

| Command | Arguments | Access Tier | Description |
| :--- | :--- | :---: | :--- |
| **`smart_team`** | `[category/type]` | Free / Standard | **Algorithmic Team Builder**. Analyzes your available card box against target stage requirements and builds an optimized team with matching Leader Skill, optimal link synergies, and element advantage. Renders an ASCII team preview. |
| **`deck_change`** | `<1-8>` | Free / Standard | Switches your currently active in-game deck slot (1 through 8) instantly. |
| **`clash`** | *interactive* | Standard / VIP | **Ultimate Clash / Battlefield Automation**. Displays live status banner (`🟢 ACTIVE` or `🔴 INACTIVE`), parses available enemies, and deploys mono-type or high-synergy category teams to defeat all bosses. |
| **`clean_box`** | `<zeni/baba>` | Free / Standard | **Bulk Box Cleaner**. Analyzes duplicate cards in your box. If a unit's 4 Hidden Potential paths are already unlocked (or if the unit is an unneeded SR/R), safely converts surplus dupes into Zeni or Baba Points. Locked units are strictly protected. |

---

## 🌟 5. Interactive APEX Web GUI (`gui`) Summary

Launching `gui` starts the local web dashboard at **`http://127.0.0.1:8080`**. It provides a modern visual alternative to CLI management:

```text
YODA $ gui
[Web GUI] Server running on http://127.0.0.1:8080 (GUI active in background — CLI ready for commands).
```

### Key Visual Features:
1. **Default Sorting & Instant Filters**:
   - Automatically sorts units by **Release (Newest)** to immediately surface your latest summons.
   - Quick filters: **`LR`**, **`UR`**, **`⚡ EZA`**, **`⚡ SEZA`**, and **`Extra Dupes`**.
2. **`⚡ Train` (1-Click Max Level & SA 10)**:
   - Instantly trains any unit to max level and feeds matching Kais/dupes for Super Attack 10 (or 20/25).
3. **`🔮 100% Potential [APEX]` (1-Click Rainbow)**:
   - Unlocks all 4 paths (Top-Left, Top-Right, Bottom-Left, Bottom-Right) and fills 100% of all potential nodes with optimal Crit/Additional/Dodge allocations.
4. **`🔥 Dokkan Awaken` (Step-by-Step 1-Click Awakening)**:
   - Calculates missing medals, farms the respective Dokkan Events automatically, and awakens the unit up to its final LR state.
   - **Interactive Stamina Refill Modal**: If stamina runs out during farming, a responsive modal appears in your browser asking if you want to spend 1 Dragon Stone to refill Stamina. Once confirmed, farming resumes smoothly without restarting.
5. **`⚡ EZA Lv 140 / SEZA`**:
   - Completes all 30/10 stages of the corresponding Extreme Z-Battle to max out the unit's awakened passive.
6. **`🗑️ Delete Dupes`**:
   - Safely cleans duplicate cards for Zeni or Baba Points with a single touch.

