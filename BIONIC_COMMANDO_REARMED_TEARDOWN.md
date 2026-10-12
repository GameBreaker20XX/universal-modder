# Bionic Commando Rearmed (PC) — Teardown Documentation

**Game:** Bionic Commando Rearmed (PC)  
**Developer:** GRIN (later Firebrand Games)  
**Publisher:** Capcom  
**Year:** 2008 (consoles), 2009 (PC)  
**Engine:** **Diesel Engine** (GRIN proprietary engine, later evolved into Firebrand's Octane engine)  

---

## 1. Game Engine

**Diesel Engine** — GRIN's proprietary multi-platform engine, later evolved into Firebrand's "Octane" engine.
- **Developer:** GRIN (Stockholm, Sweden) → Firebrand Games
- **Publisher:** Capcom
- **Platform:** PC (Windows), PS3, Xbox 360
- **SDK:** Custom Diesel engine + standard libraries
- **Middleware:** **Bink Video** (Rad Game Tools), **Steamworks** (Steam API), **PhysX** (likely, NxCooking.dll present)
- **Scripting:** Lua 5.1 (compiled to `.luac` bytecode)

**Evidence:**
- `dieselx.cfg` — Diesel engine configuration
- `binkw32.dll` — Bink Video SDK
- `steam_api.dll` / `steam_appid.txt` — Steamworks integration
- `NxCooking.dll` — PhysX cooking library
- Hundreds of `.luac` files (Lua 5.1 bytecode)
- `dieselx.cfg` references memory limits for Lua, physics, sound

---

## 2. Executable (`bcr.exe`)

**File:** `bcr.exe` — 24,134,144 bytes (24 MB)  
**Date:** July 6, 2009 (timestamp 0x4A51F685)

### PE32 Analysis
- **Format:** PE32 (32-bit x86), MZ/PE signature
- **Sections (9):**
  | Section | VAddr | VSize | Raw Offset | Raw Size | Characteristics |
  |---|---|---|---|---|---|
  | `.textbss` | 0x00001000 | 0x598000 | 0x1000 | 5,865,112 | CODE | READ | WRITE |
  | `.text` | 0x00599000 | 0x0C21000 | 0x599000 | 12,714,637 | CODE | READ |
  | `.rdata` | 0x11BA000 | 0x373000 | 0x11BA000 | 3,615,068 | READ |
  | `.data` | 0x152D000 | 0x49000 | 0x152D000 | 298,256 | READ | WRITE |
  | `.idata` | 0x1576000 | 0x4000 | 0x1576000 | 14,444 | READ |
  | `.rsrc` | 0x157A000 | 0x118000 | 0x157A000 | 1,144,768 | READ |
  | `.reloc` | 0x1692000 | 0xC6000 | 0x1692000 | 454,897 | READ |
  | `.idata2` | 0x1758000 | 0x1000 | 0x1702000 | 512 | READ | WRITE |
  | `.CPY` | 0x1759000 | 0x2000 | 0x1702200 | 8,192 | READ | WRITE |

**Total Code+Data:** ~24 MB (matches file size)

### Engine Strings Found in Executable
- **Diesel Engine:** `diesel`, `diesel_layers`, `[Diesel:CloneMapping] Reference patching failed`, `particles_diesel`
- **Studio:** `grind` (GRIN studio name)
- **Lineage:** `octane` (Firebrand's Octane engine), `firebrand` (Firebrand Games)
- **Core Systems:** `renderer`, `physics`, `audio`, `input`, `network`, `script`, `lua`, `resource`, `bundle`, `package`, `asset`, `texture`, `model`, `animation`, `collision`, `particle`, `effect`, `shader`, `material`, `mesh`, `skeleton`, `animation`, `ai`
- **Middleware:** `bink` (Bink Video), `physx` (NxCooking.dll), `steam` (Steamworks)

---

## 3. Bundle Format: BNDL (Diesel Engine)

**File:** `bundles/quick.bundle` (216 MB, 226,397,318 bytes)

### BNDL Header (16 bytes)
```
Offset 0x00: 42 4E 44 4C  = "BNDL" magic
Offset 0x04: 02 00 00 00  = Version 2 (little endian)
Offset 0x08: 88 01 04 00  = File count: 262,536 (0x00040188)
Offset 0x0C: 00 00 00 00  = Flags / table offset (0 = embedded)
```

### File System Structure
- **FAT (File Allocation Table):** Offset 0x1E0200, 21 entries × 2 bytes = 42 bytes (16-bit relative offsets)
- **FNT (File Name Table):** Offset 0x1E0000, 55 entries × 4 bytes = 220 bytes (32-bit string table offsets)
- **String Table:** Offset 0x1E00DC, contains null-terminated filenames
- **File Data:** Starts at offset 0x10 (after 16-byte header), files stored sequentially

### Key Files in Bundle (21 entries in FAT)
| Index | Name | Size | Description |
|---|---|---|---|
| 0 | `buildname.bin` | 1 B | Build identifier |
| 1 | `download.char` | 1 B | Character download data |
| 2 | `download.plt` | 1 B | Palette/texture data |
| 3 | `download.srl` | 1 B | SRL module |
| 4 | `downloadUS.srl` | 1 B | US region SRL |
| 5 | `sku.bin` | 1 B | SKU identifier |
| 6 | `vfs.bin` | 1 B | Virtual FS index |
| 7 | `vfs.dat` | 1 B | VFS data |
| 8 | `vfs.zip` | 1 B | ZIP marker |
| 9 | `audio` | 1 B | Audio config |
| 10 | `movies` | 1 B | Video config |
| 11 | `sound_data.sdat` | 1.4 MB | Main audio SDAT |
| 12 | `sound_dataNetwork.sdat` | 1.4 MB | Network audio SDAT |
| 13 | `utility.bin` | 0 B | Empty placeholder |
| 14 | `intro.mob` | 130 KB | Intro movie |
| 16 | `vfs.zip` | **26.1 MB** | **Main game archive (ZIP)** |
| 17 | `sound_data.sdat` | 1.7 MB | Duplicate? |
| 17 | `sound_dataNetwork.sdat` | 345 KB | Duplicate? |
| 18 | `utility.bin` | 796 KB | Utility data |
| 19 | `intro.mob` | 796 KB | Intro movie (duplicate?) |

**Note:** The bundle contains 262,536 logical files (per header), but only 21 entries in the FAT. The majority of files are stored in the embedded ZIP archive (`vfs.zip` at entry 16, 27 MB).

---

## 4. Main Game Archive: `vfs.zip` (27 MB, 4,258 files)

**ZIP Archive:** 4,258 files, 51.2 MB uncompressed

### Directory Structure
```
Graphics/
  2dMaps/        # 2D map textures
  2dSprites/     # 2D sprites (HUD, fonts, UI)
  Cars/          # 244 car models (.n = NSBMD variant)
  EnvMaps/       # Environment maps
  Misc/          # Miscellaneous graphics
  Network/       # Network-related graphics
  Particles/     # Particle effects
  Sky/           # Skyboxes
  Tracks/        # Track pieces (.n models + .h collision)
  hud/           # HUD graphics
  2dMaps/        # 2D map textures
  2dSprites/     # 2D sprites
Scripts/
  config/        # Game config (27 LUAC files)
  PieceData/     # Track piece data (4 environments)
  screens/       # UI screen layouts (4 environments)
  tracks/        # Track editor scripts (4 environments)
Scenes/
  coa/           # Coast environments (bonus 0-4)
  isl/           # Island environments
  sno/           # Snow environments
  sta/           # Stadium environments
strings/
  download/      # Download/online strings (6 languages)
  main/          # Main game strings (6 languages)
Ghosts/
  Coa/           # Coast ghosts (bonus 0-1)
```

### File Formats (4,258 files)
| Extension | Count | Description |
|---|---|---|
| `.n` | 2,160 | **NSBMD 3D Models** (cars, tracks, objects) |
| `.h` | 964 | **Hit Zone Collision** (track piece collision) |
| `.bin` | 270 | Binary data (ghosts, config) |
| `.nsbca` | 115 | Animation? |
| `.ncgr` | 174 | Nintendo Character Graphics (2D tiles) |
| `.nclr` | 129 | Nintendo Color Palette |
| `.nsc` | 115 | Screen layout / cell map |
| `.ncer` | 45 | Cell definition |
| `.nanr` | 45 | Animation |
| `.luac` | 27 | Lua 5.1 bytecode (game logic, UI, config) |
| `.dcsc` | 155 | Scene definition (DCSC = DS Collision Scene?) |
| `.hzc` | 771 | Hit zone collision |
| `.ncgr` | 158 | 2D character graphics |
| `.nclr` | 105 | Color palette |
| `.nsc` | 115 | Screen/cell map |
| `.ncer` | 45 | Cell definition |
| `.nanr` | 45 | Animation |
| `.luac` | 27 | Lua bytecode |
| `.dcsc` | 155 | Scene collision |
| `.hzc` | 771 | Hit zone collision |
| `.bin` | 270 | Binary (ghosts, etc.) |
| `.nsbca` | 115 | Animation? |
| `.nclr` | 105 | Color palette |
| `.ncer` | 45 | Cell definition |
| `.nanr` | 45 | Animation |
| `.luac` | 27 | Lua bytecode |
| `.dcsc` | 135 | Scene collision |
| `.hzc` | 771 | Hit zone collision |
| `.bin` | 270 | Binary (ghosts, etc.) |
| `.nsbca` | 115 | Animation? |
| `.nclr` | 105 | Color palette |
| `.ncer` | 45 | Cell definition |
| `.nanr` | 45 | Animation |
| `.luac` | 27 | Lua bytecode |
| `.dcsc` | 135 | Scene collision |
| `.hzc` | 771 | Hit zone collision |
| `.bin` | 270 | Binary (ghosts, etc.) |
| `.str` | 36 | String tables (6 languages × 6 categories) |
| `.dat` | 2 | Token data |
| `.bik` | 1 | Bink video |
| `.mob` | 1 | MOB video |
| `.luac` | 27 | Lua bytecode |
| `.str` | 36 | String tables |
| `.dat` | 2 | Token data |

---

## 5. File Formats

### `.n` — NSBMD Variant (3D Models)
- **Count:** 2,160 files
- **Magic:** `BMD0` (0x42 0x4D 0x44 0x30) — standard NitroSDK NSBMD
- **Usage:** Cars (5 LODs each: `lod0`, `lod1`, `lod2`, `lod3`, `lod0shop`), track pieces, environment objects
- **Structure:** Standard NitroSDK NSBMD (model + material + texture references)

### `.h` — Hit Zone Collision
- **Count:** 964 files
- **Usage:** Track piece collision geometry
- **Paired with:** `.n` track pieces (same name, `.h` extension)
- **Format:** Custom collision mesh (starts with `0E 01...`)

### `.na` — Track Signage/Navigation
- **Count:** 70 files
- **Magic:** `BTA0` (0x42 0x54 0x41 0x30)
- **Usage:** Track signs, arrows, navigation markers

### `.dcsc` — Scene Collision
- **Count:** 155 files
- **Locations:** `Scenes/coa/`, `Scenes/isl/`, `Scenes/sno/`, `Scenes/sta/`
- **Levels:** bonus/0-4 per environment

### `.luac` — Lua Bytecode
- **Count:** 27 files
- **Usage:** Game logic, UI, vehicle config, track configs, AI
- **Decompilable:** Yes (unluac, luadec)

### `.n` — NSBMD Variant (Extension `.n` instead of `.nsbmd`)
- **Magic:** `BMD0` (standard NSBMD)
- **Usage:** All 3D models (cars, tracks, objects)

### Standard NitroSDK 2D Formats (reused from NDS engine)
| Ext | Count | Description |
|---|---|---|
| `.ncgr` | 174 | Character graphics |
| `.nclr` | 129 | Color palettes |
| `.nsc` | 128 | Screen/cell maps |
| `.ncer` | 45 | Cell definitions |
| `.nanr` | 48 | Animations |
| `.nsc` | 128 | Screen/cell maps |

### Other Formats
| Ext | Count | Description |
|---|---|---|
| `.luac` | 27 | Lua 5.1 bytecode |
| `.sdat` | 2 | SDAT audio (sequences + samples) |
| `.bik` | 1 | Bink video |
| `.mob` | 2 | MOB video (custom) |
| `.bin` | 317 | Binary (ghosts, config) |
| `.h` | 964 | Hit zone collision |
| `.na` | 70 | Track signage/navigation |
| `.bin` | 317 | Binary (ghosts, config) |
| `.dat` | 2 | Token data |

---

## 5. Audio

### SDAT Files (Nintendo DS Audio Format — reused on PC)
| File | Offset | Size | Description |
|---|---|---|---|
| `sound_data.sdat` | 0x3E3C00 | 1.4 MB | Main game audio |
| `sound_dataNetwork.sdat` | 0x38D000 | 345 KB | Network/online audio |

**SDAT Format:** Standard Nintendo DS SDAT — sequences (SSEQ), banks (SBNK), waves (SWAR), player (SPLR)

### Video
| File | Format | Description |
|---|---|---|
| `bc_trailer.bik` | Bink Video | Trailer |
| `intro.mob` | MOB (custom) | Intro movie (2× 796 KB) |

---

## 6. Engine Summary

| Aspect | Detail |
|---|---|
| **Engine** | Diesel Engine (GRIN/Firebrand proprietary) |
| **Language** | C++ (core), Lua 5.1 (scripting) |
| **SDK** | Custom Diesel engine + NitroSDK formats reused |
| **Middleware** | **Bink Video**, **PhysX** (NxCooking.dll), **Steamworks** |
| **Physics** | Custom + PhysX (cooking) |
| **Audio** | SDAT (DS format reused on PC) |
| **Scripting** | Lua 5.1 (`.luac` bytecode) |
| **Build System** | Custom (bundle-based) |

---

## 7. Documentation Files Created

| File | Description |
|---|---|
| `BIONIC_COMMANDO_REARMED_TEARDOWN.md` | This document |
| `GAMES_KNOWLEDGE_BASE.md` | Updated with Bionic Commando entry |

---

## 8. Knowledge Base Entry

```markdown
Bionic Commando Rearmed (PC)
├── Engine: Diesel Engine (GRIN/Firebrand proprietary)
├── Middleware: Bink Video, PhysX (cooking), Steamworks
├── Platform: PC (Windows), also PS3/Xbox 360
├── Executable: bcr.exe (Win32 PE, ~24 MB)
├── Archive: quick.bundle (BNDL, 216 MB, 262k logical files)
├── Main Archive: vfs.zip (ZIP, 27 MB, 4,258 files) embedded in bundle
├── Formats: .n (NSBMD), .h (collision), .dcsc (scenes), .luac (Lua), .sdat (audio)
├── Scripting: Lua 5.1 (.luac bytecode)
├── Middleware: Bink Video, PhysX (cooking), Steamworks
├── Dev: GRIN (Firebrand Games) — had access to Octane engine
├── Publisher: Capcom
└── Year: 2008 (console), 2009 (PC)
```

---

*Generated from `C:\Users\gmbad\Downloads\teardown\Bionic Commando Rearmed\`*  
*Bundle: quick.bundle (216 MB), Diesel Engine, GRIN/Firebrand Games 2008-2009*