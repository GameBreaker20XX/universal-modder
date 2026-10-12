# Game Engine Knowledge Base

Maintained from teardown analyses. Updated 2026-10-12.

---

## 1. Pursuit Force (USA) — PSP (2005)
| Field | Value |
|---|---|
| **Title** | Pursuit Force (USA) |
| **Platform** | PSP |
| **Disc ID** | UCUS98640 |
| **Developer** | Bigbig Studios |
| **Publisher** | Sony Computer Entertainment |
| **Year** | 2005 |
| **Engine** | Bigbig `Game03` (proprietary) |
| **Middleware** | **NONE** — Sony PSP SDK only |
| **Executable** | `BOOT.BIN` (decrypted ELF32LE MIPS), `EBOOT.BIN` (`~PSP` encrypted) |
| **Firmware** | 2.50 |
| **Container** | PAK v2 (`02 PAK`), 16-byte index entries |
| **Asset Formats** | `.pspptx`, `.pspp3d`, `.psppve`, `.pspppprt`, `.psppfnt`, `.chpsp`, `.anp`, `.pph`, `.pob`, `.inp`, `.stf`, `.vib/.vdb`, `.at3`, `.pmf` |
| **Movies** | 12x PMF (H.264 480x272), extracted with audio via `psmfdump.exe` |
| **Audio** | ATRAC3 (`.at3`), VAG (`.vib/.vdb`), extracted to WAV |
| **Tools Used** | `psmfdump.exe` (PMF demux), `dattool` (not needed), `ffmpeg` |

**Key Finding:** 100% proprietary Bigbig engine on native PSP SDK. No licensed middleware.

---

## 2. Pursuit Force: Extreme Justice (USA) — PSP (2007)
| Field | Value |
|---|---|
| **Title** | Pursuit Force: Extreme Justice (USA) |
| **Platform** | PSP |
| **Disc ID** | UCUS98640 (same as PF1) |
| **Developer** | Bigbig Studios |
| **Publisher** | Sony Computer Entertainment |
| **Year** | 2007 |
| **Engine** | Bigbig `Game03` evolved (`PursuitForce2` module) |
| **Middleware** | **NONE** — Sony PSP SDK + AdHoc (`sceNetAdhoc`) |
| **Executable** | `BOOT.BIN` (decrypted ELF32LE MIPS, 3.1MB) |
| **Firmware** | 5.55 (per UPDATE/) |
| **Container** | PAK v2, 1508 files, 1.3GB MAIN.PAK |
| **Asset Formats** | Same as PF1 + multi-lang speech (`.vib/.vdb` EN/FR/SP) |
| **New Features** | AdHoc multiplayer, mission "Chains" system |

**Key Finding:** Direct evolution of PF1 engine. Same proprietary tech, added multiplayer.

---

## 3. MotorStorm: Arctic Edge (PSP) — PSP (2009)
| Field | Value |
|---|---|
| **Title** | MotorStorm: Arctic Edge |
| **Platform** | PSP |
| **Disc ID** | UCUS98743 |
| **Developer** | Bigbig Studios |
| **Publisher** | Sony Computer Entertainment |
| **Year** | 2009 |
| **Engine** | Bigbig `Game03` (same lineage) |
| **Middleware** | **NONE** — Sony PSP SDK only |
| **Executable** | `EBOOT.BIN` (`~PSP` encrypted, `MSPSP` tag), `BOOT.BIN` (zeros in dump) |
| **Firmware** | 5.55 |
| **Container** | PAK (`PAK ` magic), 24-byte linked-list entries |
| **Asset Formats** | `.PSP_PTX_MAIN` textures (identified), others expected same as PF1 |
| **Modules** | `psmf.prx` only |

**Key Finding:** Same `Game03` engine. PSP port by Bigbig (not Virtuos). Same PAK format, different magic.

---

## 4. MotorStorm: Arctic Edge (PS2) — PS2 (2009)
| Field | Value |
|---|---|
| **Title** | MotorStorm: Arctic Edge |
| **Platform** | PS2 |
| **Disc ID** | SCUS-97654 |
| **Developer** | Virtuos (port) |
| **Publisher** | Sony Computer Entertainment |
| **Year** | 2009 |
| **Engine** | Bigbig `Game03` (Virtuos port) |
| **Middleware** | CRI (audio/video), ODE physics (variable names) |
| **Executable** | `SCUS_976.54` (ELF32LE MIPS, 2.3MB) |
| **Container** | PAK (`PAK ` magic), same 24-byte linked-list as PSP |
| **Build Path** | `:\Workdir\MotorStormPSP\Game` (confirms PSP→PS2 port) |

**Key Finding:** Virtuos port of Bigbig's PSP code to PS2. Same engine, same assets.

---

