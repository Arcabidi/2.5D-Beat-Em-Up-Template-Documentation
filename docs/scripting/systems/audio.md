# Audio

!!! Summary

    This section summarizes all aspects of the audio system, which is responsible for playing background music and sound effects.

## Scripting

### CSharp

#### AudioEvents

``` mermaid
classDiagram
    class AudioEvents{
        <<Static>>
    }
```

### MonoBehaviours

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