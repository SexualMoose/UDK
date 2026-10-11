UDK
===

Prototyping II
----

This repo holds one Unreal Development Kit map, `June_1_Team3_Map.udk`, saved from a "Prototyping II" course team project in June 2013. UDK is Epic's free edition of Unreal Engine 3.

**Status:** archived. The repo has been read-only on GitHub since 2026-10-10. The map has been dormant since it was committed on 2013-06-03, and no further development is planned.

Quickstart
----
1. On Windows, install a UDK build that can load Unreal Engine 3 package version 865. The commit date points to a roughly 2012–2013 build; the exact release is unverified. UE4/UE5 cannot open `.udk` files.
2. Copy `June_1_Team3_Map.udk` into `<UDK-install>\UDKGame\Content\Maps\`.
3. Open the map in the UDK Editor (File → Open) and walk it with Play In Editor.

The map contains only UDK's stock daytime template set (floor, a TexPropCube prop, a sky sphere, dominant directional light, height fog, Lightmass importance volume and a player start, plus the editor builder brush), with baked lighting. No further authored geometry, scripting or custom assets are present. Most of the file is baked lightmap data. For details, licensing and IP notes, see [PROJECT-DOCUMENTATION.md](PROJECT-DOCUMENTATION.md).

License
----
No license has been chosen yet, so all rights are reserved by default. The `.udk` format and the stock engine content it references belong to Epic Games and are governed by Epic's UDK EULA. "Unreal", "UDK" and "Unreal Engine" are Epic Games trademarks, and this repo is not affiliated with Epic.
