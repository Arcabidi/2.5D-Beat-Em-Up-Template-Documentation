# Scenes

!!! Summary

    This page explains how scenes are loaded, unloaded, and transition between each other.

## Flowchart

``` mermaid
flowchart LR
  subgraph Addressable scenes
    direction TB
    subgraph Always Loaded
        direction TB
        Persistent
    end
    subgraph Loaded/Unloaded
        direction LR
        Boot --> Title
        Title --> Training
        Training --> |Lose| Boot
        Training --> |Win| Title
    end
  end
Initialization --> Persistent
Persistent --> Loaded/Unloaded
```

All [scene](https://docs.unity3d.com/Manual/CreatingScenes.html) files are located at `BeatEmUpTemplate/Assets/WorkingInUnity/Scenes`.

| <div style="width:160px" /> Scene Name | Description                          |
| ---------------: | :----------------------------------- |
| `Initialization`            | The only non-Addressable scene in the project and the initial scene in the final build. It is near empty by design to minimize build size since all other scenes can be loaded dynamically as needed. All this scene does is load the Persistent scene before unloading itself. |
| `Persistent`            | This scene persists throughout the lifetime of the game and does not unload until the application exits. It contains all essential GameObjects and scripts that shouldn’t be destroyed between scenes such as the [SceneLoader](systems/game.md#sceneloaders) and [Cursor](systems/ui.md#cursor).<br><br>It allows these core game systems to initialize completely before additively loading one of the following scenes (by default this is the Boot scene, but it can load into any other scene directly for development purposes). |
| `Boot`            | The first scene that has any visual elements. It plays the game’s opening credits while asynchronously loading the Title scene in the background. Once it is 90% loaded the player can either skip the rest of the credits or wait until they finish, after which the Title scene will fully load and the Boot scene will unload. |
| `Title`            | The scene that contains the game’s title along with the main menu. The player can choose to Start The Game after which the Training Scene will load and the Title scene will unload. |
| `Training`            | The scene that contains the core gameplay loop. It is presented in 2.5D, where graphics are in 3D but gameplay is in 2D. The player fights until all enemies are defeated or they are.<br><br>If the player is defeated they will have until a countdown timer expires to attempt to continue. If they fail to continue the Boot scene will load and the Training scene will unload. If they successfully continue the Training scene will reload instead.<br><br>If the enemy is defeated the Title scene will load and the Training scene will unload. |