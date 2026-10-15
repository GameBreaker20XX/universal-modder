# Bully: Anniversary Edition (Android) — Teardown Documentation

**Game:** Bully: Anniversary Edition  
**Platform:** Android  
**Developer:** Rockstar Games (War Drum Studios port)  
**Publisher:** Rockstar Games  
**Year:** 2016  
**Engine:** **Rockstar RAGE** (verified: `RAGE`/`rage`/`Rockstar`/`R*`/`Bully` strings in `libGame.so`)

---

## 1. Game Engine

**Engine:** **Rockstar RAGE** (Android port of PS2 RenderWare title)  
- **Middleware (verified via `config.arm64_v8a.apk` → `libGame.so`):**
  - **Rockstar RAGE** — 6× `RAGE`, 160× `rage`, 95× `Rockstar`, 492× `R*`
  - **RenderWare legacy** — 7× `RenderWare` (PS2 asset format references)
  - **Flutter** — `libflutter.so` (11 MB) + `libapp.so` (3.4 MB) — UI/framework layer
  - **OpenAL** — `libopenal.so` (780 KB) — audio
  - **mpg123** — `libVendor_mpg123.so` (192 KB) — MP3 decoding
  - **Sentry** — `libsentry.so` + `libsentry-android.so` — crash reporting
  - **Bully formats** — 747× `Bully`, 55× `bully`, 11× `SCL`, 9× `IMG`, 242× `ipl` (PS2 archive/map formats)
- **Executable:** `libGame.so` (19 MB, ARM64) — main RAGE engine port
- **Container:** Split APKs (`config.*.apk` per ABI/locale) + `config.arm64_v8a.apk` (14.5 MB) contains native libs
- **Architecture:** Flutter UI shell + native RAGE `libGame.so` for gameplay

**Falsified:** No Unity/Unreal/Godot/Gamebryo/Criterion/FMOD/Wwise/Bink in `libGame.so`. `Unity` ×1 / `Gamebryo` ×1 = noise.

---

## 2. Key Technical Details

- War Drum Studios port of PS2 Bully (RenderWare) → Android via RAGE
- `libGame.so` retains PS2-era format strings: `IMG` (archive), `IPL` (item placement), `SCL` (collision)
- Flutter used for frontend/UI (modern Android requirement), RAGE for gameplay
- Split APKs per ABI (`arm64_v8a`, `armeabi-v7a`, etc.) and locale (`config.en.apk`, `config.de.apk`, etc.)
- No OBB — all assets in split APKs or downloaded at runtime

---

*Generated from `config.arm64_v8a.apk` → `lib/arm64-v8a/libGame.so` (19 MB)*  
*Engine: Rockstar RAGE, War Drum Studios/Rockstar Games 2016*