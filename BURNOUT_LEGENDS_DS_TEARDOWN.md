# Burnout Legends (DS) — Teardown Documentation

**Game:** Burnout Legends (USA)  
**Platform:** Nintendo DS  
**Developer:** Criterion Games  
**Publisher:** Electronic Arts  
**Year:** 2005  
**Engine:** Criterion custom DS engine (Nintendo Nitro System SDK)

---

## 1. Game Engine

**Engine:** Criterion custom engine on **Nintendo Nitro System (NNS)** SDK  
- **Middleware (verified via ROM strings):**
  - **CRI ADX** (29× `CRI`, 1× `ADX`) — audio streaming
  - **Nintendo SDAT** (6× `SDAT`, 6× `BNK`, 8× `WAV`) — sequenced audio banks
  - **NNS** (4× `NNS`) — Nintendo Nitro System (standard DS SDK)
- **Executable:** ARM9 binary in FAT[0] (2.2 MB, `Burnout DS` header, game code `ABOE`)
- **Container:** Standard DS ROM filesystem (FAT/FNT) with multiple SDAT audio banks (FAT[10–13,15])
- **Graphics:** NNS G3D (NSBMD/NSBTX not found in main SDAT — likely in separate overlay or compressed)
- **Scripting:** None visible (compiled ARM9/ARM7)

**Falsified:** No Firebrand/Octane/Marmalade/RenderWare/Havok/PhysX/FMOD/Lua/Bink. `Nitro` = DS SDK reference only.

---

## 2. Key Technical Details

- Criterion's first DS title — custom engine on standard Nitro SDK
- Audio entirely CRI ADX streaming + Nintendo SDAT sequenced banks (6 separate SDATs)
- No NARC archive detected in main SDAT; model/texture format TBD (possibly overlay-loaded)
- ARM9 at FAT[0] (offset 0xBE000), ARM7 at FAT[1] — standard DS binary layout

---

*Generated from `Burnout Legends (USA) (En,Fr,Es).nds` (32 MB, game code ABOE)*  
*Engine: Criterion custom / Nintendo Nitro System, Criterion Games 2005*