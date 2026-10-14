# Tools Linkage — Modding Tools ↔ Torn-Down Games

For every engine family in `GAMES_KNOWLEDGE_BASE.md`: which tools apply, and where to get the ones not already on disk. Tool names at minimum; download sources only where certain.

---

## Nintendo Wii / GameCube (TrackMania Wii RVZ, Mario Power Tennis RVZ, Sunshine RVZ)
- **Dolphin** — https://dolphin-emu.org/download/ (includes **DolphinTool** for batch RVZ→ISO conversion)
- **Wiimm wit** — https://wit.wiimm.de/ (WBFS/WIT image handling)
- **BrawlCrate** — https://github.com/soopercool101/BrawlCrate (BRRES models, BRSAR audio)
- SZS Modifier, SuperBMD, CTools, BRSAR Extractor, BRRES Viewer, ShowMiiWads (WiiWare side: FAST/Jett/Onslaught lineage)

## Nintendo 3DS (Crash Time 3D CIA + MK7/SM3DL/ACNL CIA batch, all encrypted)
- **HackingToolkit9DS** — https://github.com/evan0312/HackingToolkit9DS (CIA decrypt/extract)
- **Ohana3DS** — https://github.com/gdkchan/Ohana3DS (`.bch`/`.bfres` models, `.bclim` textures)
- **pk3DS** — https://github.com/kwsch/pk3DS (Gen VI-adjacent tooling patterns)
- CtrStudio, ctpktool, Retsuko Sound Tool (`.bcwav`), Caesar, ExtraTools, PackEnglish (names only)

## Nintendo DS (25+ teardowns: Firebrand, TrackMania, GRID DS, Ridge DS, Wild World, Pokémon…)
- **Tinke** — https://github.com/pleonex/tinke (ROM split/rebuild)
- **ndstool** — https://github.com/devkitPro/ndstool (ROM split/rebuild)
- **devkitPro** — https://devkitpro.org/ (homebrew toolchain, FSPDS-grade analysis)
- **Lua 5.1 luac** — https://www.lua.org/ (disassemble Firebrand `.luac` bytecode)
- NDSFactory, NDSeditor, DSLazy, NitroModel ConverterGUI, nsbmd-texture-tool, SDATTool, SDATxtract, MKDSCM — MKDS Course Modifier (`.carc`/`.prm`, direct fit for MARIOKART_DS + CTGP_NITRO docs)

## PSP (PMF/ATRAC3 era: Burnout Legends, Crisis Core, RR1/2, TFU, Dissidia, GoW, NOVA, Pac-Man World 3…)
- **UMDGen** (ISO rebuild)
- **pmftools** (PMF video — 129 localized paths in Burnout Legends alone)
- Pursuit Force: MFAudio + VDB_extract scripts (match PF1's `.vib`/`.vdb` + `.at3` banks exactly)

## PS3 / Xbox 360 (Burnout Crash PS3 PKG, XBLA STFS, Moneyshot STFS)
- **ps3tools** (PKG decrypt — Burnout Crash trial PKG + EDAT still needs console keys)
- **extract-xiso** — https://github.com/XboxDev/extract-xiso (STFS/XISO handling)

## Synetic (Crash Time 0–5, Undercover)
- WR PTXTool with full Delphi source + `tga2ptx` (`.ptx` textures, 945–1,467 per game)
- AFC11BW/CT/HN/N Managers, WR Manager, FVR/MBTR Managers, 3DEdit, MTLWriter, WR MTKit/STKit, WR EditCar, MultiEx, DSExplorer (`.mox`/`.mtl`/archives) — validates every CT format table independently

## EGO / Codemasters (GRID PC, DiRT Showdown + sequel folders)
- 3DSimED32c, Ego PSSG Editor (PSSG assets)

## Criterion / RenderWare (Burnout family, NFS ProStreet EAGL)
- RenderWare SDK installer (abandonware copy on disk — verify version before use)
- Burnout per-title folders; QuickBMS + rpk_extract.py + DRIVECLUB/MOTORSTORM_APOCALYPSE scripts for adjacent PAK work

## Nadeo ManiaPlanet — gap, no tools on disk
- `NadeoPak` v0x12 tables are plaintext (parsed by hand already); no GBX toolchain present

## Unreal Engine 4.27 (Cyber Clutch, Head2Head, City Patrol UE4)
- **FModel** — https://github.com/4sval/FModel (`.pak`/`.ucas` + AES_finder key recovery)
- **umodel** — https://www.gildor.org/en/projects/umodel (assets, no-write inspection)
- UnrealPakTool, UPK Explorer, ue-explorer, custom UE4 scripts, sound_extraction_UE4

## Unity 4.7–2020 (Battle Riders, Draw & Drift, Track Racing Pursuit, APKs)
- **AssetRipper** — https://github.com/AssetRipper/AssetRipper
- **AssetStudio** — https://github.com/Perfare/AssetStudio
- **UABE** — https://github.com/DerPopo/UABE (bundle editing)

## FOX Engine (MGSV:GZ — opaque `.g0s`, `.ftex` ×208)
- FoxKit, GzsTool (3 versions), FtexTool, FMDL Studio, FsmTool, FvTwool, AutoPftxsTool, TranslationTool (names only)

## Rockstar AGE/RAGE + Saints Row + racing misc
- Midnight Club 2: iRipper, mc2noarchive, ar_extract video guides (`assets_p.dat`)
- RRUnpacker + Vita scripts (candidate for RRU DataProvider chunks)
- Split Second `unpack-ark.exe` + texture/streamtex unpackers (note: our PC docs are Director/Shockwave ports — these target console `.ark` builds)
- Saints Row per-title folders (no Moneyshot folder — X360 STFS set is the fallback for the prototype)

## Gaps (no tool on disk, manual methods only)
1. Firebrand Octane tooling (biggest — 6 teardowns; use Lua `luac` + NDS NitroModel tools above)
2. **chdman** (Type-0 CHD) — https://www.mamedev.org/ (ships with MAME)
3. DolphinTool CLI — ships inside Dolphin (see Wii section)
4. MSAE PAK unpacker (folder empty; Apocalypse/DriveClub-era QuickBMS scripts are adjacent, not direct)
5. Nadeo GBX toolchain · Monster/Excite tooling · 7-Zip (general ISO work) — https://www.7-zip.org/

---

*Revised Oct 14, 2026: tool names + download sources only, no local paths. Re-check against the tools folder when new dumps land: match engine → tool name → update the teardown doc with what it unlocked.*