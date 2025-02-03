# Action

!!! Summary

    This section summarizes all aspects of the action system, which is responsible for controlling what in-game actions a unit can perform.

## Scripting

### CSharp

#### AbilityData

``` mermaid
classDiagram
    AbilityData <|-- CrossAbilityData
    AbilityData <|-- JabAbilityData
    class AbilityData{
        <<Abstract>>
    }
```

### MonoBehaviours

#### Abilities

``` mermaid
classDiagram
    Ability <|-- Cross
    Ability <|-- Jab
    Ability <|-- BeltScrollMove
    BeltScrollMove <|-- ExampleBeltScrollMove
    class Ability{
        <<Abstract>>
    }
    class BeltScrollMove{
        <<Abstract>>
    }
```

#### AbilityResponders

``` mermaid
classDiagram
    class AbilityResponder{
    }
```

#### UnitActionManagers

``` mermaid
classDiagram
    class UnitActionManager{
    }
```

### ScriptableObjects

#### UnitActions

``` mermaid
classDiagram
    UnitAction <|-- CrossUnitAction
    UnitAction <|-- JabUnitAction
    UnitAction <|-- BeltScrollMoveUnitAction
    BeltScrollMoveUnitAction <|-- ExampleBeltScrollMoveUnitAction
    class UnitAction{
        <<Abstract>>
    }
    class BeltScrollMoveUnitAction{
        <<Abstract>>
    }
```

### Structs

#### AbilityDataPacket

``` mermaid
classDiagram
    class AbilityDataPacket{
    <<Struct>>
    }
```