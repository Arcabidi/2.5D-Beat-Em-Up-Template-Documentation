# Game

!!! Summary

    This section summarizes all aspects of the game system, which is responsible for changing the game's state and directing its flow.

## Scripting

All code files below are located at `Assets/_Project/Scripting/Systems/01 - Game`.

### CSharp

These scripts are not meant to be attached to GameObjects in the scene. Many of them represent static event classes that are meant to be invoked, or are abstract classes representing concepts.

#### GameEvents

``` mermaid
classDiagram
    class GameEvents{
        <<Static>>
    }
```

`GameEvents.cs` contains all events related to general game management. Events in this class are invoked whenever you need to signal or direct gameflow on the game's highest level. This includes things like pausing, running, resetting, or exiting the game.

#### StageEvents

``` mermaid
classDiagram
    class StageEvents{
        <<Static>>
    }
```

`StageEvents.cs` contains all events related to stage management. Events in the StageEvent class are invoked whenever you need to signal or direct gameflow on a stage level. This includes things like triggering a loss or a win.

!!! Note

    For this template we've defined stages as scenes where the main gameplay takes place. For now this is just the Training scene, but the stage designation also includes any future levels.

### MonoBehaviours

These scripts are meant to be attached to GameObjects in the scene as components and inherit from Unity's [MonoBehaviour](https://docs.unity3d.com/6000.0/Documentation/Manual/class-MonoBehaviour.html) class.

#### GameManagers

``` mermaid
classDiagram
    GameManager <|-- PersistentGameManager
    GameManager <|-- StageGameManager
    class GameManager{
        <<Abstract>>
    }
```

GameManagers control the changing state of the game.

`GameManager.cs` defines functionality common across all GameManagers, regardless of game. This includes a boolean that represents if a GameManager is currently in debug mode.

`PersistentGameManager.cs` defines game behaviour at the game level. This includes things like determining what to do when the game is reset or exited. This component can be found attached to the GameManager GameObject in the Persistent scene.

`StageGameManager.cs` defines game behaviour at the stage level. This includes things like determining what to do when the game is paused, unpaused, or won. This component can be found attached to the GameManager object in the Training scene.

!!! Note

    For this template we've defined stages as scenes where the main gameplay takes place. For now this is just the Training scene, but the stage designation also includes any future levels.

#### SceneLoaders

``` mermaid
classDiagram
    class SceneLoader{
    }
```

SceneLoaders load and unload scenes.

`SceneLoader.cs` represents a basic, general-purpose SceneLoader used by our example game. This component can be found attached to the SceneLoader GameObject in the Persistent scene.