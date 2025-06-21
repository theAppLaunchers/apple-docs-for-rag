*   [UIKit](/documentation/uikit)
*   UIFindInteraction

Class

# UIFindInteraction

An interaction that provides text finding and replacing operations using a system find panel.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+visionOS 1.0+

```swift
```swift
```swift
```swift
```swift
```swift
```swift

```swift
@[`MainActor`](/documentation/Swift/MainActor)
class UIFindInteraction
```

```
```
```
```
```
```
```

## [Mentioned in](/documentation/UIKit/UIFindInteraction#mentions)

[

Building a desktop-class iPad app](/documentation/uikit/building-a-desktop-class-ipad-app)

## [Overview](/documentation/UIKit/UIFindInteraction#overview)

Use a find interaction to add text-finding capabilities to your view.

When invoking the interaction, the system displays a find panel for entering a string to search, with buttons for navigating between results. When supporting replacement, this also includes a field for the text replacing matches. The find panel presents as a part of the onscreen keyboard when visible, or inline as part of the receiver’s view hierarchy.

Input from a hardware keyboard triggers a find interaction using standard system shortcuts such as Command+F for find, Command+G for find next, and Command+Shift+G for find previous. Adding the interaction also enables these commands in the menu bar on macOS when your view becomes first responder. You can also trigger the interaction by calling the [`presentFindNavigator(showingReplace:)`](/documentation/uikit/uifindinteraction/presentfindnavigator\(showingreplace:\)) method on the interaction object, providing access to find and replace operations programatically.

Some classes, such as [`UITextView`](/documentation/uikit/uitextview), [`WKWebView`](/documentation/WebKit/WKWebView), and [`PDFView`](/documentation/PDFKit/PDFView), support built-in find interactions. To enable the interaction on these views, set [`isFindInteractionEnabled`](/documentation/uikit/uitextview/isfindinteractionenabled) to `true`.

```

```
textView.isFindInteractionEnabled = true
```

```

To add find and replace operations to other views:

1.  Create the find interaction object, passing a delegate into the default initializer.
    
2.  Add the interaction by calling the [`addInteraction(_:)`](/documentation/uikit/uiview/addinteraction\(_:\)) method on the view.
    
3.  Provide a [`UIFindSession`](/documentation/uikit/uifindsession) object to manage the search performed on the content displayed in the view. You return this object through the [`findInteraction(_:sessionFor:)`](/documentation/uikit/uifindinteractiondelegate/findinteraction\(_:sessionfor:\)) method on the delegate.
    

The following example creates a find interaction for a view that presents searchable content for a document.

```swift
```swift
```swift
```swift
```swift
```swift
let document = Document(string: "")
```
```
lazy var interactionView = InteractionView(document: document)
lazy var findInteraction = UIFindInteraction(sessionDelegate: self)
override func viewDidLoad() {
    super.viewDidLoad()
    // Add the find interaction.
    interactionView.addInteraction(findInteraction)
}
```swift
```swift
func findInteraction(_ interaction: UIFindInteraction, sessionFor view: UIView) -> UIFindSession? {
```
```
    // Return a searchable object.
    return UITextSearchingFindSession(searchableObject: document)
}
```
```
```
```

Implement the [`UITextSearching`](/documentation/uikit/uitextsearching-53wjq) protocol on the class that encapsulates the searchable content for your view to use an instance of [`UITextSearchingFindSession`](/documentation/uikit/uitextsearchingfindsession) as the session object. Alternatively, you can subclass [`UIFindSession`](/documentation/uikit/uifindsession) when you want to manage the details of the session using a custom class.

Related Sessions from WWDC22

