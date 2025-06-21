*   [UIKit](/documentation/uikit)
*   [UIViewController](/documentation/uikit/uiviewcontroller)
*   interactionActivityTrackingBaseName

Instance Property

# interactionActivityTrackingBaseName

The base name the view controller uses for logging signposts that annotate user interactions.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+tvOS 16.0+visionOS 1.0+

```swift
```swift
```swift
```swift
```swift
```swift
```swift

```swift
@[`MainActor`](/documentation/Swift/MainActor)
var interactionActivityTrackingBaseName: [`String`](/documentation/Swift/String)? { get set }
```

```
```
```
```
```
```
```

## [Discussion](/documentation/UIKit/UIViewController/interactionActivityTrackingBaseName#Discussion)

To help you investigate perfomance issues in your app, UIKit annotates significant user interactions with signpost messages. It creates activities that span the duration of the interaction and sets one of the [`ProcessInfo.ActivityOptions`](/documentation/Foundation/ProcessInfo/ActivityOptions) for tracking: doc://com.apple.documentation/documentation/foundation/processinfo/activityoptions/3967425-animationtrackingenabled or doc://com.apple.documentation/documentation/foundation/processinfo/activityoptions/3967426-trackingenabled.

Use this property to customize the tracking name the activity uses in the signpost messages. Scroll views that can derive their enclosing view controller also use the tracking name to annotate interactive dragging and programmatic scrolling events.

In many cases, you can set the tracking name once in `init`, `viewDidLoad,` or `awakeFromNib`. You can, however, change the tracking name in response to different configurations. In this example, the tracking name updates in response to toggling a switch.

```swift
```swift
```swift
```swift
```swift
```swift
```swift
```swift
```swift
```swift
```swift
func showImagesSwitchDidChange(_ sender: UISwitch) {
```
```
    model.shadowImages = sender.isOn
    interactionActivityTrackingBaseName = sender.isOn ? "FancyList" : "PlainList"
    collectionView.reloadData()
}
```
```
```
```
```

```

```
- (void)showImagesSwitchDidChange:(UISwitch *)sender {
    self.model.showImages = sender.isOn;
    self.interactionActivityTrackingBaseName = sender.on ? @"FancyList" : @"PlainList";
    [self.collectionView reloadData];
}
```

```
```
```
```
```

When not explicitly set, custom subclasses use their class name as the base name, while base classes may use the [`accessibilityIdentifier`](/documentation/uikit/uiaccessibilityidentification/accessibilityidentifier) of the controller’s managed view.

If the view controller is a prominent child view controller of a [`UINavigationController`](/documentation/uikit/uinavigationcontroller), [`UITabBarController`](/documentation/uikit/uitabbarcontroller), or [`UISplitViewController`](/documentation/uikit/uisplitviewcontroller), the parent may derive a name by applying a prefix:

*   `UINC-` for a navigation controller
    
*   `UITBC-` for a tab bar controller
    
*   `UISVC-` for a split view controller
    

The system applies a suffix to the base name to denote the type of user interaction:

*   `-Appearing` when presenting the view controller
    
*   `-Disappearing` when dismising the view controller
    
*   `-Scrolling` when scrolling the view controller’s managed `UIScrollView`
    
*   `-Dragging` when dragging the view controller’s managed `UIScrollView`
    

For example, UIKit uses the tracking name `UINC-MyListTableViewController-Appearing` in a signpost when presenting a navigation controler with a `MyListTableViewController` prominent child controller.

## [See Also](/documentation/UIKit/UIViewController/interactionActivityTrackingBaseName#see-also)

### [Related Documentation](/documentation/UIKit/UIViewController/interactionActivityTrackingBaseName#Related-Documentation)

[

Recording Performance Data](/documentation/os/recording-performance-data)

Add signposts to record interesting time-based events.

[

Improving app responsiveness](/documentation/Xcode/improving-app-responsiveness)

Create a user experience that feels responsive by removing hangs and hitches from your app.