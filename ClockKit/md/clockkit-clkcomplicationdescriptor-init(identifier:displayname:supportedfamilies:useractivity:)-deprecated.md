

- ClockKit
- CLKComplicationDescriptor
-  init(identifier:displayName:supportedFamilies:userActivity:) Deprecated

Initializer

# init(identifier:displayName:supportedFamilies:userActivity:)

Returns a new complication descriptor with an associated user activity.

watchOS 7.0–9.0Deprecated

``` source
convenience init(
    identifier: String,
    displayName: String,
    supportedFamilies: [CLKComplicationFamily],
    userActivity: NSUserActivity
)
```

Deprecated

On watchOS 9.0 or later, use WidgetKit instead

## Parameters 

`identifier`  

A string that uniquely identifies the descriptor.

`displayName`  

A localized name that ClockKit shows to the user to identify complications from the descriptor.

`supportedFamilies`  

The families that support this type of complication. Note that different descriptors can support different sets of families.

`userActivity`  

A user activity object that represents the state of the app at a moment in time.

## Mentioned in 

Declaring complications for your app

## Discussion

If the user taps on a complication specified by this descriptor, the system launches the app and calls handle(_:), passing the user activity. Your handle(_:) method should update the app so that it’s in the specified state.

Because the system can pass configurations as part of a shared watch face, only include data useable by any instance of the app. For example, avoid using identifiers that might change between users, like an index into the user’s favorites list. Instead, use items that remain constant across all copies of the app, like unique string identifiers.

## See Also

### Creating descriptors

convenience init(identifier: String, displayName: String, supportedFamilies: [CLKComplicationFamily])

Returns a new complication descriptor.

Deprecated

convenience init(identifier: String, displayName: String, supportedFamilies: [CLKComplicationFamily], userInfo: [AnyHashable : Any])

Returns a new complication descriptor with an associated dictionary of user data.

Deprecated

