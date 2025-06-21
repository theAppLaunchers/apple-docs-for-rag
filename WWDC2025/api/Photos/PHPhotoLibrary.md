*   [Photos](/documentation/photos)
*   PHPhotoLibrary

Class

# PHPhotoLibrary

An object that manages access and changes to the user’s photo library.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.1+macOS 10.13+tvOS 10.0+visionOS 1.0+

```swift
```swift
```swift
```swift
```swift
```swift
```swift
```swift
class PHPhotoLibrary
```
```
```
```
```
```
```
```

## [Mentioned in](/documentation/Photos/PHPhotoLibrary#mentions)

[

Editing Asset Content](/documentation/photokit/editing-asset-content)

[

Fetching Assets](/documentation/photokit/fetching-assets)

[

Delivering an Enhanced Privacy Experience in Your Photos App](/documentation/photokit/delivering-an-enhanced-privacy-experience-in-your-photos-app)

[

Fetching Objects and Requesting Changes](/documentation/photokit/fetching-objects-and-requesting-changes)

[

Observing Changes in the Photo Library](/documentation/photokit/observing-changes-in-the-photo-library)

## [Overview](/documentation/Photos/PHPhotoLibrary#overview)

The object represents the entire set of assets and collections that the Photos app manages, including assets stored on the local device and those stored in iCloud Photos. Use this object for the following tasks:

*   Retrieving or verifying the user’s permission for your app to access Photos content
    
*   Making changes to assets and collections; for example, editing asset metadata or content, inserting new assets, or rearranging the members of a collection
    
*   Determining which records change since a previous state of the Photos library
    
*   Registering for update messages the system sends when the library changes
    

## [Topics](/documentation/Photos/PHPhotoLibrary#topics)

### [Verifying Authorization](/documentation/Photos/PHPhotoLibrary#Verifying-Authorization)

```swift
```swift
```swift
```swift
class func authorizationStatus(for: PHAccessLevel) -> PHAuthorizationStatus
```
```

Returns the app’s authorization to access the user’s photo library for the specified access level.
```
```swift
```swift
```swift
class func requestAuthorization(for: PHAccessLevel, handler: (PHAuthorizationStatus) -> Void)
```
```

Prompts the user to grant the app permission to access the photo library.
```
```swift
```swift
```swift
enum PHAccessLevel
```
```

The app’s level of access to the user’s photo library.
```
```swift
```swift
```swift
enum PHAuthorizationStatus
```
```

Information about your app’s authorization to access the user’s photo library.
```
```swift
```swift
```swift
class func authorizationStatus() -> PHAuthorizationStatus
```
```

Returns information about your app’s authorization to access the user’s photo library.

Deprecated
```
```swift
```swift
```swift
class func requestAuthorization((PHAuthorizationStatus) -> Void)
```
```

Requests the user’s permission, if needed, to access the photo library.

Deprecated
```
```

### [Accessing the Shared Library](/documentation/Photos/PHPhotoLibrary#Accessing-the-Shared-Library)

```swift
```swift
```swift
```swift
class func shared() -> PHPhotoLibrary
```
```

Retrieves the shared photo library object.
```
```

### [Presenting the Limited Library Picker](/documentation/Photos/PHPhotoLibrary#Presenting-the-Limited-Library-Picker)

```swift
```swift
```swift
```swift
func presentLimitedLibraryPicker(from: UIViewController)
```
```

Prompts the user to update their limited library selection.
```
```swift
```swift
```swift
func presentLimitedLibraryPicker(from: UIViewController, completionHandler: ([String]) -> Void)
```
```

Prompts the user to update their limited library selection with a callback providing newly selected identifiers.
```
```

### [Updating the Library](/documentation/Photos/PHPhotoLibrary#Updating-the-Library)

[

Requesting Changes to the Photo Library](/documentation/photokit/requesting-changes-to-the-photo-library)

Create, delete, or modify assets and collections in a photo library by making change requests.

```swift
```swift
```swift
func performChanges(() -> Void, completionHandler: ((Bool, (any Error)?) -> Void)?)
```
```

Asynchronously runs a block that requests changes to the photo library.
```
```swift
```swift
```swift
func performChangesAndWait(() -> Void) throws
```
```

Synchronously runs a block that requests changes to be performed in the photo library.
```
```swift
```swift
```swift
class PHChangeRequest
```
```

The abstract base class of the framework’s photo library change requests.
```
```swift
```swift
```swift
class PHAssetChangeRequest
```
```

A request to create, delete, change metadata for, or edit the content of a Photos asset, for use in a photo library change block.
```
```swift
```swift
```swift
class PHAssetCollectionChangeRequest
```
```

A request to create, delete, or modify a Photos asset collection, for use in a photo library change block.
```
```swift
```swift
```swift
class PHCollectionListChangeRequest
```
```

A request to create, delete, or modify a Photos collection list, for use in a photo library change block.
```
```swift
```swift
```swift
class PHObjectPlaceholder
```
```

A read-only proxy object that represents a Photos asset or collection to create.
```

