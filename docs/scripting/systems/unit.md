# Unit

!!! Summary

    This section summarizes all aspects of the unit system, which is responsible for creating, customizing, and managing the lifetime of in-game units.

## Scripting

### CSharp

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