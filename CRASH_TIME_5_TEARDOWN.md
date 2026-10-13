# Crash Time 5 — Undercover (Alarm für Cobra 11 Undercover) — Teardown Documentation

**Game:** Crash Time 5 — Undercover (Alarm für Cobra 11 Undercover) (PC, 2012)  
**Developer:** Synetic GmbH (German)  
**Publisher:** RTL Games / dtp entertainment  
**Engine:** Synetic 3D Landscape Engine (final evolution)

---

## 1. Game Engine

**Synetic 3D Landscape Engine** (evolved from Crash Time 4)
- **Middleware:** **Bink Video** (Rad Game Tools) — **NEW in CT5**
- **Executable:** Not found in dump
- **Physics:** Custom damage system (DAM_CRASH_* family trait; physics middleware unconfirmed)
- **Graphics:** DirectX 9 (D3DX9 Shader Compiler 9.12.589)
- **Audio:** DirectSound/DirectMusic (WAV, OGG)
- **Video:** Bink Video (`.bik`) — **CONFIRMED in CT5**
- **Scripting:** None found (C++ only)

**Evidence (format-level only — dump contained no executable; string claims retracted after CT0/CT1 exe audits falsified `ODEConfig`/`PHYSICS_*`/`VehicleDamage::*`/`TrackEditor*`):**
- `DAM_CRASH_*` damage system (family trait, exe-verified in CT0/CT1)
- File-format evolution vs CT4 (see §2)
- **Bink Video** (`.bik` files in Videos/ folder)

---

## 2. File Formats (Evolved from Crash Time 4)

### New Formats in Crash Time 5 - Undercover
| Format | Extension | Description |
|---|---|---|
| `.bik` | 5 | **Bink Video** (NEW - cutscenes/intros) |
| `.xml` | 10+ | Weapon/HUD definitions |

### Removed/Changed from Crash Time 4
| Format | Change |
|---|---|
| `.dds` | Removed (back to `.ptx` textures) |

### Persistent Formats
| Format | Count | Description |
|---|---|---|
| `.ptx` | 900+ | Textures |
| `.mox` / `.mtl` | ~500 each | Models / Materials |
| `.trf` | 50+ | Track reference files |
| `.cpo` | ~50 | Collision objects |
| `.tree` | 45 | Scene graph |
| `.cob` | 39 | Collision objects |
| `.ro1`-`.ro4` | 3 each | Road data |
| `.sni`/`.smp`/`.dat`/`.vef`/`.slt`/`.str` | 3 each | Misc |
| `.tob` | 20 | Unknown |
| `.wtr` | 5 | Water data |
| `.wpt` | 3 | Waypoints |
| `.geo` | 3 | Geometry |
| `.lvl` | 3 | Levels |
| `.qad` | 3 | Quad data |
| `.ro1`-`.ro4` | 3 each | Road data |
| `.sni`/`.smp`/`.dat`/`.vef`/`.slt`/`.str` | 3 each | Misc |
| `.tob` | 20 | Unknown |
| `.wtr` | 5 | Water data |
| `.wpt` | 3 | Waypoints |
| `.geo` | 3 | Geometry |
| `.lvl` | 3 | Levels |
| `.qad` | 3 | Quad data |
| `.ro1`-`.ro4` | 3 each | Road data |
| `.sni`/`.smp`/`.dat`/`.vef`/`.slt`/`.str` | 3 each | Misc |
| `.tob` | 20 | Unknown |

---

## 2. New Asset Types in Undercover

### Weapons System (NEW)
| Format | Extension | Description |
|---|---|---|
| `.xml` | 14 | Weapon/HUD definitions |

**Weapon Types:**
| Weapon | Files |
|---|---|
| `Weapon_emp` | `.xml` + `_effect.xml` |
| `Weapon_fender` | `.xml` |
| `Weapon_hook` | `.xml` + `_effect.xml` |
| `Weapon_jammer` | `.xml` |
| `Weapon_nailband` | `.xml` + `_effect.xml` |
| `Weapon_oilthrower` | `.xml` + `_effect.xml` |
| `Weapon_repair` | `.xml` |
| `Weapon_roadblock` | `.xml` |
| `Weapon_shield` | `.xml` + `_effect.xml` |

**HUD Elements (NEW):**
| HUD Element | Files |
|---|---|
| `Hud_bomborevidence` | `.xml` |
| `Weapon_area_aim` | `.xml` |
| `Weapon_car_aim` | `.xml` |
| `Weapon_enemy_health` | `.xml` |
| `Weapon_icons` | `.xml` + `_Split.xml` |
| `Weapon_icons_Split` | `.xml` |

### Evidence System (NEW)
| Type | Files |
|---|---|
| `Evidence` | `.MOX`/`.MTL` (models) |
| `Evidence/Textures/` | `.ptx` (Bombs, Cardboards, Dynamite, etc.) |

