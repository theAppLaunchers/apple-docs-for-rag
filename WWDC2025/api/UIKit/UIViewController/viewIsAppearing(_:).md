*   [UIKit](/documentation/uikit)
*   [UIViewController](/documentation/uikit/uiviewcontroller)
*   viewIsAppearing(\_:)

Instance Method

# viewIsAppearing(\_:)

Notifies the view controller that the system is adding the view controller’s view to a view hierarchy.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.1+tvOS 13.0+visionOS 1.0+

```swift
```swift
```swift
```swift
```swift
```swift
```swift

```swift
@[`MainActor`](/documentation/Swift/MainActor)
func viewIsAppearing(_ animated: [`Bool`](/documentation/Swift/Bool))
```

```
```
```
```
```
```
```

## [Parameters](/documentation/UIKit/UIViewController/viewIsAppearing\(_:\)#parameters)

`animated`

If [`true`](/documentation/swift/true), the system is adding the view to the window using an animation.

## [Mentioned in](/documentation/UIKit/UIViewController/viewIsAppearing\(_:\)#mentions)

[

Displaying and managing views with a view controller](/documentation/uikit/displaying-and-managing-views-with-a-view-controller)

[

Enhancing your app with fluid transitions](/documentation/uikit/enhancing-your-app-with-fluid-transitions)

## [Discussion](/documentation/UIKit/UIViewController/viewIsAppearing\(_:\)#Discussion)

The system calls this method once each time a view controller’s view appears after the [`viewWillAppear(_:)`](/documentation/uikit/uiviewcontroller/viewwillappear\(_:\)) call. In contrast to `viewWillAppear(_:)`, the system calls this method after it adds the view controller’s view to the view hierarchy, and the superview lays out the view controller’s view. By the time the system calls this method, both the view controller and its view have received updated trait collections and the view has accurate geometry.

You can override this method to perform custom tasks associated with displaying the view. For example, you might use this method to configure or update views based on the trait collections of the view or view controller. Or, because computing a scroll position relies on the view’s size and geometry, you might programmatically scroll a collection or table view to ensure a selected cell is visible when the view appears.

If you override this method, you need to call `super` at some point in your implementation.

### [Choosing the appropriate callback](/documentation/UIKit/UIViewController/viewIsAppearing\(_:\)#Choosing-the-appropriate-callback)

Although the system calls this method after [`viewWillAppear(_:)`](/documentation/uikit/uiviewcontroller/viewwillappear\(_:\)), both callbacks occur within the same [`CATransaction`](/documentation/QuartzCore/CATransaction). This means that changes you make in either method become visible to the user at the same time.

![A diagram titled View controller appearance that consists of seven stacked horizontal bars in three distinct sections. An arrow on the right labeled Time descends from the top to the bottom. The top section is labeled Transaction and contains two horizontal bars labeled viewWillAppear and View added to hierarchy. The second section is labeled Layout and contains four horizontal bars labeled View laid out by superview; traits updated; viewIsAppearing; viewWillLayoutSubviews; and viewDidLayoutSubviews. There is a gap between the second and third sections that contains the text: Transition animates. The third section is labeled Transaction and contains one horizontal bar labeled viewDidAppear.](https://docs-assets.developer.apple.com/published/9f4992bcbe7b9858109d61db6c864256/media-4250012%402x.png)

The traits and geometry aren’t up to date when the system calls [`viewWillAppear(_:)`](/documentation/uikit/uiviewcontroller/viewwillappear\(_:\)), but they are when the system calls `viewIsAppearing(_:)`, so use `viewIsAppearing(_:)` to update your views.

Use `viewWillAppear(:_)` only when:

*   You need a callback before the view transition begins, such as when accessing the [`transitionCoordinator`](/documentation/uikit/uiviewcontroller/transitioncoordinator) to add alongside animations. Alongside animations are animations that you direct the framework to perform concurrently with the view controller transition animations.
    
*   You need balanced callbacks to do something that doesn’t depend on the view controller or view traits, hierarchy, or geometry. Use cases include registering for database notifications in [`viewWillAppear(_:)`](/documentation/uikit/uiviewcontroller/viewwillappear\(_:\)) and unregistering in [`viewDidDisappear(_:)`](/documentation/uikit/uiviewcontroller/viewdiddisappear\(_:\)).
    

For all other cases, use `viewIsAppearing(_:)` to update your views.

State at callback time

`viewWillAppear(_:)`

`viewIsAppearing(_:)`

Transition coordinator available for adding alongside animations

**✓**

✘

View added to hierarchy

**✘**

**✓**

View controller and view trait collections updated

✘

**✓**

View geometry (size, safe area, and so forth) is accurate

✘

**✓**

The system calls layout methods, such as [`viewWillLayoutSubviews()`](/documentation/uikit/uiviewcontroller/viewwilllayoutsubviews\(\)) and [`viewDidLayoutSubviews()`](/documentation/uikit/uiviewcontroller/viewdidlayoutsubviews\(\)), whenever the view runs [`layoutSubviews()`](/documentation/uikit/uiview/layoutsubviews\(\)), which can happen multiple times during the transition, or at any time while the view is visible. However, the system calls `viewIsAppearing(_:)` only once during the appearance transition, and calls it even if the view doesn’t require laying out when it appears.

For more information about how a view controller adds views to view hierarchies, and the sequence of messages that occur, see [Displaying and managing views with a view controller](/documentation/uikit/displaying-and-managing-views-with-a-view-controller).

## [See Also](/documentation/UIKit/UIViewController/viewIsAppearing\(_:\)#see-also)

### [Related Documentation](/documentation/UIKit/UIViewController/viewIsAppearing\(_:\)#Related-Documentation)

```swift
```swift
```swift
```swift
func viewDidLoad()
```
```

Called after the controller’s view is loaded into memory.
```
```

### [Responding to view-related events](/documentation/UIKit/UIViewController/viewIsAppearing\(_:\)#Responding-to-view-related-events)

```swift
```swift
```swift
```swift
func viewWillAppear(Bool)
```
```

Notifies the view controller that its view is about to be added to a view hierarchy.
```
```swift
```swift
```swift
func viewDidAppear(Bool)
```
```

Notifies the view controller that its view was added to a view hierarchy.
```
```swift
```swift
```swift
func viewWillDisappear(Bool)
```
```

Notifies the view controller that its view is about to be removed from a view hierarchy.
```
```swift
```swift
```swift
func viewDidDisappear(Bool)
```
```

Notifies the view controller that its view was removed from a view hierarchy.
```
```swift
```swift
```swift
var isBeingDismissed: Bool
```
```

A Boolean value indicating whether the view controller is in the process of being dismissed by one of its ancestors.
```
```swift
```swift
```swift
var isBeingPresented: Bool
```
```

A Boolean value indicating whether the view controller in the process of being presented by one of its ancestors.
```
```swift
```swift
```swift
var isMovingFromParent: Bool
```
```

A Boolean value indicating whether the view controller is moving from a parent view controller.
```
```swift
```swift
```swift
var isMovingToParent: Bool
```
```

A Boolean value indicating whether the view controller is moving to a parent view controller.
```
```