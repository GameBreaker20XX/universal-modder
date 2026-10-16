---
kind: game
title: "What an unreleased Halo vertical slice on UE3 tells us"
game: "Mega Halo Game"
games_also: []
game_version: "Xbox 360 vertical slice, 2013-era (unreleased prototype; no build distributed with this note)"
platform: console
engine: unreal
route: data
tools: ["Python (string and header reader)", "7-Zip"]
anti_cheat: "none observed; single-player slice, Xbox Live plumbing only"
status: in-progress
agents: ["OpenCode (Big Pickle)"]
humans: ["GeoffreyMba"]
date: 2026-10-16
links: []
tags: [unreal-engine-3, xbox-360, prototype, halo, wwise, scaleform, facefx, cooked-packages]
---

# What an unreleased Halo vertical slice on UE3 tells us

> A circulating unreleased Halo prototype built on stock UE3: standard base packages plus a full 2010-era
> licensed middleware stack (Wwise, Scaleform, FaceFX, GameWare Navigation, Bink, Xbox Live), cooked
> content split into mission chapters, and full debug symbols for the executable. Static reading only -
> nothing was booted, and per this repo's rule no build files, links or hashes appear below.

## Setup
- **Copy used:** a circulating copy of the unreleased slice (2013-era Xbox 360 build). The build itself is left out per the repo's leaks rule: no files, links or hashes for fetching it. Everything below comes from reading it statically.
- **What came with it:** a disc-layout table, cooked content, executables, profiling artifacts, launch logs and a symbol database for the main executable.
- **Tools:** one-off Python string/header reads and archive listings. Nothing was executed; the symbol database was string-scanned, not loaded in a debugger.

## Route and why
Route: **data** - the durable value is the cooked package layout and middleware map: that is what anyone studying or modding the slice would edit. Hooking or running the executable was considered and skipped - static evidence was enough for this pass, and booting unreleased content was out of scope.

## How the game works (what we had to learn)
- **It is stock UE3 on Xbox 360**, not a forked engine: the cooked content references the standard base packages (Engine, Core, GameFramework, IpDrv and the UT/UDK game bases). Custom game code lives only in the game's own packages.
- **Cooked layout:** content is grouped into mission chapters (`2_1C`, `2_2C`, `2_3C`), each package carrying a purpose suffix (ai, ds, mi, nav, wb, vs, mis). Textures live in external texture caches, there is a cooked global shader cache, and localization sits in a coalesced strings file - all standard UE3 cooked forms, which means standard UE3 tooling applies.
- **Middleware, each confirmed by identifiers inside the content:**
  - **Wwise** audio - over a hundred banks with metadata and voiced lines named after characters and weapons (MasterChief, Grunt, Elite, Jackal, Warthog, Needler, Scorpion...).
  - **Scaleform GFx** for the UI (GFx UI package present).
  - **Autodesk GameWare Navigation** for pathfinding (nav engine package present).
  - **FaceFX** facial animation - its SDK object set appears among the symbol names.
  - **Bink** video for loading/logo/intro movies.
  - **Xbox Live** services plumbing (online subsystem plus a cloud config).
- **Scripting** is UnrealScript bytecode inside the cooked packages.
- **Symbols:** the shipped symbol database names every function (a VS2010 Xenon build), so the code side is fully nameable without guessing.
- **Content:** Forerunner/Covenant/UNSC sets (infantry plus Warthog, Scorpion, Banshee, Wraith), Master Chief voice lines, mission chapters, cinematics and a cheats package - a vertical slice with real missions, not a tech demo.
- **Timeline:** profiling artifacts date the work to mid-2013 (with stray older stamps - clock skew or inherited template data); launch logs inside the copy are stamped 2026, so the slice does still boot somewhere.

## Build steps (reproduce this pass)
1. Start from the disc-layout table - it maps everything else.
2. Group the cooked packages by chapter prefix and purpose suffix; that is the content inventory.
3. String-scan the executable and the symbol database for middleware identifiers (audio, UI, video, nav, online).
4. List the sound banks and their metadata to read the voice/weapon naming.
5. Read the profiling and log artifacts for the build's timeline.

## Verification
- **Verified (static):** engine identity from base package references; every middleware item from concrete identifiers inside the content; package grouping from the file inventory; timeline from profiling/log artifacts; toolchain from executable headers and symbol names.
- **Not verified:** nothing was booted - no emulator or development-hardware run, no assets extracted and re-imported, the symbol database was never loaded into a debugger, and no custom UnrealScript was read. No mod was built.

## Gotchas
1. **Symptom.** Everything looks like an off-the-shelf UE3/UDK build and there is no "Halo engine" to be found. **Cause:** the slice leans on stock base packages plus licensed middleware; the custom game code sits only in the game's own packages. **Fix:** audit the game-specific packages first instead of hunting for proprietary tech in the base ones.
2. **Symptom.** File timestamps disagree about the build's age (stray 2005 stamps in a 2013 build). **Cause:** clock skew or data inherited from templates in the profiling artifacts. **Fix:** trust the profiling-session dates over individual stray stamps.
3. **Symptom.** You assume a console executable is a closed book. **Cause:** a full symbol database shipped with this copy. **Fix:** string-scan the symbol file - it turns "unknown native code" into a named map.
4. **Symptom.** Middleware names make the build look custom-heavy. **Cause:** Wwise/GFx/FaceFX/GwNav/Bink were the standard licensed AAA UE3 stack of the era. **Fix:** treat them as stock components, not as evidence of proprietary engine work.

## Open questions
- How much custom UnrealScript lives in the game packages (not scanned this pass).
- Which UE3 branch/build the slice was cut from.
- Long-term runnability - the copy's launch logs show recent boots, but nothing was launched here.
