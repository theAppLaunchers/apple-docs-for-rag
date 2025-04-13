

- watchOS Release Notes
-  watchOS 10 Release Notes 

Article

# watchOS 10 Release Notes

Update your apps to use new features, and test your apps against API changes.

## Overview

The watchOS 10 SDK provides support to develop watchOS apps for Apple Watch devices running watchOS 10. The SDK comes bundled with Xcode 15, available from the Mac App Store. For information on the compatibility requirements for Xcode 15, see Xcode 15 Release Notes.

### General

#### New Features

- Optimized Charge Limit is now available on Apple Watch SE, Series 6, Series 7, and Series 8. See About Optimized Battery Charging on your Apple Watch for more information. (110117793)

#### Resolved Issues

- Fixed: Apple Watch Series 6 (40mm) estimates maximum battery capacity more accurately. (109589671)

### Accelerate

#### New Features

- Spatial

  - Introduced trigonometry functions for Spatial angle type.

  - Introduced spherical linear interpolation for Spatial rotations.

  - Introduced swing-twist decomposition for Spatial rotations.

- BNNS

  - Introduced BNNSRandomFillCategoricalFloat that fills a tensor with random values from the categorical distributions with event probabilities.

  - Introduced k-nearest neighbors calculation.

- vImage

  - Introduced vImageConvolveFloatKernel_ARGB8888 that applies convolution to 8-bit-per-channel, 4-channel interleaved images using 32-bit floating-point weights.

  - Introduced vImageSepConvolve_ARGB8888 that applies separable convolution to 8-bit-per-channel, 4-channel interleaved images.

  - Added flood fill, perspective transform, and new lookup table transforms to vImage.PixelBuffer. (105830806)

### Accessibility

#### Resolved Issues

- Fixed: Attempting to input text using Scribble doesn’t work for unsupported languages. (108703755)

### Camera and AVFoundation Capture

#### Resolved Issues

- Fixed: On iPhone 14 and 14 Plus models third-party camera applications might fail to capture images, and the built-in Camera app and third-party applications using the new Deferred Processing API might fail to process final images. (113158045)

### Cellular Waypoints

#### Known Issues

- Cellular and SOS Waypoints might not appear in the Compass app when the user is in the back country. (113973758)

  **Workaround:** Quit and re-launch the app.

### Complication Picker

#### Resolved Issues

- Fixed: The complication picker no longer shows entries for uninstalled system apps. (110474713)

### CoreMotion Movement Disorder API

#### Resolved Issues

- Fixes an internal crash that can occur when device is locked or turned off for an extended period of time. (110964474)

### FinanceKit

#### Resolved Issues

- Fixed: It isn’t currently possible to import FinanceKit. (109450892)

### Find My

#### Resolved Issues

- Fixed: Watches in Standalone mode don’t monitor for when AirTags, items, or iPhone are left behind. (109787334)

### Home Screen

#### Resolved Issues

- Fixed: The new Grid View & List View buttons might exhibit formatting issues. (109476908)

### Localization

#### Resolved Issues

- Fixed: Some content might appear in English. Some strings might appear clipped. (109393568)

### Maps

#### Resolved Issues

- Fixed: When using `Map`, Xcode emits a runtime warning that “Publishing changes from within view updates is not allowed.” (106174743)

- Fixed: At certain zoom levels, the title of a selected `MKMarkerAnnotationView` can overlap other marker titles. (109491779)

### Media

#### Resolved Issues

- Fixed: MP3 files with malformed ID3 tags will fail to play (110230071)

### NetworkExtension

#### Deprecations

- Algorithms DES, 3DES, SHA1-96 and SHA1-160 as well as Diffie-Hellman groups less than 14 are deprecated for IKEv2 VPNs. (109427094)

### Networking

#### New Features

- `URLSession` supports resumable uploads in HTTP. Just like download tasks, upload tasks can now be paused and resumed if the server supports the latest protocol draft. To learn more, see Resumable Uploads for HTTP. (68890505)

