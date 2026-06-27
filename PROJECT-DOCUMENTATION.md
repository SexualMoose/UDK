# UDK — Prototyping II Game Level

A single Unreal Development Kit (UDK / Unreal Engine 3) map file committed for a college "Prototyping II" course (Team 3, June 2013).

## Overview / Purpose
This repository stores one binary game level (`June_1_Team3_Map.udk`) authored in Epic Games' Unreal Development Kit. It appears to be a class deliverable / level-design prototype rather than a software project. The repo exists to version/back up the map file; there is no source code, build pipeline, or runnable application in the repo itself.

## Status
Abandoned / archival. Evidence:
- Last and only meaningful activity is from 2013-06-03 (~13 years old as of this audit).
- Only 2 commits total: `253bbbf Initial commit` and `dcaac9a Added map to repo`.
- Working tree is clean; nothing unpushed; single `master` branch.
- README is a 4-line stub ("UDK" / "Prototyping II"). No further development is implied.

## Technical Requirements
- **Tool:** Unreal Development Kit (UDK), the free edition of Unreal Engine 3. The package header reports Unreal Engine package version **865**, which corresponds to a 2012–2013-era UDK build (the era matching the 2013 commit). To open/edit/cook the map you need a UDK install of a compatible version; newer Unreal Engine 4/5 cannot open `.udk` packages.
- **OS:** Windows (UDK is Windows-only).
- **Hardware:** A desktop GPU capable of running the UDK editor; no special hardware otherwise.
- **Accounts/keys:** None required to open the file. (Historically, shipping a UDK title required agreeing to Epic's UDK EULA, but nothing in this repo invokes that.)

## Dependencies
- No package-manager dependencies (no `build.gradle`, `package.json`, `requirements.txt`, `Podfile`, `platformio.ini`, `CMakeLists.txt`, etc.).
- The map references **stock UDK engine content** by name only (e.g. `EngineMaterials`, `EditorMeshes`, `DefaultMaterial`, `Engine_MI_Shaders`, `DominantDirectionalLight`, `LightmassImportanceVolume`, `StaticMeshActor`). These are assets shipped inside UDK itself, not separate third-party libraries with their own licenses. No purchased/marketplace asset packs were detected in the strings.

## Setup Instructions
1. On a Windows machine, install a 2012–2013-era Unreal Development Kit (UDK) build (engine package version 865 or compatible).
2. Clone this repo:
   ```
   gh repo clone SexualMoose/UDK
   ```
3. Copy `June_1_Team3_Map.udk` into your UDK content directory, conventionally:
   ```
   <UDK-install>\UDKGame\Content\Maps\
   ```

## Build & Run
- **Open in editor:** Launch the UDK Editor (`UDK.exe editor`) and use File → Open to load `June_1_Team3_Map.udk`, or double-click the file from within the editor content browser.
- **Play:** Use "Play In Editor" (PIE) inside the UDK Editor to walk the level.
- **Cook/package:** From the UDK Frontend you can cook the map for a standalone build; this requires the full UDK toolchain and is outside what this repo provides.
- There is **no automated build** (no Makefile/CI). The artifact is the map file itself.

## Usage
Open the map in UDK and inspect/play the level. It is a level-design prototype; gameplay behavior depends on whatever GameInfo the UDK install defaults to.

## Architecture
- Single Unreal Engine 3 binary package (`.udk`).
- Internally it is a standard UE3 map: a `LevelInfo`/`WorldInfo`, lighting actors (a `DominantDirectionalLight`, Lightmass importance volume), static-mesh actors, and material/lightmap/shadowmap texture data baked into the package. There is no scripting (UnrealScript) source in the repo — only the cooked/editor map package.
- **Data flow:** none at the repo level; the file is consumed entirely by the UDK editor/runtime.

## Integrations & Interconnects
- **Epic Games Unreal Development Kit / Unreal Engine 3** — the only external system. The file is meaningless outside a UDK install.
- No network services, APIs, cloud, sibling repos, or hardware integrations.

## Configuration & Secrets
- None. No `.env`, config files, keys, tokens, or credentials are present or required. A string scan of the binary found no secrets, no embedded file paths, and no usernames/emails.

## Testing
- No tests, and none are applicable (binary art asset). Validation would be manual: open in UDK and verify the level loads, lighting builds, and plays.

## Known Issues / TODO
- README is a near-empty stub; it does not describe the map, controls, or how to open it.
- No `.gitignore` (not strictly needed here, but absent).
- No LICENSE file.
- A 3.9 MB binary is committed directly to git history with no Git LFS; acceptable at this size but worth noting if more map revisions were ever added.

## Third-party & Licensing notes
- **No LICENSE file** in the repo — default "all rights reserved" applies to the author's original level-design work.
- The **`.udk` file format and the referenced engine asset names are Epic Games' proprietary Unreal Engine 3 / UDK technology.** The map cannot be opened, used, or redistributed independently of Epic's UDK, which is governed by Epic's UDK EULA. The level *content* (geometry/layout) authored by the team is the team's, but it is inseparable from Epic's engine format/assets.
- **Trademark sensitivity:** "Unreal", "UDK", and "Unreal Engine" are Epic Games trademarks. The repo name "UDK" and the file's dependence on Epic's format reference Epic's product. This is descriptive use (a UDK map), not a claim of affiliation, so risk is low — but a clean-room reimplementation is not meaningful here, since the deliverable *is* an Epic-format asset.
- The map was authored by a multi-person student team ("Team3"). If reused, co-author/IP attribution among the team and the school's coursework-ownership policy could apply.

## Security notes
- No secrets, credentials, keys, tokens, or PII found in the working tree or in the (2-commit) history.
- No code, so no injection / eval / TLS / WebView / permission issues are possible.
- Only residual concern is generic: opening untrusted binary game-engine packages in an editor always carries some parser-exploit risk, but this file is the author's own and benign.
- Overall: clean.
