

- Foundation
- URLFileProtection
-  none 

Type Property

# none

An option that indicates the file has no special protections associated with it.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.1+macOS 11.0+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
static let none: URLFileProtection
```

## Discussion

A file with this type of protection can be read from or written to at any time.

## See Also

### Protection levels

static let complete: URLFileProtection

An option that instructs the system to store the file in an encrypted format on-disk that your app can’t access for reading or writing to while the device is locked or booting.

static let completeUnlessOpen: URLFileProtection

An option that instructs the system to store the file in an encrypted format on-disk after it closes.

static let completeUntilFirstUserAuthentication: URLFileProtection

An option that instructs the system to store the file in an encrypted format on-disk that your app can’t access until after the device boots.

static let completeWhenUserInactive: URLFileProtection

An option that instructs the system to store the file in an encrypted format on-disk that your app can access only after device unlock and before expiration.

