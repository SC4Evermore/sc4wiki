---
title: SC4PIM
description: ''
published: true
date: '2026-11-01T08:32:04.456Z'
tags:
  - Tool
  - Custom Tools
editor: markdown
dateCreated: '2008-08-31T11:11:26.000Z'
---

<div class="infobox">
<table>
<tr><th colspan="2">SC4PIM-X</th></tr>
<tr><td><strong>Authors</strong></td><td><a href="/people/wouanagaine">wouanagaine</a> (original), CasperVg (2026 edition)</td></tr>
<tr><td><strong>Download</strong></td><td><a href="https://community.simtropolis.com/files/file/37485-sc4pim-x-2026/">SC4PIM-X 2026 on Simtropolis</a><br><a href="https://www.sc4evermore.com/index.php/downloads/download/29-modding-and-creation-tools/480-sc4pim-x-2026">SC4PIM-X 2026 on SC4Evermore</a><br><a href="https://github.com/caspervg/SC4PIM-X/releases">GitHub releases</a><br><a href="http://sc4devotion.com/csxlex/lex_filedesc.php?lotGET=2260">Original version on the LEX</a></td></tr>
<tr><td><strong>Version</strong></td><td>2026.9.18 (September 2026)</td></tr>
<tr><td><strong>Platforms</strong></td><td>Windows, macOS (Apple Silicon, experimental)</td></tr>
<tr><td><strong>Languages</strong></td><td>English, German, French, Spanish</td></tr>
<tr><td><strong>Source</strong></td><td><a href="https://github.com/caspervg/SC4PIM-X">caspervg/SC4PIM-X</a></td></tr>
<tr><td><strong>Desc</strong></td><td>Replacement for the <a href="/plugin-manager">Plugin Manager</a> and <a href="/lot-editor">Lot Editor</a></td></tr>
</table>
</div>

**SC4PIM-X**, also known as **SC4PIM**, **PIM-X**, **X-PIM** or the **X-Tool**, is a plugin manager and lot editor for [SimCity 4](/simcity-4). It replaces the [Maxis](/maxis) [Plugin Manager](/plugin-manager) and [Lot Editor](/lot-editor). It creates building, prop, flora and foundation exemplars from SC4 models. It also creates and edits growable and ploppable [lots](/lot), manages building and prop families, and lists the dependencies of lots.

