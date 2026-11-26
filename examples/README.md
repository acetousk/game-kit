# Example games

Two games made with this kit, from the first idea to a release. Each one is its own repo. Open it to see what a kid's game repo looks like after some weeks.

| Game | What it is | What it shows |
|---|---|---|
| [**Stormring**](https://github.com/acetousk/stormring) | A small 3D battle royale on an island. Glide down, find a rifle, build walls, and stay inside the shrinking storm. Solo with 3 bots, or online with up to 4 players. | 3D scenes from simple shapes, a third-person camera, bots that find a path, online rooms, sounds made by a script |
| [**Lantern Deep**](https://github.com/acetousk/lantern-deep) | A 2D turn-based cave crawler. Carry a lantern down 3 floors to grab the Ember Relic. 1–4 players. | Random caves, a field of view in the dark, pixel art made by a script, turn-based co-op online |

## Open one in Godot

1. On the game's GitHub page, click **Code → Download ZIP**. Unzip it.
2. In Godot, click **Import**. Choose the `project.godot` file. Click **Import & Edit**.
3. Press **F5**.

Online rooms in a downloaded copy work only inside Godot (2 windows, local mode). The released builds need their own GD-Sync keys.

## What to read in each repo

| File | What you learn |
|---|---|
| `DESIGN.md` | The kid's design: one sentence, controls, how you win and lose, the palette |
| `PLAN.md` | The cards, one task each, with Input, Output, and "Done when" |
| `PLAYTEST.md` | What players said, and what changed after it |
| `CHANGELOG.md` | What is new in each version |
| `scripts/tune.gd` | Every feel number with a plain name |
| `CREDITS.md` | Where each picture and sound came from |

Try the 4 small jobs in [docs/2-godot-basics.md](../docs/2-godot-basics.md) on one of these games.
