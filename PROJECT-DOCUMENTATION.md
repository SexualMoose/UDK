# UDK — Project Documentation

One Unreal Development Kit (UDK / Unreal Engine 3) map file, `June_1_Team3_Map.udk`, kept from a 2013 "Prototyping II" course team project.

_Last audited: 2026-10-11 against master @ 098b88e._

## Overview / Purpose
This repository stores one binary game level, `June_1_Team3_Map.udk` (4,121,464 bytes, ~3.9 MiB), saved in the package format of Epic Games' Unreal Development Kit. The README names it "Prototyping II", and the filename points to Team 3 and June 1. The school or institution is not recorded in the repo. It is a class deliverable / level prototype, not a software project. The repo only versions and backs up the map file. There is no source code, build pipeline or runnable application in it.

## Status
**Archived (read-only on GitHub since 2026-10-10) because it is dormant.** Evidence:
- The repo was created and the map committed on 2013-06-03 (`253bbbf` Initial commit added the README; `dcaac9a` Added map to repo) and has not changed since.
- The only later commit is `098b88e` (2026-06-27), which added generated documentation. There are 3 commits in total.
- There is a single branch (`master`), no tags and no other remote branches.
- No further development is planned. Because the repo is archived, documentation edits like this one can only be pushed if the repo is unarchived.

## Technical Requirements
- **Tool:** Unreal Development Kit (UDK), the free edition of Unreal Engine 3. Package header facts:
  - File (package) version **865**, licensee version 0
  - Engine build field 10499
  - Cooker version 0
  - No compression
  - "contains map" package flag set

  To open the map you need a UDK release that can load package version 865. The commit date points to a roughly 2012–2013 UDK build. The exact UDK release is unverified. Unreal Engine 4/5 cannot open UE3 `.udk` packages.
- **OS:** Windows. The UDK editor is a Windows application.
- **Hardware:** a desktop GPU that can run the UDK editor. Nothing else is needed.
- **Accounts/keys:** none are needed to open the file. Using or shipping anything built with UDK falls under Epic's UDK EULA. Nothing in this repo invokes it.

## Dependencies
- There are no package-manager or build dependencies. The repo has no `build.gradle`, `package.json`, `requirements.txt`, `Podfile`, `platformio.ini`, `CMakeLists.txt` or similar files.
- The map's import table references only **stock UDK packages**:
  - `Engine`
  - `EngineMaterials` (`DefaultMaterial`)
  - `EditorMeshes` (`TexPropCube`)
  - `Engine_MI_Shaders` (`M_ES_Phong_Opaque_Master_01`, `T_Normal`, `T_Reflection`)
  - `MapTemplates` (`SM_Template_Map_Floor`, `Sky.SM_SkySphere`, `Sky.M_Procedural_Sky_Daytime`, `lut.LUT_Daytime`)

  These ship inside UDK itself. They are Epic content under the UDK EULA, not separately licensed libraries. The map references them by name and does not copy them into the file. No purchased, marketplace or custom asset packages are referenced.

## Setup Instructions
1. On a Windows machine, install a UDK build that can load Unreal Engine 3 package version 865 (see Technical Requirements).
2. Clone this repo. Archived repos can still be cloned.
   ```
   gh repo clone SexualMoose/UDK
   ```
3. Copy `June_1_Team3_Map.udk` into your UDK content directory. By standard UDK convention (not defined by this repo) that is:
   ```
   <UDK-install>\UDKGame\Content\Maps\
   ```

