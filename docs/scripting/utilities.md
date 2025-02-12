# Utilities

!!! Summary

    This section outlines the utilitiy scripts used by the 2.5D Beat 'Em Up Template. These classes don't belong to any one game system and act as general-purpose tools that can be used anywhere, in any game, when needed. 

## Scripting

### CSharp

These scripts are not meant to be attached to GameObjects in the scene. Many of them represent static event classes that are meant to be invoked, or are abstract classes representing concepts.

#### ActionWrapper

``` mermaid
classDiagram
    class ActionWrapper{
    }
```

`ActionWrapper.cs` is used by `PersistentGameManager.cs` to define the EventLinks in its StateMachine. In effect, it connects two nodes in the StateMachine by subscribing to GameEvents.

#### Constants

``` mermaid
classDiagram
    class Constants{
    }
```

`Constants.cs` contains all the constants in the template. 

#### StateMachine

``` mermaid
classDiagram
    class StateMachine{
    }
```

`StateMachine.cs` represents a basic, general-purpose state machine. It is used by `PersistentGameManager.cs` to represent the game's state.

### Enums

These scripts contain groups of related constants that are meant to be used by other scripts. All classes in these folders use the `enum` keyword in their declaration.

#### Direction

``` mermaid
classDiagram
    class Direction{
    <<Enum>>
    }
```

`Direction.cs` enumerates all possible in-game directions in the template.

### Interfaces

These scripts contain collections of method signatures and properties that can be implemented by other scripts. All classes in these folder use the `interface` keyword in their declaration.

Interfaces act like a contract; when a class implements an interface, an instance of that class can also be treated as an instance of that interface. This functionality means that two unrelated classes can be treated in the same way through an interface that they both implement.

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

ICan interfaces are implemented by classes that can perform a specific functionality.

`ICanFace.cs` is implemented by classes that can face a specific direction. It is implemented by `VillainController.cs` so that `BasicEnemyAI.cs` can control the direction the unit faces.

`ICanMove.cs` is implemented by classes that can move conditionally. It is implemented by `UnitController.cs` so that `TemplateBeltScrollMove.cs` can know if the unit can currently move.

`ICanStop.cs` is implemented by classes that can stop. It is implemented by `TemplateBeltScrollMove.cs` so that `UnitController.cs` can stop the unit from moving when needed.

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

IHave interfaces are implemented by classes that have a specific property.

