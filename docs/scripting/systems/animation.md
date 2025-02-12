# Animation

!!! Summary

    This section summarizes all aspects of the animation system, which is responsible for bringing GameObjects in the scene to life.

## Design decisions

This template makes the following design decisions regarding the default way Unity handles animation:

### Animation system

This project uses Unity's built-in animation system, known as the [Mecanim Animation system](https://docs.unity3d.com/Manual/AnimationOverview.html), to bring its in-game units to life.

## Animation

All non-code files below are located at `Assets/_Project/Animation`.

### MecanimAnimation

#### AnimationClips

#### AnimatorControllers

AnimatorControllers are state machines that decide what AnimationClip to play. They are referenced by a unit's Animator component. 

## Scripting

All code files below are located at `Assets/_Project/Scripting/Systems/08 - Animation`.

### StateMachineBehaviours

#### BoolClearedBy

``` mermaid
classDiagram
    class BoolClearedByIPauseAnimatorUnpauseAnimator{
    }
```

#### BoolSetBy

``` mermaid
classDiagram
    class BoolSetByAbility{
    }
    class BoolSetByIDamageableDamaged{
    }
    class BoolSetByIDamageableDamagedBack{
    }
```
``` mermaid
classDiagram
    class BoolSetByIDefeatableDefeated{
    }
    class BoolSetByIDefeatableDefeatedBack{
    }
    class BoolSetByIPauseAnimatorPauseAnimator{
    }
```
``` mermaid
classDiagram
    class BoolSetByIRaiseMoveExecutedMovement{
    }
    class BoolSetByIRaiseMoveExecutedNoMovement{
    }
    class BoolSetByIRaiseMoveExecutedNonPositiveYMovement{
    }
```
``` mermaid
classDiagram
    class BoolSetByIRaiseMoveExecutedPositiveYMovement{
    }
    class BoolSetByIRaiseWonWon{
    }
```

#### BoolSetOn

``` mermaid
classDiagram
    class BoolSetOnAnimationFinished{
    }
    class BoolSetOnStateExited{
    }
```

#### BoolsSetBy

``` mermaid
classDiagram
    class BoolsSetByIRaiseMoveExecutedNoMovement{
    }
```

#### BoolsSetOn

``` mermaid
classDiagram
    class BoolsSetOnStateExited{
    }
```

#### BroadcastOn

``` mermaid
classDiagram
    class BroadcastOnStateExit{
    }
```

#### TriggerSetBy

``` mermaid
classDiagram
    class TriggerSetByTimer{
    }
```

### Structs

These scripts contain user-defined data types that combine fields of different types underneath a single type. All classes in this folder use the `struct` keyword in their declaration.

#### BoolParameter

``` mermaid
classDiagram
    class BoolParameter{
    <<Struct>>
    }
```