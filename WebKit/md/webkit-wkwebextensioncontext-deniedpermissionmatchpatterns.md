

- WebKit
- WKWebExtensionContext
-  deniedPermissionMatchPatterns 

Instance Property

# deniedPermissionMatchPatterns

The currently denied permission match patterns and their expiration dates.

iOS 18.4+iPadOS 18.4+Mac Catalyst 18.4+macOS 15.4+visionOS 2.4+

``` source
@MainActor
var deniedPermissionMatchPatterns: [WKWebExtension.MatchPattern : Date] { get set }
```

## Discussion

Match patterns that don’t expire will have a distant future date. This will never include expired entries at time of access.

Setting this property will replace all existing entries. Use this property for saving and restoring permission status in bulk.

Match patterns in this dictionary should be explicitly denied by the user before being added. Any match pattern in this collection will not be presented for approval again until they expire. This value should be saved and restored as needed by the app.

## See Also

### Related Documentation

func setPermissionStatus(WKWebExtensionContext.PermissionStatus, for: WKWebExtension.MatchPattern)

Sets the status of a match pattern with a distant future expiration date.

func setPermissionStatus(WKWebExtensionContext.PermissionStatus, for: WKWebExtension.MatchPattern, expirationDate: Date?)

Sets the status of a match pattern with a specific expiration date.

