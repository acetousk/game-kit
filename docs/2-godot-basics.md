# 2. Godot basics

Read this once before your first game. It takes about 30 minutes with Godot open.
You do not have to remember it all. Claude explains each part again when you use it. Ask `how does X work?` at any time.

## 1. What Godot is

**Godot** is a free game engine. A game engine is a program that does the hard, common jobs of every game for you:

| Job | What the engine does for you |
|---|---|
| Draw | Shows pictures, 3D models, light, and text on the screen, 60 times a second |
| Move | Moves things and stops them when they hit a wall (physics) |
| Listen | Reads the keyboard, mouse, gamepad, and touch screen |
| Play | Plays sounds and music |
| Connect | Sends data between players (with GD-Sync, in this kit) |
| Build | Turns your project into a game file for web, Android, Windows, and Linux |

Your game only has to say **what is special about it**: the rules, the look, and the feel.

Godot has two parts:
- **The editor:** the window where you build and test the game. You use it every day.
- **The engine:** the part that runs the game. It goes inside every build, so your friends do not need Godot.

This kit uses **Godot 4.7.2** and the language **GDScript**. GDScript looks like Python. It is made for games.

## 2. How a Godot game is built

A Godot game is made of 5 kinds of parts.

```
Project ─ the game folder (project.godot)
 └─ Scenes ─ saved pieces of the game (.tscn): a level, the player, a menu
     └─ Nodes ─ the building blocks in a scene, in a tree
         ├─ Scripts ─ code on a node (.gd): what the node does
         └─ Resources ─ data a node uses: pictures, sounds, models, colors
Autoloads ─ scripts that are always running, in every scene
```

### Nodes: the building blocks

A **node** does one job. Godot has hundreds of node types. You put nodes together to make a thing.

| Node type | Its one job | 2D version | 3D version |
|---|---|---|---|
| Body | A thing that moves and hits walls | `CharacterBody2D` | `CharacterBody3D` |
| Shape | The size of the thing for hits | `CollisionShape2D` | `CollisionShape3D` |
| Look | What you see | `Sprite2D` | `MeshInstance3D` |
| Camera | What the screen shows | `Camera2D` | `Camera3D` |
| Wall or floor | A thing that does not move | `StaticBody2D` | `StaticBody3D` |
| Trigger zone | Notices when something goes in | `Area2D` | `Area3D` |
| Sound | Plays a sound | `AudioStreamPlayer` | `AudioStreamPlayer3D` |
| Timer | Waits, then says "time is up" | `Timer` | `Timer` |
| UI | Buttons, labels, health bars | `Control`, `Button`, `Label` | (same) |

### The scene tree: nodes inside nodes

Nodes go **inside** other nodes, like folders. This is the **scene tree**. A child node moves with its parent.

