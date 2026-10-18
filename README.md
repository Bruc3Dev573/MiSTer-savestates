# MiSTer savestates

Savestates for MiSTer cores that do not have them yet. Unofficial test builds, not MiSTer-devel releases. Report problems in the repository of each core, not on the official repos.

| Core | Latest release | Copy to `_Console` | Modified Main needed |
|---|---|---|---|
| TurboGrafx16 / PC Engine | [v0.2.0-pre2](https://github.com/Bruc3Dev573/TurboGrafx16_MiSTer/releases/tag/v0.2.0-pre2) | `TurboGrafx16_SS_20261011.rbf` | CD games only |
| MegaCD / Sega CD | [v0.1.0-pre6](https://github.com/Bruc3Dev573/MegaCD_MiSTer/releases/tag/v0.1.0-pre6) | `MegaCD_SS_20261018.rbf` | Yes |

## Install

1. Copy the RBF to `_Console` on the SD card and remove older `*_SS_*.rbf` files of the same core. Back up your slots; compatibility between core versions is not guaranteed.
2. Install the modified Main of the core from [the table below](#which-main), either by replacing the official one or, to keep it for every other core, through [`MiSTer.ini`](#use-a-different-main-for-each-core).
3. TurboGrafx16 only: set **MB128** to **Disabled** in the OSD, then reload the core. With MB128 on, Save state and Restore state stay greyed out.

> [!WARNING]
> CD savestates need the modified Main. With the official Main, CD slots are not kept under the disc's name and can overwrite the slots of a HuCard loaded earlier in the same session, and loading a slot from another game can hang the core.

## Controls

| | TurboGrafx16 | MegaCD |
|---|---|---|
| Keyboard | **Alt+F1-F4** save to slot 1-4, **F1-F4** load | same |
| Pad | Hold the button mapped to **Savestates**, then **Down** save, **Up** load, **Left/Right** change slot | Hold **Savestate**, then **Mode+Down** save, **Mode+Up** load, **Left/Right** change slot |
| OSD | Save state and Restore state | same, with a slot selector |
| Notes | Enable **Savestates to SDCard** to keep slots on the SD card. Writing a slot to the SD card can cause a short CD audio gap. | Set the region in the OSD; F1-F3 no longer change it. |

Load a state with the same game or disc, BIOS and region you saved it with. Each release lists its known limits.

## Which Main

The Main is the MiSTer program at the SD root. Each savestate core has its own modified Main. You can replace the official one, keeping a copy (`update_all` and Physical Disc Support updates put the original back), or keep it and [let MiSTer start the modified Main only for that core](#use-a-different-main-for-each-core). If you use both savestate cores, use one Main per core.

| Core | Disc images (`MiSTer`) | Real CD drive with [Physical Disc Support](https://github.com/Anime0t4ku/Main_MiSTer_Physical_Disc) (`MiSTer_Physical-CD`) |
|---|---|---|
| MegaCD | [20261010-megacd-savestates-r4](https://github.com/Bruc3Dev573/Main_MiSTer/releases/tag/20261010-megacd-savestates-r4) | [v2.10.0-megacd-savestates-r4](https://github.com/Bruc3Dev573/Main_MiSTer_Physical_Disc/releases/tag/v2.10.0-megacd-savestates-r4) |
| TurboGrafx16 | [20261010-pcecd-savestates](https://github.com/Bruc3Dev573/Main_MiSTer/releases/tag/20261010-pcecd-savestates) | [v2.10.0-pcecd-savestates](https://github.com/Bruc3Dev573/Main_MiSTer_Physical_Disc/releases/tag/v2.10.0-pcecd-savestates) |

The builds for disc images were tested on MiSTer with the latest cores. The MegaCD build for real drives was run on MiSTer with disc images only, with save and load in Mighty Morphin Power Rangers; no real drive was tried with it. A user tested the TurboGrafx16 changes with a real drive on a September build of Physical Disc Support.

The Mains with both cores in one file, [20261010-savestates-r4](https://github.com/Bruc3Dev573/Main_MiSTer/releases/tag/20261010-savestates-r4) and [v2.10.0-savestates-r4](https://github.com/Bruc3Dev573/Main_MiSTer_Physical_Disc/releases/tag/v2.10.0-savestates-r4), stay online but are no longer updated. Later MegaCD fixes will not be in them.

The MegaCD builds also fix Thunder Storm FX (Japan) and Flashback (see the table below). These two fixes apply to the official MegaCD core too; other cores work as with the official Main. Use r4 with the MegaCD core v0.1.0-pre6: its other fixes need both.

### MegaCD games fixed so far

| Game | What was wrong | Fixed in |
|---|---|---|
| Microcosm | After Start it showed "Document ends" and went back to the intro ([#66](https://github.com/MiSTer-devel/MegaCD_MiSTer/issues/66)) | core v0.1.0-pre2 |
| Mighty Morphin Power Rangers | Starting an episode went black for up to 80 s or skipped it ([#84](https://github.com/MiSTer-devel/MegaCD_MiSTer/issues/84)) | core v0.1.0-pre3 |
| Mighty Morphin Power Rangers | Froze a few seconds after loading a savestate, about once in 130 loads | core v0.1.0-pre5 |
| Ultraverse Prime | Over HDMI the picture sheared for about 2 s every 10 s ([#36](https://github.com/MiSTer-devel/MegaCD_MiSTer/issues/36)) | core v0.1.0-pre3 |
| Thunder Storm FX (Japan) | Froze on the Sega logo ([#111](https://github.com/MiSTer-devel/MegaCD_MiSTer/issues/111)) | Main r2, also with the official core |
| Flashback | With CHD images, hung after the level 2 machine cutscene ([#49](https://github.com/MiSTer-devel/MegaCD_MiSTer/issues/49)) | Main r2, also with the official core |

The other MegaCD fixes are not tied to a known game; each release lists them.

<details>
<summary>What was tested</summary>

- TurboGrafx16 v0.2.0-pre2 with [20261010-pcecd-savestates](https://github.com/Bruc3Dev573/Main_MiSTer/releases/tag/20261010-pcecd-savestates): 50 Sherlock restores, Rondo intro and gameplay save/load with CD audio, and Bonk movement and save/load.
- MegaCD v0.1.0-pre6 with [20261010-megacd-savestates-r4](https://github.com/Bruc3Dev573/Main_MiSTer/releases/tag/20261010-megacd-savestates-r4): krikzz's mcd-verificator, 100 save/load cycles and saves without loading in Power Rangers, save and load in a Crime Patrol mission, slots from earlier versions in Crime Patrol, Flashback and Power Rangers, and ten games without savestates.

These were targeted checks, not the full suite. Details are in each release.

</details>

## Use a different Main for each core

Keep the official Main and let MiSTer start a modified one only for the savestate cores, with the `main=` option of `MiSTer.ini`. This is an [official MiSTer setting](https://github.com/MiSTer-devel/Main_MiSTer/blob/738cb7acc246c830739d02d862c0cc2a275738bb/MiSTer.ini), not part of the savestate builds. MiSTer switches Main when you load a core; the menu and the other cores keep the Main they had.

Power off and back up `MiSTer.ini` before you start. If a section below already exists, add the `main=` line to it instead of a second copy.

### Disc images

1. Download `MiSTer` from each core's release in [the table above](#which-main) and rename it:

   | Core | Rename to |
   |---|---|
   | MegaCD | `MiSTer_MegaCD_SS` |
   | TurboGrafx16 | `MiSTer_PCECD_SS` |

2. Copy the renamed files to the SD root, next to `MiSTer`. Leave `MiSTer` as it is.
3. Add the sections you need to `MiSTer.ini`:

   ```ini
   [MegaCD]
   main=MiSTer_MegaCD_SS

   [TGFX16]
   main=MiSTer_PCECD_SS
   ```

`MegaCD` and `TGFX16` are core names, not file names. The official MegaCD and TurboGrafx16 cores have the same names, so they also start the modified Main. That is fine: other games run as with the official Main, and the MegaCD fixes for Thunder Storm FX and Flashback help the official core too.

### Real CD drive (Physical Disc Support)

Physical Disc Support starts its cores under profile names such as `A0CD-MegaCD` and `A0CD-TurboGrafx16-CD`, and selects its Main with an `[A0CD-*]` section in `MiSTer.ini` ([its guide](https://github.com/Anime0t4ku/Main_MiSTer_Physical_Disc#misterini-configuration)). A section for one profile can name another Main.

1. Download `MiSTer_Physical-CD` from each core's release in [the table above](#which-main) and rename it:

   | Core | Rename to |
   |---|---|
   | MegaCD | `MiSTer_Physical-CD_MegaCD_SS` |
   | TurboGrafx16 | `MiSTer_Physical-CD_PCECD_SS` |

2. Copy the renamed files to the SD root, next to `MiSTer_Physical-CD`. Leave `MiSTer_Physical-CD` as it is.
3. Add these sections to `MiSTer.ini`, **below** the `[A0CD-*]` section that Physical Disc Support added. When several sections match, the last `main=` wins, so a section above `[A0CD-*]` would be overridden.

   ```ini
   [A0CD-MegaCD]
   main=MiSTer_Physical-CD_MegaCD_SS

   [A0CD-TurboGrafx16-CD]
   main=MiSTer_Physical-CD_PCECD_SS
   ```

The other Physical Disc cores keep `MiSTer_Physical-CD`, and Auto Disc Detection works as before: it starts the core, then MiSTer switches to the savestate Main. If the MegaCD MGL in `_Physical Disc Cores` still starts the official core, set its rbf entry to `_Console/MegaCD_SS`. This setup was checked on MiSTer with the profile names and disc images; it was not tried with a real drive.

### Notes

- The names after `main=` must match the files on the card exactly. If a file is missing, MiSTer stays on the Main it is running. To check over SSH, run `ps -eo pid,args` after loading the core and look for that file name.
- Existing `main=` lines in `[MiSTer]`, `[MENU]` or a matching core section can override these.
- To update a modified Main, download it again and rename it the same way.

## Source

| Repository | Upstream | Branches |
|---|---|---|
| [TurboGrafx16_MiSTer](https://github.com/Bruc3Dev573/TurboGrafx16_MiSTer) | [MiSTer-devel/TurboGrafx16_MiSTer](https://github.com/MiSTer-devel/TurboGrafx16_MiSTer) | `savestates` |
| [MegaCD_MiSTer](https://github.com/Bruc3Dev573/MegaCD_MiSTer) | [MiSTer-devel/MegaCD_MiSTer](https://github.com/MiSTer-devel/MegaCD_MiSTer) | `savestates` |
| [Main_MiSTer](https://github.com/Bruc3Dev573/Main_MiSTer) | [MiSTer-devel/Main_MiSTer](https://github.com/MiSTer-devel/Main_MiSTer) | `megacd-savestates`, `pcecd-savestates` (`savestates`, both cores, no longer updated) |
| [Main_MiSTer_Physical_Disc](https://github.com/Bruc3Dev573/Main_MiSTer_Physical_Disc) | [Anime0t4ku/Main_MiSTer_Physical_Disc](https://github.com/Anime0t4ku/Main_MiSTer_Physical_Disc) | `megacd-savestates`, `pcecd-savestates` (`savestates`, both cores, no longer updated) |

## Report a problem

Open an issue in the repository of the core: [TurboGrafx16](https://github.com/Bruc3Dev573/TurboGrafx16_MiSTer/issues) or [MegaCD](https://github.com/Bruc3Dev573/MegaCD_MiSTer/issues). Say which game, HuCard, disc image or real drive, what you did and what happened.
