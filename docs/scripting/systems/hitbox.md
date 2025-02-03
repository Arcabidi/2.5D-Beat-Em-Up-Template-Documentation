# Hitbox

!!! Summary

    This section summarizes all aspects of the hitbox system, which is responsible for transfering data between two bodies on collision.
    
## Scripting

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