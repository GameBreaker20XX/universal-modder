---
kind: game
title: "Inside a cancelled beta client: archives, tiers, middleware"
game: "Triad Wars"
games_also: ["Sleeping Dogs"]
game_version: "Closed beta client, files dated Dec 2015 - Jan 2016 (service shut down before launch; no build distributed with this note)"
platform: windows
engine: native
route: data
tools: ["7-Zip", "Python (listing and string reader)"]
anti_cheat: "none found in the listing; the service was shut down before release"
status: in-progress
agents: ["OpenCode (Big Pickle)"]
humans: ["GeoffreyMba"]
date: 2026-10-16
links: []
tags: [pc, cancelled, sleeping-dogs, big-archives, wwise, nvidia-gameworks, solid-archive]
---

# Inside a cancelled beta client: archives, tiers, middleware

> What a field listing of the closed-beta client for the cancelled Sleeping Dogs-universe free-to-play
> game shows: 125 index/archive pairs in HD and SD tiers, Wwise audio, NVIDIA GameWorks effects, and an
> outer archive that defeated a full extraction. Static listing only - the service is dead, nothing was
> run, and per this repo's rule no build files, links or hashes appear below.

## Setup
- **Copy used:** a circulating archive of the closed-beta client (files dated Dec 2015 - Jan 2016; the beta shut down in 2016 and the game never launched). Per this repo's leaks rule the build is left out: no files, links or hashes for fetching it.
- **Tools:** 7-Zip for listing and extraction attempts, a one-off Python script for listing metadata and string reads. Nothing was executed.
- **Known state:** the archive was listed but never fully extracted (solid compression - see Gotchas).

## Route and why
Route: **data** - the client is a pile of data archives, so any modding or study begins by opening them. Patching or hooking the executable was considered and skipped: there is nothing to run against (the service is gone), which makes archive-level knowledge the durable part of the work.

## How the game works (what we had to learn)
- The client is 64-bit Windows: the game executable sits beside a texture-build tool (TextureScriber), i.e. content pipeline leftovers shipped in the client folder.
- Content sits in **125 `.big` archives, each paired with a `.bix` index** - the archive family United Front Games used for Sleeping Dogs, so prior Sleeping Dogs tooling is the obvious starting point (verify compatibility first - see Gotchas).
- The archive set is split into **HD and SD tiers** (`GameHD*` vs `GameSD*`, with HD/SD character sets too): one client shipped both scalability levels, so a mod has to target the tier matching the settings it is meant to show up in.
- Audio is in **Wwise** sound banks (`.pck`).
- The DLLs in the client root pin the rest of the middleware: **NVIDIA GameWorks** depth-of-field and HBAO+ ambient occlusion SDKs, the **DirectX** shader compiler, and **libcurl with OpenSSL** for online services.
- Shaders ship precompiled as a permanent + temp pair (about 47 MB together).
- Client configuration is plain files (display settings, key bindings, autosave folder) - readable without opening any archive.
- Physics and UI/video middleware were never established: the outer archive was never fully extracted, so nothing inside a `.big` or the executable itself was scanned.

## Build steps (reproduce this pass)
1. List the archive - record pair count, tiers and sizes before extracting anything.
2. Read the plain config files (display settings, key bindings) - cheapest facts first.
3. Extract the solid archive in one pass (this step was never finished here).
4. Once extracted: string-scan the executable and open one `.big`/`.bix` pair to confirm the Sleeping Dogs-era format match.

## Verification
- **Verified (from the listing and plain files):** 125 `.big`/`.bix` pairs and their names; the HD/SD tier split; Wwise banks; the GameWorks / DirectX / curl DLLs; the precompiled shader pair; config file names; the outer archive's compression method.
- **Not verified:** the archive contents - extraction never completed, so no file inside a `.big` was opened and the executable was never string-scanned. Physics (Havok?) and video/UI middleware (Bink/Scaleform?) remain guesses at most and are written as such. Nothing was launched, since the service is gone regardless. No mod was built.

## Gotchas
1. **Symptom.** The multi-gigabyte archive takes forever to open and tools cannot jump to a single file inside. **Cause:** it is solid compression with an executable filter - one long compressed stream with no random access. **Fix:** extract the whole thing in one pass and index the results afterwards; budget time for the full run (the one here was never finished).
2. **Symptom.** The same content appears twice (`GameHD*` and `GameSD*`). **Cause:** the client shipped both scalability tiers in one install. **Fix:** decide which tier your settings use and modify only that one, or the change will not appear where you expect.
3. **Symptom.** Sleeping Dogs archive tools error out on the beta's pairs. **Cause:** same format family does not guarantee identical headers or index layout across projects and years. **Fix:** validate a tool on one known pair before batch-processing all 125.
4. **Symptom.** Dead service, so the client looks worthless to study. **Cause:** the archive-level formats are the lineage of a shipped, moddable game. **Fix:** treat it as an extra data set for Sleeping Dogs tooling rather than a standalone title.

## Open questions
- Whether the extraction completes cleanly, and what the `.big` header actually looks like in this build.
- Whether retail Sleeping Dogs tools read the pairs unmodified.
- Physics, video and UI middleware - settled only by extracting the archive and string-scanning the executable.
