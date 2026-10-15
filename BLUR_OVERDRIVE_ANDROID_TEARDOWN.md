# Blur Overdrive (Android) — Teardown Documentation

**Game:** Blur Overdrive  
**Platform:** Android  
**Developer:** Marmalade / Activision (port of Bizarre Creations' Blur)  
**Publisher:** Activision  
**Year:** 2011 (Android port)  
**Engine:** **Marmalade SDK** (verified: `Marmalade`/`marmalade`/`s3e` strings in `libblur.so`)

---

## 1. Game Engine

**Engine:** **Marmalade SDK** (S3E) — C++ cross-platform framework  
- **Middleware (verified via APK/OBB contents):**
  - **Marmalade S3E** — 4× `Marmalade`, 21× `marmalade`, 407× `s3e`, 42× `S3E` in `libblur.so`
  - **Flurry Analytics** — `libflurry_ext.so`, `com/flurry/` in APK
  - **Facebook SDK** — `libs3efacebook_ext.so`
  - **Google Play Games** — `libs3egoogleplaygames_ext.so`
  - **Android Market Billing** — `libs3eandroidmarketbilling_ext.so`
  - **Android Helper** — `libs3eandroidhelper_ext.so`
- **Executable:** `libblur.so` (789 KB, ARM) — main game logic
- **Container (APK):**
  - `assets/groups/` — `.group.bin` archives (blur.group.bin 8.8 MB, uiSmall.group.bin 11 MB)
  - `assets/BlurOverdrive.s3e` (877 KB) — Marmalade app descriptor
  - `assets/languages/` — localized strings (`userstrings_*.bin`)
  - `assets/shaders/` — `uiShader.group.bin`
  - `assets/derbh/expansionFiles.txt` — OBB manifest
- **Container (OBB): `main.1000007.com.marmalade.blur.obb` (156 MB, custom `DTRZ` header)**
  - `.group.bin` packs: `autodrome_audio`, `coastal_audio`, `city_audio`, `common_audio`, `frontend_audio`, `levelup_audio`, `splashSmall/large/huge.group.bin`
  - Audio: `.mp3` (blur_fe_loop.mp3), `.wav` (push.wav)
  - Images: `.png` (tweetpictemp.png, splash*.png)
- **Java:** `classes.dex` (2.5 MB) — Marmalade bootstrap + Flurry

**Falsified:** No Unity/Unreal/FMOD/Havok/PhysX/Bink/Lua/Scaleform/CRI/Wwise/Ogg/Vorbis in `libblur.so`.

---

## 2. Key Technical Details

- Marmalade SDK port of Bizarre Creations' Blur (console: custom engine)
- Assets in Marmalade `.group.bin` archives (both APK and OBB)
- OBB uses custom `DTRZ` header (not standard ZIP) — file table with names: `blur_fe_loop.mp3`, `push.wav`, `tweetpictemp.png`, `splash*.group.bin`, `*_audio.group.bin`
- Flurry Analytics + Facebook + Google Play Games via Marmalade extensions
- No native physics/audio middleware exposed — Marmalade abstraction layer

---

*Generated from `blur-overdrive-1-1-1-es-en-fr-de-it-android.apk` (22 MB) + `main.1000007.com.marmalade.blur.obb` (156 MB) + `libblur.so`*  
*Engine: Marmalade SDK (S3E), Marmalade/Activision 2011*