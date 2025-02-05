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
`AudioEvents.cs` contains all events related to audio. Events in this class are invoked whenever you need to signal a change in the game's audio. This includes things like changing the background music, playing a sound effect, or updating the volume.

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

AudioManagers manage the background music and sound effects within a scene.

`AudioManager.cs` defines what is common across all AudioManagers, regardless of game. This includes things like maintaining a data structure of AudioSources to play.

`PersistentAudioManager.cs` defines AudioManager behaviour unique to the Persistent scene, like playing sound effects when the mouse enters Button VisualElements. This component can be found attached to the AudioManager GameObject in the Persistent scene.

`BootAudioManager.cs` defines AudioManager behaviour unique to the Boot scene, like playing sound effects when the Company Logo video player starts. This component can be found attached to the AudioManager GameObject in the Boot scene.

`TitleAudioManager.cs` defines AudioManager behaviour unique to the Title scene, like playing sound effects when a coin is first inserted. This component can be found attached to the AudioManager GameObject in the Title scene.

`StageAudioManager.cs` defines AudioManager behaviour unique to stage scenes, like pausing audio when the game is paused. This component can be found attached to the AudioManager GameObject in the Training scene.

!!! Note

    For this template we've defined stages as scenes where the main gameplay takes place. For now this is just the Training scene, but the stage designation also includes any future levels.