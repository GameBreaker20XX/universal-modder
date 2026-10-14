# God of War: Ghost of Sparta (PSP) — Teardown Documentation

**Game:** God of War: Ghost of Sparta (UCUS98737, v2.00)  
**Platform:** PlayStation Portable  
**Developer:** Ready at Dawn  
**Publisher:** Sony Computer Entertainment  
**Year:** 2010 (FW 6.31)  
**Format:** UMD ISO (1,747,714,048 bytes, 844 entries)

---

## 1. Game Engine

**Engine:** Ready at Dawn proprietary PSP engine (unconfirmed — BOOT.BIN yields zero strings in 5.6 MB, packed code)  
- **Middleware (verified via file evidence):**
  - **ATRAC3 Audio** (`.at3` ×131 — orchestral score + combat SFX)
  - **PMF Video** (`.pmf` ×35 — cinematics)
- **Executable:** `PSP_GAME\SYSDIR\BOOT.BIN` (5,608,257 bytes, string-sparse) + `EBOOT.BIN`
- **Assets:** `.bin` (619 — data chunks, the bulk of the disc), `.prx` (38 PSP modules!), `.fnt`, `.xml`, `.png`, `PARAM.SFO` ×2
- **Physics/scripting:** Unconfirmed (packed binary)

**Evidence from dump:**
- `PARAM.SFO`: `DISC_ID UCUS98737`, `DISC_VERSION 2.00`, `PSP_SYSTEM_VER 6.31`
- 38 PRX modules = heavily modular engine (graphics/audio/system split)

---

## 2. Key Technical Details

- Ready at Dawn's second PSP GoW (after Chains of Olympus) — the studio's PSP engine at peak maturity
- `.bin`-chunked data (619 files) + 38 modules = streaming-first design for UMD seeks

---

*Generated from `God of War - Ghost of Sparta (USA) (En,Fr,Es).iso`*  
*Engine: Ready at Dawn proprietary PSP (packed binary), 2010*