---
kind: game
title: "How CTGP-7 layers custom tracks onto Mario Kart 7"
game: "CTGP-7"
games_also: ["Mario Kart 7"]
game_version: "Public CTGP-7 distribution (free community release), LayeredFS layout"
platform: console
engine: native
route: data
tools: ["7-Zip", "Python (listing reader)"]
anti_cheat: "none; offline LayeredFS mod, no Nintendo Network connection from the mod itself"
status: in-progress
agents: ["OpenCode (Big Pickle)"]
humans: ["GeoffreyMba"]
date: 2026-10-16
links: []
tags: [nintendo-3ds, homebrew, layeredfs, romfs, custom-tracks, mario-kart-7, cfw]
---

# How CTGP-7 layers custom tracks onto Mario Kart 7

> A read of the free CTGP-7 distribution: how a community mod ships new cups, courses and music for Mario
> Kart 7 without touching the game's code - a homebrew launcher CIA plus a `gamefs/` RomFS overlay and a
> `savefs/` save redirect, gated by small version blobs. Read-only, on the mod's own files; the base game is
> neither redistributed nor analysed here.

## Setup
- **Copy used:** the public CTGP-7 distribution - a free community mod, no purchase needed. It ships no base-game data; Mario Kart 7 itself is a separate (owned) game and is not part of this pass.
- **Tools:** 7-Zip for the packages and a one-off Python script to list the structure and read the config blobs. Nothing was launched - no 3DS run, no emulator.
- **What the distribution contains:** a launcher CIA; a `gamefs/` tree of RomFS overrides split into `Course/`, `Missions/`, `Sound/` and `UI/`; a `savefs/` redirect folder; small `config/*.bin` handshake files; and `resources/`, `MyStuff/`, `Photos/` extras.

## Route and why
Route: **data** - the mod works by replacing data files at runtime, so the whole modding surface is the RomFS tree (courses, missions, audio, UI). There is no code patch and nothing to hook, which is also why the mod is removable and survives game updates as long as the file paths hold. Hooking the game executable was considered and skipped: it would break the mod's core advantage and is unnecessary for custom tracks.

## How the game works (what we had to learn)
- **LayeredFS, not patching.** On a modded (CFW) 3DS the launcher starts the game with a layered filesystem: any file present under `gamefs/` shadows the same path in the game's RomFS at runtime. The base game on the SD card is left untouched.
- **What the mod replaces:** course data, mission definitions, sound and UI layouts, in the game's own SARC-style archives. Custom tracks therefore ship as first-party game assets, not as code - which is why no engine modification is needed.
- **A version handshake in `config/`:** small blobs (`version.bin`, `expectedVer.bin`, `launchopt.bin`) carry the launcher's version check and options. The mod refuses a mismatched launcher/base combination instead of failing mid-race.
- **Save data is redirected** (`savefs/`): mod saves live apart from stock saves, so installing or removing the mod does not disturb normal Mario Kart 7 progress.
- **The base engine is Nintendo's own** - Mario Kart 7's in-house engine, built on the 3DS SDK family (CTR SDK). Older write-ups sometimes call this "NitroSDK"; that is the DS SDK and is wrong for a 3DS title. Either way, only the content layer is replaced: no engine code is modified.
- **Online is community-run:** Nintendo's original service is gone, so custom-track online play runs through community servers (per the project's own description). The mod's structure is otherwise entirely local.

## Build steps (reproduce this pass)
1. Unpack the distribution and split it into launcher, `gamefs/`, `savefs/`, `config/` and extras.
2. Walk `gamefs/` - every file there is an override; group them by the game's own folder names (`Course`, `Missions`, `Sound`, `UI`).
3. Read the `config/*.bin` blobs to see the version handshake and options fields.
4. To test a change, add a file under `gamefs/` mirroring its RomFS path and boot the game through the mod's launcher.

## Verification
- **Verified (static):** the distribution's layout - launcher CIA, `gamefs/` overrides grouped by game folder, `savefs/`, `config/` blobs and extras - and that it follows the standard LayeredFS convention; the mod ships no base-game files; the `config/*.bin` handshake files exist as described.
- **Not verified:** the mod was never booted - no 3DS run and no course played. The `config` blobs were treated as opaque binaries (no field map), the game archives inside `gamefs/` were not parsed, and no custom track was repacked or tested. No file was changed.

## Gotchas
1. **Symptom.** Booting the game normally shows only stock tracks. **Cause:** the LayeredFS layer is only active when the game is started through the mod's own launcher (with CFW on). **Fix:** launch via the CTGP-7 CIA, not the home-menu game icon.
2. **Symptom.** The launcher refuses to start after updating the mod or the game. **Cause:** the `config/` version handshake compares launcher and base versions. **Fix:** update launcher and content together; don't mix old config blobs with a newer `gamefs/`.
3. **Symptom.** Progress looks reset after installing. **Cause:** `savefs/` is a deliberately separate save store. **Fix:** expect mod saves to be distinct from stock saves; copy the stock save back if the mod is removed.
4. **Symptom.** Treating this like a normal game teardown and hunting for middleware or DRM. **Cause:** it is a content-layer mod distribution with no real executable beyond the launcher. **Fix:** study the RomFS override set, not the code.

## Assets
None produced - this was a read-only reconnaissance pass over the mod's own files.

## Open questions
- Which SARC/BCRES variants are used inside `gamefs/`, and whether existing retail-tool bootstraps (SARC packers) work on them unmodified.
- The exact field layout of the `config/*.bin` handshake/option blobs.
- Whether the mod tolerates a partial overlay (a single replaced course) - a cheap and useful test.
