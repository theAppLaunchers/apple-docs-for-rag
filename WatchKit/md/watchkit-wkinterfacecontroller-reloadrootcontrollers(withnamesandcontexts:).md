

- WatchKit
- WKInterfaceController
-  reloadRootControllers(withNamesAndContexts:) 

Type Method

# reloadRootControllers(withNamesAndContexts:)

Loads the specified interface controllers and rebuilds the app’s page-based interface.

iOS 8.2+iPadOS 8.2+watchOS

``` source
@MainActor @preconcurrency
class func reloadRootControllers(withNamesAndContexts namesAndContexts: [(name: String, context: AnyObject)])
```

## Parameters 

`namesAndContexts`  

An array of tuples. Each tuple must contain the following named elements:

name  
The name of the interface controller you want to display. In your storyboard, the name of an interface controller is stored in the object’s Identifier property, which is located in the attributes inspector. This element must not be `nil`.

context  
An object to pass to the new interface controller. Use the object in this parameter to communicate important information to the new interface controller, such as the data to display or any relevant state information. You may specify `nil` for this element if you want but doing so is not recommended.

## Discussion

Call this method to reload the pages in your app’s page-based interface:

- **At launch time.** Use this method to customize the set of pages you want displayed.

- **At runtime.** Use it to change the active set of pages, adding or removing pages as needed.

## See Also

### Navigating a page-based interface

class func reloadRootPageControllers(withNames: [String], contexts: [Any]?, orientation: WKPageOrientation, pageIndex: Int)

Loads the specified interface controllers and rebuilds the app’s page-based interface for the given scrolling orientation.

enum WKPageOrientation

Scrolling orientations for page-based interfaces.

func becomeCurrentPage()

Displays the interface controller in the page-based interface.

