

- Foundation
- FileManager
-  delegate 

Instance Property

# delegate

The delegate of the file manager object.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.1+macOS 10.5+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
unowned(unsafe) var delegate: (any FileManagerDelegate)? { get set }
```

## Discussion

It is recommended that you assign a delegate to the file manager object only if you allocated and initialized the object yourself. Avoid assigning a delegate to the shared file manager obtained from the default method.

The default value of this property is `nil`. When assigning a delegate to this property, your object must conform to the FileManagerDelegate protocol.

