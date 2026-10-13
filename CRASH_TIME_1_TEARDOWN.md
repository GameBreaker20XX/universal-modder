# Crash Time 1 (Alarm für Cobra 11) — Teardown Documentation

**Game:** Crash Time (Alarm für Cobra 11) (PC, 2007)  
**Developer:** Synetic GmbH (German)  
**Publisher:** RTL Games / JoWooD  
**Engine:** Synetic 3D Landscape Engine (proprietary)  

---

## 1. Game Engine

**Synetic 3D Landscape Engine** (proprietary, German) — evolved from Crash Time 0
- **Middleware:** **None** — DirectX 9, custom physics (ODE references)
- **Executable:** Not found in dump (likely missing from dump)
- **Physics:** Custom damage system (DAM_CRASH_*) + ODE Physics (ODEConfig referenced)
- **Graphics:** DirectX 9 (D3DX9 Shader Compiler 9.12.589)
- **Audio:** DirectSound/DirectMusic (WAV, WMA)
- **Video:** WMV (Windows Media Video)
- **Scripting:** None found (C++ only)

---

## 2. File Formats

### 3D Models & Vehicles
| Format | Extension | Description |
|---|---|---|
| `.mox` | 429 files | Vehicle/environment models |
| `.mtl` | 390 files | Materials (paired with .mox) |
| `.cob` / `.cpo` | 39 / 87 | Collision objects / physics |
| `.tree` | 45 | Scene graph / hierarchy |
| `.ro1`-`.ro4` | 3 each | Road segment data |
| `.tob` | 20 | Unknown binary |

### Vehicles (13 total)
Each vehicle has:
| File | Description |
|---|---|
| `VEHICLE.3DF` | Main model |
| `FESPL.3DF` | Front-end split model |
| `FEWHEELS.3DF` / `.SPR` | Front-end wheels |
| `SPL1-5.3DF` | Spline/spline data |
| `WHEEL1-5.3DF/.SPR` | Wheel models |
| `PAINT.SPR` | Paint texture |
| `CAMERA.TWK` / `CONFIG.TWK` / `config.txt` | Config |

### Track Data
| Format | Extension | Description |
|---|---|---|
| `.BIN` | Track geometry (binary) |
| `.TRK` / `.trk` | Track definition (86 KB fixed) |
| `.3DF` | Theme/scene data |
| `.dcsc` | Scene collision |

### Textures
| Format | Description |
|---|---|
| `.ptx` | Textures (945 files in Crash Time 0, similar here) |

### Audio
| Format | Description |
|---|---|
| `.wav` | PCM audio (492 files) |
| `.wma` | Windows Media Audio (19 files) |

### Video
| Format | Description |
|---|---|
| `.wmv` | Windows Media Video (61 files) |

### Physics / Collision
| Format | Count | Description |
|---|---|---|
| `.cob` / `.cpo` | 39 / 87 | Collision objects / physics |
| `.ro1`-`.ro4` | 3 each | Road segment data |
| `.tob` | 20 | Unknown |

### Audio
| Format | Count |
|---|---|
| `.wav` | 492 |
| `.wma` | 19 |
| `.wtr` | 5 |

### Video
| Format | Count |
|---|---|
| `.wmv` | 61 |

### Config / Text
| Format | Description |
|---|---|
| `.ini` / `.tzw` / `.txt` | Config files |
| `.txt` | Text files (23) |

---

## 3. Engine Analysis

**Engine:** Synetic 3D Landscape Engine (evolved from Crash Time 0)
- **Graphics:** DirectX 9 (D3DX9 Shader Compiler 9.12.589)
- **Physics:** Custom damage system + **ODE Physics** (ODEConfig referenced)
- **Audio:** DirectSound/DirectMusic (WMA, WAV)
- **Video:** WMV
- **Scripting:** None (C++ only)

### Physics
- **ODE Physics** referenced (`ODEConfig`, `PHYSICS_BODY_GF`, `PHYSICS_BODY_TRIMESH_G`, `PHYSICS_INSTANCE_GF`)
- Custom damage system: `DAM_CRASH_ANIM`, `DAM_CRASH_GEAR`, `DAM_CRASH_MOTOR`, `DAM_CRASH_CHASS`, `DAM_CRASH_BRAKE`
- Vehicle damage: `VehicleDamage::InitMorphSections`

### Editor/Tools
- Built-in track editor: `TrackEditorGUI`, `TrackEditorLoadTrackGUI`, `TrackEditorGUI`
- Editor config: `CITY_EditorSunColourR/G/B`, `RALLY_EditorAmbientColourB`, `RALLY_EditorSunColourR/G/B`, `RALLY_EditorSunRotY`

---

## 3. Documentation Files Created

| File | Description |
|---|---|
| `CRASH_TIME_1_TEARDOWN.md` | This document |
| `GAMES_KNOWLEDGE_BASE.md` | Updated with Crash Time 1 entry |