## 5. Pursuit Force: Extreme Justice (USA) — PSP (2007) [Re-analyzed]
| Field | Value |
|---|---|
| **Title** | Pursuit Force: Extreme Justice (USA) |
| **Platform** | PSP |
| **Disc ID** | UCUS98640 |
| **Developer** | Bigbig Studios |
| **Year** | 2007 |
| **Engine** | Bigbig `Game03` (`PursuitForce2` module) |
| **Middleware** | **NONE** — Sony PSP SDK + AdHoc |
| **Executable** | `BOOT.BIN` (decrypted ELF, 3.1MB), `EBOOT.BIN` (`~PSP` encrypted) |
| **Firmware** | 5.55 |
| **Container** | PAK v2, 1508 files, 1.3GB MAIN.PAK |
| **Extracted** | 962/1508 files (music, speech banks EN/FR/SP, surfaces) |

---

## 6. Metal Gear Rising Revengeance (PC) — PC/PS3/X360 (2013)
| Field | Value |
|---|---|
| **Title** | Metal Gear Rising Revengeance |
| **Platform** | PC (Steam), PS3, Xbox 360 |
| **Developer** | PlatinumGames |
| **Publisher** | Konami |
| **Year** | 2013 |
| **Engine** | PlatinumGames proprietary (Bayonetta/Vanquish lineage) |
| **Middleware** | **Havok** (physics/animation `.hkx`), **Wwise** (audio `.bnk`) |
| **Asset Formats** | `.fbx` (models), `.hkx` (anim/physics), `.dds` (textures), `.bnk` (Wwise audio), `.dat` (custom container), `.eff` (effects), `.bxm` (binary XML) |
| **Archive Layout** | 12x 7z category archives → `.dat` + `.eff` per model → `dattool.exe` unpacks |
| **Tools Provided** | `dattool.exe`, `bxmtool.exe`, `mcdtool.exe`, `texconv.exe`, `wtbtool.exe`, `txttool.exe` |

**Key Finding:** Clean PlatinumGames proprietary engine. Only Havok + Wwise as middleware. Standard modern formats (FBX/HKX/DDS/BNK). Tools included.

---

## 7. MotorStorm: Arctic Edge (PSP) — PSP (2009) [Re-analyzed]
| Field | Value |
|---|---|
| **Title** | MotorStorm: Arctic Edge (PSP) |
| **Platform** | PSP |
| **Disc ID** | UCUS98743 |
| **Developer** | Bigbig Studios |
| **Year** | 2009 |
| **Engine** | Bigbig `Game03` |
| **Middleware** | **NONE** |
| **Executable** | `EBOOT.BIN` (`~PSP`/`MSPSP`), `BOOT.BIN` (zeros in dump) |
| **Firmware** | 5.55 |
| **Container** | PAK (`PAK ` magic), 24-byte linked-list entries |
| **Asset Formats** | `.PSP_PTX_MAIN` textures (verified in FE.PAK) |
| **PAK Format** | `PAK ` magic, 24-byte linked-list (`off,size,next_off,next_sz`) |
| **Extracted** | FE.PAK: 146 files (vehicle liveries `.PSP_PTX_MAIN`, UI) |

**Key Finding:** Same `Game03` engine. PSP port by Bigbig. Same PAK format as PS2 but different magic (`PAK ` vs `02 PAK`).

---

## 6. TrackMania DS (USA) — NDS (2009)

| Field | Value |
|---|---|
| **Title** | TrackMania DS (USA) (En,Fr,Es) |
| **Platform** | Nintendo DS |
| **Disc ID** | CTRE |
| **Developer** | Firebrand Games (Atod AB) |
| **Publisher** | Atari / Nintendo |
| **Year** | 2009 |
| **Engine** | Firebrand Games proprietary NDS engine |
| **Middleware** | **NONE** — Nintendo NitroSDK only |
| **Executable** | ARM9 (C++, 972 KB), ARM7 (NitroSDK, 155 KB) |
| **Scripting** | Lua 5.1 (`.luac` bytecode, 28 files) |
| **Firmware** | NDS (no firmware version) |
| **Container** | NDS ROM → FAT/FNT (13 files) → ZIP (3,457 files, 47.4 MB) |
| **Asset Formats** | `.nsbmd` (3D models), `.hzc` (collision), `.dcsc` (scenes), `.luac` (scripts), `.nsbca` (anim), `.nclr`/`.ncer`/`.nanr` (2D), `.hzc` (collision), `.bin` (ghosts), `.sdat` (audio) |
| **Languages** | EN, FR, ES, DE, IT, NL (6 languages) |
| **Audio** | SDAT (`.sdat` — sequences + samples) |

**Key Finding:** Firebrand Games (Atod AB) proprietary NDS engine. Zero licensed middleware. Main game data in a ZIP archive (3,457 files, 47 MB) at offset 0x645C00. ARM9 is C++ with STL. Lua for game logic/UI/config. No middleware whatsoever.

---

## 6. TrackMania Turbo DS (USA) — NDS (2010)

