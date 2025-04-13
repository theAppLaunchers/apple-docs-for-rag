

- UIKit
- App and environment
- Scenes
-  Specifying the scenes your app supports 

Article

# Specifying the scenes your app supports

Tell the system about your app’s scenes, including the objects you use to manage each scene and its initial user interface.

## Overview

Add support for scenes to your app to receive scene-specific life-cycle events that UIKit provides, and use scene objects and methods to manage your user interface. If you enable support for multiple windows as part of your app’s scene configuration, people can create multiple copies of your app’s UI on platforms that support it. For each copy of your app’s UI, you use a scene object to manage the window, views, and view controllers that present the UI onscreen.

When your app or user requests a new scene, UIKit creates the corresponding scene object and handles its initial setup. To do that, UIKit relies on information that you provide. In your app’s Xcode project, declare one or more types of scenes that your app supports and the objects that your app uses to manage those scenes. You can do that statically in Xcode’s Info tab for your app’s target or dynamically at runtime.

### Enable scene support in your project settings

Update your app’s configuration settings to opt in to scenes:

1.  Open your Xcode project.

2.  Navigate to the Info settings tab for your app target.

3.  Add the UIApplicationSceneManifest dictionary key in the Custom iOS Target Properties section.

The value of this key is a dictionary, which initially contains the UIApplicationSupportsMultipleScenes key and the UISceneConfigurations key.

Set the value of the UIApplicationSupportsMultipleScenes key to true to tell the system if your app supports multiple simultaneous scenes, or false if you want to display only one scene at a time. Supporting multiple scenes requires extra work on your part to ensure that your scenes don’t interfere with each other. For example, if your scenes use the same shared data structures, they must coordinate access to those structures to preserve the integrity of your app’s data.

### Configure the details for each scene

UIKit handles the creation of your app’s scenes using information that you provide. The simplest way to provide this information is in your app’s Info settings:

1.  Open your Xcode project and navigate to the Info settings tab for your app target.

2.  Expand the Application Scene Manifest entry. This entry corresponds to the UIApplicationSceneManifest key. If it isn’t present, add it as described in Enable scene support in your project settings.

3.  In the Scene Configuration entry, click the Add (+) button.

4.  Select Window Application Session Role to add a main scene to your app.

5.  Fill in the scene details in the provided entry.

Most apps need only one main scene, but you may add multiple scenes and configure each differently. For example, you might include a second scene specifically to display notification-related content. UIKit requires the following information for each scene:

- The class name of the scene, which is UIWindowScene.

- The class name of the custom delegate object your app uses to manage the scene. The class must adopt the UIWindowSceneDelegate protocol.

- A unique name that your app uses to identify the scene internally.

- The name of the storyboard containing the scene’s initial UI. Specify the name without the `.storyboard` filename extension.

For more information about how to configure your scenes, see UISceneConfigurations.

### Create the interface for your scene

You specify the UI for your scene using storyboards. The storyboard you assign to the UISceneStoryboardFile key contains the initial view controller you want to display for your scene. In addition to creating the scene object, UIKit creates a window for your scene automatically and installs the initial view controller from your storyboard in it. You can replace that view controller programmatically using the methods of your UIWindowSceneDelegate object.

Important

Don’t forget to designate an initial view controller in your storyboard. UIKit relies on the presence of this view controller when configuring your UI.

### Change your scene’s configuration dynamically

Before actually creating your scene object, UIKit calls the application(_:configurationForConnecting:options:) method of your app delegate to let you change the scene-related details. You might use this method to adjust the scene configuration based on the options that UIKit provides. For example, when the system passes a notification response to your scene, you might specify a different storyboard with your notification-related interface.

If you don’t implement configure scenes dynamically, UIKit uses the information in your app’s `Info.plist` file to create your scenes.

### Adopt scene-based life-cycle semantics

Adding support for scenes changes how your app responds to life-cycle events. In an app that doesn’t use the scene life-cycle objects, the app delegate object handles transitions to the foreground or background. When you add scene support to your app, UIKit shifts that responsibility to your scene delegate objects. Scene life cycles are independent of one another, and independent of the app itself, so your scene delegate objects must handle the transitions.

For information about how to handle life-cycle events, see Managing your app’s life cycle.

## See Also

### Configuration

UIApplicationSceneManifest

The information about the app’s scene-based life-cycle support.

class UISceneConfiguration

Information about the objects and storyboard for UKit to use when creating a particular scene.

class UISceneSession

An object that contains information about one of your app’s scenes.

