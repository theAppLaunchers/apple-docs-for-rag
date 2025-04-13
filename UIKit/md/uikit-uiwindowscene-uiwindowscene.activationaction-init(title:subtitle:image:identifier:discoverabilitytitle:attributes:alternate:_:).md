

- UIKit
- UIWindowScene
- UIWindowScene.ActivationAction
-  init(title:subtitle:image:identifier:discoverabilityTitle:attributes:alternate:\_:) 

Initializer

# init(title:subtitle:image:identifier:discoverabilityTitle:attributes:alternate:\_:)

Creates an activation action using the specified parameters.

iOS 15.0+iPadOS 15.0+Mac CatalystvisionOS

``` source
@MainActor @preconcurrency
convenience init(
    title: String? = nil,
    subtitle: String? = nil,
    image: UIImage? = nil,
    identifier: UIAction.Identifier? = nil,
    discoverabilityTitle: String? = nil,
    attributes: UIMenuElement.Attributes = [],
    alternate: UIAction? = nil,
    _ configuration: @escaping UIWindowScene.ActivationAction.ConfigurationProvider
)
```

## Parameters 

`title`  

The title to display for the action.

`subtitle`  

The subtitle to display for the action.

`image`  

The image to display next to the action’s title. Only the context menu system supports the display of an image, and only when the app is running in iOS.

`identifier`  

The unique identifier for the action. Specify `nil` to let this method create a unique identifier for you.

`discoverabilityTitle`  

An elaborated title that explains the purpose of the action.

`attributes`  

The attributes indicating the style of the action.

`alternate`  

An alternate action to perform if the platform doesn’t support multiple scenes or if requesting a scene fails.

`configuration`  

The closure the system calls when the user selects the action. The closure should return a UIWindowScene.ActivationConfiguration object.

## See Also

### Creating an activation action

typealias ConfigurationProvider

A type alias defining a closure that provides an activation configuration for the activation action.

