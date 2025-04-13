

- WatchKit
- WKInterfaceController
-  presentController(withNamesAndContexts:) 

Instance Method

# presentController(withNamesAndContexts:)

Presents a page-based interface modally.

iOS 8.2+iPadOS 8.2+watchOS

``` source
@MainActor @preconcurrency
func presentController(withNamesAndContexts namesAndContexts: [(name: String, context: AnyObject)])
```

## Parameters 

`namesAndContexts`  

An array of tuples. Each tuple must contain the following named elements:

name  
The name of the interface controller you want to display. In your storyboard, the name of an interface controller is stored in the object’s Identifier property, which is located in the attributes inspector. This element must not be `nil`.

context  
An object to pass to the new interface controller. Use the object in this parameter to communicate important information to the new interface controller, such as the data to display or any relevant state information. You may specify `nil` for this element, but doing so is not recommended.

## Mentioned in 

Navigating Between Scenes

## Discussion

After calling this method, the WatchKit extension loads and initializes the new interface controllers and animates them into position on top of the current interface controller. A modal interface slides up from the bottom of the screen and completely covers the previous interface. The watchOS app displays the first interface controller in the `names` array initially. The user can navigate to the other interfaces by swiping horizontally.

The title of the modal interface is set to the string `Cancel` by default. Change the title using the setTitle(_:) method. Tapping the title dismisses the interface automatically. To dismiss the interface programmatically, call the dismiss() method.

Always call this method from your WatchKit extension’s main thread.

## See Also

### Presenting interface controllers modally

func presentController(withName: String, context: Any?)

Presents a single interface controller modally.

func presentController(withNames: [String], contexts: [Any]?)

Presents a page-based interface modally.

func presentAlert(withTitle: String?, message: String?, preferredStyle: WKAlertControllerStyle, actions: [WKAlertAction])

Presents an alert or action sheet over the current interface controller.

enum WKAlertControllerStyle

Constants indicating the styles for standard system alerts.

func dismiss()

Dismisses the current interface controller from the screen.