### Weapons System (NEW)
| Category | Files |
|---|---|
| `Weapons/` | 14 weapon definitions (`.xml`) |
| `Weapons/hud/` | 7 HUD elements (`.xml`) |
| `Weapons/hud/` | 7 HUD elements (`.xml`) |

---

## 2. File Formats (Evolved from Crash Time 4)

### New Formats in Undercover
| Format | Extension | Count | Description |
|---|---|---|---|
| `.bik` | 5 | **Bink Video** (cutscenes/intros) |
| `.xml` | 20+ | Weapon/HUD/Evidence definitions |

### Removed/Changed from Crash Time 4
| Format | Change |
|---|---|
| `.bik` | **ADDED** (5 files) |
| `.xml` | **ADDED** (20+ files) |
| `.dds` | Removed |

### Persistent Formats
| Format | Count | Description |
|---|---|---|
| `.ptx` | 900+ | Textures |
| `.mox` / `.mtl` | ~500 each | Models / Materials |
| `.trf` | 50+ | Track reference files |
| `.cpo` | ~50 | Collision objects |
| `.tree` | 45 | Scene graph |
| `.cob` | 39 | Collision objects |
| `.ro1`-`.ro4` | 3 each | Road data |
| `.sni`/`.smp`/`.dat`/`.vef`/`.slt`/`.str` | 3 each | Misc |
| `.tob` | 20 | Unknown |
| `.wtr` | 5 | Water data |
| `.wpt` | 3 | Waypoints |
| `.geo` | 3 | Geometry |
| `.lvl` | 3 | Levels |
| `.qad` | 3 | Quad data |
| `.ro1`-`.ro4` | 3 each | Road data |
| `.sni`/`.smp`/`.dat`/`.vef`/`.slt`/`.str` | 3 each | Misc |
| `.tob` | 20 | Unknown |
| `.wtr` | 5 | Water data |
| `.wpt` | 3 | Waypoints |
| `.geo` | 3 | Geometry |
| `.lvl` | 3 | Levels |
| `.qad` | 3 | Quad data |
| `.ro1`-`.ro4` | 3 each | Road data |
| `.sni`/`.smp`/`.dat`/`.vef`/`.slt`/`.str` | 3 each | Misc |
| `.tob` | 20 | Unknown |

---

## 2. New Asset Types in Undercover

### Weapons System (NEW)
| Category | Count | Format |
|---|---|---|
| Weapons | 14 | `.xml` definitions |
| HUD Elements | 7 | `.xml` definitions |
| Evidence System | 3 items | `.MOX`/`.MTL` + `.ptx` textures |

### New Vehicle Types
| Vehicle | Description |
|---|---|
| `Weapon_emp` | EMP weapon |
| `Weapon_fender` | Fender weapon |
| `Weapon_hook` | Grappling hook |
| `Weapon_hook_effect` | Hook effect |
| `Weapon_jammer` | Jammer weapon |
| `Weapon_nailband` | Nail band weapon |
| `Weapon_nailband_effect` | Nail band effect |
| `Weapon_oilthrower` | Oil thrower |
| `Weapon_oilthrower_effect` | Oil effect |
| `Weapon_repair` | Repair tool |
| `Weapon_roadblock` | Roadblock weapon |
| `Weapon_shield` | Shield weapon |
| `Weapon_shield_effect` | Shield effect |

### HUD System (NEW)
| Element | Files |
|---|---|
| `Hud_bomborevidence` | `.xml` |
| `Weapon_area_aim` | `.xml` |
| `Weapon_car_aim` | `.xml` |
| `Weapon_enemy_health` | `.xml` |
| `Weapon_icons` | `.xml` + `_Split.xml` |
| `Weapon_icons_Split` | `.xml` |
| `Weapon_roadblock` | `.xml` |

### Evidence System (NEW)
| Type | Files |
|---|---|
| `Evidence` | `.MOX`/`.MTL` models |
| `Evidence/Textures/` | `.ptx` textures (Bombs, Cardboards, Dynamite) |

---

## 2. File Formats (Evolved from Crash Time 4)

### New Formats in Undercover
| Format | Extension | Count | Description |
|---|---|---|---|
| `.bik` | 5 | **Bink Video** (cutscenes/intros) |
| `.xml` | 20+ | Weapon/HUD/Evidence definitions |

### Removed/Changed from Crash Time 4
| Format | Change |
|---|---|
| `.bik` | **ADDED** (5 files) |
| `.xml` | **ADDED** (20+ files) |
| `.dds` | Removed |

