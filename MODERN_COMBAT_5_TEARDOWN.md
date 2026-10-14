# Modern Combat 5 (PC) — Teardown Documentation

**Game:** Modern Combat 5 (PC port)  
**Platform:** PC (Windows, Steam AppID 921060)  
**Developer:** Gameloft  
**Publisher:** Gameloft  
**Year:** 2017 (PC port; mobile original 2014)  
**Engine:** Gameloft proprietary (verified: `Gameloft` ×5, `com.gameloft.ModernCombat5` in exe)

---

## 1. Game Engine

**Engine:** Gameloft proprietary engine (verified in exe strings)  
- **Middleware (verified via binary/DLL evidence):**
  - **Vivox Voice** (`Vivox` ×96 + `vivoxsdk.dll` 8.3 MB + `ortp.dll` — squad voice for the multiplayer FPS)
  - **Steamworks** (`SteamFriends017`, user-stats interfaces + `steam_api.dll`, AppID 921060)
  - **Chromium/CEF UI** (`libcef.dll` 93 MB + full `.pak` locale set + `CEFHelperProcess.exe` — menus/launcher in Chromium)
  - **OpenSSL** (×36: `libeay32`/`ssleay32` — payment/auth cryptograms, not game crypto)
  - **Ogg container** (`OggS` page headers + `NetStream.Play.*` — streamed media playback)
  - **Vorbis/stb decoder** (`vox::DecoderStbVorbisFactory`, `fmod_codec_oggvorbis.cpp` path strings — Gameloft VOX audio path)
  - **DirectX 11-era** (`d3dcompiler_47.dll`, `GpuCache_D3D11_SM4/SM5`, `swiftshader/` software fallback)
  - **ICU data** (`icudtl.dat` 10 MB — localization)
- **Executable:** `mc5.exe` (24,729,088 bytes) + `.iobj`/`.ipdb` (incremental build artifacts shipped by accident!)
- **Scripting:** None evidenced (`Lua` ×11 = code-byte noise, no Lua API strings)
- **Physics:** Unconfirmed (no Havok/PhysX strings; `Nx` ×165 = opcode noise)

**Falsified:** `Miles` ×3 = event-milestone strings. `fmod` ×4 = CRT math. `Cry` ×32 = payment cryptograms (not CryEngine). No Havok/PhysX/Bink/FMOD/Miles/Unreal/Anvil.

**Evidence from dump:**
- `data/`, `locales/`, `Documents/` dirs; `.cur` cursors, Steam configs

---

## 2. Key Technical Details

- **Mobile-to-PC port anatomy**: Android package ID baked into the PC exe, CEF menus, SwiftShader fallback, Steamworks grafted on
- **Voice-first multiplayer**: Vivox + oRTP beside the game traffic — full FPS comms stack
- Shipped `.iobj`/`.ipdb` build artifacts (unusual leak of the compile pipeline)

---

*Generated from `C:\Users\gmbad\Downloads\teardown\Research\Modern Combat 5\mc5.exe`*  
*Engine: Gameloft proprietary, Gameloft 2017 (AppID 921060)*