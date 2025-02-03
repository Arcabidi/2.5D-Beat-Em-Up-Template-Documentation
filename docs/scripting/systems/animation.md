# Animation

!!! Summary

    This section summarizes all aspects of the animation system, which is responsible for bringing GameObjects in the scene to life.

This project uses Unity's built-in animation system, known as the [Mecanim Animation system](https://docs.unity3d.com/Manual/AnimationOverview.html), to bring its in-game units to life. This folder contains state machines called AnimatiorControllers that are referenced by a unit's Animator component to decide what AnimationClip to play.

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

#### BoolParameter

``` mermaid
classDiagram
    class BoolParameter{
    <<Struct>>
    }
```