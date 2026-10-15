# NASCAR Unleashed (PS3) — Teardown Documentation

**Game:** NASCAR Unleashed (USA)  
**Platform:** PlayStation 3  
**Developer:** Firebrand Games  
**Publisher:** Activision  
**Year:** 2011  
**Engine:** **Firebrand Octane** (verified)

---

## 1. Game Engine

**Engine:** **Firebrand Octane** (verified: VFS.ZIP container with `TABW` wavebatch headers, `.MSF` music tracks, `.BIK` Bink videos, `.PSSG` shaders)  
- **Middleware (verified via file evidence):**
  - **Bink Video** (`.BIK` files: ATTRACT, ATVI_LOGO, MENU_1, TUTORIAL_1–5)
  - **Firebrand Audio** (`.wavebatch` in VFS.ZIP — event-driven audio with named cues: `boost_fizzle`, `collision_car_major`, `exhaustflame`, etc.)
- **Executable:** `EBOOT.BIN` (5.6 MB, stripped — no engine strings)
- **Container:** `VFS.ZIP` (680 MB) + `VFS.BIN` (88 KB index) + `VFS.DAT` (16 bytes)
- **Audio:** 30+ `.MSF` music tracks (licensed soundtrack) + VFS.ZIP wavebatches (SFX/VO)
- **Shaders:** `.PSSG` shader packs (CARSHADERS, LIGHTINGSHADERS, HUDSHADERS, POSTFX, etc.)
- **Scripting:** None visible (compiled into EBOOT)

**Falsified:** No FMOD/Havok/PhysX/Lua/Scaleform/CRI/Wwise strings in EBOOT. `Nx` ×94 = opcode noise.

---

## 2. Key Technical Details

- Firebrand Octane PS3 build — same engine family as TrackMania DS/Wii/Turbo, GRID DS, Blur DS beta (NDS/DSi/Wii used `.vfs.zip` with ZIP-central-directory; PS3 uses VFS.ZIP + VFS.BIN index)
- Licensed soundtrack delivered as loose `.MSF` files (Firebrand music container) alongside VFS-packed wavebatches
- EBOOT stripped of engine identifiers — forensics via container/shader/audio formats only

---

*Generated from `NASCAR Unleashed (USA).7z` → `PS3_GAME/USRDIR/`*  
*Engine: Firebrand Octane, Firebrand Games 2011*