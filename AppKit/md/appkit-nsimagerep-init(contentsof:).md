

- AppKit
- NSImageRep
-  init(contentsOf:) 

Initializer

# init(contentsOf:)

Creates and returns an image representation object using the data at the specified URL.

macOS

``` source
init?(contentsOf url: URL)
```

## Parameters 

`url`  

The URL pointing to the image data.

## Return Value

An initialized instance of an `NSImageRep` subclass, or `nil` if the image data could not be read.

## Discussion

If sent to the `NSImageRep` class object, this method returns a newly allocated instance of a subclass of `NSImageRep` initialized with the contents of the specified URL. If sent to a subclass of `NSImageRep` that recognizes the data contained in the URL, it returns an instance of that subclass initialized with the data in the URL.

This method returns `nil` in any of the following cases:

- The message is sent to the `NSImageRep` class object and there are no subclasses in the `NSImageRep` class registry that handle the data contained in the specified URL.

- The message is sent to a subclass of `NSImageRep` and that subclass cannot handle the data contained in the specified URL.

- The `NSImageRep` subclass is unable to initialize itself with the contents of the specified URL.

The `NSImageRep` subclass is initialized by creating an `NSData` object based on the contents of the file, then passing it to the `imageRepWithData:` method.

## See Also

### Creating Representations of Images

class func imageReps(withContentsOfFile: String) -> [NSImageRep]?

Creates and returns an array of image representation objects initialized using the contents of the specified file.

class func imageReps(with: NSPasteboard) -> [NSImageRep]?

Creates and returns an array of image representation objects initialized using the contents of the pasteboard.

class func imageReps(withContentsOf: URL) -> [NSImageRep]?

Creates and returns an array of image representation objects initialized using the contents of the specified URL.

init?(contentsOfFile: String)

Creates and returns an image representation object using the contents of the specified file.

init?(pasteboard: NSPasteboard)

Creates and returns an image representation object using the contents of the specified pasteboard.

init()

Creates and returns an image representation object.

init?(coder: NSCoder)

Creates and returns an image representation object from data in an unarchiver.

