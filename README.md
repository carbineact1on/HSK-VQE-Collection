# HSK-VQE-Collection

HSK/CE-patched compatibility patches for the **Vanilla Quests Expanded** mod series by Oskar Potocki et al., tuned for the [Hardcore SK](https://github.com/skyarkhangel/Hardcore-SK) modpack.

These are **thin overlay mods** — they don't fork the upstream VQE mods; they just apply XML PatchOperations on top to bring quest content into HSK conventions (HSK-native materials, CE weapon/ammo bindings, balance tweaks).

## Requirements

- **RimWorld 1.5**
- **Harmony**
- **Hardcore SK Modpack**
- **Combat Extended**
- The relevant upstream **Vanilla Quests Expanded** sub-mod (each patch is gated to its own VQE target)

## What's Inside

### 💀 HSK-VQE-Deadlife
Compatibility patch for **Vanilla Quests Expanded — Deadlife**. Adapts ancient quest content to HSK's economy and CE's combat math.

- **Material swaps** on deconstructable ancient structures so deconstruction yields HSK-tier refined materials:
  - `Steel → SteelBar` on Open/Closed Deadlife caskets, Dormant/Ancient Military Turrets, Kino Screen, Kino Projector
  - `Uranium → DepletedUranium` on the Deadlife caskets
- **CE patches** for the 4 ancient weapons so they fire correctly under HSK CE:
  - Ancient Autopistol → 9×19mm Parabellum
  - Ancient Machine Pistol → 9×19mm Parabellum (burst)
  - Ancient Pump Shotgun → 12 Gauge buckshot
  - Ancient LMG → 7.62×51mm NATO

Requires **Anomaly DLC** (carried over from upstream VQE Deadlife dependency).

### ⚡ HSK-VQE-Generator
Compatibility patch for **Vanilla Quests Expanded — The Generator**. Adapts the ARC megastructure quest line to HSK's economy and CE's combat math.

- **Material swaps** on all 16 player-spawned ARC genetrons (Basic, Wood-fired ×4, Chemfuel ×4, Geothermal ×4, Nuclear ×4) and on 8 ruined ancient ARC structures so deconstruction yields HSK-tier refined materials:
  - `Steel → SteelBar`
  - `Uranium → DepletedUranium`
  - Plasteel / ComponentSpacer / ComponentIndustrial / Gold left as-is (already HSK-native)
- **CE patch** for the Ancient Tight Parka so it provides meaningful protection on the HSK CE armor scale (Sharp 8 / Blunt 4 + Bulk / WornBulk).

### ❄️ HSK-VQE-Cryptoforge
Compatibility patch for **Vanilla Quests Expanded — Cryptoforge**. Adapts the crashed cryptoship quest line to HSK's economy and CE's combat math.

Bundles the **official upstream CE patch** (PR #3780 by Airomeda, merged into CombatExtended-Continued) so it works inside HSK's stripped CE redistribution:

- Crypto weapons (Cryptobolter + Cryptoaxe) — full CE conversion preserving cryptofreeze mechanics
- Crypto armors (light / heavy + helmets) — HSK CE armor scale (Sharp 16–28, Blunt 36–60)
- Cryptofused insectoid race — CE armor + body part scaling
- Crypto bolt ammo + AmmoSet definitions

HSK overlay on top of the bundled CE patches:

- Crypto bolt **ammo recipe**: `Steel → SteelBar` so HSK colonists craft from refined alloys
- **Building costList** swaps on 25 deconstructable structures (cryptopods, production benches, ancient turrets, ship debris):
  - `Steel → SteelBar`
  - `Uranium → DepletedUranium` (cryptopods)
- Plasteel / ComponentSpacer / ComponentIndustrial / Gold left as-is (already HSK-native)

## Installation

1. Clone or download this repo
2. Place each subfolder in your RimWorld `Mods/` directory (or point your HSK launcher at this repo URL — it will scan the subfolders automatically)
3. Enable each patch alongside its target VQE sub-mod
4. Load **after** Hardcore SK, Combat Extended, and the upstream VQE mods

⚠ **These patches require the upstream VQE mod they target** (e.g. HSK-VQE-Deadlife requires Vanilla Quests Expanded - Deadlife). The launcher will warn if dependencies are missing.

## How It Works

Each patch is a thin XML overlay using `PatchOperationReplace` / `PatchOperationAdd`:

- **Material swaps** target `<costList>` entries on deconstructable ancient buildings and replace raw vanilla materials with HSK-tier refined alloys
- **CE weapon patches** use `CombatExtended.PatchOperationMakeGunCECompatible` to inject `Verb_ShootCE` + `CompProperties_AmmoUser` + projectile bindings on top of the upstream weapon defs
- No content is added or removed — purely a compatibility overlay

## Reporting Issues

If you find a bug, please attach your `Player.log` and which sub-patch the issue is in. Issues without logs may be closed.

## Authorship

- Original mods: **Oskar Potocki**, **Sarg Bjornson**, **Taranchuk**, **Ferny** (Vanilla Quests Expanded series)
- HSK/CE conversion patches: **CarbineAction**
- CE patches by the **Combat Extended community**
- HSK material economy and bench conventions: **Hardcore SK Team**

## License

Each subfolder follows the original mod author's license where applicable. The HSK/CE compatibility work (XML patches) is released under the same terms as the upstream mods — free use, modification, and redistribution. Credit appreciated.

## Contact

Issues / suggestions / PRs → open an issue on this repo.
