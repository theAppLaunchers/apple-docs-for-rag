

- WatchKit
- Storyboard support
- Building watchOS app Interfaces Using the Storyboard
-  Navigating Between Scenes 

Article

# Navigating Between Scenes

Help users navigate between interface controllers.

## Overview

WatchKit supports three styles for navigating between scenes in watchOS.

Paged navigation  
A paged interface contains two or more independent interface controllers, displaying one at any given time. By default, the user swipes left or right to navigate between the scenes. A Page Control at the bottom of the screen shows the user’s current position among the pages. To switch to vertical paging, set the interface controller’s Page Direction attribute in the Attributes inspector.

Push navigation  
A push interface starts with a single root interface controller. Controls from the current interface *push* a new scene onto the screen. Similarly, you can *pop* back to a previous controller. Push navigations are particularly useful for displaying hierarchical information; for example, when the user selects an item from a list, you can push the detailed view for that item.

Modal Presentations  
Use a modal presentation to interrupt the user’s workflow to request input or display additional information. The modal presentation itself can consist of a single screen or a paged layout containing multiple screens.

WatchKit also supports several standard interfaces for gathering input or displaying specific types of information. To present these interfaces, use the methods listed below:

Alert and action sheets  
Use the presentAlert(withTitle:message:preferredStyle:actions:) method to display alerts and request user input using a standard interface.

Text input  
Use the presentTextInputController(withSuggestions:allowedInputMode:completion:) method to receive text input from the user. This method presents a controller with relevant input options, which may include predefined phrases, dictation, and Scribble.

Video and audio playback  
Use the presentMediaPlayerController(with:options:completion:) method to play audio and video.

Audio recording  
Use the presentAudioRecorderController(withOutputURL:preset:options:completion:) method to display the standard audio recording interface.

PassKit passes  
Use the presentAddPassesController(withPasses:completion:) method to display an interface for adding passes to the user’s Apple Watch.

The standard interfaces have built-in buttons so users can dismiss them at any time. Many of the interfaces also have a dismiss method that you can use to close the interface programmatically. While an interface is active, your app doesn’t have direct control over the interactions with that interface. Use actions or a completion handler for tasks related to the interface itself.

### Implement Page Navigation

To set up page navigation, connect two or more interface controllers in your storyboard with next-page segues.

Start by adding an interface controller for each page to the storyboard:

Control-click the first interface controller and drag to the second interface controller. The second controller should highlights to indicate that a segue is possible.

Release the mouse button and select “next page” from the Relationship Segue pop-up menu:

Continue to control-click and drag to connect the rest of your pages.

The order in which you create your segues defines the order of the pages in your interface. When the system launches your app, it creates and initializes all of the interface controllers connected by next page segues. By default, the system displays the first interface controller in the sequence. You can specify a different starting point by calling the interface controller’s becomeCurrentPage() method in its init() or awake(withContext:) method.

You can also change the set of pages to display. Call your interface controller’s reloadRootPageControllers(withNames:contexts:orientation:pageIndex:) method and pass an array of identifiers for interface controllers defined in your storyboard.

As the user navigates from page to page, watchOS activates and deactivates the interface controllers. Use the controllers’ willActivate(), didAppear(), willDisappear(), and didDeactivate() methods to track these transitions.

### Implement Push Navigation

When using push navigation, you can define the push segues either in the storyboard, or programmatically in code. To add a push segue to the storyboard, Control-drag from a button, group, or table row to the desired control in the new interface controller.

Next, select Push from the Action Segue pop-up menu:

Alternatively, you can programmatically initiate the push transition by calling the pushController(withName:context:) method:

```
@IBAction func pushNextScene() {
    // Do something before triggering the segue here.
    pushController(withName: "nextSegue", context: nil)
}
```

When pushing a new interface controller onto the screen, use the segue’s *context* to pass data to the new interface controller:

- For segues defined in the Storyboard, override the interface controller’s contextForSegue(withIdentifier:) method (or one of the related methods) to provide the context.

- For programatically triggered segues, pass the data as the `context` parameter of the pushController(withName:context:) method.

Use the context to pass state data to the new interface controller before it appears onscreen.

A pushed interface controller displays a back button in the upper-left corner of the screen to indicate that the user can navigate backward. When the user taps the back button or performs a left-edge swipe, watchOS automatically dismisses the top-most interface controller. You can also dismiss the interface controller programmatically by calling its pop() method; however, you can’t dismiss your app’s main interface controller.

Tables support item pagination. When enabled, users can easily scroll through a series of detail views. The user selects an item from the table, and the app displays a detailed view for that item. The user can scroll up and down to navigate between an item’s siblings. For more information, see Support Item Pagination in the WKInterfaceTable Class Reference.

### Present Modal Interfaces

A modal interface temporarily interrupts the current navigation flow to prompt the user or display additional information. You can present a modal interface from any interface controller, regardless of the primary navigation style used by your app. To display an interface controller modally, do one of the following:

- Create a modal segue in your storyboard file.

- Call the presentController(withName:context:) method to present a single interface controller modally.

- Call the presentController(withNames:contexts:) or presentController(withNamesAndContexts:) method to present two or more interface controllers modally using a page-based layout.

To create a modal segue in your storyboard file, Control-drag from a button, group, or table row (just like adding a Push segue). Select the Modal segue from the Action Segue pop-up menu:

To present multiple scenes in a page-based layout, connect all of the modal scenes together using next page segues (just as you would for Page navigation). Then create a modal segue to the first interface controller in that group. If you connect a modal segue to the middle of the group, the system won’t display the interface controllers that precede it.

A modal interface displays its title in the top-left corner. When the user taps the title, watchOS dismisses the modal interface. Set the interface controller’s title to reflect the meaning of dismissing the modal interface. For example, you could set it to Done or Close. If you don’t specify a title for the modal interface controller, watchOS displays Cancel by default.

