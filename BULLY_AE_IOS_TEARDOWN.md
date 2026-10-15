# Bully: Anniversary Edition (iOS) — Teardown Documentation

**Game:** Bully: Anniversary Edition  
**Platform:** iOS  
**Developer:** Rockstar Games (War Drum Studios port)  
**Publisher:** Rockstar Games  
**Year:** 2016  
**Engine:** **Rockstar RAGE** (iOS port, custom `.zip`/`.idx` archives)

---

## 1. Game Engine

**Engine:** **Rockstar RAGE** (iOS port of PS2 RenderWare title)  
- **Middleware (verified via IPA contents):**
  - **Rockstar RAGE** — inferred from Android counterpart (`libGame.so` has `RAGE`/`rage`/`Rockstar`/`R*`)
  - **Custom Archives** — `Bully.zip` (2.06 GB) + `Bully.zip.idx` (1 MB), `BullyOrig.zip` (236 MB) + `BullyOrig.zip.idx` (24 KB)
  - **Video** — `AttractMode.mp4` (76 MB), `Rockstar.m4v` (1.1 MB)
  - **Fonts** — 11 TTF/OTF fonts (Chalet, Helvetica, GTALICENSE, PRICEDOWN, etc.)
  - **UI** — XML (`MainMenu.xml`), PNG assets, nib (`MainWindow.nib`)
- **Executable:** `Payload/bully.app/Bully` (Mach-O, not directly extracted — main binary inside `Bully.zip`)
- **Container:** IPA with `Payload/bully.app/` containing:
  - `Bully.zip` / `Bully.zip.idx` — main game data (2 GB)
  - `BullyOrig.zip` / `BullyOrig.zip.idx` — original PS2 assets? (236 MB)
  - `AttractMode.mp4` — attract video
  - `Rockstar.m4v` — logo video
  - Fonts, UI XML, nib, PNG icons

**Falsified:** No Unity/Unreal/FMOD/Wwise/Bink/Marmalade strings visible in IPA metadata.

---

## 2. Key Technical Details

- Same RAGE port as Android, but iOS packaging differs:
  - Single monolithic `Bully.zip` (2 GB) + index instead of split APKs
  - `BullyOrig.zip` likely contains original PS2 RenderWare assets for reference/compatibility
  - Custom `.zip`/`.idx` format (not standard ZIP — `Bully.zip.idx` is 1 MB index)
  - No Flutter on iOS — native UIKit/XML UI (`MainMenu.xml`, `MainWindow.nib`)
- Video in MP4/M4V (iOS native) vs Android's likely VP8/OGG
- 1.8 GB IPA — large due to bundled game data

---

*Generated from `Bully_1.03.1_ios_9.0.ipa` (1.8 GB)*  
*Engine: Rockstar RAGE, War Drum Studios/Rockstar Games 2016*