## Build & Run
These steps follow the standard UDK workflow. They are not scripted or verifiable from this repo.
- **Open in editor:** start the UDK Editor (`UDK.exe editor` from the UDK install's binaries folder, or the UDK Editor shortcut). Use File → Open to load `June_1_Team3_Map.udk`.
- **Play:** use Play In Editor (PIE) inside the UDK Editor to walk the level.
- **Rebuild lighting:** Build → Build Lighting. The file already contains baked lightmaps and shadowmaps.
- **Cook/package:** to make a standalone build, cook the map with UDK's Unreal Frontend. This needs the full UDK toolchain and is outside what this repo provides.
- There is **no automated build**: no Makefile, scripts or CI. The deliverable is the map file itself.

## Usage
Open the map in UDK, inspect it, and play it with PIE. The map does not override the game type, so gameplay uses the UDK install's default GameInfo. The level content is minimal (see Architecture).

## Architecture
- The repo holds one **uncooked, uncompressed** Unreal Engine 3 map package (`.udk`): cooker version 0, with the "cooked" package flag clear.
- The package has 182 names, 51 imports and 36 exports. Its contents:
  - `World` / `PersistentLevel` with a `WorldInfo`, whose lighting quality is set to Production and whose post-process settings use the stock `MapTemplates.lut.LUT_Daytime` colour-grading LUT.
  - Lighting and atmosphere: a `DominantDirectionalLight`, an `ExponentialHeightFog` and a `LightmassImportanceVolume`.
  - Two `StaticMeshActor`s: the stock `MapTemplates.SM_Template_Map_Floor` floor and one `EditorMeshes.TexPropCube` prop cube, both using `Engine_MI_Shaders.M_ES_Phong_Opaque_Master_01`.
  - One `PlayerStart`.
  - One `InterpActor`, the sky dome: `MapTemplates.Sky.SM_SkySphere` at DrawScale 100 with the `M_Procedural_Sky_Daytime` material.
  - The editor's default builder brush (`Brush_0` + Model `Brush` + `Polys_1`, present in every UE3 level) and one editor `BookMark`. The level BSP (`Model_0`/`Polys_20`) is empty, so there is no authored CSG geometry.
  - Baked `LightMapTexture2D` / `ShadowMapTexture2D` data. This is about 4.09 MB, roughly 99% of the file.
- The map has no Kismet sequences, no Matinee data, no custom meshes, materials or textures, and no UnrealScript. The map contains only stock UDK content matching UDK's daytime new-map template (floor, a TexPropCube prop, a sky sphere, dominant directional light, height fog, Lightmass importance volume and a player start, plus the editor builder brush), with baked lighting. No further authored geometry, scripting or custom assets are present.
- **Data flow:** none at the repo level. The UDK editor and runtime consume the file directly.

## Integrations & Interconnects
- **Epic Games Unreal Development Kit / Unreal Engine 3** is the only external system. The file cannot be used outside a UDK install.
- There are no network services, APIs, cloud services or hardware integrations. It does not connect to any other repo in the portfolio or to the self-hosted fleet server, and has no self-update or self-report.

## Configuration & Secrets
- None. The repo has no `.env` or config files, and no keys, tokens or credentials are present or needed.
- The binary's name table contains only engine class, property and enum names, stock asset/package names and auto-generated object names. A string scan found no embedded file paths, usernames or emails.

## Testing
- There are no tests and none apply, because the repo holds a binary art asset with no code and no CI (`.github/` is absent).
- Validation is manual: open the map in UDK, check that it loads, rebuild lighting, and play it in PIE.

## Known Issues / TODO
- There is no LICENSE file (see Third-party & Licensing notes).
- There is no `.gitignore`. It is not strictly needed for a single-asset repo.
- The ~3.9 MiB binary is committed directly to git without Git LFS. That is acceptable at this size (it compresses to well under 1 MiB in the git pack), but it would matter if more map revisions were added.
- Getting a compatible UDK build today may be difficult (unverified).
- `PROJECT-DOCUMENTATION.docx` is the Word companion of this file, but it is currently **stale**: it still holds the earlier version ("Abandoned / archival", "2 commits", README called a stub). Regenerate it from this file before committing the doc updates.

## Third-party & Licensing notes
- **No license has been chosen yet** (there is no LICENSE file), so all rights are reserved by default. Before choosing one, consider the two points below.
- **Epic Games IP:** the `.udk` package format and the stock engine content the map references (Engine, EngineMaterials, EditorMeshes, Engine_MI_Shaders, MapTemplates) are Epic Games' proprietary Unreal Engine 3 / UDK technology. They are governed by Epic's UDK EULA. The map cannot be opened, used or redistributed apart from UDK. No Epic assets are embedded in the file, only references to them. So there is no vendored third-party content and no NOTICE file is needed.
- **Multi-author coursework:** the filename and README point to a team course project. Any reuse or relicensing may need agreement from the co-authors, and may be subject to the institution's coursework-ownership policy.
- **Trademark in identity:** "Unreal", "UDK" and "Unreal Engine" are Epic Games trademarks, and the repo name is "UDK". This is descriptive use (it is a UDK map) with no claim of affiliation, so the risk is low.
- No copyleft (GPL/LGPL/MPL/AGPL) components are present.

## Security notes
- **Trust boundary / auth model:** none. The repo holds a static binary asset with no code, no network access and no authentication.
- **Secrets:** none are needed and none are stored, in either the working tree or the git history.
- **Risk categories (high level):** loading binary packages into legacy, unmaintained editor software is a generic risk. The file is the author's own.
