# AGENTS.md — NTNH-Guide-Pack context

## What this is
- **NTNH-Guide-Pack**: in-game guide content for **NTNH (Nuclear Tech: New Horizons)**,
  a hardcore quest-based Minecraft 1.7.10 modpack. Org: `NTNewHorizons`.
- Fork of `GTNewHorizons/GTNH-Guide-Pack`, adapted for NTNH. Guide framework is
  **GuideNH** (`GTNewHorizons/GuideNH`); this repo ships only content as a resource pack.
- Local instance for reference:
  `/home/bufka2011/.var/app/org.prismlauncher.PrismLauncher/data/PrismLauncher/instances/NTNH/minecraft/`
  (pack version 2.15.0, 337 mods, GuideNH 1.3.35 + txloader present).

## Mods present vs absent (do not document absent mods)
- PRESENT: HBM NTM, **GTNH-fork AE2** (`appliedenergistics2-rv3-beta-1070-GTNH` + ae2fc,
  ae2stuff, NEE, WCT, betterp2p), AgriCraft, Pam's HarvestCraft, Ex Nihilo,
  StorageDrawers, OpenComputers, ProjectRed/Blue, ArchitectureCraft, Angelica,
  Chromatic Tooltips, InGameInfoXML, OpenBlocks, Matter Manipulator,
  VendingBlockRevived, Hodgepodge, **GTNHLib**, BetterQuesting, ServerUtilities.
- ABSENT (never add guides for these): GregTech, Thaumcraft, Botania, Blood Magic,
  Forestry — and no magic content in general. Their namespaces were deleted.

## Namespaces (`assets/<modid>/`)
- `appliedenergistics2/` — full AE2 guide, keep as-is (untouched upstream content).
- `features/` — repurposed from GTNH `changelog/`; it lists **features**, not versions.
  Kept categories only: `misc/`, `qol/`, `ae2/` (the 9 AE2-delta pages describe QoL
  from the shared GTNH AE2 fork line, so they apply to NTNH; reworded to NTNH-neutral).
  Deleted GT-only categories: `crops` (CropsNH≠AgriCraft), `magic`, `multis`, `reworks`.
- `ntnh/` — new NTNH content, v1 scope is minimal: `index.md`, `ore-generation.md`,
  `agriculture/` (7 pages). `zh_cn/` for these are **English-fallback stubs**
  (mirrored frontmatter + untranslated note) — full translation is a later task.

## Owner's standing rules
- **Always push to `main` directly — no PRs.**
- Reword inherited GTNH text to NTNH-neutral (drop "2.9"/"GTNH" framing, fix icons
  pointing at absent mods to vanilla equivalents, drop examples using absent blocks
  like EBF/GT machines). `zh_cn` gets token-level fixes only; translators do the rest.
- Ponders are broken — strip `<GameScene>`/`<ImportPonder>` blocks when porting pages;
  do not ship orphan `.snbt`/`.json` ponder assets.
- The TXLoader-hosted guide is gone (deleted from the instance:
  `config/txloader/load/ntnh`, `load/changelog`, `forceload/appliedenergistics2`).
  The guide is a **separate resource pack** now. Never touch non-guide TXLoader
  payloads (bugtorch sounds, BQ themes, mainmenu textures, etc.).

## Updater (GTNHLib Resource Pack Update Notifier — notify-only, no auto-install)
- Code: `GTNHLib/.../client/ResourcePackUpdater/`. Hodgepodge has NO updater role.
- `pack.mcmeta` needs `gtnh_resource_pack_updater` {schema:1, pack_name, pack_version,
  pack_game_version, source:{type:github_releases, owner, repo}}.
- `pack_game_version` = NTNH line, currently **`2.15.X`**; extend with `;` if lines split.
- NTNH ships no DreamMaster `Refstrings`, so the player line resolves to `unknown`
  and the checker falls back to the installed pack's own line (exact string match).
- Every GitHub Release MUST contain `gtnh-pack-update.json` =
  `{schema: 1, pack_version, pack_game_version}` — **`schema: 1` as a JSON number
  is required** (string or missing ⇒ release ignored + 30-min failure cooldown).
  The `release-tags.yml` workflow generates it — keep the `--argjson s 1`.
- Releases: bare semver tags (`1.0.1`), zip named `NTNH-Guide-Pack-<ver>.zip`.
  Check manually in-game with `/resourcepack updateCheck`.

## Validation
- CI `validate-guide-pack.yml` runs GuideVSC (`ABKQPO/GuideNH-VSC`). Unknown items =
  warnings (non-blocking); everything else errors.
- Asset refs like `../assets/...` resolve against the `guidenh/` content root, NOT the
  page dir — naive file-exists checkers false-positive on these; trust GuideVSC.
- Layout: pages at `assets/<modid>/guidenh/_<lang>/**/*.md`, shared assets at
  `assets/<modid>/guidenh/assets/`, frontmatter must start with exactly `---`,
  image names in snake_case.

## Known TODOs
- `pack.png` is still the GTNH logo; `pack.mcmeta` `pack_version` stays `1.0.0`
  in-repo (stamped at release time).
- `features/.../misc/guide.md` still uses gregtech IDs in tag demos (validator-clean).
- `quest_percentage.md` assumes NTNH's BetterQuesting shows completion % — verify in-game.
- In-game check pending: copy repo to `resourcepacks/`, `F3+T`, browse all sections.