[wouanagaine](/people/wouanagaine) created the original tool. It was released on November 6, [2009](/2009), 3 days after [BarbyW](/people/barbyw) released the [PIM-X User Guide](http://sc4devotion.com/csxlex/lex_filedesc.php?lotGET=2257). Since 2026, a community edition called **SC4PIM-X 2026** has continued the development of the tool.

## History

wouanagaine wrote SC4PIM-X in Python 2.4. It was distributed only as compiled bytecode. The source code was later lost, so the original tool could not be maintained.

SC4PIM-X 2026 is an unofficial preservation project. It is not affiliated with EA, Maxis or wouanagaine. wouanagaine never published a license for SC4PIM-X, so all rights to the original work remain with him. The repository is provided as-is, and the maintainers will change or remove it if the rights holder asks.

## SC4PIM-X 2026

SC4PIM-X 2026 keeps the functions of the original tool and adds many new functions.

### Plugin manager

- A new dependency dialog:
  - It lists all files that a lot uses, with filters for missing, found, overridden and ignored files, and for each kind of resource. Unlike the original dialog, it finds all missing resources and does not stop at the first problem. It also knows more resource types, such as SC4Path files, sounds and icons.
  - It uses the [SC4 Prop & Texture Catalog](https://github.com/noah-severyn/SC4PropTextureCatalog) to show where missing dependencies can be found. The program downloads a local copy of the catalog (about 23 MB) and uses the online catalog if the download is not available. The catalog includes entries by Tyberius06.
  - The "Identify packages" function groups the dependencies into the packages that an upload must list.
  - The list can be copied to the clipboard.
- Submenu tools for the Submenus DLL:
  - A Submenu Tree window that shows all submenus and their items. It includes the submenus that other plugins add.
  - Creation of new submenus, with a name, a description, a parent menu, a button ID and an icon.
  - Two ways to put buildings and flora into a submenu: edit their exemplars directly (with optional backups), or create a separate patch file (an Exemplar Patch Targets cohort) that does not change the original files. Both ways work for many items at the same time.
  - Icon templates for submenus, with 12 styles and 9 color presets.
- A conversion wizard that clones a lot and its building, or overrides them, as a different growable or ploppable building type. The lot layout and the building appearance do not change.
- A persistent cache of the plugin files. When the plugins have not changed, the program starts much faster.
- An SC4Path picker. It shows all loaded SC4Path files, with filters for transport type and IID, and with 3D thumbnails that show differences in height.
- Editors for exemplar properties:
  - A response-curve editor.
  - An Occupant Groups picker, with a box for raw hex values.
  - An Occupant Type editor, with a dropdown list and a hex table.
  - A Transit Switch Points editor, with presets and a raw hex mode.
  - A Building Submenus editor.
  - A prop timing editor.
- A "Keep compressed" option in the exemplar property editor.
- Safer recomputation of properties and the Filling Degree. A comparison shows which values will be added, changed or removed. You can select the individual changes before they are applied, so manual values (for example Occupant Groups) are kept.
- Family variations in the inspector.
- Search by file name and by family member name.

### Lot editor

- Undo and redo.
- An asset browser with favorites, sorting, adjustable thumbnail size and hover popups. Assets can be found by name, family member or file name. The browser also shows effects. Animated S3D and ATC models have animated thumbnails.
- Editable position and rotation in the inspector, and a summary of the lot when nothing is selected.
- Toolbar buttons for alignment, rotation, mirroring, edit modes, saving and fitting the view to the lot. The toolbar tooltips show keyboard shortcuts.
- Center alignment of props and flora, horizontally and vertically.
- A Lot Properties dialog to edit the attributes of a lot.
- Layer visibility, and separate land and water modes for tile constraints.
- Configurable grid snapping. Ctrl+click on the snap button sets the grid size.
- A transit mode for transit-enabled lots. The original version had very limited support for these lots. The transit mode includes:
  - Placement and inspection of transit objects, with an overlay that shows them on the lot.
  - Editing of edge directions and edge bytes.
  - Display and selection of [SC4Path](/sc4path-format) files, so a custom path can be assigned to a transit tile.
  - Presets for common stations and transport combinations.
  - Automatic calculation of the transit properties, costs and capacities.
- Behaviour dots on prop and flora thumbnails. They show if a prop is day/night, timed, seasonal or random (chance).
- A preview of props that appear only at certain times, dates or by chance. The preview uses the night hours of the installed plugins, so it also respects mods that change them.
- Separate zoom and rotation controls for the 2D and 3D panes. The 7 and 8 keys zoom in further than in the original tool.

### Rendering

- A modern OpenGL renderer.
- Day and night rendering, with night lighting textures. Both Maxis night and SimFox DarkNite lighting are included as lighting profiles.
- Shadows and environment mapping.
- Emissive materials, and models with more than one state.
- A city context: a generated 3D neighbourhood around the lot, which cannot be edited (Shift+B). The style, density, height, traffic, pedestrians, season and level of detail can be configured.
- A time system with playback controls and loop modes.
- Configurable colors for the 2D overlay and the prop markers.

### Interface

- A dark mode on Windows.
- HiDPI support on Windows.
- New toolbar icons.
- Translations into German, French and Spanish. The language can be selected in the program. Partial translations are possible, because missing text falls back to English.
- The program can remember the main window size and the column widths.
- The location of the SimCity 4 Plugins folder can be configured.
- Plugin files with paths longer than 260 characters can be loaded on Windows.

## Credits

- [wouanagaine](/people/wouanagaine) created the original SC4PIM-X.
- CasperVg made the reconstruction and the 2026 edition.
- Tyberius06 contributed catalog entries, transit presets and knowledge about transit-enabled lots.
- nos.17 provides the SC4 Prop & Texture Catalog that the dependency dialog uses.
- Ulisse Wolf maintains and expands `new_properties.xml`, which SC4PIM-X uses to calculate property values.
- Andreas (German), hugues aroux (French) and nikoxlaux (Spanish) translated the interface.
- TiepiNL contributed long-path support on Windows.

## See Also

- [Plugin Manager](/plugin-manager)
- [Lot Editor](/lot-editor)
- [Lot](/lot)
- [SC4Path Format](/sc4path-format)

## External Links

- [SC4PIM-X 2026](https://community.simtropolis.com/files/file/37485-sc4pim-x-2026/) on Simtropolis
- [SC4PIM-X 2026](https://www.sc4evermore.com/index.php/downloads/download/29-modding-and-creation-tools/480-sc4pim-x-2026) on SC4Evermore
- [caspervg/SC4PIM-X](https://github.com/caspervg/SC4PIM-X) on GitHub
- [Original SC4PIM-X](http://sc4devotion.com/csxlex/lex_filedesc.php?lotGET=2260) on the LEX
- [PIM-X User Guide](http://sc4devotion.com/csxlex/lex_filedesc.php?lotGET=2257) by BarbyW on the LEX

