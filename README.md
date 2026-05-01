# HSK-VQE-Collection

HSK/CE-patched standalone bundles of the **Vanilla Quests Expanded** mod series by Oskar Potocki et al., tuned for the [Hardcore SK](https://github.com/skyarkhangel/Hardcore-SK) modpack.

These are **full-bundle mods** — they include the entire upstream VQE content plus HSK-native material conversions and Combat Extended patches baked in. You do **not** need the Steam Workshop versions of the upstream VQE mods. Same architecture as `HSK-VFE-*` packages (Insectoids 2, Pirates, Mechanoids, Ancients, Deserters).

## Requirements

- **RimWorld 1.5**
- **Harmony**
- **Vanilla Expanded Framework**
- **Hardcore SK Modpack**
- **Combat Extended**
- DLCs as required by each sub-mod (Anomaly for Deadlife, Biotech for VEF features in Cryptoforge insectoid race)

⚠ **Do not enable the Steam Workshop versions of these VQE mods alongside these bundles** — each sub-mod declares `<incompatibleWith>` against its upstream packageId. Disable / unsubscribe from the Workshop versions before enabling these.

## What's Inside

### 💀 VQE Deadlife (HSK/CE Patched)
Standalone bundle of **Vanilla Quests Expanded — Deadlife**. Adapts ancient quest content to HSK's economy and CE's combat math.

- **HSK material conversion** on deconstructable ancient structures (21 buildings) so deconstruction yields HSK-tier refined materials:
  - `Steel → SteelBar` on Open/Closed Deadlife caskets, Dormant/Ancient Military Turrets, Kino Screen, Kino Projector
  - `Uranium → DepletedUranium` on the Deadlife caskets
  - `+ComponentIndustrial` / `+ComponentSpacer` / `+Plasteel` layers added per HSK tech tier (industrial vs ultratech)
- **CE patches** for the 4 ancient weapons so they fire correctly under HSK CE:
  - Ancient Autopistol → 9×19mm Parabellum
  - Ancient Machine Pistol → 9×19mm Parabellum (burst)
  - Ancient Pump Shotgun → 12 Gauge buckshot
  - Ancient LMG → 7.62×51mm NATO
- **HSK CE armor rescale** on the Military Coat (Sharp 8 / Blunt 4 + Bulk 4.0 / WornBulk 1.4)

Requires **Anomaly DLC** (carried over from upstream VQE Deadlife dependency).

### ⚡ VQE Generator (HSK/CE Patched)
Standalone bundle of **Vanilla Quests Expanded — The Generator**. The ARC megastructure quest line, full content + HSK/CE.

- **HSK material conversion** on all 16 player-spawned ARC genetrons (Basic, Wood-fired ×4, Chemfuel ×4, Geothermal ×4, Nuclear ×4) and 7 ruined ancient ARC structures + cryptosleep casket:
  - `Steel → SteelBar`
  - `Uranium → DepletedUranium`
  - `Gold → GoldBar` (HSK refined alloy, used for ultratech-tier genetrons)
  - Plasteel / ComponentSpacer / ComponentIndustrial left as-is (already HSK-native)
- **CE patch** for the Ancient Tight Parka so it provides meaningful protection on the HSK CE armor scale (Sharp 8 / Blunt 4 + Bulk / WornBulk).

### ❄️ VQE Cryptoforge (HSK/CE Patched)
Standalone bundle of **Vanilla Quests Expanded — Cryptoforge**. The crashed cryptoship quest line, full content + HSK/CE.

Bundles the **official upstream CE patch** (PR #3780 by Airomeda, merged into CombatExtended-Continued) so it works inside HSK's stripped CE redistribution:

- Crypto weapons (Cryptobolter + Cryptoaxe) — full CE conversion preserving cryptofreeze mechanics
- Crypto armors (light / heavy + helmets) — HSK CE armor scale (Sharp 16–28, Blunt 36–60)
- Cryptofused insectoid race — CE armor + body part scaling
- Crypto bolt ammo + AmmoSet definitions
- Ancient sentry turret CE conversion

HSK overlay on top of the bundled CE patches:

- Crypto bolt **ammo recipe**: `Steel → SteelBar` so HSK colonists craft from refined alloys
- **6 craftable items** (cryptoaxe, cryptobolter, 2 armors, 2 helmets): `Gold → GoldBar`
- **25 deconstructable building costLists**: `Steel → SteelBar`
- **2 cryptopods**: `Uranium → DepletedUranium`
- VQE_GoldPile loot building intentionally kept as raw `Gold` (ore-pile flavor)
- Plasteel / ComponentSpacer / ComponentIndustrial left as-is (already HSK-native)

**Quest design preserved:** Cryptobolter and Cryptoaxe stay locked to the AncientCryptoforge bench during the limited quest crafting window, exactly as upstream intended. HSKRNRouter intentionally does not move them.

## Installation

1. Clone or download this repo
2. Place each subfolder in your RimWorld `Mods/` directory (or point your HSK launcher at this repo URL — it will scan the subfolders automatically)
3. **Disable / unsubscribe from the Steam Workshop versions** of the corresponding upstream VQE mods (Deadlife, The Generator, Cryptoforge)
4. Enable the bundled versions in the mod menu
5. Load **after** Hardcore SK and Combat Extended

## How It Works

Each sub-mod is a full standalone fork of its upstream VQE counterpart with HSK/CE patches layered on:

- **Upstream content** (Defs, Assemblies, Patches, Textures, Sounds, Languages) is bundled directly — no external Workshop dependency
- **HSK material swaps** apply via XML `PatchOperationReplace` overlays in `1.5/Patches/HSK_*.xml` against the bundled defs
- **CE weapon patches** use `CombatExtended.PatchOperationMakeGunCECompatible` to inject `Verb_ShootCE` + `CompProperties_AmmoUser` + projectile bindings
- **packageId** uses `CarbineAction.HSK.VQE.X` (not the upstream `vanillaquestsexpanded.X`) — `<incompatibleWith>` blocks dual-loading

Materials all verified present in HSK Core_SK:
- `SteelBar`, `DepletedUranium`, `GoldBar` in `Items_Resource_Alloys_Industrial.xml` / `Items_Resource_Alloys_Medieval.xml`
- `ComponentIndustrial`, `ComponentSpacer` in `Items_Resource_Parts.xml`
- `ChunkSlagSteel` in `Various_Stone.xml`

## Reporting Issues

If you find a bug, please attach your `Player.log` and specify which sub-mod the issue is in. Issues without logs may be closed.

## Authorship

- **Original mods:** Oskar Potocki, Sarg Bjornson, Taranchuk, Ferny, Bread mo (Vanilla Quests Expanded series)
- **Cryptoforge CE patch:** Airomeda (CombatExtended-Continued PR #3780)
- **HSK/CE conversion + bundling:** CarbineAction
- **CE math:** Combat Extended community
- **HSK material economy and bench conventions:** Hardcore SK Team

## License

Each subfolder follows the original mod author's license where applicable. The HSK/CE compatibility work (XML patches and bundling layout) is released under the same terms as the upstream mods — free use, modification, and redistribution. Credit appreciated.

## Contact

Issues / suggestions / PRs → open an issue on this repo.
