Framework

# TVUIKit

Show common user interface elements from Apple TV in your native app.

tvOS 12.0+

## [Overview](/documentation/TVUIKit#overview)

When you build an app for tvOS with [UIKit](/documentation/UIKit), you can use [TVUIKit](/documentation/tvuikit) to refine the display of your content for a TV environment. Use the [TV Services](/documentation/TVServices) framework to provide deeper integration between your app and Apple TV.

For more information about combining Apple technologies to build a great Apple TV experience, see [Planning your tvOS app](https://developer.apple.com/tvos/planning/#build-the-data-structures-youll-use-in-your-app).

![A figure containing a hexagonal UIKit framework icon, an arrow pointing to the right, a hexagon with the label TVUIKit, an arrow pointing to the right, and a TV screen. The TV screen shows a centered image of a palm tree, with other images partially visible on either side of the palm tree.](https://docs-assets.developer.apple.com/published/0ac9f4c161a4bb424a89960bc2d42e7a/media-4133629%402x.png)

## [Topics](/documentation/TVUIKit#topics)

### [Collections of content](/documentation/TVUIKit#Collections-of-content)

[

Creating immersive experiences using a full-screen layout](/documentation/tvuikit/creating-immersive-experiences-using-a-full-screen-layout)

Display content with a collection view that maximizes the tvOS experience.

```swift
```swift
```swift
class TVCollectionViewFullScreenLayout
```
```

A collection view layout that organizes items into a browsable, full-screen display format.
```
```swift
```swift
```swift
protocol TVCollectionViewDelegateFullScreenLayout
```
```

Methods that send notifications of events during cell transitions.
```
```swift
```swift
```swift
class TVCollectionViewFullScreenCell
```
```

A full-screen cell to use in full-screen display format.
```
```swift
```swift
```swift
class TVCollectionViewFullScreenLayoutAttributes
```
```

Attributes to manage the appearance of the collection view’s layout.
```

### [Content views](/documentation/TVUIKit#Content-views)

```swift
```swift
```swift
```swift
class TVMediaItemContentView
```
```

A view that represents media content, such as movies and TV shows.
```
```swift
```swift
```swift
class TVMonogramContentView
```
```

A view that contains a circular image of a person or the person’s initials.
```
```

### [Numeric input](/documentation/TVUIKit#Numeric-input)

```swift
```swift
```swift
```swift
class TVDigitEntryViewController
```
```

A view controller that enables the user to enter digits, like a passcode, in your app.
```
```

### [Lockup views](/documentation/TVUIKit#Lockup-views)

```swift
```swift
```swift
```swift
class TVLockupView
```
```

A focusable view that presents main content, like a movie poster, and an optional header and footer.
```
```swift
```swift
```swift
protocol TVLockupViewComponent
```
```

The protocol for responding to lockup view state changes.
```
```swift
```swift
```swift
class TVLockupHeaderFooterView
```
```

A view that contains header and footer information.
```
```swift
```swift
```swift
class TVCardView
```
```

A view that responds to focus interaction with a motion effect it applies to all of its subviews.
```
```swift
```swift
```swift
class TVPosterView
```
```

An optimized view for displaying an image, a header, and a footer.
```
```swift
```swift
```swift
class TVCaptionButtonView
```
```

A button-like view that responds to user interactions.
```
```swift
```swift
```swift
class TVMonogramView
```
```

A specialized lockup view that contains a circular image of a person or the person’s initials, along with a footer view.

Deprecated
```
```