# Tools Linkage — Modding Tools ↔ Torn-Down Games

**Tools root:** `C:\Users\gmbad\Desktop\Modding Tools\` (surveyed Oct 14, 2026)  
**Purpose:** for every engine family in `GAMES_KNOWLEDGE_BASE.md`, which tool folder applies, which exact tools unlock the next forensics step, and where the gaps are.

---

## Nintendo Wii / GameCube — `GCN - Wii/`
- **Dolphin-x64** (`Dolphin.exe` GUI + Updater): play + file-browser for the unextracted RVZs — TrackMania Wii (`TRACKMANIA_WII`), Mario Power Tennis (`MPTENNIS`), Sunshine (`SUNSHINE`)
- **Wiimm tools + SZS Modifier + CTools + SuperBMD + BrawlCrate + BRRES viewer + BRSAR Extractor**: SZS/Yaz0, BRRES models, BRSAR audio once RVZs are extracted
- **ShowMiiWads**: WAD side (FAST/Jett/Onslaught WiiWare lineage)
- **Gap:** no `DolphinTool` CLI found (GUI-only Dolphin) — batch RVZ→ISO conversion needs a DolphinTool download

## Nintendo 3DS — `3DS/`
- **HackingToolkit9DS**: decrypt/extract CIA dumps (Crash Time 3D, MK7/SM3DL/ACNL batch — all currently encrypted-wall docs)
- **Ohana3DS (+Rebirth), CtrStudio, Sun-Moon Ohana**: `.bch`/`.bfres` models, `.bclim` textures once decrypted
- **Retsuko Sound Tool, Citric Composer**: `.bcwav` audio
- **pk3DS, PackEnglish, Caesar**: ORAS-centric, tangential

## Nintendo DS — `NDS/`
- **Tinke, NDSFactory, ndstool, NDSeditor, DSLazy, devkitPro**: ROM split/rebuild for all 25+ DS teardowns
- **NitroModel_ConverterGUI, nsbmd-texture-tool, apicula**: `.nsbmd`/`.nsbtx` models/textures (TrackMania, GRID DS, Ridge DS, Wild World, Camping Mama…)
- **SDATTool, SDATxtract**: `.sdat` audio banks across the DS set
- **MKDSCMLast.zip** (MKDS Course Modifier): `.carc`/`.prm` courses — direct fit for `MARIOKART_DS` + `CTGP_NITRO` docs

## PSP — `PSP General/` + `PS1 General/` + system homes
- **pmftools**: PMF video (Burnout Legends ×129 paths, Crisis Core, RR1/2, TFU, Dissidia, GoW, NOVA minis)
- **UMDGen_v4.00**: ISO rebuild (Burnout/NFS/PSP batch)
- **Pursuit Force/**: `MFAudiov11` + `VDB_extract[.py]` — matches PF1's `.vib`/`.vdb` audio banks + `.at3` exactly
- **Motorstorm Scripts/**: QuickBMS scripts (Apocalypse/DriveClub `.bms`) + `rpk_extract.py` — MSAE PAK-adjacent; MSAE tool folder itself is **empty** (gap)

## PS3 / Xbox 360 — `PS3 General/`, `XBOX 360/`
- **ps3tools (4.8.1)**: PKG decrypt — Burnout Crash PS3 trial PKG + EDAT (blocked today for lack of keys, tool is ready)
- **extract-xiso / xisoextract / Xbox Image Browse**: STFS browsers — Burnout Crash XBLA + Moneyshot prototype STFS dumps
- No Velocity/Xbox360 Neighborhood — STFS key extraction still manual

## Synetic (Crash Time 0–5, Undercover) — `Synetic General/`
- **WR PTXTool** (full Delphi source + exe, `tga2ptx`): `.ptx` textures (945–1,467 per game)
- **AFC11BW/CT/HN/N Managers, WR Manager, FVR/MBTR Managers**: game-specific managers (Alarm für Cobra 11 series coverage)
- **3DEdit, MTLWriter, WR MTKit/STKit, WR EditCar, MultiEx, DSExplorer**: `.mox`/`.mtl` models/materials + archives
- Direct fit for every CT doc's format tables; validates `.mox`/`.mtl`/`.ptx` assessments independently

## EGO / Codemasters — `Ego Engine/`, `GRID 2/`, `GRID Autosport/`, `Dirt Showdown/`, `DiRT*`, `Colin McRae Rally*/`, `Fuel (2009)/`
- **Ego PSSG Editor, 3DSimED32c**: PSSG assets (GRID/Showdown-era)
- Applies to `GRID_PC` (EGO verified) + `DIRT_SHOWDOWN` (EGO verified); DiRT/GRID sequel folders await their dumps

## Criterion / RenderWare — `RenderWare/`, `Burnout Crash/`, `Burnout Paradise/`, `Burnout Takedown Era/`
- **setup_11_rc3.zip** (RenderWare SDK installer — version-check before use)
- Burnout folders per-title; Paradise Remastered findings (Lua/EA WebKit/XAudio2) have no dedicated unpacker here — BNDL/BUNDLE parsing still manual

## Firebrand Octane — ⚠️ NO FOLDER (gap)
- TrackMania DS/Turbo, GRID DS, Blur DS beta, NASCAR Unleashed, TrackMania Wii have **no tools**: `vfs.zip` inspection is manual (ZIP-central-directory scripts), `.luac` needs stock Lua 5.1 `luac`, `.nsbmd` needs NitroModel tools from `NDS/`

## Nadeo ManiaPlanet — ⚠️ NO FOLDER (gap)
- `NadeoPak` v0x12 tables are plaintext (parseable by hand, as done); no GBX toolchain present (would live under a future `ManiaPlanet/` folder)

## Unreal Engine — `Unreal Engine/`
- **FModel, umodel, UnrealPakTool, UPK Explorer, ue-explorer**: `.pak`/`.ucas` (Cyber Clutch UE4.27, Head2Head, City Patrol UE4)
- **AES_finder**: encrypted-pak key recovery path
- **custom_UE4_scripts, sound_extraction_UE4**: audio follow-ups

## Unity — `Unity Engine/`
- **AssetRipper, AssetStudio.net6, UABEANext4**: Unity 4.7 (Battle Riders), 5.3 (Draw & Drift), 2020+ (Track Racing Pursuit), Mono/IL2CPP-era APKs

## FOX Engine — `MGSV/`
- **FoxKit, GzsTool (×3 versions), FtexTool, FMDL Studio, FsmTool, FvTwool, AutoPftxsTool, TranslationTool**: `.g0s`/`.ftex`/`.fmdl` — direct fit for `MGSV_GZ` (opaque `.g0s` + `.ftex` ×208)

## Monster/Excite/Pilotwings — ⚠️ NO FOLDER (gap)
- Excite Truck (`.car`/`.trk`/`.toc`), Pilotwings Resort: no tools; Wii `GCN - Wii/` tooling is the fallback

## Rockstar (RAGE + AGE) — `Rockstar Advanced Game Engine/`, `Midnight Club 1/2/3/`, `GTA IV/`, `GTA V/`
- AGE rows (Midnight Club 1/2, RDR Revolver) + RAGE rows (MGR? no — Platinum; GTA/Midnight LA/RDR) map here; MC2 `assets_p.dat` has its own video+extractor docs in `Midnight Club 2/`

## Saints Row — `Saints Row 1/2/3/3R/4/GOOH/Reboot/`
- No Moneyshot folder (cancelled prototype) — nearest tooling is the X360 STFS set for its container

## Racing misc — `Driver General/`, `NASCAR Unleashed X360/`, `NFS HPR/`, `NFS MW12/`, `Ridge Racer General/`, `Ridge Racer Vita/`, `Ridge Racer Unbounded/`, `Fuel (2009)/`, `Scarface*/`, `Simpsons - Hit & Run/`, `Sleeping Dogs*/`, `Watch Dogs/`, `Split Second/`, `Transformers Armada (PS2)/`, `Mafia*/`, `Just Cause General/`, `Jett Rocket Scripts/`, `MotorStorm *`, `Colin McRae*`
- **Split Second/**: `unpack-ark.exe` + texture/streamtex unpackers + README — note: our Split/Second PC docs are Director/Shockwave ports; these tools target the console `.ark` builds
- **Midnight Club 2/**: `iRipper`, `mc2noarchive`, `ar_extract` video guides for `assets_p.dat`
- **RRUnpacker** (+Vita scripts): candidate for RRU DataProvider chunks
- **Jett Rocket Scripts/**: SHIN'ENGINE follow-up path

## Gaps summary (no tool, manual methods only)
1. Firebrand Octane tooling (biggest gap — 6 teardowns)
2. chdman (Type-0 CHD) — searched, not present
3. DolphinTool CLI (RVZ batch work)
4. MSAE PAK unpacker (folder empty; QuickBMS scripts are Apocalypse/DriveClub-era)
5. Nadeo GBX toolchain · Monster/Excite tooling · Excite `.toc` parsers

---

*Survey of `C:\Users\gmbad\Desktop\Modding Tools\` (top-level + key subfolders), Oct 14, 2026. Re-run when new dumps land: match engine → folder → exact binary, then update the teardown doc with what the tool unlocked.*