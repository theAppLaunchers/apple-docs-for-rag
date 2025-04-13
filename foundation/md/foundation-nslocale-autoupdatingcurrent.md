

- Foundation
- NSLocale
-  autoupdatingCurrent 

Type Property

# autoupdatingCurrent

A locale which tracks the user’s current preferences.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.1+macOS 10.5+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
class var autoupdatingCurrent: Locale { get }
```

## Discussion

The locale is formed from the settings for the current user’s chosen system locale overlaid with any custom settings the user has specified.

Use this property when you want a locale that always reflects the latest configuration settings. When the user changes settings, a locale instance obtained from this property alters its behavior to match. If you need to rely on a locale that does not change, use the locale given by the current property instead.

Although the locale obtained here automatically follows the latest region settings, it provides no indication when the settings change. To receive notification of locale changes, add your object as an observer of currentLocaleDidChangeNotification.

## See Also

### Getting the User’s Locale

class var current: Locale

A locale representing the user’s region settings at the time the property is read.

class let currentLocaleDidChangeNotification: NSNotification.Name

A notification that indicates that the user’s locale changed.

class var system: Locale

A locale representing the generic root values with little localization.

