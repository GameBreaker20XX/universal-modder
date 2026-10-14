# N.O.V.A. (PSP Minis) — Teardown Documentation

**Game:** N.O.V.A. (Near Orbit Vanguard Alliance, NPUZ00179, v1.01, PSN minis)  
**Platform:** PlayStation Portable (PSN minis)  
**Developer:** Gameloft (NOVA franchise)  
**Publisher:** Gameloft  
**Year:** 2010 (minis build; FW 6.20)  
**Format:** PSP minis ISO (214,204,416 bytes, 489 entries)

---

## 1. Game Engine

**Engine:** Gameloft proprietary minis engine (unconfirmed — EBOOT.BIN encrypted, no BOOT.BIN in dump)  
- **Middleware:** PSP native audio evidenced (`.vag` ×417, `.at3` ×31); no licensed middleware provable without decrypted code
- **Executable:** `PSP_GAME\SYSDIR\EBOOT.BIN` (4,905,920 bytes, encrypted) + FW updater
- **Container:** 17 `.pack` archives + loose `.bin` (6)
- **Assets:** `.png` (6), `.pmf` (2 movies), `PARAM.SFO` ×2
- **Audio:** `.vag` (417!) + `.at3` (31) — voice-heavy FPS design (squad radio chatter)

**Evidence from dump:**
- `PARAM.SFO`: `DISC_ID NPUZ00179` (PSN minis ID range), `TITLE N.O.V.A.`, `DISC_VERSION 1.01`, `PSP_SYSTEM_VER 6.20`
- Minis constraints (small EBOOT, FW 6.20 floor) match the 2010 Gameloft minis wave

---

## 2. Key Technical Details

- VAG-count (417) vs tiny movies footprint (2 PMF) = audio-led FPS bootstrapping on minis budget
- `.pack` containers (17) hold the level data; engine core unconfirmed (encrypted EBOOT)

---

*Generated from `Nova (USA) (minis) (PSN).iso` (`PARAM.SFO`, file listing)*  
*Engine: Gameloft proprietary minis engine, Gameloft 2010*