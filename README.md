# MiSTer savestates

Savestates for MiSTer cores that do not have them yet. These are unofficial test builds, not MiSTer-devel releases. Please report problems in the repository of each core, not on the official repos.

## Cores

| Core | Release | Download | Needs a Main |
|---|---|---|---|
| [TurboGrafx16 / PC Engine](https://github.com/Bruc3Dev573/TurboGrafx16_MiSTer) | [v0.2.0-pre1](https://github.com/Bruc3Dev573/TurboGrafx16_MiSTer/releases/tag/v0.2.0-pre1) | `TurboGrafx16_SS_v0.2.0-pre1.rbf` | CD games only |
| [MegaCD / Sega CD](https://github.com/Bruc3Dev573/MegaCD_MiSTer-savestates) | [v0.1.0-pre1](https://github.com/Bruc3Dev573/MegaCD_MiSTer-savestates/releases/tag/v0.1.0-pre1) | `MegaCD_SS_v0.1.0-pre1.rbf` | Yes |

Copy the RBF to `_Console` on the SD card. Both cores save with Alt+F1-F4 and load with F1-F4. Each release explains the pad controls and the known limits.

## Main

CD savestates need a modified Main. It replaces a file in `/media/fat`, so keep a copy of the original. `update_all` puts the official file back.

| Discs | Core | Main release | Replaces |
|---|---|---|---|
| Images | MegaCD v0.1.0-pre1 | [savestates-20261011](https://github.com/Bruc3Dev573/Main_MiSTer/releases/tag/savestates-20261011) | `MiSTer` |
| Images | TurboGrafx16 v0.2.0-pre1 | [tg16-savestates-v0.2.0-pre1](https://github.com/Bruc3Dev573/Main_MiSTer/releases/tag/tg16-savestates-v0.2.0-pre1) | `MiSTer` |
| Real discs with [Physical Disc Support](https://github.com/Anime0t4ku/Main_MiSTer_Physical_Disc) | MegaCD v0.1.0-pre1 | [savestates-20261011](https://github.com/Bruc3Dev573/Main_MiSTer_Physical_Disc/releases/tag/savestates-20261011) | `MiSTer_Physical-CD` |
| Real discs with Physical Disc Support | TurboGrafx16 v0.2.0-pre1 | [tg16-savestates-physdisc-v0.2.0-pre1](https://github.com/Bruc3Dev573/Main_MiSTer_Physical_Disc/releases/tag/tg16-savestates-physdisc-v0.2.0-pre1) | `MiSTer_Physical-CD` |

The savestates-20261011 Mains also include the TurboGrafx16 CD changes, but they have not been tested with that core yet.

## Source

| Repository | Upstream | Branch |
|---|---|---|
| [TurboGrafx16_MiSTer](https://github.com/Bruc3Dev573/TurboGrafx16_MiSTer) | [MiSTer-devel/TurboGrafx16_MiSTer](https://github.com/MiSTer-devel/TurboGrafx16_MiSTer) | `savestates` |
| [MegaCD_MiSTer-savestates](https://github.com/Bruc3Dev573/MegaCD_MiSTer-savestates) | [MiSTer-devel/MegaCD_MiSTer](https://github.com/MiSTer-devel/MegaCD_MiSTer) | `savestates` |
| [Main_MiSTer](https://github.com/Bruc3Dev573/Main_MiSTer) | [MiSTer-devel/Main_MiSTer](https://github.com/MiSTer-devel/Main_MiSTer) | `savestates` |
| [Main_MiSTer_Physical_Disc](https://github.com/Bruc3Dev573/Main_MiSTer_Physical_Disc) | [Anime0t4ku/Main_MiSTer_Physical_Disc](https://github.com/Anime0t4ku/Main_MiSTer_Physical_Disc) | `savestates` |

## Report a problem

Open an issue in the repository of the core: [TurboGrafx16](https://github.com/Bruc3Dev573/TurboGrafx16_MiSTer/issues) or [MegaCD](https://github.com/Bruc3Dev573/MegaCD_MiSTer-savestates/issues). Say which game, disc image or real drive, what you did and what happened.
