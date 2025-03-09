# Scripting

!!! Summary

    This page explains the different types of script files used in this template and how they are organized.

## Project Window

<figure markdown="span">
    ![scripting.png](../assets/images/scripting.png)
</figure>

### Folders

All code in the project is located at `Assets/Arcabidi/BeatEmUpTemplate/Scripting`.

| <div style="width:180px" /> Folder Name | Description                          |
| ---------------: | :----------------------------------- |
| `Systems`            | Contains all code belonging to the game's twelve core systems. For a more detailed summary of each script's purpose, look under its associated section in the [Systems](systems/index.md) page. |
| `Utilities`            | Contains code that doesn't belong to any one game system. These classes act as general-purpose tools that can be used anywhere, in any game, when needed. For a more detailed summary of each script's purpose, look under its associated section in the [Utilities](utilities.md) page. |

### Subfolders

The subfolders in these directories are divided by script type:

| <div style="width:190px" /> Folder Name | Description                          |
| ---------------: | :----------------------------------- |
| `CSharp`            | Contains scripts that are not meant to be attached to GameObjects in the scene. Many of them represent static event classes that are meant to be invoked, or are abstract classes representing concepts like [Players](systems/player.md#players) or [Teams](systems/unit.md#teams). |
| `Enums`            | Contains groups of related constants that are meant to be used by other scripts. All classes in these folders use the `enum` keyword in their declaration. |
| `Interfaces`            | Contain collections of method signatures and properties that can be implemented by other scripts. All classes in these folder use the `interface` keyword in their declaration.<br><br>Interfaces act like a contract; when a class implements an interface, an instance of that class can also be treated as an instance of that interface. This functionality means that two unrelated classes can be treated in the same way through an interface that they both implement. |
| `MonoBehaviours`            | Contain scripts that are meant to be attached to GameObjects in the scene as components. All classes in these folders inherit from Unity's [MonoBehaviour](https://docs.unity3d.com/6000.0/Documentation/Manual/class-MonoBehaviour.html) class. Many of them represent managers, controllers, and responders specific to scenes or prefabs. |
| `PropertyAttributes`            | Contains custom attributes for script variables. All classes in this folder derive from Unity's base [PropertyAttribute](https://docs.unity3d.com/6000.0/Documentation/ScriptReference/PropertyAttribute.html) class. |
| `PropertyDrawers`            | Contains custom drawers to control how script variables with custom PropertyAttributes appear in the Inspector. All classes in this folder derive from Unity's base [PropertyDrawer](https://docs.unity3d.com/6000.0/Documentation/ScriptReference/PropertyDrawer.html) class. |
| `ScriptableObjects`            | Contains centralized data that can be conveniently accessed from scenes and assets within a project. All classes in this folder derive from Unity's base [ScriptableObject](https://docs.unity3d.com/6000.0/Documentation/ScriptReference/ScriptableObject.html) class.<br><br>ScriptableObjects are stored on disk and live independently of GameObjects and class instances. They are used as data containers to save large amounts of data, reducing a project’s memory usage by not duplicating values. |
| `StateMachineBehaviours`            | Contains components that can be added to a state machine state. All classes in this folder derive from Unity's base [StateMachineBehaviour](https://docs.unity3d.com/ScriptReference/StateMachineBehaviour.html) class. See the [Animation](systems/animation.md#statemachinebehaviours) page for more information. |
| `Structs`            | Contains user-defined data types that combine fields of different types underneath a single type. All classes in this folder use the `struct` keyword in their declaration. |
| `VisualElements`            | Contains objects that are part of the UIElements visual tree. All classes in this folder derive from Unity's base [VisualElement](https://docs.unity3d.com/6000.0/Documentation/ScriptReference/UIElements.VisualElement.html) class. See the [User Interface](systems/user-interface.md#visualelements) page for more information. |