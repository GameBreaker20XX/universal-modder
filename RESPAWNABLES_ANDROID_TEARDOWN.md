# Respawnables (Android) — Teardown Documentation

**Game:** Respawnables  
**Platform:** Android  
**Developer:** Digital Legends Entertainment  
**Publisher:** Digital Legends Entertainment  
**Year:** 2014+ (v11.4.0 analyzed)  
**Engine:** **ShooterPunch** (proprietary Digital Legends engine)

---

## 1. Game Engine

**Engine:** **ShooterPunch** (Digital Legends custom engine)  
- **Middleware (verified via `libshooterpunch.so`):**
  - **ShooterPunch** — 125× `ShooterPunch`, 35× `shooterpunch` (engine name pervasive)
  - **Digital Legends** — 1× `Digital`
  - **Respawnables** — 5× `Respawn`, 12× `respawn`
  - **FMOD** — 1× `fmod` (likely false positive / minimal)
  - **Unity** — 31× `unity` (false positive — substrings, not Unity engine)
- **Executable:** `libshooterpunch.so` (17.6 MB ARM64, 17.3 MB ARMv7) — main engine + game logic
- **Container:** XAPK (`respawnables-11-4.0.xapk`) containing:
  - `com.dle.respawnables.apk` (21.5 MB) — Java bootstrap + `libshooterpunch.so`
  - `main.110400005.com.dle.respawnables.obb` (788 MB) — game assets (not extracted)
- **Java:** `com.dle.respawnables.apk` → `classes.dex` + `lib/armeabi-v7a/libshooterpunch.so` + `lib/arm64-v8a/libshooterpunch.so`

**Falsified:** `unity` = substring noise (not Unity engine). No Unreal/Cocos/Godot/Flutter/Wwise/Bink/Marmalade.

---

## 2. Key Technical Details

- Digital Legends' proprietary **ShooterPunch** engine — name appears 160× in native lib
- XAPK distribution (APK + OBB) — OBB 788 MB contains bulk assets
- Minimal Java layer — bootstrap only, all gameplay in `libshooterpunch.so`
- FMOD reference (1×) likely dead code or minimal usage
- Sequel/spiritual successor to "Legends" (1× `Legends`, 7× `legends` in iOS binary)

---

*Generated from `respawnables-11-4.0.xapk` → `com.dle.respawnables.apk` → `lib/arm64-v8a/libshooterpunch.so` (17.6 MB)*  
*Engine: ShooterPunch (Digital Legends), Digital Legends Entertainment 2014+*