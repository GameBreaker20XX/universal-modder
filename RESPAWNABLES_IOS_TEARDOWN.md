# Respawnables (iOS) — Teardown Documentation

**Game:** Respawnables  
**Platform:** iOS  
**Developer:** Digital Legends Entertainment  
**Publisher:** Digital Legends Entertainment  
**Year:** 2014+ (v2.3.0 analyzed)  
**Engine:** **ShooterPunch** (proprietary Digital Legends engine)

---

## 1. Game Engine

**Engine:** **ShooterPunch** (Digital Legends custom engine)  
- **Middleware (verified via `Payload/Respawnables.app/Respawnables` executable):**
  - **ShooterPunch** — 12× `ShooterPunch` (engine name)
  - **Digital Legends** — 1× `Digital`, 9× `digital`
  - **Respawnables** — 68× `Respawn`, 17× `respawn`
  - **FMOD** — 2× `fmod` (minimal/dead code)
  - **OpenGL ES** — 2× `OpenGLES`, 3× `OpenGL`
  - **Unity** — 1× `Unity`, 153× `unity` (false positive — substrings)
- **Executable:** `Respawnables` (14.2 MB, Mach-O ARM64) — main engine + game logic
- **Container:** IPA (`Respawnables-v2-3-0.ipa`, 85 MB) containing:
  - `Payload/Respawnables.app/Respawnables` — main binary
  - `GameApp.cfg` (3 KB) — config
  - `FacebookSDKResources.bundle` — Facebook SDK
  - `TapjoyResources.bundle` — Tapjoy analytics/ads
  - Standard iOS resources (icons, launch images, nibs, plists)
- **Signing:** `_CodeSignature/`, `Crackalicious-AppAddict` (48 bytes — scene crack marker), `Cert.pem`, `Key_NoPass.pem`

**Falsified:** `unity` = substring noise. No Unreal/Cocos/Godot/Flutter/Wwise/Bink/Marmalade/Metal.

---

## 2. Key Technical Details

- Same **ShooterPunch** engine as Android version — Digital Legends proprietary tech
- iOS binary smaller (14 MB vs 17 MB) — likely stripped symbols
- Facebook SDK + Tapjoy for social/ads (standard 2014 mobile stack)
- Scene crack artifact (`Crackalicious-AppAddict`) in IPA — dumped from cracked source
- OpenGL ES 2.0/3.0 rendering (no Metal — pre-Metal era or compatibility)

---

*Generated from `Respawnables-v2-3-0.ipa` (85 MB) → `Payload/Respawnables.app/Respawnables` (14.2 MB)*  
*Engine: ShooterPunch (Digital Legends), Digital Legends Entertainment 2014+*