Here is the real player from the example game [Stormring](https://github.com/acetousk/stormring):

```
Player          CharacterBody3D   moves, falls, hits walls   ← player.gd is on this node
├─ Body         kid.tscn          the kid you see (a scene inside a scene)
│  └─ Napkin    napkin.tscn       open while you float down
├─ Shape        CollisionShape3D  the capsule's size for hits
├─ Ghost        MeshInstance3D    the see-through tray wall when you build
└─ CamYaw       Node3D            turns left and right
   └─ CamPitch  Node3D            turns up and down
      └─ SpringArm                pulls the camera in front of walls
         └─ Camera  Camera3D      what your screen shows
```

When the player runs, every child runs with it. The camera stays behind the player, and you do not need any code for that.

### Scenes: pieces you use again

A **scene** is a saved tree of nodes, in a `.tscn` file. A scene can go inside another scene. This is called an **instance**.

In Stormring, `player.tscn` is one scene. `main.tscn` is the lunchroom. When a match starts, the game makes one copy of the player scene for each person and puts it in the lunchroom. Change `player.tscn` once, and every player changes.

```
main.tscn (the lunchroom)
├─ Room, Tables, Props, Sun ...
├─ Players
│  ├─ player.tscn  (you)
│  └─ player.tscn  (a friend)
└─ Bots
   ├─ bot.tscn
   └─ bot.tscn
```

The **main scene** is the first scene that opens when the game starts. In Stormring, it is the start screen, `lobby.tscn`.

### Scripts: what a node does

A **script** is a `.gd` file on a node. It says what the node does. Godot calls some functions in your script by itself:

| Function | When Godot calls it | Example use |
|---|---|---|
| `_ready()` | Once, when the node appears | Set the start health |
| `_process(delta)` | Every frame (about 60 times a second) | Turn a coin |
| `_physics_process(delta)` | Every physics step (60 times a second) | Move the player, add gravity |
| `_input(event)` | When you press a key, click, or touch | Open the pause menu |

`delta` is the time since the last frame, in seconds (about 0.016). Speed × `delta` gives the same speed on a fast PC and a slow phone.

A small example:

```gdscript
extends CharacterBody3D

func _physics_process(delta: float) -> void:
	if not is_on_floor():
		velocity.y -= Tune.gravity * delta   # fall a bit faster each step
	move_and_slide()                         # move, and stop at walls
```

### Signals: a node says "this happened"

A **signal** is a message that a node sends when something happens. Other nodes **connect** to it and react.

| Node | Signal | Means |
|---|---|---|
| `Button` | `pressed` | Someone clicked it |
| `Area3D` | `body_entered` | Something walked into the zone |
| `Timer` | `timeout` | The time is up |
| Your own script | `eliminated` | (Stormring) a fighter is splatted and out of the round |

The real Stormring start screen connects the Host button like this:

```gdscript
$Box/Host.pressed.connect(Net.host_room)   # click Host → make a room
```

Signals keep parts apart. The button does not have to know about rooms. It only says "I was pressed."

### Resources: the data

A **resource** is data that nodes use: a picture (`.png`, `.svg`), a sound (`.wav`), a 3D model (`.glb`), a material (a color and how shiny it is), or a font.
Godot makes a `.import` file next to each one. Leave those files alone, because Godot makes them again.

### Autoloads: always running

An **autoload** is a script that runs from start to end, in every scene. Any script can use it by its name. This kit uses these autoloads:

| Name | What it holds |
|---|---|
| `Tune` | Every feel number: speed, jump height, gravity, damage. Change a number here to change the feel. |
| `Net` | Online rooms: host, join, and who is in the room |
| `Sfx` | Plays sounds |
| `GDSync` | The GD-Sync add-on that sends data between players |

### Paths: `res://` and `user://`

| Path | Means | Who can change it |
|---|---|---|
| `res://` | Your game folder, for example `res://scenes/player.tscn` | You, in the editor. It is read-only in a build. |
| `user://` | A save folder on each player's device | The game, while it runs (saves and settings) |

### One frame, step by step

About 60 times a second, Godot does this:

```
read input ─► _physics_process on every node ─► physics moves bodies ─► _process ─► draw the screen
   ▲                                                                                │
   └────────────────────────────── next frame (about 16 ms) ◄────────────────────────┘
```

If a frame takes too long, the game gets choppy. This is why the kit keeps lights, shadows, and objects few on phones and on the web.

## 3. The editor, part by part

Open the example game: in Godot, click **Import** and choose the `project.godot` file of [Lantern Deep](https://github.com/acetousk/lantern-deep) or Stormring.

```
┌──────────────┬───────────────────────────────────────┬───────────────┐
│ Scene        │  [2D] [3D] [Script] [AssetLib]        │ Inspector     │
│ (the tree of │                                       │ (the settings │
│  the open    │        Viewport                       │  of the node  │
│  scene)      │   (the scene you edit, or the code)   │  you clicked) │
├──────────────┤                                       │               │
│ FileSystem   │                                       │               │
│ (all files,  ├───────────────────────────────────────┤               │
│  res://)     │ Output · Debugger · Audio · Animation │               │
└──────────────┴───────────────────────────────────────┴───────────────┘
```

| Part | What it is for | Try it |
|---|---|---|
| **FileSystem** | All files in the game folder | Double-click `scenes/player.tscn` to open it |
| **Scene** | The node tree of the open scene | Click each node. See its type next to its name. |
| **Viewport** | You see and move things here. The tabs at the top switch between 2D, 3D, and Script. | Click **3D** or **2D**. Hold the right mouse button and use WASD to fly around in 3D. |
| **Inspector** | The settings of the node you clicked | Click the camera node. Find **Fov** and see the number. |
| **Script editor** | The code | Click the scroll icon next to a node to open its script |
| **Output** | Messages and errors while the game runs | Errors are red. Copy the exact red line for Claude. |
| **Debugger** | Errors with the file and line, and the speed (FPS) | Open it when the game crashes |

### Keys you use every day

| Keys | What it does |
|---|---|
| **F5** | Play the game from the main scene |
| **F6** | Play only the open scene |
| **F8** | Stop the game |
| **Ctrl + S** | Save the scene |
| **Ctrl + Shift + F** | Search all files |
| **F3** (after you add play stats) | Show the stats: FPS and the feel numbers |

### While the game runs

- Press F5. In the **Scene** dock, click **Remote**. You see the live tree: each player, bot, and bullet that the game made.
- Click a live node. The Inspector shows its real values right now, for example its position.
- Two windows for online tests: **Debug > Customize Run Instances**, turn on **Enable Multiple Instances**, set it to **2**. Then F5 opens 2 games.

## 4. Try it: 4 small jobs (20 minutes)

Do these in an example game. Nothing here can break your own game. To undo a change, close Godot and click **Don't Save**.

1. **Find the player.** Open the player scene. Name the node that moves and the node you see. Which one has the script?
2. **Change a feel number.** Open `scripts/tune.gd`. In Stormring, change `jump_height` to `3.0`. In Lantern Deep, change `player_hp` to `99`. Save with Ctrl + S. Press F5 and test it. Then set it back.
3. **Read a signal.** Open `scripts/lobby.gd` (Stormring) or `scripts/menu.gd` (Lantern Deep). Find `.connect(`. Which signal does it connect, and what happens when that signal comes?
4. **Make an error on purpose.** In any script, delete one `)`. Look at the red line at the bottom of the script editor. Then press Ctrl + Z.

Now ask Claude about one of them, for example: `how does the jump work?`. Claude reads the real code and explains it.

## 5. Who does what in Godot

| You | Claude |
|---|---|
| Press F5 and play after every step | Writes the scripts and the scenes |
| Click nodes and read the Inspector to see how things work | Explains each node and each line when you ask |
| Change a feel number in `Tune`, or ask for it with the tune loop | Adds the numbers to `Tune` with a plain name and a comment |
| Install GD-Sync from the AssetLib when Claude asks | Writes the online code in `Net` |
| Copy the exact red line from Output when something breaks | Finds the cause and fixes only that |

Claude never edits the export settings. The builds for web, phone, and PC come from `export_presets.cfg` and GitHub, when you say "ship it".

## 6. Learn more (free)

- The official Godot docs: [Getting started](https://docs.godotengine.org/en/stable/getting_started/introduction/index.html) and [Your first 2D game](https://docs.godotengine.org/en/stable/getting_started/first_2d_game/index.html).
- In the editor: hold **Ctrl** and click a node type or a function name in the script editor. The built-in help opens.

Next: [3-make-the-game.md](3-make-the-game.md).
