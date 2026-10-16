---
kind: game
title: "Identifying a cancelled XBLA prototype from its container"
game: "Saints Row: Moneyshot"
games_also: []
game_version: "Unreleased Xbox 360 Arcade prototype, 2011-era (container metadata only; no build distributed with this note)"
platform: console
engine: unknown
route: other
tools: ["Python (one-off container header reader)"]
anti_cheat: "none observed; offline console content with console-side encryption"
status: abandoned
agents: ["OpenCode (Big Pickle)"]
humans: ["GeoffreyMba"]
date: 2026-10-16
links: []
tags: [xbox-360, stfs, prototype, cancelled, container-forensics]
---

# Identifying a cancelled XBLA prototype from its container

> The cancelled Saints Row Xbox Live Arcade spin-off, identified from its content container alone:
> everything the package admits is header metadata (title ID, display name, size) while the payload
> stays encrypted with console content keys. This note records what the container teaches, where the
> analysis deliberately stops, and why no engine claim is made. Nothing was run; no keys, files or
> hashes are included.

## Setup
- **Copy used:** a circulating prototype package of the cancelled XBLA project (2011-era). Per this repo's rule the build itself is left out: no files, links or hashes for fetching it.
- **Tools:** a one-off Python header reader. No extraction tooling, no key material, nothing executed.
- **Shape of the thing:** one large signed container (roughly 608 MB) in the console's standard content-store folder layout.

## Route and why
Route: **other** - container identification, not data editing. Reading the payload would require Xbox 360 content keys; pulling keys and publishing unpacking walkthroughs is out of scope for this repo, so the route stops at metadata by design. Header reading was the entire achievable route here.

## How the game works (what we had to learn)
- Xbox 360 console titles package downloadable/Arcade content in a standard signed container (STFS): a header with a magic marker, title ID, display name and a file table, followed by data blocks.
- This package identifies itself in the header: display name "Saint's Row Moneyshot" and title ID `58410B87`. That header pair - not the folder name - is what attributes the prototype.
- The folder layout is the console's normal content store: a folder named after the title ID, a content-type subfolder below it, then the package file addressed by hash. The layout plus the header name are enough for attribution even while closed.
- The payload blocks are encrypted with the console's content keys, so no assets, strings or executables were readable. That is a hard boundary for static analysis here, not a temporary gap - nothing about the engine, gameplay or middleware can be evidenced from this package.
- Public reporting on the cancelled XBLA spin-off credits Digital Extremes with development for THQ; the package itself cannot confirm that, so the note keeps the engine as `unknown`.

## Build steps (reproduce this pass)
1. Read the container header: magic marker, title ID, display name, size.
2. Compare the folder layout against the console's standard content-store structure.
3. Confirm the payload has no readable blocks before spending time on anything deeper.
4. Stop - further progress needs console key material, which this note deliberately does not carry.

## Verification
- **Verified:** header fields (magic marker, title ID `58410B87`, display name, size around 608 MB) read directly from the package; folder layout matches the standard content store; payload not readable without keys.
- **Not verified:** everything inside - no assets, code or audio were inspected, no engine identification was possible, and nothing was run (an unreleased XBLA prototype has no live service to reach anyway). No mod, and none was possible.

## Gotchas
1. **Symptom.** The container opens but shows no usable files. **Cause:** the payload is encrypted with the console's content keys. **Fix:** treat header metadata as everything you get; do not burn time on block carving.
2. **Symptom.** The folder names are meaningless hashes. **Cause:** the content store addresses packages by hash; identity lives in the header (display name plus title ID). **Fix:** parse the header before trusting or doubting the folder name.
3. **Symptom.** Pressure to name the engine from sibling titles or developer reports. **Cause:** encrypted content proves nothing - attribution from outside the package is hearsay. **Fix:** keep `engine: unknown` until something readable says otherwise.

## Open questions
- Whether the container's unencrypted index (if it has one) lists file names that would hint at contents - not pursued beyond the header.
- Whether community tooling could open it with public key material - deliberately not pursued; this repo does not carry keys or unpacking how-tos.
