

- AppKit
-  NSMediaLibraryBrowserController 

Class

# NSMediaLibraryBrowserController

An object that configures and displays a Media Library Browser panel.

macOS 10.9+

``` source
class NSMediaLibraryBrowserController
```

## Overview

From this panel a user can drag media into views in their app. The class provides a standard interface to the MediaLibrary framework content.

Note

The Media Library Browser panel is not an `NSPanel` instance. It has panel like methods to remotely control the Media Library Browser. Clients have no direct programmatic access to the panel displaying the Media Library Browser.

For more information see MLMediaLibrary, MLMediaSource, MLMediaGroup, and MLMediaObject in Media Library.

### Pasteboard Types

The Media Library Browser defines two pasteboard types for decoding the dragged content and retrieving the media content that is appropriate, one for mediagroup content and one for individual media items

- The `com.apple.MediaLibrary.PboardType.MediaGroupIdentifiersPlist` pasteboard type describes media group content and is published when the user drags items from the upper media-group-organized pane of the Media Library Browser.

- The `com.apple.MediaLibrary.PboardType.MediaObjectIdentifiersPlist` pasteboard type describes individual media items and is published when the user drags media items such as images, movies, or sounds from the media item pane of the Media Library Browser.

There is a third, less specialized, type of media library pasteboard. When the user initiates a drag the pasteboard will contain an array with one more more NSFilenamesPboardType pasteboard items, one for each of the files within the group dragged from the media-group-organized pane, and one or more items when a media item or items are dragged from the media item pane.

If you do not need access to the associated Media Library metadata, using the `NSFilenamesPboardType` pasteboard data is the simplest means of retrieving the dragged content, although accessing the media in this manner when your app is sandboxed requires that you use the `NSURL` startAccessingSecurityScopedResource() and stopAccessingSecurityScopedResource() methods.

#### The Media Group Pasteboard Type

The `"com.apple.MediaLibrary.PboardType.MediaGroupIdentifiersPlist"` pasteboard type is published when the user drags items from the upper media-group-organized pane of the Media Library Browser.

It consists of an `NSDictionary` plist that contains`keys` with the media source identifiers and corresponding `value` that are arrays of media group identifiers.

To decode the pasteboard data and get `MLMediaGroup` instances, assuming you have an `MLMediaLibrary` instance, use the techniques illustrated in the code listing below.

Listing 1. Retrieving MLMediaGroup instances from the pasteboard

```
NSDictionary *mediaGroupsDict = [dragPasteboard propertyListForType:@"com.apple.MediaLibrary.PBoardType.MediaGroupIdentifiersPlist"];
    if ( mediaGroupsDict )
    {
        [s appendFormat:@"Media Groups Dictionary: %@\n", mediaGroupsDict];
        [s appendString:@"Media Groups:\n"];
        for ( NSString *sourceIdentifier in [mediaGroupsDict allKeys] )
        {
            MLTAppDelegate *appDelegate = (MLTAppDelegate *)[[NSApplication sharedApplication] delegate];
            MLMediaLibrary *mediaLibrary = appDelegate.mediaLibrary;
            MLMediaSource *mediaSource = [mediaLibrary.mediaSources objectForKey:sourceIdentifier];
            if ( mediaSource )
            {
                NSArray *groupIdentifiers = [mediaGroupsDict objectForKey:sourceIdentifier];
                for ( NSString *groupIdentifier in groupIdentifiers )
                {
                    MLMediaGroup *mediaGroup = [mediaSource mediaGroupForIdentifier:groupIdentifier];
                    [s appendFormat:@"%@\n", mediaGroup];
                }
            }
        }
    }
```

#### The Media Object Pasteboard Type

The `"com.apple.MediaLibrary.PboardType.MediaObjectIdentifiersPlist"` pasteboard type is published when the user drags an item from the media item pane of the Media Library Browser.

It consists of an `NSDictionary` plist that contains`keys` with the media source identifiers and corresponding `value` that are arrays of media object identifiers.

To decode the pasteboard data and get `MLMediaObject` instances, assuming that you have an MLMediaLibrary instance, use the techniques illustrated in the code listing below.

Listing 2. Retrieving MLMediaObject instances from the pasteboard

```
 NSDictionary *mediaObjectsDict = [dragPasteboard propertyListForType:@"com.apple.MediaLibrary.PBoardType.MediaObjectIdentifiersPlist"];
    if ( mediaObjectsDict )
    {
        [s appendFormat:@"Media Objects Dictionary: %@\n", mediaObjectsDict];
        [s appendString:@"Media Objects:\n"];
        for ( NSString *sourceIdentifier in [mediaObjectsDict allKeys] )
        {
            MLTAppDelegate *appDelegate = (MLTAppDelegate *)[[NSApplication sharedApplication] delegate];
            MLMediaLibrary *mediaLibrary = appDelegate.mediaLibrary;
            MLMediaSource *mediaSource = [mediaLibrary.mediaSources objectForKey:sourceIdentifier];
            if ( mediaSource )
            {
                NSArray *objectIdentifiers = [mediaObjectsDict objectForKey:sourceIdentifier];
                for ( NSString *objectIdentifier in objectIdentifiers )
                {
                    MLMediaObject *mediaObject = [mediaSource mediaObjectForIdentifier:objectIdentifier];
                    [s appendFormat:@"%@\n", mediaObject];
                }
            }
        }
    }
```

## Topics

### Creating a Media Library Browser Panel

class var shared: NSMediaLibraryBrowserController

Returns the shared Media Library Browser instance.

### Displaying the Media Library Browser Panel

var frame: NSRect

The frame, in global coordinates, used to display the Media Library Browser panel.

func togglePanel(Any?)

Toggles the visibility of the Media Library Browser.

var isVisible: Bool

A Boolean value that determines whether the Media Library Browser panel is visible.

### Displayed Media Library Types

var mediaLibraries: NSMediaLibraryBrowserController.Library

The media library that is in use.

### Constants

struct Library

These constants are masks used to configure a Media Library Browser to display specific types of media. Combined masks are not yet supported. In other words, only one nonzero mask value is supported at a time. If masks are combined, the lowest mask value is used.

## Relationships

### Inherits From

- NSObject

### Conforms To

- CVarArg
- CustomDebugStringConvertible
- CustomStringConvertible
- Equatable
- Hashable
- NSObjectProtocol

