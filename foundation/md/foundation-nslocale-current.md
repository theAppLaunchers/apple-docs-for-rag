

- Foundation
- NSLocale
-  current 

Type Property

# current

A locale representing the user’s region settings at the time the property is read.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.0+macOS 10.0+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
class var current: Locale { get }
```

## Discussion

The locale is formed from the settings for the current user’s chosen system locale overlaid with any custom settings the user has specified.

Use this property when you need to rely on a consistent locale. A locale instance obtained this way does not change even when the user changes region settings. If you want a locale instance that always reflects the current configuration, use the one provided by the autoupdatingCurrent property instead.

To receive notification of locale changes, add your object as an observer of the a currentLocaleDidChangeNotification.

## See Also

### Getting the User’s Locale

class var autoupdatingCurrent: Locale

A locale which tracks the user’s current preferences.

class let currentLocaleDidChangeNotification: NSNotification.Name

A notification that indicates that the user’s locale changed.

class var system: Locale

A locale representing the generic root values with little localization.

