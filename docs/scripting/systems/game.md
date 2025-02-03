# Game

!!! Summary

    This section summarizes all aspects of the game system, which is responsible for changing the game's state and directing its flow.

## Scripting

### CSharp

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

`StageEvents.cs` contains all events related to stage management. For this template we've defined stages as scenes where the main gameplay takes place. For now this is just the Training scene, but the stage designation also includes any future levels. Events in the StageEvent class are invoked whenever you need to signal or direct gameflow on a stage level. This includes things like triggering a loss or a win.

### MonoBehaviours

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

`GameManager.cs` defines functionality common across all GameManagers, regardless of game. This currently includes a boolean representing if the GameManager is currently in debug mode.

`PersistentGameManager.cs` defines game behaviour at the game level. This includes things like determining what to do when the game is reset or exited. This component can be found attached to the GameManager GameObject in the Persistent scene.

`StageGameManager.cs` defines game behaviour at the stage level. For this template we've defined stages as scenes where the main gameplay takes place. For now this is just the Training scene, but the stage designation also includes any future levels. It determines what to do when the game is paused, unpaused, or won. This component can be found attached to the GameManager object in the Training scene.

#### SceneLoaders

``` mermaid
classDiagram
    class SceneLoader{
    }
```

SceneLoaders load and unload scenes.

`SceneLoader.cs` represents a basic, general-purpose SceneLoader used by our example game. This component can be found attached to the SceneLoader GameObject in the Persistent scene.