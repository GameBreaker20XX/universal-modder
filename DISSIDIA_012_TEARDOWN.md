# Dissidia 012 Duodecim (PSP) — Teardown Documentation

**Game:** DISSIDIA duodecim FINAL FANTASY (ULUS10566, v1.00)  
**Platform:** PlayStation Portable  
**Developer:** Square Enix (1st Production Department)  
**Publisher:** Square Enix  
**Year:** 2011 (USA; FW 6.37)  
**Format:** UMD ISO (1,754,529,792 bytes, 195 entries)

---

## 1. Game Engine

**Engine:** Square Enix proprietary PSP engine (unconfirmed — BOOT.BIN yields zero strings in 4.6 MB, packed code)  
- **Middleware (verified via file evidence):**
  - **ATRAC3 Audio** (`.at3` ×135 — voice-heavy fighter: summons, EX bursts, dialogue)
  - **PMF Video** (`.pmf` ×35 — cutscenes/endings)
- **Executable:** `PSP_GAME\SYSDIR\BOOT.BIN` (4,640,948 bytes, string-sparse) + `EBOOT.BIN`
- **Modules:** 9 unencrypted `.elf` files + 2 `.prx` (analyzable surface for follow-up)
- **Assets:** `.bin` (8), `.png`, `PARAM.SFO` ×2

**Evidence from dump:**
- `PARAM.SFO`: `DISC_ID ULUS10566`, `DISC_VERSION 1.00`, `PSP_SYSTEM_VER 6.37`
- Zero engine/middleware strings in BOOT.BIN (packed) — audit limited to formats

---

## 2. Key Technical Details

- Prequel/expansion to Dissidia (2008/09); FF fighting system on PSP
- The 9 `.elf` modules are the soft target for deeper analysis (unpacked, unlike BOOT.BIN)

---

*Generated from `Dissidia 012 - Duodecim Final Fantasy (USA) (En,Fr,De,Es,It).iso`*  
*Engine: Square Enix proprietary PSP (packed binary), Square Enix 2011*