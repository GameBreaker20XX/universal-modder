# Dante's Inferno (PSP) — Teardown Documentation

**Game:** Dante's Inferno (ULUS10469, v1.01)  
**Platform:** PlayStation Portable  
**Developer:** Artificial Mind & Movement (Behaviour Interactive) — widely credited; unconfirmed from binary (packed BOOT.BIN)  
**Publisher:** Electronic Arts  
**Year:** 2010 (FW 6.20)  
**Format:** UMD ISO (1,812,725,760 bytes, 1,632 entries)

---

## 1. Game Engine

**Engine:** A2M/Behaviour PSP engine (unconfirmed — BOOT.BIN yields zero strings, packed code)  
- **Middleware (verified via file evidence):**
  - **Bink Video** (`.bik` ×227 — full-motion cutscenes)
- **Executable:** `PSP_GAME\SYSDIR\BOOT.BIN` (3,034,980 bytes, string-sparse) + `EBOOT.BIN`
- **Container:** 720 `.psp` packages (same container family as Pac-Man World 3 PSP's 39 `.psp` — shared porter tech?)
- **Audio:** `.sbk` (202 sound banks) + `.str` (87 streams)
- **Assets:** `.bin` (6), `.png`, `PARAM.SFO` ×2

**Evidence from dump:**
- `PARAM.SFO`: `DISC_ID ULUS10469`, `DISC_VERSION 1.01`, `PSP_SYSTEM_VER 6.20`
- `.psp`-pack + `.bik` + `.sbk` triple is the A2M PSP-port fingerprint (cf. PMW3 PSP)

---

## 2. Key Technical Details

- PSP adaptation of Visceral's console action game; packed BOOT.BIN blocks engine-string audit
- 227 Bink movies = unusually video-heavy PSP port (animated Divine Comedy cutscenes)

---

*Generated from `Dante's Inferno (PSP).iso` (file listing + PARAM.SFO)*  
*Engine: A2M/Behaviour PSP engine (likely, unconfirmed), 2010*