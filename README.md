# 🏰 KingdomsReborn — Plugin Documentation

> **Version:** 0.1.1-Beta · **Server:** PaperMC 1.21.11 · **Language:** English (default)

KingdomsReborn is a territory-based kingdoms plugin. Players form kingdoms, claim chunks, manage a shared bank, fight wars and earn influence.

---

## 📋 Table of Contents

- [Installation](#installation)
- [Commands](#commands)
- [GUIs](#guis)
- [Economy & Bank](#economy--bank)
- [Territory & Claims](#territory--claims)
- [Wars](#wars)
- [Shop & Prices](#shop--prices)
- [Territory Border](#territory-border)
- [Configuration](#configuration)
- [Language](#language)

---

## Installation

1. Drop `KingdomsReborn-v0.1.1-Beta-1.21.11.jar` into your `plugins/` folder.
2. Start the server — the plugin generates `config.yml` and language files automatically.
3. (Optional) Install **LuckPerms** and **PlaceholderAPI** for full prefix/placeholder support.

**Required:** PaperMC 1.21.11+, Java 17+

---

## Commands

### `/kingdom` (aliases: `/k`, `/kd`)

| Sub-command | Description | Permission |
|---|---|---|
| `create` | Open the kingdom creation GUI | `kingdomsreborn.kingdom` |
| `invite <player>` | Invite a player to your kingdom | Member+ |
| `accept` | Accept a pending invite | — |
| `leave` | Leave your kingdom | Member |
| `info [name]` | Show kingdom info | `kingdomsreborn.kingdom` |
| `list` | Browse all kingdoms | `kingdomsreborn.kingdom` |
| `claim` | Open the territory map | Member |
| `bank` | Open bank GUI (at barrel block) | Member |
| `transfer` | Transfer gold to another kingdom | Admin+ |
| `debt` | View outstanding debts | Member |
| `rename` | Rename your kingdom | Admin+ |
| `admin` | Admin sub-commands | `kingdomsreborn.admin` |

### `/war` (alias: `/w`)

| Sub-command | Description |
|---|---|
| `declare <kingdom>` | Declare war on another kingdom (Owner only) |
| `status` | Show active wars |

---

## GUIs

### Main Menu — `/k`

Opened via `/k`. Shows kingdom stats and navigates to all sub-GUIs.

| Slot | Button | Description |
|---|---|---|
| 10 | 🏰 Kingdom Info | Name, owner, role, influence, chunks, founded |
| 12 | 👥 Members | Manage members |
| 14 | 💰 Bank | Balance overview (open at the barrel block) |
| 16 | 🛒 Shop | Buy colors, extensions, member slots |
| 28 | 🗺 Claim Map | Territory map |
| 30 | 💸 Transfer | Transfer gold to another kingdom |
| 32 | 📋 Debts | View war debts |
| 34 | ✦ Territory Border | Toggle particle border around claimed chunks |
| 38 | ⚙ Settings | Rename, dissolve (Admin+) |
| 41 | 👋 Leave / 💥 Dissolve | Leave or dissolve kingdom |

### Territory Map

9×5 chunk grid centered on the player. Click chunks to select, then press **Claim** to start navigation. Color codes:

| Color | Meaning |
|---|---|
| 🟡 Yellow pane | Your current position |
| 🟢 Lime pane | Selected for claiming |
| 🔵 Blue pane | Your kingdom's chunk |
| 🔴 Red pane | Enemy kingdom chunk |
| Wool color | Unclaimed (biome color) |

### Bank GUI

Opened by right-clicking your registered barrel block.

- **Deposit** — takes Gold Ingots from your inventory, adds to bank balance.
- **Withdraw** — removes balance, gives Gold Ingots back. Requires Admin role.
- **Storage Upgrades** — increase max balance (up to level 80).
- **Extensions** — apply purchased bank extensions to unlock bonuses.

### Shop

| Category | What you buy |
|---|---|
| 🎨 Colors | Kingdom name color (Admin+) |
| 🏦 Extensions | Bank bonuses — Income Boost, Storage Boost, Fast Deposit, Interest, Tax Shield (Admin+) |
| 👥 Member Slots | +10 member slots per purchase (Admin+) |

---

## Economy & Bank

- **Currency:** Gold Ingots (configurable in `config.yml`)
- **Passive income:** each online member generates income per minute
- **Income Boost extension:** +20% to passive income
- **Interest extension:** +5% daily interest on balance
- **Max balance:** starts at 10,000 Gold, increased by storage upgrades and Storage Boost extension

### Bank Extensions

| Extension | Cost | Effect |
|---|---|---|
| 💰 Income Boost | 500 | +20% passive income |
| 🧱 Storage Boost | 300 | +5,000 max balance |
| ⚡ Fast Deposit | 400 | Instant deposits |
| 🏦 Interest | 600 | +5% daily interest |
| 🛡 Tax Shield | 800 | −25% war costs |

> All extension costs are configurable — see [Shop & Prices](#shop--prices).

---

## Territory & Claims

1. Open the territory map with `/k claim` or the Claim Map button.
2. Select unclaimed chunks on the map (click to toggle selection).
3. Press **Claim** — navigation starts, guiding you chunk by chunk.
4. Walk into each target chunk to claim it for your kingdom.

**Contesting:** Walking into an enemy chunk starts a chunk contest. Kill-based resolution after the contest timer (default: 300 s). Requires Admin role to start a contest.

---

## Wars

- Declared by a kingdom **Owner** via `/war declare <kingdom>`.
- Both kingdoms get an Action Bar and Boss Bar showing kill counts and timer.
- Default duration: 5 minutes (configurable).
- At war end, influence is transferred per chunk controlled by the winner.
- Admins can **surrender** via the War GUI (loses all contested chunks).

**War Debts:** Breaking blocks in a war zone generates debt. Debt must be repaid via the Debt GUI.

---

## Shop & Prices

All prices are configurable in `config.yml` under the `shop` key.

### Member Slots

```yaml
shop:
  member-slots:
    cost: 1000    # Gold per purchase
    amount: 10    # Slots added per purchase
```

### Kingdom Colors

```yaml
shop:
  colors:
    gray: 0         # §7 — free (default)
    white: 50       # §f
    dark_gray: 100  # §8
    yellow: 100     # §e
    green: 100      # §a
    aqua: 100       # §b
    gold: 150       # §6
    blue: 150       # §9
    red: 200        # §c
    light_purple: 200  # §d
    dark_purple: 250   # §5
    dark_green: 250    # §2
    dark_aqua: 250     # §3
    dark_red: 300      # §4
    dark_blue: 400     # §1
    black: 500         # §0
```

### Bank Extension Prices

```yaml
shop:
  extensions:
    income_boost: 500
    storage_boost: 300
    fast_deposit: 400
    interest: 600
    tax_shield: 800
```

---

## Territory Border

The **✦ Territory Border** button (slot 34 in the main menu) toggles a particle border around all chunks claimed by your kingdom. Only visible to you.

### Config

```yaml
territory-border:
  particle: HAPPY_VILLAGER   # FLAME, END_ROD, DUST, etc.
  dust-color: "255,215,0"    # RGB for DUST particle
  dust-size: 1.5
  edge-spacing: 1.0          # Horizontal spacing along edges (blocks)
  y-spacing: 5               # Vertical ring spacing (blocks)
  # y-min: -64               # Uncomment to override world min height
  # y-max: 320               # Uncomment to override world max height
  refresh-ticks: 20          # Refresh rate (20 = 1 second)
  duration-seconds: 60       # Auto-hide after X seconds (0 = never)
  render-chunks: 5           # Chunk radius to render
```

> **Performance tip:** Use `render-chunks: 3–5` and `y-spacing: 5–10` to keep particle counts low.

---

## Configuration

Main config file: `plugins/KingdomsReborn/config.yml`

| Key | Default | Description |
|---|---|---|
| `language` | `en_EN` | Language file (`en_EN` or `de_DE`) |
| `storage.type` | `sqlite` | Storage backend (`sqlite` or `yaml`) |
| `economy.name` | `Gold` | Currency name |
| `economy.currency-item` | `GOLD_INGOT` | Physical currency item |
| `economy.income-per-member` | `1` | Passive income per online member/min |
| `economy.bank-block` | `BARREL` | Block type used as bank |
| `economy.storage.max-level` | `80` | Max storage upgrade level |
| `economy.storage.capacity-per-level` | `1000` | Balance increase per level |
| `economy.storage.base-upgrade-cost` | `200` | Cost for level 0 → 1 |
| `economy.storage.cost-increment` | `150` | Additional cost per existing level |
| `kingdom.max-members` | `50` | Base member cap (without shop upgrades) |
| `kingdom.invite-expiry-seconds` | `120` | Invite expiry time |
| `war.duration-minutes` | `5` | War duration |
| `war.influence-transfer-per-chunk` | `50` | Influence transferred per chunk at war end |
| `claim.contest-duration-seconds` | `300` | Chunk contest duration |
| `display.enabled` | `true` | Enable Scoreboard/TAB/Nametags |

---

## Language

Files located in `plugins/KingdomsReborn/language/`.

- `en_EN.yml` — English (default)
- `de_DE.yml` — German

Change via `config.yml`:
```yaml
language: en_EN
```

Messages use **MiniMessage** format: `<gold>text</gold>`, `<red>`, `<bold>`, etc.  
Placeholders use `{curly_braces}`, e.g. `{kingdom}`, `{amount}`, `{balance}`.

---

*KingdomsReborn v0.1.1-Beta — PaperMC 1.21.11*
