

- Foundation
- FileManager
-  url(forPublishingUbiquitousItemAt:expiration:) 

Instance Method

# url(forPublishingUbiquitousItemAt:expiration:)

Returns a URL that can be emailed to users to allow them to download a copy of a flat file item from iCloud.

iOS 5.0+iPadOS 5.0+Mac Catalyst 13.1+macOS 10.7+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func url(
    forPublishingUbiquitousItemAt url: URL,
    expiration outDate: AutoreleasingUnsafeMutablePointer?
) throws -> URL
```

## Parameters 

`url`  

The URL of the item in the cloud that you want to share. The URL must be prefixed with the base URL returned from the url(forUbiquityContainerIdentifier:) method that corresponds to the item’s location. The file must be a flat file, not a bundle. The file at the specified URL must already be uploaded to iCloud when you call this method.

`outDate`  

On input, a pointer to a variable for a date object. On output, this parameter contains the date after which the item is no longer available at the returned URL. You may specify `nil` for this parameter if you are not interested in the date.

## Return Value

A URL with which users can download a copy of the item at `url`. In Objective-C, returns `nil` if the URL could not be created for any reason.

## Discussion

This method creates a snapshot of the specified flat file and places that copy in a temporary iCloud location where it can be accessed by other users using the returned URL. The snapshot reflects the contents of the file at the time the URL was generated and is not updated when subsequent changes are made to the original file in the user’s iCloud storage. The snapshot file remains available at the specified URL until the date specified in the `outDate` parameter, after which it is automatically deleted. Explicitly deleting the item by calling the removeItem(at:) or removeItem(atPath:) method also deletes all old versions of the item, invalidating URLs to those versions returned by this method.

Your app must have access to the network for this call to succeed. If the specified file is in the process of being uploaded to iCloud, you must not call this method until the upload has finished.

Important

As of iOS 8.0 and macOS 10.10 The `url` must specify a flat file, not a bundle. Bundles have a folder as the root item.

Handling Errors in Swift

In Swift, this method returns a nonoptional result and is marked with the `throws` keyword to indicate that it throws an error in cases of failure.

You call this method in a `try` expression and handle any errors in the `catch` clauses of a `do` statement, as described in Error Handling in The Swift Programming Language and `About Imported Cocoa Error Parameters`.

## See Also

### Managing iCloud-Based Items

var ubiquityIdentityToken: (any NSCoding &amp; NSCopying &amp; NSObjectProtocol)?

An opaque token that represents the current user’s iCloud Drive Documents identity.

func url(forUbiquityContainerIdentifier: String?) -> URL?

Returns the URL for the iCloud container associated with the specified identifier and establishes access to that container.

func isUbiquitousItem(at: URL) -> Bool

Returns a Boolean indicating whether the item is targeted for storage in iCloud.

func setUbiquitous(Bool, itemAt: URL, destinationURL: URL) throws

Indicates whether the item at the specified URL should be stored in iCloud.

func startDownloadingUbiquitousItem(at: URL) throws

Starts downloading (if necessary) the specified item to the local system.

func evictUbiquitousItem(at: URL) throws

Removes the local copy of the specified item that’s stored in iCloud.

