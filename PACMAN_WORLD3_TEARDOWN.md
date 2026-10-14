# Pac-Man World 3 (PSP) — Teardown Documentation

**Game:** Pac-Man World 3 (ULUS10055, v1.01)  
**Platform:** PlayStation Portable  
**Developer:** Blitz Games (original); PSP porter unconfirmed  
**Publisher:** Namco  
**Year:** 2005 (EBOOT dated Nov 2005, FW 2.00)  
**Format:** UMD ISO (494,239,744 bytes, 100 entries)

---

## 1. Game Engine

**Engine:** BlitzTech-derived PSP port (unconfirmed — EBOOT.BIN encrypted, no BOOT.BIN in dump)  
- **Middleware:** Unconfirmed from binary (encrypted EBOOT yields zero strings)
- **Executable:** `PSP_GAME\SYSDIR\EBOOT.BIN` (5,758,304 bytes, encrypted) + FW updater
- **Container:** 39 `.psp` packages (game-data packs) + loose `.bin` (5)
- **Video:** `.pmf` (23 movies)
- **Modules:** 6 `.prx` + 7 `.o` (SDK objects)
- **Assets:** `.dat`, `.txt`, `.png`, `.cmd`, `PARAM.SFO` ×2

**Evidence from dump:**
- `PARAM.SFO`: `DISC_ID ULUS10055`, `TITLE Pac-Man World 3`, `DISC_VERSION 1.01`, `PSP_SYSTEM_VER 2.00`
- `.psp` pack count (39) + PMF movies = PSP-port packaging of the Blitz console game

---

## 2. Documentation Notes

- PSP port of the 2005 Blitz Games console title; porting studio unconfirmed
- No middleware claims possible without decrypted code (no BOOT.BIN in dump)

---

*Generated from `Pac-Man World 3 (USA).iso` (`PARAM.SFO`, file listing)*  
*Engine: BlitzTech-derived PSP port (unconfirmed), 2005*