Session 10071: [Adopt desktop-class editing interactions](https://developer.apple.com/wwdc22/10071)

## [Topics](/documentation/UIKit/UIFindInteraction#topics)

### [Creating a find interaction](/documentation/UIKit/UIFindInteraction#Creating-a-find-interaction)

[`init(sessionDelegate: any UIFindInteractionDelegate)`](/documentation/uikit/uifindinteraction/init\(sessiondelegate:\))

Initializes a find interaction object with the delegate object you specify.

### [Managing find interactions](/documentation/UIKit/UIFindInteraction#Managing-find-interactions)

```swift
```swift
```swift
```swift
var delegate: (any UIFindInteractionDelegate)?
```
```

An object that updates your app’s presentation and provides the session object for managing the interaction’s search.
```
```swift
```swift
```swift
func presentFindNavigator(showingReplace: Bool)
```
```

Begins a search, displaying the find panel.
```
```swift
```swift
```swift
func dismissFindNavigator()
```
```

Dismisses the find panel, if present.
```
```swift
```swift
```swift
func findNext()
```
```

Highlights the next found result in the content, relative to the currently highlighted result.
```
```swift
```swift
```swift
func findPrevious()
```
```

Highlights the previously found result in the document, relative to the currently highlighted result.
```
```

### [Configuring the find panel](/documentation/UIKit/UIFindInteraction#Configuring-the-find-panel)

```swift
```swift
```swift
```swift
var isFindNavigatorVisible: Bool
```
```

A Boolean value that indicates when the find panel displays onscreen.
```
```swift
```swift
```swift
var searchText: String?
```
```

The search query with which to prepopulate the find panel’s search text field.
```
```swift
```swift
```swift
var replacementText: String?
```
```

The replacement string with which to prepopulate the find panel’s replace text field.
```
```swift
```swift
```swift
var optionsMenuProvider: (([UIMenuElement]) -> UIMenu?)?
```
```

A closure that populates the search options for a find interaction.
```
```

### [Managing the search](/documentation/UIKit/UIFindInteraction#Managing-the-search)

```swift
```swift
```swift
```swift
var activeFindSession: UIFindSession?
```
```

The object that manages the state, presentation, and behavior of an active search.
```
```swift
```swift
```swift
func updateResultCount()
```
```

Updates the results the interface displays for the active search.
```
```

## [Relationships](/documentation/UIKit/UIFindInteraction#relationships)

### [Inherits From](/documentation/UIKit/UIFindInteraction#inherits-from)

*   [`NSObject`](/documentation/ObjectiveC/NSObject-swift.class)

### [Conforms To](/documentation/UIKit/UIFindInteraction#conforms-to)

*   [`CVarArg`](/documentation/Swift/CVarArg)
*   [`CustomDebugStringConvertible`](/documentation/Swift/CustomDebugStringConvertible)
*   [`CustomStringConvertible`](/documentation/Swift/CustomStringConvertible)
*   [`Equatable`](/documentation/Swift/Equatable)
*   [`Hashable`](/documentation/Swift/Hashable)
*   [`NSObjectProtocol`](/documentation/ObjectiveC/NSObjectProtocol)
*   [`Sendable`](/documentation/Swift/Sendable)
*   [`UIInteraction`](/documentation/uikit/uiinteraction)

## [See Also](/documentation/UIKit/UIFindInteraction#see-also)

### [Related Documentation](/documentation/UIKit/UIFindInteraction#Related-Documentation)

[

Building a desktop-class iPad app](/documentation/uikit/building-a-desktop-class-ipad-app)

Optimize your iPad app’s user experience by adopting desktop-class enhancements for multitasking with Stage Manager, document interactions, text editing, search, and more.

### [Find and replace](/documentation/UIKit/UIFindInteraction#Find-and-replace)

```swift
```swift
```swift
```swift
protocol UIFindInteractionDelegate
```
```

A delegate object that provides a session object to manage the search state for a find interaction and receives notifications of search session lifetimes.
```
```swift
```swift
```swift
class UIFindSession
```
```

An abstract base class that manages the state, presentation, and behavior for a search that the find interaction initiates.
```
```swift
```swift
```swift
class UITextSearchingFindSession
```
```

A find session object that wraps a searchable object implementing the text-searching protocol.
```
```swift
```swift
```swift
protocol UITextSearching
```
```

The methods you use on a find session’s searchable objects to perform search operations and decorate the found text results.
```
```swift
```swift
```swift
class UITextSearchOptions
```
```

An object containing the configurable options for a text search.
```
```swift
```swift
```swift
enum UITextSearchFoundTextStyle
```
```

Constants that describe the style a find session uses to decorate the text.
```
```swift
```swift
```swift
enum WordMatchMethod
```
```

Constants that describe the method to use when searching text for words that match a string.
```
```swift
```swift
```swift
enum SearchResultDisplayStyle
```
```

Constants that describe the results summary the find panel UI includes.
```
```