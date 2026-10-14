# Head2Head (PC) — Teardown Documentation

**Game:** Head2Head (project `BoltGame`)  
**Platform:** PC (Windows 64-bit)  
**Developer:** Unknown  
**Publisher:** Unknown  
**Engine:** **Unreal Engine 4.27** (verified)

---

## 1. Game Engine

**Engine:** **Unreal Engine 4.27** (verified: identical UE4.27 ThirdParty set + PhysX3/no-Chaos/no-Oodle fingerprint as the Cyber Clutch build family)  
- **Middleware (verified via binary/DLL evidence):**
  - **BoltFramework + GGPO** (`F:\UE4 Work\Head2Head\Plugins\BoltFramework\Source\BoltFramework\GGPO\...` — rollback netcode, p2p backend; the project's namesake)
  - **Epic Online Services** (`EOSSDK-Win64-Shipping.dll`)
  - **PhysX 3** + APEX/NvCloth + Chaos Cloth strings (UE4.27 coexistence set)
  - **Ogg/Vorbis** + **XAudio2_9**, **NVIDIA Aftermath**, **GeForceNOW SDK**, **OpenImageDenoise**, **TBB**
- **Executables:** `Head2Head.exe` (bootstrap) + `BoltGame/Binaries/Win64/BoltGame-Win64-Shipping.exe` (79 MB)
- **Container:** `pakchunk0(-optional)-WindowsNoEditor.pak`
- **Scripting:** None (C++/Blueprints)

**Falsified:** `Steam` ×7 = Steam Controller touch-input strings (engine input layer, not Steamworks — no `steam_api` in dump). `Crypto` = OpenSSL cipher tables. No FMOD/Wwise/Denuvo.

---

## 2. Key Technical Details

- **Rollback-netcode versus game** (GGPO p2p backend in a first-party plugin — fighting/versus design confirmed at source-path level)
- Same UE4.27 build family as Cyber Clutch (identical ThirdParty tree down to VS2015 DLLs)

---

*Generated from `C:\Users\gmbad\Downloads\teardown\Research\Head2Head\`*  
*Engine: Unreal Engine 4.27 + BoltFramework/GGPO, Unknown Developer*