### [Fetching Change History](/documentation/Photos/PHPhotoLibrary#Fetching-Change-History)

```swift
```swift
```swift
```swift
func fetchPersistentChanges(since: PHPersistentChangeToken) throws -> PHPersistentChangeFetchResult
```
```

Retrieves the Photos library changes since the token you specify.
```
```swift
```swift
```swift
class PHPersistentChangeFetchResult
```
```

An object that represents a fetch result and allows you to enumerate a very large set of change records.
```
```swift
```swift
```swift
var currentChangeToken: PHPersistentChangeToken
```
```

The opaque token that represents the current state of the Photos library.
```
```swift
```swift
```swift
class PHPersistentChangeToken
```
```

An opaque object that tracks the state of the Photos library between runs, and that you can copy and serialize for future use.
```
```

### [Observing Library Changes](/documentation/Photos/PHPhotoLibrary#Observing-Library-Changes)

[

Observing Changes in the Photo Library](/documentation/photokit/observing-changes-in-the-photo-library)

Register an observer to be notified of changes to the photo library.

```swift
```swift
```swift
func register(any PHPhotoLibraryChangeObserver)
```
```

Registers an object to receive messages when objects in the photo library change.
```
```swift
```swift
```swift
func unregisterChangeObserver(any PHPhotoLibraryChangeObserver)
```
```

Unregisters an object so that it no longer receives change messages.
```
```swift
```swift
```swift
protocol PHPhotoLibraryChangeObserver
```
```

A protocol to adopt to have the system notify your app of changes to the photo library.
```
```swift
```swift
```swift
class PHChange
```
```

A description of a change that occurred in the photo library.
```
```swift
```swift
```swift
class PHObjectChangeDetails
```
```

A description of changes that occurred in an asset or collection object.
```
```swift
```swift
```swift
class PHFetchResultChangeDetails
```
```

A description of changes that occurred in the set of asset or collection objects listed in a fetch result.
```

### [Observing Library Availability](/documentation/Photos/PHPhotoLibrary#Observing-Library-Availability)

```swift
```swift
```swift
```swift
func register(any PHPhotoLibraryAvailabilityObserver)
```
```

Registers an object to observe changes to the photo library’s availability.
```
```swift
```swift
```swift
func unregisterAvailabilityObserver(any PHPhotoLibraryAvailabilityObserver)
```
```

Unregisters an object from observing changes to the photo library’s availability.
```
```swift
```swift
```swift
protocol PHPhotoLibraryAvailabilityObserver
```
```

A protocol to adopt to have the system notify your app when the availability of a photo library changes.
```
```swift
```swift
```swift
var unavailabilityReason: (any Error)?
```
```

An error that describes the reason the photo library isn’t available.
```
```

### [Converting Between Local and iCloud Identifiers](/documentation/Photos/PHPhotoLibrary#Converting-Between-Local-and-iCloud-Identifiers)

```swift
```swift
```swift
```swift
func cloudIdentifierMappings(forLocalIdentifiers: [String]) -> [String : Result<PHCloudIdentifier, any Error>]
```
```

Retrieves the cloud identifier mappings for the list of local identifiers.
```
```swift
```swift
```swift
func localIdentifierMappings(for: [PHCloudIdentifier]) -> [PHCloudIdentifier : Result<String, any Error>]
```
```

Retrieves the local identifier mappings for the list of cloud identifiers.
```
```swift
```swift
```swift
class PHCloudIdentifier
```
```

An object that identifies an asset or collection that syncs through iCloud Photos.
```
```swift
```swift
```swift
func cloudIdentifiers(forLocalIdentifiers: [String]) -> [PHCloudIdentifier]
```
```

Retrieves the equivalent iCloud identifiers for the list of local identifiers.

Deprecated
```
```swift
```swift
```swift
func localIdentifiers(for: [PHCloudIdentifier]) -> [String]
```
```

Retrieves the equivalent local identifiers for the list of iCloud identifiers.

Deprecated
```
```swift
```swift
```swift
let PHLocalIdentifierNotFound: String
```
```

A constant value that indicates that the system can’t resolve a local object from a global identifier.

Deprecated
```
```

## [Relationships](/documentation/Photos/PHPhotoLibrary#relationships)

### [Inherits From](/documentation/Photos/PHPhotoLibrary#inherits-from)

*   [`NSObject`](/documentation/ObjectiveC/NSObject-swift.class)

### [Conforms To](/documentation/Photos/PHPhotoLibrary#conforms-to)

*   [`CVarArg`](/documentation/Swift/CVarArg)
*   [`CustomDebugStringConvertible`](/documentation/Swift/CustomDebugStringConvertible)
*   [`CustomStringConvertible`](/documentation/Swift/CustomStringConvertible)
*   [`Equatable`](/documentation/Swift/Equatable)
*   [`Hashable`](/documentation/Swift/Hashable)
*   [`NSObjectProtocol`](/documentation/ObjectiveC/NSObjectProtocol)
*   [`Sendable`](/documentation/Swift/Sendable)
*   [`SendableMetatype`](/documentation/Swift/SendableMetatype)