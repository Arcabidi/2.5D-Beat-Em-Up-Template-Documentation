# Unit

!!! Summary

    This section summarizes all aspects of the unit system, which is responsible for creating, customizing, and managing the lifetime of in-game units.

## Scripting

All code files below are located at `Assets/_Project/Scripting/Systems/07 - Unit`.

### CSharp

These scripts are not meant to be attached to GameObjects in the scene. Many of them represent static event classes that are meant to be invoked, or are abstract classes representing concepts.

#### Teams

``` mermaid
classDiagram
    class Team{
    }
```

Teams represent groups of allied units. A single team can have both human-controlled and AI-controlled members.

`Team.cs` defines what is common across all teams regardless of game. This includes things like having a team name and having a data structure that manages its members.

#### UnitManagerEvents

``` mermaid
classDiagram
    class UnitManagerEvents{
        <<Static>>
    }
```

`UnitManagerEvents.cs` contains all events related to unit management. This includes things like signaling when human-controlled or AI-controlled units spawn.

### Enums

These scripts contain groups of related constants that are meant to be used by other scripts. All classes in these folders use the `enum` keyword in their declaration.

#### Unit

``` mermaid
classDiagram
    class Unit{
    <<Enum>>
    }
```

`Unit.cs` enumerates all possible units in the template.

### MonoBehaviours

These scripts are meant to be attached to GameObjects in the scene as components and inherit from Unity's [MonoBehaviour](https://docs.unity3d.com/6000.0/Documentation/Manual/class-MonoBehaviour.html) class.

#### TeamManagers

``` mermaid
classDiagram
    class TeamManager{
    }
```

TeamManagers manage the lifetime of teams. This includes things like creating team prefabs and maintaining a data structure that contains the teams.

`TeamManager.cs` represents a basic, general-purpose TeamManager used by our template. This component can be found attached to the TeamManager GameObject in the Training scene.

#### UnitBehaviours

UnitBehaviours are components attached to a unit prefab . The sum of all UnitBehaviours attached to a unit represents the Unit's functionality. 

##### CrowdControlBehaviours

``` mermaid
classDiagram
    class CrowdControlBehaviour{
    }
```

CrowdControlBehaviours describe the behaviour of a unit when it is crowd controlled.

`CrowdControlBehaviour.cs` represents a basic, general-purpose CrowdControlBehaviour used by our template. This component can be found attached to the Human prefab and its Hero and Villain prefab variants. These prefabs are instantiated as children of the HumanPlayerUnitManager and AIPlayerUnitManager GameObjects in the Training scene at runtime.

##### DirectionBehaviours

``` mermaid
classDiagram
    class DirectionBehaviour{
    }
```

DirectionBehaviours describe the behaviour of a unit's direction (the way the unit is facing).

`DirectionBehaviour.cs` represents a basic, general-purpose DirectionBehaviour used by our template. This component can be found attached to the Human prefab and its Hero and Villain prefab variants. These prefabs are instantiated as children of the HumanPlayerUnitManager and AIPlayerUnitManager GameObjects in the Training scene at runtime.

##### HealthBehaviours

``` mermaid
classDiagram
    class HealthBehaviour{
    }
```

HealthBehaviours describe the behaviour of a unit's health.

`HealthBehaviour.cs` represents a basic, general-purpose HealthBehaviour used by our template. This component can be found attached to the Human prefab and its Hero and Villain prefab variants. These prefabs are instantiated as children of the HumanPlayerUnitManager and AIPlayerUnitManager GameObjects in the Training scene at runtime.

##### HurtboxMaskBehaviours

``` mermaid
classDiagram
    class HurtboxMaskBehaviour{
    }
```

HurtboxMaskBehaviours describe the behaviour of a unit's HurtboxMask. HurtboxMasks determine what HurtboxTypes a unit interacts with.

`HurtboxMaskBehaviour.cs` represents a basic, general-purpose HurtboxMaskBehaviour used by our template. This component can be found attached to the Human prefab and its Hero and Villain prefab variants. These prefabs are instantiated as children of the HumanPlayerUnitManager and AIPlayerUnitManager GameObjects in the Training scene at runtime.

