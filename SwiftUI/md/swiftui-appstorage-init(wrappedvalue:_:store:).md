

- SwiftUI
- AppStorage
-  init(wrappedValue:\_:store:) 

Initializer

# init(wrappedValue:\_:store:)

Creates a property that can save and restore tab sidebar customizations.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+visionOS 2.0+

``` source
init(
    wrappedValue: Value = TabViewCustomization(),
    _ key: String,
    store: UserDefaults? = nil
) where Value == TabViewCustomization
```

Show all declarations

## Parameters 

`wrappedValue`  

The default value if the customization is not available for the given key.

`key`  

The key to read and write the value to in the user defaults store.

`store`  

The user defaults store to read and write to. A value of `nil` will use the user default store from the environment.

## Discussion

You can set this customization on the TabView using tabViewCustomization(_:).

## See Also

### Storing a value

init(_:store:)

Creates a property that can read and write an Optional boolean user default.

