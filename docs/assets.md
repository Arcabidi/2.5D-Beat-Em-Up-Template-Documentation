# Assets

!!! Summary

    This page explains how items are dynamically loaded and unloaded using Unity's Addressables package.

## Design decisions

This template makes the following design decisions regarding the default way Unity handles [assets](https://docs.unity3d.com/6000.0/Documentation/Manual/AssetWorkflow.html):

### Asset system

Unity’s default Asset system is the [Resource system](https://docs.unity3d.com/6000.0/Documentation/Manual/UnderstandingPerformanceResourcesFolder.html). Developers store assets in one or more folders named Resources and load or unload Objects from those assets at runtime.

!!! Danger

    The Resource system is very limited and prone to bloating. Unity themselves [do not recommend using the Resource system](https://learn.unity.com/tutorial/assets-resources-and-assetbundles#5c7f8528edbc2a002053b5a6:~:text=the%20Resources%20System-,Don%27t%20use%20it.,-This%20strong%20recommendation) for projects past the prototyping phase.

An alternative to the Resource system is to use [AssetBundles](https://docs.unity3d.com/Manual/AssetBundlesIntro.html). An AssetBundle is an archive file that contains platform-specific non-code content (models, textures, prefabs, audio, etc.) that Unity can load at runtime. AssetBundles are commonly used to update or add content post-release such as DLC, limited-time promotional events, or holiday themes. They can reduce initial file size, optimize asset loading based on user platform, reduce memory runtime pressure, and even allow content to be reused from project to project.

In 2019 Unity released a new quality-of–life way to manage AssetBundles. This template will use that new asset system.

## Addressables package

### 1. Installation
The [Addressables package](https://docs.unity3d.com/Packages/com.unity.addressables@1.21/manual/index.html) is not enabled by default and must be installed using the Package Manager at  `Window > Package Manager`.<br>
<br>
<figure markdown="span">
    ![addressables_package_1.png](assets/images/addressables_package_1.png)
</figure>

### 2. Mark Addressable assets

Once it is installed the second step is to mark all Addressable content in the project. Any content marked this way can be dynamically loaded or unloaded at runtime.<br>
<br>
This is done by selecting an asset in the Project window and checking the now available Addressable box in the Inspector. In the example below the Persistent scene has been marked as an Addressable asset. You can find it at `Assets/_Project/Gameplay/Scenes`.<br>
<br>
<figure markdown="span">
    ![addressables_package_2.png](assets/images/addressables_package_2.png)
</figure>

### 3. Form Addressables groups

The third step is to organize Addressable content into groups. You can view a list of all Addressables in the project at `Window > Asset Management > Addressables > Groups`. Here you can see all of the Addressables groups in the template and the assets under each group.<br>
<br>
<figure markdown="span">
    ![addressables_package_3.png](assets/images/addressables_package_3.png)
</figure>
<br>
When you mark an asset as Addressable it is placed in the Default Local Group by default, but you can create your own custom groups and move assets into them or set a new default folder if you wish.<br>

### 4. Choose BundleModes

The fourth step is to adjust the way each Addressables group is packed into AssetBundles by changing its BundleMode. These settings can be found at `Assets/AddressableAssetsData/AssetGroups/[Addressable Group Name].asset` where each Addressables group has its own settings file.<br>
<br>
<figure markdown="span">
    ![addressables_package_4.png](assets/images/addressables_package_4.png)
</figure>
<br>
Based on the BundleMode chosen, the assets in an Addressable group will either be Packed Together into a single bundle, Packed Separately into their own individual bundles, or Packed Together By Label into a bundle with all other assets that share the same label (regardless of Addressable group). The exceptions are Scene assets, which are always packed separately.

### 5. Convert to AssetBundles

The final step is to convert the assets in your Addressables groups into AssetBundles. Whenever Addressable assets are modified during development, the project’s Addressables content must be rebuilt before building the Player. This can be done in one of two ways. The first is manually through the Build Menu of the groups window.<br>
<br>
<figure markdown="span">
    ![addressables_package_5.png](assets/images/addressables_package_5.png)
</figure>
<br>
The second is automatically as part of the Player build. This can be configured in the project’s Addressable Asset Settings file located at `Assets/AddressableAssetsData/AddressableAssetSettings.asset`. <br>
<br>
<figure markdown="span">
    ![addressables_package_6.png](assets/images/addressables_package_6.png)
</figure>
<br>
While running the Addressables content build at the same time as the Player build may be convenient, it could increase build time on larger projects, especially if no assets have been modified since the last build.

### 6. Build reports

To view the AssetBundles that were created, you must enable [Build Reports](https://docs.unity3d.com/Packages/com.unity.addressables@1.21/manual/BuildLayoutReport.html) at `Edit > Preferences > Addressables > Debug Build Layout`.<br>
<br>
<figure markdown="span">
    ![build_report_1.png](assets/images/build_report_1.png)
</figure>
<br>
You can set the report to open after every build, or view the reports manually at `Window > Asset Management > Addressables > Addressables Report`.<br>
<br>
<figure markdown="span">
    ![build_report_2.png](assets/images/build_report_2.png)
</figure>
<br>
The report will also notify you of any potential risks for asset duplication, where a single non-Addressable asset is referenced by multiple AssetBundles. If this happens, you may want to mark the risky asset as Addressable and assign it to an appropriate group.

### 7. Profiler module

Once BuildReports are enabled the Addressables [Profiler module](https://docs.unity3d.com/Packages/com.unity.addressables@1.21/manual/ProfilerModule.html) can notify you at runtime whenever AssetBundles are loaded or unloaded. You can use this information to optimize the memory usage of your game. The first step is to install the Unity Profiling Core API from the PackageManager.<br>
<br>
<figure markdown="span">
    ![profiler_module_1.png](assets/images/profiler_module_1.png)
</figure>
<br>
Next, open the Profiler window at `Window > Analysis > Profile` and enable Addressable Assets from the Profiler Modules drop down menu so that they can be monitored.<br>
<br>
<figure markdown="span">
    ![profiler_module_2.png](assets/images/profiler_module_2.png)
</figure>
<br>
Lastly, the Profiler module only supports the Use Existing Build setting for the Play Mode Script. Make sure your Addressables build exists, then select the appropriate option from the Play Mode Script menu of the groups window.<br>
<br>
<figure markdown="span">
    ![profiler_module_3.png](assets/images/profiler_module_3.png)
</figure>
<br>
Now when you enter Play Mode, the module view can display whatever Addressables content is loaded at any given point in time.<br>
<br>
<figure markdown="span">
    ![profiler_module_4.png](assets/images/profiler_module_4.png)
</figure>

## AddressableAssetsData folder

The non-code files in this section are at `Assets/AddressableAssetsData`.

<figure markdown="span">
    ![assets_addressableassetsdata_folder.png](assets/images/assets_addressableassetsdata_folder.png)
</figure>

This folder is automatically created when you install the Addressables package from the Unity Package Manager. It contains all the settings files for managing Addressables, which help you organize and package content for your application as well as load and release assets at runtime.