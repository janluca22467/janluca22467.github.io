# 🏰 KingdomsReborn

[🇩🇪 Deutsch](#-deutsch) · [🇬🇧 English](#-english)

---

## 🇩🇪 Deutsch

> Ein vollständiges, GUI-gesteuertes Kingdom-Plugin für PaperMC 1.21.  
> Baue dein Imperium, beanspruche Territorien, verwalte deine Schatzkammer und führe Kriege — ganz ohne Chat-Eingaben.

📖 **[Vollständiges Wiki →](https://janluca22467.github.io/)**

### ✨ Features

- **Kingdoms** — Kingdom erstellen mit Owner / Admin / Mitglied-Rollen, Einladungen und Mitglieder-Slot-Upgrades
- **Territorien** — Visuelle 9×5-Chunk-Karte mit Biom-Farben, Mehrfachauswahl und 1-Chunk-Navigation
- **Wirtschaft** — Barrel-Bank-Blocks, 80 Lager-Upgrades, Bank-Erweiterungen, Kingdom-zu-Kingdom-Überweisungen
- **Krieg** — Automatische Kriegserklärung, Kill-basierte Wertung, Live Actionbar + Bossbar, Kapitulation per GUI
- **Schulden** — Block-Abbau im Kriegsgebiet erzeugt Schulden mit konfigurierbaren Block-Werten
- **Anzeige** — Sidebar-Scoreboard, TAB-Liste, Nametags und Chat-Formatierung mit Kingdom-Farbe
- **Keine Chat-Eingaben** — Alle Texteingaben (Name, Betrag, Suche, Umbenennen) laufen über Amboss-GUIs
- **Speicher** — SQLite (Standard) oder YAML
- **Zweisprachig** — Deutsch (`de_DE`) und Englisch (`en_EN`) inklusive; weitere Sprachen per YAML hinzufügbar

### 📋 Voraussetzungen

| Anforderung | Details |
|---|---|
| Server-Software | **Paper 1.21+** (Spigot wird NICHT unterstützt) |
| Minecraft-Version | 1.21 – 1.21.11 |
| Java | 21+ |

**Optionale Abhängigkeiten**

| Plugin | Zweck |
|---|---|
| [LuckPerms](https://luckperms.net/download) | Prefix / Suffix in Chat, TAB und Nametags |
| [PlaceholderAPI](https://hangar.papermc.io/HelpChat/PlaceholderAPI) | `%kingdom_name%`, `%stats_kills%` etc. in externen Plugins |

### ⚡ Schnellstart

1. `KingdomsReborn-x.x.x.jar` in den `/plugins/`-Ordner legen und Server neu starten
2. Im Spiel `/k` eingeben um das Kingdom-Menü zu öffnen
3. Einen **Barrel** im eigenen Gebiet platzieren und als Admin anklicken → Bank registriert
4. `/k claim` öffnet die Gebietskarte zum Beanspruchen der ersten Chunks

### 🔧 Befehle

| Befehl | Beschreibung | Berechtigung |
|---|---|---|
| `/k` | Kingdom-Hub-GUI öffnen | Alle |
| `/k create <Name>` | Kingdom gründen | Alle |
| `/k invite <Spieler>` | Spieler einladen | Owner |
| `/k accept` | Einladung annehmen | Alle |
| `/k leave` | Kingdom verlassen | Mitglied |
| `/k claim` | Gebietskarte öffnen | Mitglied |
| `/k transfer` | Gold überweisen | Admin+ |
| `/k debt` | Schulden anzeigen | Mitglied |
| `/k rename [Name]` | Kingdom umbenennen | Owner |
| `/k info [Name]` | Kingdom-Info im Chat | Alle |
| `/k list` | Alle Kingdoms auflisten | Alle |
| `/war` | Kriegs-Übersicht öffnen | Mitglied |

### ⚙️ Konfiguration

Alle Einstellungen in `plugins/KingdomsReborn/config.yml`.  
Sprachdateien in `plugins/KingdomsReborn/language/`.

```yaml
language: de_DE          # de_DE oder en_EN
storage:
  type: sqlite           # sqlite oder yaml
economy:
  currency-item: GOLD_INGOT
  income-per-member: 1   # Passives Einkommen pro Online-Mitglied pro Minute
kingdom:
  max-members: 50
war:
  duration-minutes: 5
```

### 📦 Dateistruktur

```
plugins/
└── KingdomsReborn/
    ├── config.yml
    ├── language/
    │   ├── de_DE.yml
    │   └── en_EN.yml
    ├── kingdoms.db
    └── data/
        ├── claims.yml
        └── debts.yml
```

### 📄 Lizenz

Single project EULA — ein Kauf gilt für einen Server.  
Kein DRM, keine Lizenzprüfungen, keine externen Verbindungen. Funktioniert vollständig offline.

---

## 🇬🇧 English

> A feature-complete, GUI-driven kingdom plugin for PaperMC 1.21.  
> Build your empire, claim territory, manage your treasury and wage war — no chat input required.

📖 **[Full Wiki →](https://janluca22467.github.io/)**

### ✨ Features

- **Kingdoms** — Create and manage kingdoms with Owner / Admin / Member roles, invites and member-slot upgrades
- **Territory** — Visual 9×5 chunk map with biome colours, multi-select claiming and 1-chunk navigation
- **Economy** — Barrel bank blocks, 80-level storage upgrades, bank extensions, kingdom-to-kingdom transfers
- **War** — Automatic war declaration, kill-based scoring, live actionbar + bossbar, surrender via GUI
- **Debt** — Block-break debt system during war with configurable per-block values
- **Display** — Sidebar scoreboard, TAB list, nametags and chat formatting with kingdom colour
- **No chat input** — Every text field (kingdom name, amount, search, rename) uses an anvil GUI
- **Storage** — SQLite (default) or YAML
- **Bilingual** — German (`de_DE`) and English (`en_EN`) bundled; add more via YAML

### 📋 Requirements

| Requirement | Details |
|---|---|
| Server software | **Paper 1.21+** (Spigot is NOT supported) |
| Minecraft version | 1.21 – 1.21.11 |
| Java | 21+ |

**Optional dependencies**

| Plugin | Purpose |
|---|---|
| [LuckPerms](https://luckperms.net/download) | Prefix / suffix in chat, TAB and nametags |
| [PlaceholderAPI](https://hangar.papermc.io/HelpChat/PlaceholderAPI) | `%kingdom_name%`, `%stats_kills%` etc. in external plugins |

### ⚡ Quick Start

1. Drop `KingdomsReborn-x.x.x.jar` into your `/plugins/` folder and restart
2. Type `/k` in-game to open the kingdom menu
3. Place a **Barrel** in your territory and right-click it as Admin to register your bank
4. Use `/k claim` to open the territory map and claim your first chunks

### 🔧 Commands

| Command | Description | Permission |
|---|---|---|
| `/k` | Open the kingdom hub GUI | All |
| `/k create <name>` | Found a new kingdom | All |
| `/k invite <player>` | Invite a player | Owner |
| `/k accept` | Accept a pending invite | All |
| `/k leave` | Leave your kingdom | Member |
| `/k claim` | Open the territory map | Member |
| `/k transfer` | Send gold to another kingdom | Admin+ |
| `/k debt` | View and repay debts | Member |
| `/k rename [name]` | Rename your kingdom | Owner |
| `/k info [name]` | Show kingdom info in chat | All |
| `/k list` | List all kingdoms | All |
| `/war` | Open the war overview GUI | Member |

### ⚙️ Configuration

All settings in `plugins/KingdomsReborn/config.yml`.  
Language files in `plugins/KingdomsReborn/language/`.

```yaml
language: de_DE          # de_DE or en_EN
storage:
  type: sqlite           # sqlite or yaml
economy:
  currency-item: GOLD_INGOT
  income-per-member: 1   # passive income per online member per minute
kingdom:
  max-members: 50
war:
  duration-minutes: 5
```

### 📦 File Structure

```
plugins/
└── KingdomsReborn/
    ├── config.yml
    ├── language/
    │   ├── de_DE.yml
    │   └── en_EN.yml
    ├── kingdoms.db
    └── data/
        ├── claims.yml
        └── debts.yml
```

### 📄 License

Single project EULA — one purchase covers one server.  
No DRM, no license checks, no external calls. Works fully offline.

---

*PaperMC 1.21 · Java 21 · MiniMessage · SQLite*
