

- SwiftUI
- LayoutSubview
-  subscript(\_:) 

Instance Subscript

# subscript(\_:)

Gets the value for the subview that’s associated with the specified key.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+tvOS 16.0+visionOS 1.0+watchOS 9.0+

``` source
subscript(key: K.Type) -> K.Value where K : LayoutValueKey { get }
```

## Overview

If you define a custom layout value using LayoutValueKey, you can read the key’s associated value for a given subview in a layout container by indexing the container’s subviews with the key type. For example, if you define a `Flexibility` key type, you can put the associated values of all the layout’s subviews into an array:

```
let flexibilities = subviews.map { subview in
    subview[Flexibility.self]
}
```

For more information about creating a custom layout, see Layout.

