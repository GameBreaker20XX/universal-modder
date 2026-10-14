# Star Wars: The Force Unleashed (PSP) — Teardown Documentation

**Game:** Star Wars: The Force Unleashed (ULUS10345, v1.01)  
**Platform:** PlayStation Portable  
**Developer:** Krome Studios (verified: `KromeLogoVideo` in decrypted BOOT.BIN)  
**Publisher:** LucasArts  
**Year:** 2008 (FW 3.95)  
**Format:** UMD ISO (1,111,490,560 bytes, 28 entries)

---

## 1. Game Engine

**Engine:** Krome Studios in-house PSP engine, Merkury lineage (likely — unconfirmed beyond dev credit)  
- **Middleware (verified via binary/file evidence):**
  - **PMF Video** (`.pmf` ×4 + path refs in BOOT.BIN)
  - **ATRAC3 Audio** (`.at3` + `sceAtrac3plus`/`sceSasCore` imports)
- **Executable:** decrypted BOOT.BIN (5,656,725 bytes, string-readable)
- **Container:** `.rkv` (×3 — Krome package format) + `.bin` (5)
- **Modules:** 5 `.prx`
- **Gameplay systems in strings:** Jedi Force powers (`MindTrick`, `MindControl`, `ForceGrip`, `Maelstrom`, `Vortex` goal/AI identifiers — `Mind*` ×11 are these, NOT A2M)
- **Physics/scripting:** Unconfirmed (no Havok/PhysX/Lua; `fmod` ×2 = CRT, `D3D` ×1 = noise)

**Evidence from dump:**
- `PARAM.SFO`: `DISC_ID ULUS10345`, `DISC_VERSION 1.01`, `PSP_SYSTEM_VER 3.95`
- `KromeLogoVideo` + mainmenu/credits/language screen identifiers
- `Square` ×1 = geometry term (not Square Enix); `Ready` ×1 = state string (not Ready at Dawn)

---

## 2. Key Technical Details

- PSP/Wii/PS2 TFU versions share the Krome lineage (vs LucasArts' internal PS3/X360 Pixelux-DMM build) — handheld TFU is a different engine family from its console namesake
- `.rkv` triple + decrypted BOOT.BIN = approachable reverse-engineering surface

---

*Generated from `Star Wars - The Force Unleashed (USA) (En,Fr).iso` (BOOT.BIN strings + PARAM.SFO)*  
*Engine: Krome Studios in-house PSP (Merkury lineage likely), Krome Studios 2008*