##### NameBehaviours

``` mermaid
classDiagram
    class NameBehaviour{
    }
```

NameBehaviours describe the behaviour of a unit's name.

`NameBehaviour.cs` represents a basic, general-purpose NameBehaviour used by our template. This component can be found attached to the Human prefab and its Hero and Villain prefab variants. These prefabs are instantiated as children of the HumanPlayerUnitManager and AIPlayerUnitManager GameObjects in the Training scene at runtime.

##### StatusEffectBehaviours

``` mermaid
classDiagram
    class StatusEffectBehaviour{
    }
```

StatusEffectBehaviours describe the behaviour of a unit when it is affected by status effects.

`StatusEffectBehaviour.cs` represents a basic, general-purpose StatusEffectBehaviour used by our template. This component can be found attached to the Human prefab and its Hero and Villain prefab variants. These prefabs are instantiated as children of the HumanPlayerUnitManager and AIPlayerUnitManager GameObjects in the Training scene at runtime.

#### UnitControllers

``` mermaid
classDiagram
    UnitController <|-- HeroController
    UnitController <|-- VillainController
    class UnitController{
        <<Abstract>>
    }
```

UnitControllers control the logic of specific units.

`UnitController.cs` defines what is common across all UnitControllers, regardless of game. This includes things like setting HurtboxType.

`HeroController.cs` defines behaviour unique to the Hero unit. This includes things like facing the direction the player has their unit move. This component can be found attached to the Hero prefab, which is instantiated as a child of the HumanPlayerUnitManager GameObject in the Training scene at runtime.

`VillainController.cs` defines behaviour unique to the Villain unit. This includes things like determining what to do in response to the attack input action. This component can be found attached to the Villain prefab, which is instantiated as a child of the AIPlayerUnitManager GameObject in the Training scene at runtime.

#### UnitFactories

``` mermaid
classDiagram
    class UnitFactory{
    }
```

UnitFactories load and release addressable unit prefab assets.

`UnitFactory.cs` represents a basic, general-purpose UnitFactory used by our template. This component can be found attached to the UnitFactory GameObject in the Persistent scene.

#### UnitManagers

``` mermaid
classDiagram
    UnitManager <|-- HumanPlayerUnitManager
    UnitManager <|-- AIPlayerUnitManager
    HumanPlayerUnitManager <|-- TrainingHumanPlayerUnitManager
    AIPlayerUnitManager <|-- TrainingAIPlayerUnitManager
    class UnitManager{
        <<Abstract>>
    }
    class HumanPlayerUnitManager{
        <<Abstract>>
    }
    class AIPlayerUnitManager{
        <<Abstract>>
    }
```

UnitManagers are scripts that manage human and AI player units.

`UnitManager.cs` defines what is common across all UnitManagers, regardless of game. This includes things like spawning units.

`HumanPlayerUnitManager.cs` defines what is common across all UnitManagers that manage only humans. This includes things like signaling whenever a human player unit was spawned. 

`AIPlayerUnitManager.cs` defines what is common across all UnitManagers that manage only AI. This includes things like signaling whenever an AI player unit was spawned

`TrainingHumanPlayerUnitManager.cs` manages the lifetime of human player units in the Training scene. This includes signaling a stagae loss once all human player units have been defeated. This component can be found attached to the HumanPlayerUnitManager GameObject in the Training scene.

`TrainingAIPlayerUnitManager.cs` manages the lifetime of AI player units in the Training scene. This includes signaling a stage win once the defeated animation for all AI player units have finished. This component can be found attached to the AIPlayerUnitManager GameObject in the Training scene.

### ScriptableObjects

These scripts contain centralized data that can be conveniently accessed from scenes and assets within a project. All classes in this folder derive from Unity's base ScriptableObject class.

ScriptableObjects are stored on disk and live independently of GameObjects and class instances. They are used as data containers to save large amounts of data, reducing a project’s memory usage by not duplicating values.

#### UnitStats

``` mermaid
classDiagram
    class UnitStats{
    }
```

`UnitStats.cs` represents the innate statistics of a unit. This includes things like name, maximum health, and walk speed.