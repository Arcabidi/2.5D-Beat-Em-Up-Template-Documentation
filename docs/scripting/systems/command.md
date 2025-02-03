# Command

!!! Summary

    This section summarizes all aspects of the command system, which is responsible for determining when in-game actions should be performed.

## Scripting

All code files below are located at `Assets/_Project/Scripting/Systems/10 - Command`.

### CSharp

These scripts are not meant to be attached to GameObjects in the scene. Many of them represent static event classes that are meant to be invoked, or are abstract classes representing concepts.

#### Commands

``` mermaid
classDiagram
    class Command{
    }
```

### MonoBehaviours

These scripts are meant to be attached to GameObjects in the scene as components and inherit from Unity's [MonoBehaviour](https://docs.unity3d.com/6000.0/Documentation/Manual/class-MonoBehaviour.html) class.

#### CommandInvokers

``` mermaid
classDiagram
    class CommandInvoker{
    }
```