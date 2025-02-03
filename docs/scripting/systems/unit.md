# Unit

!!! Summary

    This section summarizes all aspects of the unit system, which is responsible for creating, customizing, and managing the lifetime of in-game units.

## Scripting

All code files below are located at `Assets/_Project/Scripting/Systems/07 - Unit`.

### CSharp

These scripts are not meant to be attached to GameObjects in the scene. Many of them represent static event classes that are meant to be invoked, or are abstract classes representing concepts.

#### TeamManagerEvents

``` mermaid
classDiagram
    class TeamManagerEvents{
        <<Static>>
    }
```

#### Teams

``` mermaid
classDiagram
    class Team{
    }
```

#### UnitManagerEvents

``` mermaid
classDiagram
    class UnitManagerEvents{
        <<Static>>
    }
```

### Enums

#### Unit

``` mermaid
classDiagram
    class Unit{
    <<Enum>>
    }
```

### MonoBehaviours

These scripts are meant to be attached to GameObjects in the scene as components and inherit from Unity's [MonoBehaviour](https://docs.unity3d.com/6000.0/Documentation/Manual/class-MonoBehaviour.html) class.

#### TeamManagers

``` mermaid
classDiagram
    class TeamManager{
    }
```

#### UnitBehaviours

##### CrowdControlBehaviours

``` mermaid
classDiagram
    class CrowdControlBehaviour{
    }
```

##### DirectionBehaviours

``` mermaid
classDiagram
    class DirectionBehaviour{
    }
```

##### HealthBehaviours

``` mermaid
classDiagram
    class HealthBehaviour{
    }
```

##### HurtboxMaskBehaviours

``` mermaid
classDiagram
    class HurtboxMaskBehaviour{
    }
```

##### NameBehaviours

``` mermaid
classDiagram
    class NameBehaviour{
    }
```

##### StatusEffectBehaviours

``` mermaid
classDiagram
    class StatusEffectBehaviour{
    }
```

#### UnitControllers

``` mermaid
classDiagram
    UnitController <|-- HeroController
    UnitController <|-- VillainController
    class UnitController{
        <<Abstract>>
    }
```

#### UnitFactories

``` mermaid
classDiagram
    class UnitFactory{
    }
```

#### UnitManagers

``` mermaid
classDiagram
    UnitManager <|-- AIPlayerUnitManager
    UnitManager <|-- HumanPlayerUnitManager
    AIPlayerUnitManager <|-- TrainingAIPlayerUnitManager
    HumanPlayerUnitManager <|-- TrainingHumanPlayerUnitManager
    class UnitManager{
        <<Abstract>>
    }
    class AIPlayerUnitManager{
        <<Abstract>>
    }
    class HumanPlayerUnitManager{
        <<Abstract>>
    }
```

### ScriptableObjects

#### UnitStats

``` mermaid
classDiagram
    class UnitStats{
    }
```