

- Foundation
- NSItemProvider
-  NSItemProvider.LoadHandler 

Type Alias

# NSItemProvider.LoadHandler

A block that loads the item provider’s data and coerces it to the specified type.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.0+macOS 10.0+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
typealias LoadHandler = (NSItemProvider.CompletionHandler?, AnyClass?, [AnyHashable : Any]?) -> Void
```

## Discussion

Use this block when registering a type-specific coercion handler with the registerItem(forTypeIdentifier:loadHandler:) method. The parameters for this block are as follows:

completionHandler  
The completion handler to call with the resulting data. For information about this block, see NSItemProvider.CompletionHandler.

expectedValueClass  
The expected class of the item being loaded. Convert the item provider’s data to this type and pass the resulting object as the first parameter of the `completionHandler` block.

options  
A dictionary with options for how to provide the requested item. For example, the dictionary may contain the pixel dimensions of a requested image. For information about the supported keys, see Options Dictionary Key.

When a client calls the loadItem(forTypeIdentifier:options:completionHandler:) method and requests the appropriate type, the item provider executes your block. In your implementation, create an object of the expected type and execute the block in the `completionHandler` parameter, passing the newly created object as the first parameter of that block. If there is an error, pass `nil` for the object and provide an appropriate NSError object explaining what happened.

This type of block is also used for generating preview images. In the case of a preview image, the `expectedValueClass` is always a NSData, NSURL, UIImage (in iOS), or NSImage (in macOS) class.

## See Also

### Constants

typealias CompletionHandler

A block that receives the item provider’s data.

Options Dictionary Key

Keys indicating options to use when generating the item provider’s data.

Keys for Items Accessed in JavaScript Code

Keys in property list items that the system recieves from or sends to JavaScript code.

class let errorDomain: String

The error domain associated with the item provider.

struct NSItemProviderFileOptions

Data-access specifications that declare how to handle items.

protocol NSItemProviderReading

The protocol for implementing a class to allow an item provider to create an instance of the class.

protocol NSItemProviderWriting

The protocol for implementing a class to allow an item provider to retrieve data from an instance of the class.

enum NSItemProviderRepresentationVisibility

Specifications that control which categories of processes can see an item.

enum ErrorCode

The error codes that describe problems with consuming data from an item provider.

