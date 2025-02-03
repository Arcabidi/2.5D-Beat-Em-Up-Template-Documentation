# Hitbox

!!! Summary

    This section summarizes all aspects of the hitbox system, which is responsible for transfering data between two bodies on collision.
    
## Scripting

All code files below are located at `Assets/_Project/Scripting/Systems/11 - Hitbox`.

### Enums

``` mermaid
classDiagram
    class HurtboxMask{
    <<Enum>>
    }
    class HurtboxType{
    <<Enum>>
    }
```

### MonoBehaviours

These scripts are meant to be attached to GameObjects in the scene as components and inherit from Unity's [MonoBehaviour](https://docs.unity3d.com/6000.0/Documentation/Manual/class-MonoBehaviour.html) class.

#### Hitboxes

``` mermaid
classDiagram
    Hitbox <|-- CrossHitbox
    Hitbox <|-- JabHitbox
    class Hitbox{
        <<Abstract>>
    }
```

#### HitDataEditors

``` mermaid
classDiagram
    class HitDataEditor{
    }
```

#### HitResponders

``` mermaid
classDiagram
    class HitResponder{
    }
```

#### Hurtboxes

``` mermaid
classDiagram
    class Hurtbox{
    }
```

#### HurtDataEditors

``` mermaid
classDiagram
    class HurtDataEditor{
    }
```

#### HurtResponders

``` mermaid
classDiagram
    class HurtResponder{
    }
```

### Structs

#### HitPacket

``` mermaid
classDiagram
    class HitPacket{
    <<Struct>>
    }
```