# Action

!!! Summary

    This section summarizes all aspects of the action system, which is responsible for controlling what in-game actions a unit can perform.

## Scripting

All code files below are located at `Assets/_Project/Scripting/Systems/09 - Action`.

### CSharp

These scripts are not meant to be attached to GameObjects in the scene. Many of them represent static event classes that are meant to be invoked, or are abstract classes representing concepts.

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

These scripts are meant to be attached to GameObjects in the scene as components and inherit from Unity's [MonoBehaviour](https://docs.unity3d.com/6000.0/Documentation/Manual/class-MonoBehaviour.html) class.

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