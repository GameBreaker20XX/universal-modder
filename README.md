# Game Engine Reverse Engineering Research

This repository contains reverse engineering research and documentation for various game engines and titles, focusing on proprietary engines with zero or minimal licensed middleware.

## 📚 Documentation Index

| Game | Platform | Engine | Year | Middleware | Status |
|---|---|---|---|---|---|
| [Pursuit Force](TRACKMANIA_DS_TEARDOWN.md) | PSP | Bigbig `Game03` | 2005 | None | ✅ Complete |
| [Pursuit Force: Extreme Justice](PURSUIT_FORCE_EJ_TEARDOWN.md) | PSP | Bigbig `Game03` | 2007 | None | ✅ Complete |
| [MotorStorm: Arctic Edge (PSP)](MOTORSTORM_ARCTIC_EDGE_PSP_TEARDOWN.md) | PSP | Bigbig `Game03` | 2009 | None | ✅ Complete |
| [MotorStorm: Arctic Edge (PS2)](MOTORSTORM_ARCTIC_EDGE_PSP_TEARDOWN.md#motorstorm-arctic-edge-ps2---ps2-2009) | PS2 | Bigbig `Game03` (Virtuos port) | 2009 | CRI, ODE (names only) | ✅ Complete |
| [TrackMania DS](TRACKMANIA_DS_TEARDOWN.md) | NDS | Firebrand Games (Octane) | 2009 | None | ✅ Complete |
| [TrackMania Turbo DS](TRACKMANIA_TURBO_DS_TEARDOWN.md) | NDS | Firebrand Games (Octane) | 2010 | None | ✅ Complete |
| [Metal Gear Rising Revengeance](MGRR_TEARDOWN.md) | PC/PS3/X360 | PlatinumGames | 2013 | Havok + Wwise | ✅ Complete |

## 🏗️ Engine Lineages

### Bigbig Studios `Game03` Engine (2005–2009)
```
Pursuit Force 1 (PSP, 2005)          → PAK v2 (`02 PAK`)
Pursuit Force: Extreme Justice (2007) → PAK v2, AdHoc multiplayer
MotorStorm: Arctic Edge PSP (2009)    → PAK (`PAK `), same engine
MotorStorm: Arctic Edge PS2 (2009)    → Virtuos port, same PAK format
```
**Key finding:** 100% proprietary, zero licensed middleware across all 4 titles.

### Firebrand Games NDS Engine (Octane Lineage, 2009–2010)
```
TrackMania DS (2009)         → 32 MB ROM, ZIP (26 MB, 3457 files)
TrackMania Turbo DS (2010)   → 64 MB ROM, ZIP (27 MB, 4258 files)
```
Browse [`knowledge/INDEX.md`](knowledge/INDEX.md). Every game is welcome. Contribution rules, for humans and
AIs, are in [`CONTRIBUTING.md`](CONTRIBUTING.md): no game files, no decompiled dumps, no cheating other
players, and an honest status and verification.

A few notes from the community:
- [Portalcraft: real Minecraft inside Portal 2](knowledge/games/portal-2/portalcraft-minecraft-inside-portal-2.md)
- [Halo 3 weapons, Covenant, vehicles and maps ported into Minecraft](knowledge/games/halo-3-mcc/halo-3-weapons-covenant-vehicles-and-maps-ported-into-minecr.md)
- [Bloons TD 6 inside Minecraft, with the game's rules as a headless sim](knowledge/games/minecraft/bloons-td-6-in-minecraft.md)
- [A CS2-style conversion of Elden Ring offline, as a native Rust DLL](knowledge/games/elden-ring/cs2-conversion-of-elden-ring-offline-native-rust-dll-via-me3.md)

## What's inside

**Skills** (`skills/`, Agent Skills format)

<table>
  <thead><tr><th width="200">Skill</th><th>What it does</th></tr></thead>
  <tbody>
    <tr><td><a href="skills/mod-any-game"><code>mod-any-game</code></a></td><td>The whole loop, hard safety rules, and <b>engine playbooks</b>: Unity, Unreal, .NET/XNA (Terraria, Stardew, Celeste), Godot, Source 1/2, Bethesda, Minecraft, AoE2/Genie, Bannerlord, RE Engine/MT Framework/FromSoft/GTA/Hedgehog Engine/Black Rock/Cyberpunk/BG3, native C++, indie engines (GameMaker, RPG Maker, Ren'Py, Paradox, Doom, HTML5, LÖVE, Java), retro decomps</td></tr>
    <tr><td><a href="skills/game-recon"><code>game-recon</code></a></td><td>Prior field notes, engine and version, managed or native, anti-cheat, loaders, save folders, community route → <code>MODDING_PLAN.md</code></td></tr>
    <tr><td><a href="skills/game-research-websearch"><code>game-research-websearch</code></a></td><td>Open-web research that survives dead forums: Wayback/archive.today, GitHub/code and Nexus/Workshop/Thunderstore APIs, Reddit/YouTube, login-gated handoff, screenshots as evidence</td></tr>
    <tr><td><a href="skills/reverse-engineering"><code>reverse-engineering</code></a></td><td>ILSpy / Cpp2IL / Vineflower / Ghidra and IDA over MCP / Cheat Engine / Frida / RenderDoc; reverse-engineer a file format and prove it with a round trip</td></tr>
    <tr><td><a href="skills/fal-assets"><code>fal-assets</code></a></td><td>Sprites with real transparency, consistent variants, pixel art, seamless textures, PBR maps, image-to-3D, auto-rigging, SFX, music, voice, cutscene video</td></tr>
    <tr><td><a href="skills/asset-pipeline"><code>asset-pipeline</code></a></td><td>Art → engine-exact frames: cutout, nearest-neighbour fit, palettes, sheets, team-colour masks, 3D → 8/16-heading sprites</td></tr>
    <tr><td><a href="skills/game-automation"><code>game-automation</code></a></td><td>Launch, screenshot (GPU-safe), click/type safely, windowed mode, crash-reporter cleanup, in-game agent bridges</td></tr>
    <tr><td><a href="skills/showcase-video"><code>showcase-video</code></a></td><td>Record the window with only the game's audio, pick moments, cut a styled video from an EDL</td></tr>
    <tr><td><a href="skills/mashup-mods"><code>mashup-mods</code></a></td><td>Game inside a game: content ports, passthrough mods (worked example: Minecraft × GTA V), decomps as libraries, reimplementations</td></tr>
    <tr><td><a href="skills/publish-mod"><code>publish-mod</code></a></td><td>Lint, package per platform, credits, the post</td></tr>
    <tr><td><a href="skills/port-a-mod"><code>port-a-mod</code></a></td><td>Port an existing mod to a newer version or loader without drift: one pinned source, a private decompile, data extracted by script, unit-by-unit tests, audits by layer, resumable status docs, and a Forge 1.7.10 → Fabric 1.20.1 mapping table</td></tr>
    <tr><td><a href="skills/share-field-notes"><code>share-field-notes</code></a></td><td>Search the knowledge base, write your own note, open the PR</td></tr>
  </tbody>
</table>

**The `um` CLI** (Python). Every command has `--help` with examples.

<!-- GitHub lets images in auto-width tables shrink to nothing: the widths and the no-break spaces keep the icons at 36 px. -->
<table>
  <thead><tr><th width="62">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</th><th width="170">Command</th><th>What it does</th></tr></thead>
  <tbody>
    <tr><td align="center"><picture><source media="(prefers-color-scheme: dark)" srcset="docs/media/icons/scan-dark.svg"><img src="docs/media/icons/scan-light.svg" width="36" height="36" alt=""></picture></td><td><code>um scan</code></td><td>Find Steam/Epic/Xbox installs; fingerprint engine and version, .NET vs native, anti-cheat, installed loaders, save folders, ranked routes</td></tr>
    <tr><td align="center"><picture><source media="(prefers-color-scheme: dark)" srcset="docs/media/icons/fal-dark.svg"><img src="docs/media/icons/fal-light.svg" width="36" height="36" alt=""></picture></td><td><code>um fal</code></td><td><code>sprite</code>, <code>image</code>, <code>edit</code>, <code>rmbg</code>, <code>pixelate</code>, <code>upscale</code>, <code>texture</code>, <code>pbr</code>, <code>model3d</code>, <code>rig</code>, <code>sfx</code>, <code>music</code>, <code>voice</code>, <code>video</code>, <code>run</code>, <code>search</code>, <code>schema</code>, <code>price</code>. Plain REST, with a manifest of every generation</td></tr>
    <tr><td align="center"><picture><source media="(prefers-color-scheme: dark)" srcset="docs/media/icons/comfy-dark.svg"><img src="docs/media/icons/comfy-light.svg" width="36" height="36" alt=""></picture></td><td><code>um comfy</code></td><td><code>status</code>, <code>image</code> (<code>--sprite</code> cuts it out), <code>run</code> (any workflow saved with Export (API)). Images from a local ComfyUI server, no API key</td></tr>
    <tr><td align="center"><picture><source media="(prefers-color-scheme: dark)" srcset="docs/media/icons/sprite-dark.svg"><img src="docs/media/icons/sprite-light.svg" width="36" height="36" alt=""></picture></td><td><code>um sprite</code></td><td><code>cutout</code>, <code>fit</code>, <code>pixelate</code>, <code>palette</code>, <code>sheet</code>, <code>slice</code>, <code>frames</code>, <code>team-mask</code>, <code>seamless</code>, <code>preview</code></td></tr>
    <tr><td align="center"><picture><source media="(prefers-color-scheme: dark)" srcset="docs/media/icons/render3d-dark.svg"><img src="docs/media/icons/render3d-light.svg" width="36" height="36" alt=""></picture></td><td><code>um render3d</code></td><td>GLB → sprite frames from the game's camera (<code>aoe2</code>, <code>iso8</code>, <code>trueiso</code>, <code>topdown</code>, <code>side</code>, <code>turntable</code>) with Blender</td></tr>
    <tr><td align="center"><picture><source media="(prefers-color-scheme: dark)" srcset="docs/media/icons/win-dark.svg"><img src="docs/media/icons/win-light.svg" width="36" height="36" alt=""></picture></td><td><code>um win</code></td><td><code>shot</code>, <code>record</code> (gfxcapture + process-loopback audio), <code>drive</code> (input that only reaches the game), <code>ps</code>, <code>kill</code>, <code>launch</code>, <code>reg</code></td></tr>
    <tr><td align="center"><picture><source media="(prefers-color-scheme: dark)" srcset="docs/media/icons/video-dark.svg"><img src="docs/media/icons/video-light.svg" width="36" height="36" alt=""></picture></td><td><code>um video</code></td><td><code>contact</code> sheets, <code>compile</code> (EDL → titled, beat-cut video with music), <code>mux</code>, <code>beats</code>, <code>first-frame</code></td></tr>
    <tr><td align="center"><picture><source media="(prefers-color-scheme: dark)" srcset="docs/media/icons/backup-dark.svg"><img src="docs/media/icons/backup-light.svg" width="36" height="36" alt=""></picture></td><td><code>um backup</code></td><td>Snapshot, diff and restore save folders</td></tr>
    <tr><td align="center"><picture><source media="(prefers-color-scheme: dark)" srcset="docs/media/icons/publish-dark.svg"><img src="docs/media/icons/publish-light.svg" width="36" height="36" alt=""></picture></td><td><code>um publish check</code></td><td>Blocks shipping game files, decompiled code and leaked keys</td></tr>
    <tr><td align="center"><picture><source media="(prefers-color-scheme: dark)" srcset="docs/media/icons/kb-dark.svg"><img src="docs/media/icons/kb-light.svg" width="36" height="36" alt=""></picture></td><td><code>um kb</code></td><td>The knowledge base: <code>search</code>, <code>show</code>, <code>new</code>, <code>check</code>, <code>index</code>, <code>sync</code>, <code>pr</code></td></tr>
  </tbody>
</table>

Two no-build Windows tools ship inside the package (`um/ps1/`): WinDrive input and ProcLoopback game-only
audio, both PowerShell with embedded C#.

<p align="center"><img src="docs/media/pipeline.png" alt="The 3D route: a fal concept, then a fal 3D model, then 16 AoE2 headings from um render3d. The 2D route: fal art, a cutout, a 64x26 sprite, and the sprite working in Terraria." width="100%"></p>

## Built with it
- **[examples/terraria-tmodloader](examples/terraria-tmodloader)**: *Fal Arsenal* for tModLoader.
  - Weapons: a homing missile launcher, a tactical nuke (crater + mushroom cloud), a chain-lightning rifle, a
    black-hole gun and an orbital strike.
  - Three new enemies and a two-phase Drone Mothership boss.
  - Every sprite came from fal.
- **[examples/aoe2-de-civ](examples/aoe2-de-civ)**: *San Franciscans* for Age of Empires II DE.
  - A new civilization with a Robotaxi unique unit and Delivery Drones, rendered from fal image-to-3D models
    at AoE2's camera angle.
  - A Transamerica Pyramid wonder.
  - A reverse-engineered `.sld` sprite writer.
- **[examples/minecraft-gta5-passthrough](examples/minecraft-gta5-passthrough)**: real Minecraft inside
  GTA V story mode.
  - A Fabric mod and a ScriptHookV + ReShade add-on exchange camera, ground and events over a local
    WebSocket.
  - Minecraft's colour + depth are depth-composited into GTA's frame.
  - Minecraft TNT, arrows and fireworks become GTA explosions and bullets, and Minecraft mobs fight the
    police.

Each has a field note with every non-obvious lesson: [knowledge/INDEX.md](knowledge/INDEX.md).

## Rules it follows
- **Any game you own: single-player, multiplayer, or servers you host.** It refuses to inject into online
  games with anti-cheat, write cheats against other players, or bypass anti-cheat, DRM or ownership checks.
- **It never ships game files or decompiled code.** Mods ship as code, your own assets, patches or
  converters.
- **It backs up before touching saves**, and kills processes by PID only.
- **It asks before** driving your mouse and keyboard, installing loaders into game folders, or publishing,
  PRs included.

Full reasoning: [`skills/mod-any-game/references/safety.md`](skills/mod-any-game/references/safety.md).

## Made a mod with it?
Show it off in the [Discord](https://discord.com/invite/sEZWaf7vV), and put the badge on your mod's page:

<p>
  <a href="https://github.com/rehan-remade/universal-modder"><picture><source media="(prefers-color-scheme: dark)" srcset="docs/media/made-with-dark.svg"><img src="docs/media/made-with-light.svg" height="32" alt="made with universal-modder"></picture></a>
</p>

```markdown
[![made with universal-modder](https://raw.githubusercontent.com/rehan-remade/universal-modder/main/docs/media/made-with-dark.svg)](https://github.com/rehan-remade/universal-modder)
```
**Key finding:** Firebrand Games proprietary NDS engine with Octane engine lineage. Zero licensed middleware across both titles.

### PlatinumGames Engine (Separate Lineage)
```
Metal Gear Rising Revengeance (2013) → Havok + Wwise, FBX/HKX/DDS/BNK
```
**Key finding:** Only title in this set using licensed middleware (Havok physics, Wwise audio).

## 📁 Documentation Files

| File | Description |
|------|-------------|
| `GAMES_KNOWLEDGE_BASE.md` | Consolidated knowledge base for all 7+ games |
| `PURSUIT_FORCE_TEARDOWN.md` | Pursuit Force 1 teardown |
| `PURSUIT_FORCE_EJ_TEARDOWN.md` | Extreme Justice teardown |
| `MOTORSTORM_ARCTIC_EDGE_PSP_TEARDOWN.md` | MotorStorm Arctic Edge (PSP) teardown |
| `TRACKMANIA_DS_TEARDOWN.md` | TrackMania DS teardown |
| `TRACKMANIA_TURBO_DS_TEARDOWN.md` | TrackMania Turbo DS teardown |
| `MGRR_TEARDOWN.md` | Metal Gear Rising Revengeance teardown |

## 🔍 Key Findings Summary

| Engine Family | Games | Middleware | Key Insight |
|---|---|---|---|
| Bigbig `Game03` | 4 games | **None** | Pure Sony PSP/PS2 SDK + custom formats |
| Firebrand NDS | 2 games | **None** | Pure Nintendo NitroSDK + Lua scripting |
| PlatinumGames | 1 game | Havok + Wwise | Only title with licensed middleware |

## 🛠️ Common Tools Used

| Tool | Purpose |
|------|---------|
| `psmfdump.exe` | PMF video demux (PSP) |
| `dattool.exe` | `.dat` archive extraction (NDS) |
| `unluac` / `luadec` | Lua bytecode decompilation |
| `ffmpeg` | Video/audio conversion |
| `py7zr` / `7z` | 7z archive extraction |
| Custom Python scripts | ROM parsing, PAK/ZIP extraction, format analysis |

## 📦 Archive Formats Discovered

| Game | Container | Format |
|------|-----------|--------|
| Pursuit Force 1/Extreme Justice | PAK v2 | `02 PAK` magic, 16-byte index entries |
| MotorStorm Arctic Edge (PSP) | PAK | `PAK ` magic, 24-byte linked-list entries |
| MotorStorm Arctic Edge (PS2) | PAK | Same as PSP version |
| TrackMania DS | ZIP | Standard ZIP at 0x645C00 (26 MB) |
| TrackMania Turbo DS | ZIP | Standard ZIP at 0x873200 (27 MB) |

## 🎮 File Formats Catalog

| Extension | Game(s) | Description |
|---|---|---|
| `.pspptx` / `.PSP_PTX_MAIN` | Pursuit Force, MotorStorm PSP | PSP texture (swizzled, paletted) |
| `.pspp3d` / `.pspl3d` | Pursuit Force | 3D models |
| `.psppve` | Pursuit Force | Vehicle models |
| `.pspppprt` | Pursuit Force | Particle systems |
| `.chpsp` / `.anp` | Pursuit Force | Characters / animations |
| `.nsbmd` / `.n` | TrackMania DS / Turbo DS | NSBMD 3D models (BMD0 magic) |
| `.hzc` / `.h` | TrackMania DS / Turbo DS | Hit zone collision |
| `.dcsc` | TrackMania DS / Turbo DS | Scene collision |
| `.luac` | TrackMania DS / Turbo DS | Lua 5.1 bytecode |
| `.hzc` / `.h` | TrackMania | Hit zone collision |
| `.sdat` | All NDS games | Nintendo DS audio (SDAT) |
| `.at3` / `.vib/.vdb` | PSP games | ATRAC3 audio / VIB+VDB audio |

## 🔧 Tools Developed

Custom Python scripts for:
- NDS ROM parsing (FAT/FNT extraction)
- PAK container parsing (PSP/PS2)
- ZIP archive extraction from ROM offsets
- File format identification (magic bytes, structure analysis)
- ARM9/ARM7 binary analysis (string extraction, engine detection)

---

## 📝 License & Usage

This research is for educational and preservation purposes only. All game assets, binaries, and code remain the property of their respective owners (Sony, Atari, Nintendo, Konami, PlatinumGames, Firebrand Games, Bigbig Studios).

**Do not** use this research to:
- Bypass DRM or anti-cheat systems
- Create cheats for online multiplayer
- Redistribute game assets or binaries
- Violate EULA terms

This research is intended for:
- Game preservation and documentation
- Engine architecture education
- Modding framework development (offline/single-player only)
- Historical documentation of game engine evolution

---

*Research conducted 2026. All analysis performed on legally obtained game dumps owned by the researcher.*