- Apple devices now support connection to 802.1X networks using EAP-TLS with TLS 1.3 (EAP-TLS 1.3). EAP-TLS 1.3 further improves security and privacy by always providing forward secrecy, never disclosing the peer identity, and by mandating use of revocation checking when compared to EAP-TLS with earlier versions of TLS. (74526852)

#### Resolved Issues

- Fixed: For apps linked on or after iOS 17 and aligned OS versions, App Transport Security now requires secure connections to external IP addresses by default. For more information on these requirements, see Preventing Insecure Network Connections. Exceptions can be made using NSExceptionDomains, which now supports exceptions for individual IP addresses and ranges specified in classless inter-domain routing (CIDR) notation. (101967030)

- Fixed: For apps linked on or after iOS 17 beta, macOS 14 beta, watchOS 10 beta, and tvOS 17 beta, the `Transfer-Encoding` header field of a streamed `HTTP/1` request is set to `chunked` instead of `Chunked`. (107390029)

### Notification

#### Resolved Issues

- Fixed: Notification long look layouts are not properly aligned. (110922537)

### Privacy

#### Resolved Issues

- Fixed: Time in Daylight is supported on Apple Watch Series 5 and later. However, when using a model of Apple Watch which doesn’t support Time in Daylight, the privacy toggle switch is still displayed even though toggling it has no effect. On Apple Watch, the toggle is located in Settings \> Privacy & Security \> Health \> Time in Daylight. On iPhone, the toggle is located in Watch app \> Privacy \> Time in Daylight. (108907052)

### ShazamKit

#### Resolved Issues

- Fixed: `SHManagedSession.State` is unavailable. (109670750)

- Fixed: `SHLibrary.default.items` is unavailable. (109670918)

### Siri Announce Notifications

#### Resolved Issues

- Fixed: Workout start and end reminder announcements don’t respect the global Announce Notifications setting. (109281407)

### StoreKit

#### New Features

- Users have access to the new `Product.SubscriptionInfo.Status.all` sequence to get the status for each of your app’s subscription groups. One can use the new `subscriptionStatus` property on the latest Transaction value for a subscription to access the full status information. (102064614)

- StoreKit 2 now provides a collection of UI components to help merchandise in-app purchases. Use `ProductView`, `StoreView` and `SubscriptionStoreView` to add in-app purchases to an app with just a few lines of code. (102066107)

- Users can access in-app purchase product metadata and entitlement information from a SwiftUI view using new view modifier APIs in StoreKit. Declare a view as dependent on a single product or collection of products using `storeProductTask(for:priority:action:)` or `storeProductsTask(for:priority:action:)` respectively. Declare a view as dependent on the current entitlement for a product using `currentEntitlementTask(for:priority:action:)`. Declare a view as dependent on the status of a subscription group with `subscriptionStatusTask(for:priority:action:)`. All of the modifiers will start a task to load the data before the view appears, and provide your action with the state of the task as it progresses and whenever the data changes. (102397222)

- User have access to the new `groupLevel` property of Product.SubscriptionInfo to understand the level of service of a subscription plan. (103885148)

- Users have access to the new `reason`, and `storefront` properties on Transaction to understand the reason why the transaction was created, and which storefront it is for. The new `renewalDate` property on RenewalInfo to understand if and when a subscription will renew next. (104246730)

- Users have access to new `groupDisplayName` property of Product.SubscriptionInfo to get the localized display name of a subscription plan’s group. (105689964)

- You can now customize the button style used for purchase and subscribe buttons in ProductView, StoreView and SubscriptionStoreView instances. Use the buttonStyle(_:) view modifier to choose any standard button style, or a custom button style. (107713282)

