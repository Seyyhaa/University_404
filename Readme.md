# University 404

A first-person horror exploration game developed by **Team 404** for the Game Development Final Project, SE G3 Gen10. Explore a repeating university hallway, watch for anomalies, and choose the correct direction to escape.

## How to play

1. Study the normal hallway so you can recognize changes in later rounds.
2. If the hallway is normal, continue forward.
3. If you notice an anomaly, turn around and leave through the entrance.
4. Make **11 correct choices in a row** to reach the ending. A wrong choice resets your streak to zero and returns you to the normal hallway.

The exit sign displays your current streak. The game includes 17 anomaly hallway scenes. After a correct choice, the next hallway has a 75% chance of being an anomaly and a 25% chance of being normal. Anomaly scenes are drawn without repeats until the available pool is exhausted or a wrong choice resets it.

## Controls

| Input | Action |
| --- | --- |
| W / A / S / D or arrow keys | Move |
| Mouse | Look around |
| Left Shift | Run |
| E | Open or close an interactable door while looking at it within range |

## Play the Windows build

If the included build folder is available in your checkout, open [`University_404_v1.0.0`](University_404_v1.0.0/) and run `Final Project Team_404.exe`. Keep the executable alongside its data folder, `MonoBleedingEdge`, and Unity runtime files.

A gameplay demonstration is included as [`University_404_version1.0.0_Demo.mp4`](University_404_version1.0.0_Demo.mp4).

## Open in Unity

- **Unity Editor:** 2022.3.47f1
- **Language:** C#
- **Main packages:** Cinemachine 2.10.5, TextMesh Pro 3.0.7, Unity UI 1.0.0, and ProBuilder 5.2.4

1. Clone or download this repository.
2. Install Unity 2022.3.47f1 through Unity Hub. Include Windows Build Support if you plan to create a Windows player.
3. In Unity Hub, add the repository root as an existing project. Select the folder containing `Assets`, `Packages`, and `ProjectSettings`.
4. Open the project and let Unity import the assets and restore its packages.
5. Open [`Assets/Scenes/MenuScene.unity`](Assets/Scenes/MenuScene.unity), enter Play mode, and select **Start**.

Start from `MenuScene` for the intended menu flow. Its Start button loads `Hallway_Normal`, which initializes the loop manager.

## Build the game

1. In Unity, open **File > Build Settings**.
2. Select **PC, Mac & Linux Standalone** and choose Windows as the target platform. Switch platform if needed.
3. Keep `MenuScene` first in Scenes In Build, with `Hallway_Normal`, all 17 numbered hallway scenes, and `WinScene` enabled. These scenes are already configured in the project's build settings.
4. Select **Build** or **Build And Run** and choose an output folder.

`MainScene` is present in the project but disabled in the current build settings.

## Project structure

| Path | Contents |
| --- | --- |
| `Assets/Scenes/` | Main menu, normal hallway, 17 anomaly hallways, ending, and additional MainScene |
| `Assets/Scripts/` | Player movement, interactions, hallway rules, scene transitions, and audio |
| `Assets/Animation/` | Animation assets |
| `Assets/Characters(player)/` | Player character assets |
| `Assets/Sound/` | Game audio |
| `Assets/UISceneResources/` | UI resources |
| `Assets/Asset_Used_From_Asset_Store/` | Imported environment, prop, and character assets |
| `Assets/Plugins/` | Editor plugins, including Asset Usage Detector |
| `Packages/` | Unity package manifest and dependency lock file |
| `ProjectSettings/` | Unity version, input mappings, player settings, and build scene list |

## Core scripts

- `PlayerController.cs`: first-person movement, mouse look, running, and door interaction.
- `LoopManager.cs`: persistent streak tracking, random hallway selection, exit sign updates, and the win transition.
- `RoomIdentity.cs`: determines whether moving forward or backward is correct for the current hallway.
- `ExitTrigger.cs`: checks the player's choice when they enter an exit trigger.
- `DoorScript.cs`: defines `DoorInteract`, which toggles door animations.
- `SceneController.cs`: menu scene loading and application exit.
- `CreditsTrigger.cs`: displays the ending credits and returns to the menu.
- `FootstepSystem.cs`, `SoundController.cs`, and `DoorControllerSound.cs`: audio behavior.

The current gameplay target is configured as `targetStreak: 11` on the loop manager in `Hallway_Normal`, overriding the default value in the script. To add an anomaly, create a hallway scene, configure its `RoomIdentity`, add it to the loop manager's anomaly list, and enable it in Build Settings.

## Credits and assets

Developed by **Team 404** for the **Game Development Final Project, SE G3 Gen10**. The in-game credits thank **Dr. Hongly VA**.

The project uses third-party assets and plugins. Refer to their included documentation and applicable licenses before reusing or redistributing them.