`IHaveDamage.cs` is implemented by classes that have damage. It is implemented by [JabAbilityData and CrossAbilityData](systems/ability.md#abilitydata) so that a target's [HurtResponder](systems/hitbox.md#hurtresponders) knows that it has to process damage as part of its hurt response.

`IHaveDirection.cs` is implemented by classes that have direction. It is implemented by [UnitController](systems/unit.md#unitcontrollers) so that [JabHitbox and CrossHitbox](systems/hitbox.md#hitboxes) know what direction to perform their boxcasts when getting hit info from a collision.

`IHaveFloatingHealthBar.cs` is implemented by classes that have a floating health bar transform. It is implemented by [VillainController](systems/unit.md#unitcontrollers) so that [FloatingHealthBarController](systems/user-interface.md#floatinghealthbarcontrollers) knows where to position the unit's floating health bar.

`IHaveHitStun.cs` is implemented by classes that have hitstun. It is implemented by [JabAbilityData and CrossAbilityData](systems/ability.md#abilitydata) so that a target's [HurtResponder](systems/hitbox.md#hurtresponders) knows that it has to process hitstun as part of its hurt response.

`IHaveHurtboxes.cs` is implemented by classes that have hurtboxes. It is implemented by [HeroController](systems/unit.md#unitcontrollers) so that [BasicEnemyAI](systems/player.md#ais) can calculate the closest possible target hurtbox.

`IHaveHurtboxMask.cs` is implemented by classes that have a hurtbox mask. It is implemented by [UnitController](systems/unit.md#unitcontrollers) so that [JabHitbox and CrossHitbox](systems/hitbox.md#hitboxes) know what type of hurtbox they collide with when active.

`IHaveKnockback.cs` is implemented by classes that have knockback. It is implemented by [JabAbilityData and CrossAbilityData](systems/ability.md#abilitydata) for two reasons:

1. So that [JabHitbox and CrossHitbox](systems/hitbox.md#hitboxes) can assign knockback direction after a collision based on hit info
2. So that a target's [HurtResponder](systems/hitbox.md#hurtresponders) knows that it has to process knockback as part of its hurt response.

`IHaveName.cs` is implemented by classes that have a name. It is implemented by [UnitController](systems/unit.md#unitcontrollers) so that [UnitActionManager](systems/action.md#unitactionmanagers) can out output debug logs when attempting to perform [UnitActions](systems/action.md#unitactions).

`IHaveRange.cs` is implemented by classes that have range. It is implemented by [JabUnitAction and CrossUnitAction](systems/action.md#unitactions) so that [BasicEnemyAI](systems/player.md#ais) knows the maximum range at which to position itself in order to hit with the edge of an ability.

`IHaveMaximumHealth.cs` is implemented by classes that have hurtboxes.

`IHealth.cs` is implemented by classes that have health.

#### IRaise

``` mermaid
classDiagram
    class IRaiseMoveExecuted{
    <<Interface>>
    }
    class IRaiseSetAnimationBool{
    <<Interface>>
    }
    class IRaiseWon{
    <<Interface>>
    }
```

IRaise interfaces are implemented by classes that raise a specific event.

`IRaiseMoveExecuted.cs` is implemented by classes that raise a move executed event. It is implemented by [TemplateBeltScrollMove](systems/ability.md#abilities) for two reasons:

1. So that [HeroController](systems/unit.md#unitcontrollers) can have the unit face the direction it is moving.

2. To notify [StateMachineBehaviours](systems/animation.md#statemachinebehaviours) that the unit is moving so that the animation state machine can update accordingly.

`IRaiseSetAnimationBool.cs` is implemented by classes that set an animation bool. It is implemented by [Jab and Cross](systems/ability.md#abilities) to notify [StateMachineBehaviours](systems/animation.md#statemachinebehaviours) that the user is executing an ability so that the animation state machine can update accordingly.

`IRaiseWon.cs` is implemented by classes that raise a win. It is implemented by [UnitController](systems/unit.md#unitcontrollers) to notify [StateMachineBehaviours](systems/animation.md#statemachinebehaviours) that the unit has won so that the animation state machine can update accordingly.

#### IDamageable

``` mermaid
classDiagram
    class IDamageable{
    <<Interface>>
    }
```

`IDamageable.cs` is implemented by classes that are damageable. It is implemented by [UnitController](systems/unit.md#unitcontrollers) to notify [StateMachineBehaviours](systems/animation.md#statemachinebehaviours) that the unit was damaged so that the animation state machine can update accordingly.

#### IDefeatable

``` mermaid
classDiagram
    class IDefeatable{
    <<Interface>>
    }
```

`IDefeatable.cs` is implemented by classes that are defeatable. It is implemented by [UnitController](systems/unit.md#unitcontrollers) to notify [StateMachineBehaviours](systems/animation.md#statemachinebehaviours) that the unit was defeated so that the animation state machine can update accordingly.

#### IPausable

``` mermaid
classDiagram
    class IPausable{
    <<Interface>>
    }
```

`IPauseable.cs` is implemented by classes that are pausable. It is implemented by [TemplateBeltScrollMove](systems/ability.md#abilities) to allow a [UnitController](systems/unit.md#unitcontrollers) to pause and unpause its behavior.

#### IPauseAnimator

``` mermaid
classDiagram
    class IPauseAnimator{
    <<Interface>>
    }
```

`IPauseAnimator.cs` is implemented by classes that can pause the animator. It is implemented by [UnitController](systems/unit.md#unitcontrollers) to notify [StateMachineBehaviours](systems/animation.md#statemachinebehaviours) that the unit was paused so that the animation state machine can update accordingly.

### MonoBehaviours

These scripts are meant to be attached to GameObjects in the scene as components and inherit from Unity's [MonoBehaviour](https://docs.unity3d.com/6000.0/Documentation/Manual/class-MonoBehaviour.html) class.

#### CycleSpriteOnEnable

``` mermaid
classDiagram
    class CycleSpriteOnEnable{
    }
```

`CycleSpriteOnEnable.cs` is used to continuously cycle between a collection of related sprites. This component can be found attached to the Street GameObject in the Title scene.

#### HorizontalDolly

``` mermaid
classDiagram
    class HorizontalDolly{
    }
```

`HorizontalDolly.cs` is used to have the x-position of a GameObject follow the x-position of a human player unit. This component can be found attached to the MainCamera GameObject in the Training scene.

#### Lerp

``` mermaid
classDiagram
    class Lerp{
    }
```

`Lerp.cs` is used to animate a GameObject's movement between two points. This component can be found attached to the Clouds GameObject in the Title scene.

####  LoadSceneOnStart

``` mermaid
classDiagram
    class LoadSceneOnStart{
    }
```

`LoadSceneOnStart.cs` is used to immediately load a new scene. This component can be found attached to the Initializer GameObject in the Initialization scene and the SceneLoader GameObject in the Persistent scene.

#### MatchScaleXSignWithTransform

``` mermaid
classDiagram
    class MatchScaleXSignWithTransform{
    }
```
`MatchScaleXSignWithTransform.cs` is used to have a GameObject's scale x sign always copy that of another GameObject's scale x sign. This component can be found attached to the UI GameObject of Human prefab and its Hero and Villain prefab variants. These prefabs are instantiated as children of the HumanPlayerUnitManager and AIPlayerUnitManager GameObjects in the Training scene at runtime.

### PropertyAttributes

These scripts contain custom attributes for script variables. All classes in this folder derive from Unity's base `PropertyAttribute` class.

#### ReadOnlyAttribute

``` mermaid
classDiagram
    class ReadOnlyAttribute{
    }
```

`ReadOnlyAttribute.cs` is used to denote fields that are read-only in the Unity Editor Inspector window.

#### RenameAttribute

``` mermaid
classDiagram
    class RenameAttribute{
    }
```

`RenameAttribute.cs`  is used to change a field's name in the Unity Editor Inspector window.

### PropertyDrawers

These scripts contain custom drawers to control how script variables with custom PropertyAttributes appear in the Inspector. All classes in this folder derive from Unity's base `PropertyDrawer` class.

#### ReadOnlyPropertyDrawer

``` mermaid
classDiagram
    class ReadOnlyPropertyDrawer{
    }
```

`ReadOnlyPropertyDrawer.cs` controls how the Serializable ReadOnlyAttribute class looks in the inspector.

#### RenamePropertyDrawers

``` mermaid
classDiagram
    class RenamePropertyDrawers{
    }
```

`RenamePropertyDrawer.cs` controls how the Serializable RenameAttribute class looks in the inspector.