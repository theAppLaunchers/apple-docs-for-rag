

- UIKit
- UIImagePickerController
-  mediaTypes 

Instance Property

# mediaTypes

An array that indicates the media types to access by the media picker controller.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.1+visionOS 1.0+

``` source
@MainActor
var mediaTypes: [String] { get set }
```

## Discussion

Depending on the media types you assign to this property, the picker displays a dedicated interface for still images or movies, or a selection control that lets the user choose the picker interface. Before setting this property, check which media types are available by calling the availableMediaTypes(for:) class method.

If you set this property to an empty array, or to an array in which none of the media types is available for the current source, the system throws an exception.

When capturing media, the value of this property determines the camera interface to display. When browsing saved media, this property determines the types of media presented in the interface.

By default, the value of this property is the image (Swift) or `kUTTypeImage` (Objective-C) identifier, which designates the still camera interface when capturing media, and specifies that only still images should be displayed in the media picker when browsing saved media. The following example shows how to designate the movie capture interface, or to indicate that only movies should be displayed when browsing saved media:

- Swift
- Objective-C

```
myImagePickerController.mediaTypes = [ UTType.movie.identifier ]
```

```
myImagePickerController.mediaTypes =
    [[NSArray alloc] initWithObjects: (NSString *) kUTTypeMovie, nil];
```

Note

If you want to display a Live Photo rendered as a Loop or a Bounce, you must include the movie (Swift) or `kUTTypeMovie` (Objective-C) identifier.

To designate all available media types for a source, use a statement like this:

- Swift
- Objective-C

```
if let mediaTypes = UIImagePickerController.availableMediaTypes(for: .camera) {
    myImagePickerController.mediaTypes = mediaTypes
}
```

```
myImagePickerController.mediaTypes =
    [UIImagePickerController availableMediaTypesForSourceType:
        UIImagePickerControllerSourceTypeCamera];
```

## See Also

### Configuring the picker

var allowsEditing: Bool

A Boolean value that indicates whether the user is allowed to edit a selected still image or movie.

