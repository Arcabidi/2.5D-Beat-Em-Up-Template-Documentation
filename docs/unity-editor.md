# Unity Editor

!!! Summary

    This section describes how we’ve organized the Unity work environment for our example game. It can help you navigate through the project’s files or bring up details you may want to consider when organizing your own Unity game.

## Project window

<figure markdown="span">
    ![project_window.png](assets/images/project_window.png)
</figure>

The [Project window](https://docs.unity3d.com/Manual/ProjectView.html) is located in the bottom left corner of the Unity Editor by default. The following is a general description of each major folder contained within.

| <div style="width:180px" /> Folder Name | Description                          |
| ---------------: | :----------------------------------- |
| `_Project`            | The main folder for all project files. This folder exists to separate your project related files from any other folders created when you install or update external packages.<br><br>Its name begins with an underscore so that it remains fixed at the top of the Project window. The names of its subfolders mirror the online [Unity 6 User Manual](https://docs.unity3d.com/6000.0/Documentation/Manual/UnityManual.html) to allow quick references to documentation. |
| `Animation`            | Contains all non-code files related to animation. See the [Animation](scripting/systems/animation.md) section for more information. |
| `Audio`            | Contains all non-code files related to audio. See the [Audio](scripting/systems/audio.md) section for more information. |
| `MaterialsAndShaders`            | Contains all non-code files related to how surfaces are rendered. See the [Materials](https://docs.unity3d.com/Manual/Materials.html) and [Textures](https://docs.unity3d.com/Manual/Textures-landing.html) pages in the Unity 6 User Manual for more information. |
| `Physics`            | Contains all non-code files related to how physics is simulated. See the [PhysicsMaterial](https://docs.unity3d.com/Manual/class-PhysicsMaterial.html) page in the Unity 6 User Manual for more information. |
| `Rendering`            | Contains all non-code files related to how scene content is displayed on screen. See the [Universal Render Pipeline asset](https://docs.unity3d.com/Manual/urp/urp-asset-and-renderer.html) page in the Unity 6 User Manual for more information. |
| `Scripting`            | Contains all code files. See the [Scripting](scripting/index.md) section for more information. |
| `Unity`            | Contains all non-code files related to working in Unity. |
| `2D`            | Contains all non-code files related to 2D development. See the [PSD Importer](https://docs.unity3d.com/Packages/com.unity.2d.psdimporter@9.0/manual/index.html) page in the Unity 6 User Manual for more information. |
| `GameObjects`            | Contains all non-code files related to GameObjects. See the [Models](https://docs.unity3d.com/Manual/models.html) and [Prefabs](https://docs.unity3d.com/Manual/Prefabs.html) pages in the Unity 6 User Manual for more information. |
| `Input`            | Contains all non-code files related to input. See the [Input](scripting/systems/input.md#unity) section for more information.|
| `Scenes`            | Contains all non-code files related to scenes. See the [Scenes](scenes.md) section for more information. |
| `UI`            | Contains all non-code files related to UI. See the [User Interface](scripting/systems/user-interface.md#unity) section for more information.|
| `Video`            | Contains all non-code files related to video. See the [Video Clip Importer](https://docs.unity3d.com/Manual/class-VideoClip.html) page in the Unity 6 User Manual for more information.|
| `AddressableAssetsData`            | A folder that is automatically created when you install the Addressables package from the Unity Package Manager.<br><br>This folder contains all the settings files for managing Addressables, which help you organize and package content for your application as well as load and release assets at runtime.<br><br>See the [Assets](assets.md) section for more information. |

## Hierarchy window

<figure markdown="span">
    ![hierarchy_window_1.png](assets/images/hierarchy_window_1.png)
</figure>

The [Hierarchy window](https://docs.unity3d.com/Manual/Hierarchy.html) is located in the top left corner of the Unity Editor by default. GameObjects in the hierarchy are divided based on the game system they belong to and sorted by their transforms rather than alphanumerically.

In the Training scene above, the UIManager is placed under the UI system while the AudioManager is placed under the Audio system. See the [Systems](scripting/systems/index.md) section for more information on each of the eleven game systems and their responsibilities.

!!! Info

    Unity uses this game system format for the hierarchy window in its own sample projects.<br> [Dragon Crashers (URP 2D sample project)](https://assetstore.unity.com/packages/essentials/tutorial-projects/dragon-crashers-urp-2d-sample-project-190721?srsltid=AfmBOoqwWEulvRLm8O6SG66BZFlzVuN-H4BR2vGijbf-9IsTwyJstfzF) <figure markdown="span">
    ![hierarchy_window_2.png](assets/images/hierarchy_window_2.png)</figure>