# Utilities

!!! Summary

    This section outlines the utilitiy scripts used by the 2.5D Beat 'Em Up Template.

## Scripting

### CSharp

#### ActionWrapper

``` mermaid
classDiagram
    class ActionWrapper{
    }
```

#### Constants

``` mermaid
classDiagram
    class Constants{
    }
```

#### StateMachine

``` mermaid
classDiagram
    class StateMachine{
    }
```

### Enums

#### Direction

``` mermaid
classDiagram
    class Direction{
    <<Enum>>
    }
```

### Interfaces

#### ICan

``` mermaid
classDiagram
    class ICanFace{
    <<Interface>>
    }
    class ICanMove{
    <<Interface>>
    }
    class ICanStop{
    <<Interface>>
    }
```

#### IHave

``` mermaid
classDiagram
    class IHaveDamage{
    <<Interface>>
    }
    class IHaveDirection{
    <<Interface>>
    }
    class IHaveFloatingHealthBar{
    <<Interface>>
    }
    class IHaveHitStun{
    <<Interface>>
    }
    class IHaveHurtboxes{
    <<Interface>>
    }
```
``` mermaid
classDiagram
    class IHaveHurtboxMask{
    <<Interface>>
    }
    class IHaveKnockback{
    <<Interface>>
    }
    class IHaveName{
    <<Interface>>
    }
    class IHaveRange{
    <<Interface>>
    }
    IHaveMaximumHealth <|-- IHealth
    class IHaveMaximumHealth{
    <<Interface>>
    }
    class IHealth{
    <<Interface>>
    }
```

#### IRaise

#### IDamageable

``` mermaid
classDiagram
    class IDamageable{
    <<Interface>>
    }
```

#### IDefeatable

``` mermaid
classDiagram
    class IDefeatable{
    <<Interface>>
    }
```

#### IPausable

``` mermaid
classDiagram
    class IPausable{
    <<Interface>>
    }
```

#### IPauseAnimator

``` mermaid
classDiagram
    class IPauseAnimator{
    <<Interface>>
    }
```

### MonoBehaviours

#### CycleSpriteOnEnable

``` mermaid
classDiagram
    class CycleSpriteOnEnable{
    }
```

#### HorizontalDolly

``` mermaid
classDiagram
    class HorizontalDolly{
    }
```

#### Lerp

``` mermaid
classDiagram
    class Lerp{
    }
```

####  LoadSceneOnStart

``` mermaid
classDiagram
    class LoadSceneOnStart{
    }
```

#### MatchScaleXSignWithTransform

``` mermaid
classDiagram
    class MatchScaleXSignWithTransform{
    }
```

### PropertyAttributes

#### ReadOnlyAttribute

``` mermaid
classDiagram
    class ReadOnlyAttribute{
    }
```

#### RenameAttribute

``` mermaid
classDiagram
    class RenameAttribute{
    }
```

### PropertyDrawers

#### ReadOnlyPropertyDrawer

``` mermaid
classDiagram
    class ReadOnlyPropertyDrawer{
    }
```

#### RenamePropertyDrawers

``` mermaid
classDiagram
    class RenamePropertyDrawers{
    }
```