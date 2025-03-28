# Animation

!!! Summary

    This page summarizes all aspects of the animation system, which is responsible for bringing objects in the scene to life.

## Design decisions

This template makes the following design decisions regarding the default way Unity handles animation:

### Animation system

This project uses Unity's default built-in animation system, known as the [Mecanim Animation system](https://docs.unity3d.com/Manual/AnimationOverview.html), to bring its in-game units to life.

<figure markdown="span">
    ![animation_system.png](../../assets/images/animation_system.png)
</figure>

## Animation folder

The non-code files in this section are at `BeatEmUpTemplate/Assets/Animation`.

<figure markdown="span">
    ![animation_animation_folder.png](../../assets/images/animation_animation_folder.png)
</figure>

### MecanimAnimation

The non-code files in this section are in the `MecanimAnimation` subfolder.

#### AnimationClips

<figure markdown="span">
    ![animationclips.png](../../assets/images/animationclips.png)
</figure>

[AnimationClips](https://docs.unity3d.com/Manual/AnimationClips.html) are imported from an external source or created within Unity. They are then placed and arranged in an AnimatorController.

#### AnimatorControllers

<figure markdown="span">
    ![animatorcontrollers.png](../../assets/images/animatorcontrollers.png)
</figure>

[AnimatorControllers](https://docs.unity3d.com/Manual/class-AnimatorController.html) use state machines to determine what [AnimationClip](https://docs.unity3d.com/Manual/AnimationClips.html) to play. They are referenced by the [Animator](https://docs.unity3d.com/Manual/class-Animator.html) components on the Hero and Villain prefabs. 

## Scripting folder

The code files in this section are at `BeatEmUpTemplate/Assets/Scripting/Animation`.

<figure markdown="span">
    ![animation_scripting.png](../../assets/images/animation_scripting.png)
</figure>

### StateMachineBehaviours

These scripts are components that can be added to a state machine state. All classes in this folder derive from Unity's base [StateMachineBehaviour](https://docs.unity3d.com/6000.0/Documentation/ScriptReference/StateMachineBehaviour.html) class.

#### BoolClearedByIPauseAnimatorUnpauseAnimator

``` mermaid
classDiagram
    class BoolClearedByIPauseAnimatorUnpauseAnimator{
    }
```

`BoolClearedByIPauseAnimatorUnpauseAnimator.cs` defines a bool parameter to be cleared if the UnpauseAnimator event is fired by an [IPauseAnimator](../utilities.md#ipauseanimator) interface implementation.

#### BoolSetByAbility

``` mermaid
classDiagram
    class BoolSetByAbility{
    }
```

`BoolSetByAbility.cs` define a bool parameter to be set if the SetAnimationBool event is fired by an [IRaiseSetAnimationBool](../utilities.md#iraisesetanimationbool) interface implementation. It also listens for when new abilities are added via a unit's [AbilityResponder](ability.md#abilityresponders).

#### BoolSetByIDamageableDamaged

``` mermaid
classDiagram
    class BoolSetByIDamageableDamaged{
    }
```

`BoolSetByIDamageableDamaged.cs` defines a bool parameter to be set if the Damaged event is fired by an [IDamageable](../utilities.md#idamageable) interface implementation.

#### BoolSetByIDamageableDamagedBack

``` mermaid
classDiagram
    class BoolSetByIDamageableDamagedBack{
    }
```

`BoolSetByIDamageableDamagedBack.cs` defines a bool parameter to be set if the DamagedBack event is fired by an [IDamageable](../utilities.md#idamageable) interface implementation.

#### BoolSetByIDefeatableDefeated

``` mermaid
classDiagram
    class BoolSetByIDefeatableDefeated{
    }
```

`BoolSetByIDefeatableDefeated.cs` defines a bool parameter to be set if the Defeated event is fired by an [IDefeatable](../utilities.md#idefeatable) interface implementation.

#### BoolSetByIDefeatableDefeatedBack

``` mermaid
classDiagram
    class BoolSetByIDefeatableDefeatedBack{
    }
```

`BoolSetByIDefeatableDefeatedBack.cs` defines a bool parameter to be set if the DefeatedBack event is fired by an [IDefeatable](../utilities.md#idefeatable) interface implementation.

#### BoolSetByIPauseAnimatorPauseAnimator

``` mermaid
classDiagram
    class BoolSetByIPauseAnimatorPauseAnimator{
    }
```

`BoolSetByIPauseAnimatorPauseAnimator.cs` defines a bool parameter to be set if the PauseAnimator event is fired by an [IPauseAnimator](../utilities.md#ipauseanimator) interface implementation.

#### BoolSetByIRaiseMoveExecutedMovement

``` mermaid
classDiagram
    class BoolSetByIRaiseMoveExecutedMovement{
    }
```

`BoolSetByIRaiseMoveExecutedMovement.cs` defines a bool parameter to be set if the MoveExecuted event is fired with a non-zero vector by an [IRaiseMoveExecuted](../utilities.md#iraisemoveexecuted) interface implementation.

#### BoolSetByIRaiseMoveExecutedNoMovement

``` mermaid
classDiagram
    class BoolSetByIRaiseMoveExecutedNoMovement{
    }
```

`BoolSetByIRaiseMoveExecutedNoMovement.cs` defines a bool parameter to be set if the MoveExecuted event is fired with a zero vector by an [IRaiseMoveExecuted](../utilities.md#iraisemoveexecuted) interface implementation.

#### BoolSetByIRaiseMoveExecutedNonPositiveYMovement

``` mermaid
classDiagram
    class BoolSetByIRaiseMoveExecutedNonPositiveYMovement{
    }
```

`BoolSetByIRaiseMoveExecutedNonPositiveYMovement.cs` defines a bool parameter to be set if the MoveExecuted event is fired with a non-positive y-vector by an [IRaiseMoveExecuted](../utilities.md#iraisemoveexecuted) interface implementation.

#### BoolSetByIRaiseMoveExecutedPositiveYMovement

``` mermaid
classDiagram
    class BoolSetByIRaiseMoveExecutedPositiveYMovement{
    }
```

`BoolSetByIRaiseMoveExecutedPositiveYMovement.cs` defines a bool parameter to be set if the MoveExecuted event is fired with a positive y-vector by an [IRaiseMoveExecuted](../utilities.md#iraisemoveexecuted) interface implementation.

#### BoolSetByIRaiseWonWon

``` mermaid
classDiagram
    class BoolSetByIRaiseWonWon{
    }
```

`BoolSetByIRaiseWonWon.cs` defines a bool parameter to be set if the Won event is fired by an [IRaiseWon](../utilities.md#iraisewon) interface implementation.

#### BoolSetByJumpAbility

``` mermaid
classDiagram
    class BoolSetByJumpAbility{
    }
```

`BoolSetByJumpAbility.cs` defines a bool parameter to be set if the SetAnimationBool event is fired by a [Jump](ability.md#abilities) ability.

The difference between this script and [BoolSetByAbility](#boolsetbyability) is that it correctly subscribes to the Jump ability even when two abilities
are attached to the player's character at the same time. In the case of this template, even when the player is [BeltScrollMoving](ability.md#abilities).

#### BoolSetOnAnimationFinished

``` mermaid
classDiagram
    class BoolSetOnAnimationFinished{
    }
```

`BoolSetOnAnimationFinished.cs` defines a bool parameter to be set when the current state's animation finishes.

#### BoolSetOnStateExited

``` mermaid
classDiagram
    class BoolSetOnStateExited{
    }
```

`BoolSetOnStateExited.cs` defines a bool parameter to be set when the current state exits.

#### BoolsSetByIRaiseMoveExecutedNoMovement

``` mermaid
classDiagram
    class BoolsSetByIRaiseMoveExecutedNoMovement{
    }
```

`BoolsSetByIRaiseMoveExecutedNoMovement.cs` defines multiple bool parameters to be set when the MoveExecuted event is fired with a zero vector by an [IRaiseMoveExecuted](../utilities.md#iraisemoveexecuted) interface implementation.

#### BoolsSetOnStateExited

``` mermaid
classDiagram
    class BoolsSetOnStateExited{
    }
```

`BoolsSetOnStateExited.cs` defines multiple bool parameters to be set when the current state exits.

#### BroadcastOnStateExit

``` mermaid
classDiagram
    class BroadcastOnStateExit{
    }
```

`BroadcastOnStateExit.cs` fires a StateExited event when the current state exits.

#### TriggerSetByTimer

``` mermaid
classDiagram
    class TriggerSetByTimer{
    }
```

`TriggerSetByTimer.cs` defines a trigger parameter to be triggered when a set amount of time has elapsed.

### Structs

These scripts contain user-defined data types that combine fields of different types underneath a single type. All classes in this folder use the `struct` keyword in their declaration.

#### BoolParameter

``` mermaid
classDiagram
    class BoolParameter{
    <<Struct>>
    }
```

`BoolParameter.cs` is used by [StateMachineBehaviours](#statemachinebehaviours) to set a bool parameter with name 'name' to value 'value'.