- StoreKit Views`ProductView` and `StoreView` have initializers have initializers that give you access to the promotional icon as a SwiftUI view and the various phases of the loading operation. Use initializers such as init(id:icon:placeholderIcon:), \[`init(_:icon:)]`(https://developer.apple.com/documentation/storekit/productview/4202214-init), init(ids:icon:placeholderIcon:)](https://developer.apple.com/documentation/storekit/storeview/4203378-init), and [init(products:icon:)` to provide an icon view for each phase. (110470147)

- The following StoreKit types are renamed:

  • `DefaultProductViewStyle` is renamed to AutomaticProductViewStyle

  • `DefaultSubscriptionStoreMarketingContent` is renamed to AutomaticSubscriptionStoreMarketingContent

  • `DefaultProductPlaceholderIcon` is renamed to AutomaticProductPlaceholderIcon (111185321)

#### Resolved Issues

- Fixed: When testing in the sandbox environment, the `groupDisplayName` property on Product.SubscriptionInfo might return an empty string if the localization in the current storefront is not in an approved state. When using the `SubscriptionStoreView` without providing a marketing content view, the automatic view might show the name of the app instead of the subscription group’s display name. (107206601)

- Fixed issue where StoreView or SubscriptionStoreView content might appear in English, or show a localization key, instead of showing localized text for the App Store storefront. (110734447)

### Swift

#### New Features

- Properties of @Observable and @Model types currently always require default values or optionality. (109441094)

### Swift Charts

#### New Features

- Enable scrolling in a chart using view modifier `chartScrollableAxes(_:)`. (70444254)

- Use `chartXSelection`, `chartYSelection` and `chartAngleSelection` to enable selection on a chart. If needed, use `chartGesture` to override the default gesture for selection. (79083764)

- Swift Charts now supports creating pie charts and donut charts using the new `SectorMark` API. (102309263)

- Pass an `AnnotationOverflowResolution` to the `annotation` modifier to specify how to align an annotation when it would otherwise overflow the bounds of the chart or the plot. (106009062)

- Use `ChartProxy.plotContainerFrame` to obtain the visible portion of the plot in a scrollable chart.

  ```
  ```

  (109675790)

#### Resolved Issues

- Fixed a crash with certain combinations of chart content. (105197081)

- Fixed an issue where frequent updates to a chart caused unexpected growth in memory footprint. (107611114)

- Fixed: When a selection gesture goes out of bounds, the selection binding will now be clamped to the nearest data value rather than set to `nil`. (108398019)

- Fixed: Improved performance and CPU usage for charts with selection bindings. (108954531)

- Fixed: Scrolling charts might behave unexpectedly on right-to-left languages. (109129343)

- Fixed: Improved animations for charts in a widget. (110035011)

- Fixed an issue where the `compositingLayer` chart content modifier caused marks with custom symbols to disappear. (110399956)

- Fixed an issue where the `compositingLayer` chart content modifier caused annotation boundary resolutions to behave unexpectedly. (112232314)

- Fixed: Improved performance and CPU usage for scrolling charts with scroll position bindings. (113149095)

#### Known Issues

- Annotations on a scrollable chart might be clipped. (109164195)

### SwiftData

#### New Features

- Existing `@Query` property declarations might not always correctly infer the model type for predicate and sort descriptor parameters. (Note: the `@Query` attribute is now resolved as a macro, instead of as a property wrapper.)

  For example, specifying a filter predicate as a parameter to the `@Query` attribute will now require explicitly providing the model type used in the predicate, i.e. `#Predicate { … }` instead of `#Predicate { … }`:

  ```
  ```

  Another example: passing a sort descriptor or key path will now require explicitly providing the model type used for the root type of the key path, i.e. `\ModelType.property` instead of `\.property`:

  ```
  ```

  In all cases, the model type used in the `filter:` and `sort:` parameters is still required to be the same type used as the element in the query’s wrapped array type, and will emit a build error if not. (109433172)

#### Resolved Issues

- Fixed: Properties with default values are not initialized correctly. (107887871)

- Fixed: @Query results can appear stale or fail to refresh. (108385553)

- Fixed: Case value is not stored properly for a string rawvalue enumeration. (108634193)

- Fixed: Schema migration can fail when nesting non-optional properties inside an optional containing struct. (108854663)

- Fixed: Properties with .externalStorage are not being stored in peripheral files. (108972391)

- Fixed: Scene modifier isUndoEnabled does not propagate correctly. (109373617)

- Fixed: Modeled enum properties with default values won’t compile unless they are fully qualified values. (109421492)

- Fixed: SwiftData queries will not work with \#Predicate { true } and \#Predicate { false } will cause a crash. (109425342)

- Fixed: Conflicting writes from other processes sharing the same file can cause a crash. (109488127)

- Fixed: `#Predicate` does not support UUID, Date, and URL properties. (109539652)

- Fixed: `@Query` using `SortDescriptors` based on `.reverse` sorting on strings can fail to fetch results. (109572633)

- Fixed: Creating a @Query with a sortdescriptor that uses a relationship keypath will crash. (109626376)

- Fixed: `willSet` and `didSet` observers will prevent `@Model` from properly transforming those stored properties and they will not persist. (109664186)

- Fixed: SwiftData queries don’t support some `#Predicate` `flatmap` and `nil` coalescing behaviors. (109723704)

- Fixed: Xcode code generation for SwiftData Models from CoreData xcdatamodels will refer to `originalName` instead of `renamingIdentifier`. (109782236)

- Fixed: Unsigned applications using Document API without a proper app container might overwrite the default container. (109784405)

- Fixed: After deleting an item, SwiftUI might attempt to reference the deleted content during the animation causing a crash. (109838173)

- Fixed: Custom schema migrations with SchemaMigrationPlan will fail. (110114696)

- Fixed in beta 7: Apps using SwiftData that are built with Xcode 15 beta 6 have known issues when running on watchOS 10 beta 6. (113971391)

#### Known Issues

- SwiftData models with implicitly unwrapped optional properties will generate a compiler error that all stored properties were not set. (114140139)

  **Workaround:** Set the value of non-relationship stored properties in the initializer, and mark relationship properties as optional.

### SwiftUI

#### New Features

- `RoundedRectangle` now defaults to the continuous corner style. (63246947)

- `.onChange` has new overloads where the closure takes 0 or 2 arguments, these new versions will call the new version of the closure (i.e. after the specified value has changed), so any captured properties will have up to date values. The previous overload (which calls the old version of the closure) has been deprecated. (67344857)

- Spring animations will now default to being critically damped (i.e. a bounce of 0). (75149732)

- `List`s using the `SidebarListStyle` hosted in primary column of a UIKit `UISplitNavigationController` were previously rendering with an `insetGrouped` appearance. With this change they will render as the expected `sidebar` appearance similar to if the `List` were hosted in a SwiftUI `NavigationSplitView`. (96909195)

- DatePicker is available for watchOS. (100660577)

- The `.scenePadding` modifier is updated with new values for the bottom edge. (100770506)

- `ContainerRelativeShape` can be used with `.listRowBackground` to clip a custom list row view. (100807501)

- Use the `buttonRepeatBehavior(_:)` view modifier to make buttons repeatedly trigger their actions on prolonged interactions. Apply this to buttons that increment or decrement a value or perform some other inherently iterative operation. Interactions such as pressing-and-holding on the button, holding the button’s keyboard shortcut, and holding down the space key while the button is focused trigger this repeat behavior. (102156410)

- `Button` now defaults to a capsule border shape. The `.controlSize` modifier can be used on `Button` to adjust the size. (102831384)

- `Animation.default` now uses a spring animation equivalent to `Animation.spring`. In addition, `Animation.default` is now only equal to itself when using `==`, allowing users to differentiate between animations that were intentionally chosen and those that use the `default` animation. (103169056)

- `NavigationSplitView` has an updated appearance and navigation animation. (103369829)

- During gesture change callbacks, velocity will automatically be tracked so that it can be applied to animations that finish when the gesture finishes. (103371523)

- Lists using `CarouselListStyle` can now use section headers and footers. (103455814)

- When two Text are vertically adjacent (for example in a VStack with no spacer in between) SwiftUI will automatically calculate appropriate spacing. To opt-out if this behavior either place a Spacer or specify spacing parameter to the container view. (104782785)

- The default style for List headers has been updated to be sentence case and use a white foreground color. (104893841)

- For apps built using the macOS 14 SDK, using `DismissAction` to close a window will default to using `DismissBehavior.interactive`. (105406945)

- Applying a `.listItemTint` to a `List` item will use an updated vibrant fill `Color`. (105684967)

- `.fullScreenCover` and `.sheet` presentation now use a thin material blur background by default. The `.presentationBackground` modifier can be used to customize this behavior. (105862381)

- A `NavigationSplitView` collapses into a single column in some situations, such as on iPhone, Apple Watch, or iPad in slide-over. When this happens the columns of the split view are arranged into a stack. By default, the split view automatically decides which column appears as the top of this stack based on the contents of the columns. It considers whether any embedded `List` views have selections and whether any embedded `NavigationStack` views have non-empty paths.

  `NavigationSplitView` provides new initializers that give users control over which column of the split view appears on top. Use initializers like `NavigationSplitView(preferredTopColumn:sidebar:content:detail:)` or `NavigationSplitView(preferredTopColumn:sidebar:detail:)` and provide a binding specifying the column that should be visible when the split view is collapsed into a stack. When using an app pops the stack, SwiftUI updates the binding. (106241051)

- When using `@Environment(\.self)` to capture an entire `EnvironmentValues`, SwiftUI will now track which properties are accessed to only invalidate the property when those properties change. (106310433)

- Use the new `navigationDestination(item:destination:)` overload to present a navigation destination when a bound item is non-`nil`, or to dismiss the destination when the bound item becomes `nil` again. (106319528)

- Lists, buttons, and other controls and content will automatically use a vibrant appearance when used with a presentation with a Material background or a `containerBackground` color gradient. (106621782)

- Shapes now default to mirroring when in a right to left layout direction. (107405880)

- Changing from one Gradient value to another will now animate, but only once apps are rebuilt against the new SDK. (107408691)

- All `Section`s inside `List` and `Table` can be configured to be collapsible using new initializers on Section. Previously all `Section`s inside `List`s using the `SidebarListStyle` received outline disclosure indicators in every header. Section headers will no longer render this control by default. An outline disclosure will only be provided in the header if the `Section` is initialized with an `isExpanded` binding to a bool. This bool represents the `isExpanded` state of the `Section`. Sections created with an `isExpanded` binding inside a `Table` on macOS will now provide a default outline disclosure indicator to collapse or expand the `Section`. (107592493)

#### Resolved Issues

- Fixed: `NavigationSplitView` reuses view controllers in more cases, resulting in significantly improved performance. This might change the behavior of code that relies on the life cycle messages sent to `UIHostingController` because such controllers will be created less often. (88880547)

- Fixed: Scroll environment properties like isScrollEnabled and scrollDismissesKeyboardMode are no longer propagated past nested scroll views. (99195890)

- Fixed: Previously it was possible for views animating their removal via a transition to be drawn above a view with the same zIndex that has not yet been removed. This was unintentional and has now been updated: views transitioning out of the view hierarchy are always drawn below non-removed views with the same zIndex. (101085960)

- Fixed: LazyVGrid or LazyHGrid has an improved layout when used with fixedSize(). (103075945)

- Fixed: Animations coordinated with `TabView` selection won’t interactively update as the tab selection changes. (105618295)

- Fixed: The new `.navigationDestination(item:content:)` modifier now works correctly both inside a `NavigationStack` and outside a stack but inside a column of a `NavigationSplitView`.

  Inside a stack, setting the bound item to a non-nil value will push a view onto the stack immediate above the view containing the modifier. Setting the bound item to a nil value will pop the view.

  Outside a stack but inside a column of a `NavigationSplitView`, setting the bound item to a non-nil value will replace the root view of the subsequent column. Setting the bound item to a nil value will restore the original root view. (106106406)

- Fixed: In some circumstances, the first view pushed onto a `NavigationStack` or collapsed `NavigationSplitView` might fail to animate. (106602046)

- Fixed: When a flexible frame modifier (e.g. frame(minHeight: 100, maxHeight: 200)) is used inside a scroll view the modified view could end up truncating content. This would most often be visible with the content view being a VStack with multiline text. (107014454)

- Fixed: When scrolling to the end of a scroll view using ScrollViewReader, the final offset will be clamped to the scroll view’s total content size and no longer overscroll. (107558652) (FB12094127)

- Fixed: Removed a spurious warning, “NavigationLink presenting a value must appear inside a NavigationContent-based NavigationView. Link will be disabled.” (107877668) (FB12111423)

- Fixed: ScrollView when used with the searchable modifier has an improved transition when presenting or dismissing search on iOS and iPadOS. (109265624)

- Fixed: Two `NavigationSplitView` initializers taking `columnVisibility` as a value rather than a `Binding`. (109426553)

#### Known Issues

- On iOS, using an `Observable` object’s property as a selection value of a `List` inside `NavigationSplitView` may cause a “Simultaneous accesses to …” error when a list selection is made via tap gesture. (113978783) (FB12981860)

  **Workaround:** There is no current workaround for `Observable` properties. Alternatives include factoring out the selection value into separate state stored outside the object, or using `ObservableObject` instead.

### Symbol Effects

#### Resolved Issues

- Fixed: In the objective-C API in Symbols.framework, requesting `effectWithWholeSymbol` on `NSSymbolPulseEffect` and `NSSymbolBounceEffect` will result in the effect being configured to animate by layer instead. (109284710)

### Voicemail

#### Resolved Issues

- Fixed: Watches using Family Setup are currently missing carrier voicemail setup options. (108240544)

- Fixed: Voicemails don’t sync to Watch. (108818345)

### Watch Faces

#### Resolved Issues

- Fixed: Complication previews might not appear in the Face Gallery in the Watch app on iPhone. (109134263)

### WidgetKit

#### Resolved Issues

- Fixed: `accessoryCorner` widgets that use the `widgetCurvesContent` modifier don’t get their `widgetURL` passed to their containing app on launch. (109372819)

- Fixed: Using ViewThatFits within a .widgetLabel will result in the .widgetLabel not appearing in .accessoryCorner widgets. (109782549)

- Fixed: Apps that use the `.showsWidgetContainerBackground` environment variable no longer crash. (113947483) (FB12974903)

### Workout

#### Resolved Issues

- Fixed: A workout might not display Speed or Distance. (110127447)

#### Known Issues

- Changing the watch language or region only updates some of the text in the watch browsing views for Fitness+ Meditations and Time to Walk/Time to Run Workouts. (113168750)

  **Workaround:** Change the language or region setting for the watch while Workout app is open to the New Releases view of Time to Walk/Time to Run (Workout app \> Time to Walk/Time to Run tile) or while the Mind app is open to the New Releases view of Fitness+ Meditations (Mind app \> Fitness+)

## See Also

### watchOS 10

watchOS 10.6 Release Notes

Update your apps to use new features, and test your apps against API changes.

watchOS 10.5 Release Notes

Update your apps to use new features, and test your apps against API changes.

watchOS 10.4 Release Notes

Update your apps to use new features, and test your apps against API changes.

watchOS 10.3 Release Notes

Update your apps to use new features, and test your apps against API changes.

watchOS 10.2 Release Notes

Update your apps to use new features, and test your apps against API changes.

watchOS 10.1 Release Notes

Update your apps to use new features, and test your apps against API changes.

