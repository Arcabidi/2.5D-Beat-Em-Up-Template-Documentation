# Audio

!!! Summary

    This section summarizes all aspects of the audio system, which is responsible for playing background music and sound effects.

## Scripting

All code files below are located at `Assets/_Project/Scripting/Systems/05 - Audio`.

### CSharp

These scripts are not meant to be attached to GameObjects in the scene. Many of them represent static event classes that are meant to be invoked, or are abstract classes representing concepts.

#### AudioEvents

``` mermaid
classDiagram
    class AudioEvents{
        <<Static>>
    }
```

### MonoBehaviours

These scripts are meant to be attached to GameObjects in the scene as components and inherit from Unity's [MonoBehaviour](https://docs.unity3d.com/6000.0/Documentation/Manual/class-MonoBehaviour.html) class.

#### AudioManagers

``` mermaid
classDiagram
    AudioManager <|-- PersistentAudioManager
    AudioManager <|-- BootAudioManager
    AudioManager <|-- TitleAudioManager
    AudioManager <|-- StageAudioManager
    class AudioManager{
        <<Static>>
    }
```