| Field | Value |
|---|---|
| **Title** | TrackMania Turbo DS (USA) (En,Fr,Es) |
| **Platform** | Nintendo DS |
| **Disc ID** | BT2E |
| **Developer** | Firebrand Games (Atod AB) — *had access to Octane engine* |
| **Publisher** | Atari / Nintendo |
| **Year** | 2010 |
| **Engine** | Firebrand Games proprietary NDS engine (Octane engine lineage) |
| **Middleware** | **NONE** — Nintendo NitroSDK only |
| **Executable** | ARM9 (C++/STL, 830 KB), ARM7 (NitroSDK, 156 KB) |
| **Scripting** | Lua 5.1 (`.luac` bytecode, 27 files) |
| **Firmware** | NDS (no firmware version) |
| **Container** | NDS ROM → FAT/FNT (21 files) → ZIP (4,258 files, 51.2 MB) |
| **Asset Formats** | `.n` (NSBMD models), `.h` (collision), `.dcsc` (scenes), `.luac` (scripts), `.nclr`/`.ncer`/`.nanr` (2D), `.h` (collision), `.na` (signage), `.bin` (ghosts), `.sdat` (audio) |
| **Languages** | EN, FR, ES, DE, IT, NL (6 languages) |
| **Audio** | SDAT (`.sdat` — sequences + samples) |

**Key Finding:** Firebrand Games proprietary NDS engine with Octane engine lineage. Zero licensed middleware. Main game data in a ZIP archive (4,258 files, 51 MB) at offset 0x873200. ARM9 is C++ with STL. Lua for game logic/UI/config. **Different file extensions** than TrackMania DS (`.n` for NSBMD, `.h` for collision vs `.nsbmd`/`.hzc`). Same engine lineage, evolved asset pipeline.

---

## Engine Lineage Summary

```
Bigbig Studios Game03 Engine
├── Pursuit Force 1 (PSP, 2005)          → PAK v2 (`02 PAK`)
├── Pursuit Force: Extreme Justice (2007) → PAK v2, AdHoc multiplayer
├── MotorStorm: Arctic Edge PSP (2009)    → PAK (`PAK `), same engine
└── MotorStorm: Arctic Edge PS2 (2009)    → Virtuos port, same PAK format
```

**Commonalities across all 4 Bigbig titles:**
- Proprietary Bigbig `Game03` engine
- Custom PAK container (linked-list entries)
- PSP/PS2 native SDK only — **zero licensed middleware**
- Custom texture (`.pspptx`/`.PSP_PTX_MAIN`), model (`.pspp3d`), animation (`.anp`), audio (`.at3`/`.vib/.vdb`) formats
- Build paths: `c:/Workdir/Game03/`, `c:/Workdir/PursuitForce2/`, `:\Workdir\MotorStormPSP\Game`

---

## Firebrand Games NDS Engine Lineage

```
Firebrand Games NDS Engine (Octane lineage)
├── TrackMania DS (2009)         → 32 MB ROM, ZIP (26 MB, 3457 files)
└── TrackMania Turbo DS (2010)   → 64 MB ROM, ZIP (27 MB, 4258 files)
```

**Commonalities across both Firebrand NDS titles:**
- Proprietary Firebrand Games NDS engine (Octane engine lineage)
- Zero licensed middleware — pure Nintendo NitroSDK
- ZIP archive for main game data (embedded in ROM)
- ARM9 C++ with STL, ARM7 NitroSDK
- Lua 5.1 scripting (`.luac` bytecode)
- NitroSDK 2D formats (NCGR/NCLR/NSC/NCE/NANR)
- SDAT audio
- **TrackMania Turbo DS evolves the format:** `.n` for NSBMD (vs `.nsbmd`), `.h` for collision (vs `.hzc`), more environments (4 vs 6), larger ROM (64 MB vs 32 MB)

---

## 8. PlatinumGames Engine (Separate Lineage)

```
PlatinumGames Engine
└── Metal Gear Rising Revengeance (2013) → Havok + Wwise, FBX/HKX/DDS/BNK
```

**No relation** to Bigbig/Sony engine lineage.

---

## Tools Catalog

| Tool | Game | Purpose |
|---|---|---|
| `psmfdump.exe` | Pursuit Force | PMF → `.264` + `.oma` (ATRAC) |
| `dattool.exe` | MGR | `.dat` → `.bnk` + `.bxm` |
| `bxmtool.exe` | MGR | Binary XML processing |
| `texconv.exe` | MGR | `.dds` conversion |
| `mcdtool.exe` | MGR | `.mcd` message data |
| `wtbtool.exe` | MGR | `.wtb` texture bins |
| `txttool.exe` | MGR | Text/localization |
| `ffmpeg` | All | Video/audio conversion |
| `py7zr` / `7z` | MGR | 7z archive extraction |

---

*Knowledge base maintained from hands-on teardown analyses. All findings from direct binary analysis of provided game dumps.*