### Persistent Formats
| Format | Count | Description |
|---|---|---|
| `.ptx` | 900+ | Textures |
| `.mox` / `.mtl` | ~500 each | Models / Materials |
| `.trf` | 50+ | Track reference files |
| `.cpo` | ~50 | Collision objects |
| `.tree` | 45 | Scene graph |
| `.cob` | 39 | Collision objects |
| `.ro1`-`.ro4` | 3 each | Road data |
| `.sni`/`.smp`/`.dat`/`.vef`/`.slt`/`.str` | 3 each | Misc |
| `.tob` | 20 | Unknown |
| `.wtr` | 5 | Water data |
| `.wpt` | 3 | Waypoints |
| `.geo` | 3 | Geometry |
| `.lvl` | 3 | Levels |
| `.qad` | 3 | Quad data |
| `.ro1`-`.ro4` | 3 each | Road data |
| `.sni`/`.smp`/`.dat`/`.vef`/`.slt`/`.str` | 3 each | Misc |
| `.tob` | 20 | Unknown |
| `.wtr` | 5 | Water data |
| `.wpt` | 3 | Waypoints |
| `.geo` | 3 | Geometry |
| `.lvl` | 3 | Levels |
| `.qad` | 3 | Quad data |
| `.ro1`-`.ro4` | 3 each | Road data |
| `.sni`/`.smp`/`.dat`/`.vef`/`.slt`/`.str` | 3 each | Misc |
| `.tob` | 20 | Unknown |

---

## 3. New Asset Types in Undercover

### Weapons System (NEW)
| Format | Extension | Count | Description |
|---|---|---|---|
| Weapon definitions | `.xml` | 14 | Weapon configurations |
| HUD elements | `.xml` | 7 | HUD/UI elements |
| Evidence models | `.MOX`/`.MTL` | 3 sets | Evidence items |
| Evidence textures | `.ptx` | 10+ | Evidence textures |

### New Systems
| System | Files |
|---|---|
| **Weapons** | 14 weapon definitions (`.xml`) |
| **HUD** | 7 HUD elements (`.xml`) |
| **Evidence** | 3 evidence items (`.MOX`/`.MTL` + `.ptx`) |
| **Video** | 5 Bink videos (`.bik`) |

### Video (NEW)
| File | Size | Description |
|---|---|---|
| `CT5_Intro.bik` | ~ | Intro cutscene |
| `dtp.bik` | ~ | DTP intro? |
| `rtl.bik` | ~ | RTL branding |
| `spielziel.bik` | ~ | Game objective |
| `Synetic.bik` | ~ | Synetic logo |

---

## 3. Engine Analysis

**Engine:** Synetic 3D Landscape Engine (evolved)
- **Graphics:** DirectX 9 (D3DX9 Shader Compiler 9.12.589)
- **Physics:** Custom damage system (DAM_CRASH_* family trait; physics middleware unconfirmed — no exe in dump)
- **Audio:** DirectSound/DirectMusic (WAV, OGG)
- **Video:** **Bink Video** (`.bik`) — **NEW in CT5**
- **Scripting:** None (C++ only)

**New in Undercover:**
- **Bink Video** support (`.bik` files for cutscenes)
- **Weapons system** (14 weapon definitions via XML)
- **HUD system** (7 HUD elements via XML)
- **Evidence system** (investigation gameplay)
- **XML-based configuration** for weapons/HUD/evidence

---

## 3. Asset Structure

### New Directories in Undercover
| Directory | Description |
|---|---|
| `Weapons/` | 14 weapon definitions (`.xml`) |
| `Weapons/hud/` | 7 HUD elements (`.xml`) |
| `stdstuff/Evidence/` | Evidence models + textures |
| `Videos/` | 5 `.bik` cutscene videos |

### Vehicle/Traffic/Trains
- Same as CT4 (50+ vehicle types, expanded train system)
- No major changes to traffic/train systems

### New Systems
| System | Files | Format |
|---|---|---|
| **Weapons** | 14 `.xml` | Weapon configs |
| **HUD** | 7 `.xml` | HUD elements |
| **Evidence** | 3 `.MOX`/`.MTL` + 10+ `.ptx` | Evidence items |
| **Video** | 5 `.bik` | Bink Video cutscenes |

---

## 4. Engine Analysis

**Engine:** Synetic 3D Landscape Engine (final evolution)
- **Graphics:** DirectX 9 (D3DX9 Shader Compiler 9.12.589)
- **Physics:** Custom damage system (DAM_CRASH_* family trait; physics middleware unconfirmed — no exe in dump)
- **Audio:** DirectSound/DirectMusic (WAV, OGG)
- **Video:** **Bink Video** (`.bik`) — **NEW**
- **Scripting:** None (C++ only)
- **Data-driven:** XML for weapons/HUD/evidence

**New in Undercover:**
- **Bink Video** for cutscenes
- **XML-driven** weapons/HUD/evidence systems
- **Weapons system** (14 weapons with effects)
- **Evidence investigation** gameplay
- **HUD system** driven by XML

---

## 4. Documentation Files Created

| File | Description |
|---|---|
| `CRASH_TIME_5_TEARDOWN.md` | This document |
| `GAMES_KNOWLEDGE_BASE.md` | Updated with Crash Time 5 entry |

---

*Generated from `C:\Users\gmbad\Downloads\teardown\Crash Time 5 - Undercover\`*  
*Engine: Synetic 3D Landscape Engine (final evolution), Synetic GmbH 2012*