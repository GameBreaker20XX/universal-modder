# Ghost Recon Phantoms (PC) — Teardown Documentation

**Game:** Tom Clancy's Ghost Recon Phantoms (F2P, shut down Dec 2016)  
**Platform:** PC (Windows, Steam AppID 243870)  
**Developer:** Ubisoft Singapore (Yeti engine via `C:\Build\GRO\live-dev\Yeti\` build path; GRO = Ghost Recon Online, the original title)  
**Publisher:** Ubisoft  
**Year:** 2014 (client: `Nightly-live-dev` build 369518→369879)  
**Engine:** Ubisoft Yeti Engine (verified)

---

## 1. Game Engine

**Engine:** Ubisoft Yeti Engine (verified: `C:\Build\GRO\live-dev\Yeti\engine\bin\vs2008\Client\GhostReconPhantoms_UserFacing.pdb` PDB path in exe)  
- **Middleware (verified via binary/DLL evidence):**
  - **Bink Video** (`_BinkSetSoundTrack@8` + `binkw32.dll`)
  - **Awesomium** (web UI, `awesomium.dll` 20 MB)
  - **FFmpeg** (`avcodec/avformat/avutil/swscale/swresample` DLLs + `avcodec` strings)
  - **Vivox Voice** (`vivoxsdk.dll` 7 MB + `vivoxoal.dll` + `oRTP` stack: `ortp.dll`)
  - **Steamworks** (`SteamAPI_Init` + `steam_api.dll`, AppID 243870)
  - **DirectX 9** (`D3DX`; VS2008 toolchain; `YetiShadersPC2.sat/.sdf`, 5.4 MB `shaderlistPC.txt`)
  - **ICU + OpenSSL stack** (`icudt.dll` 10 MB, `ca-bundle.crt`, `libsndfile`, `FreeImage`, `DDSCompress`, `glut32`)
- **Executable:** `Game\NCSA-Live\GhostReconPhantoms.exe` (20.6 MB)
- **Container:** `Yeti.big` (**2.77 GB**) + `Yeti.bigmap` (4.5 MB index)
- **Configs:** `Yeti.ini.enc` (encrypted!), `YetiCaps*.cap`, `GraphicPresets/Settings.ini`, `Sound.ini`, `KeyMappingsPC*.ini`
- **Crash reporting:** `BloombergReports/` (Ubisoft Bloomberg crash pipeline)
- **Physics:** Unconfirmed (no Havok/PhysX strings; `Nx` ×426 = opcode noise)

**Falsified:** `GFx` ×2 = opcode noise (no Scaleform). `Miles`/FMOD/Wwise/Quazal/CryEngine ×0.

**Evidence from dump:**
- .NET Ubisoft launcher layer (`Launcher.exe` + 20 Ubisoft.*.dll: StorageService, Update, Localization, WCF/IPC) + torrent stack (`MonoTorrent.dll`, `Mono.Nat.dll`) + reporters/metrics DLLs
- `Sound_Bin_PC/`, `video/`, `Shaders/`, `Language/`, `DLC/`, `DXRedist/`, `Resources/`
- `version.txt`: `Nightly-live-dev-Enc-GRO-369518.2-to-Nightly-live-dev-Enc-GRO-369879.2` (live-service nightly channel)

---

## 2. Key Technical Details

- **Yeti.big single-archive layout** (2.77 GB + external index) with encrypted main ini — F2P anti-datamine posture
- **Voice-first middleware**: Vivox + oRTP + FFmpeg + Awesomium = full live-service communication/UI stack around the Yeti core
- Nightly live-dev versioning evidences continuous-delivery F2P ops (2014–2016)

---

*Generated from `.../Tom Clancy's Ghost Recon Phantoms NA/Game/NCSA-Live/GhostReconPhantoms.exe`*  
*Engine: Ubisoft Yeti Engine, Ubisoft Singapore 2014*