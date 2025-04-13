

- Swift
- Objective-C and C Code Customization
-  Renaming Objective-C APIs for Swift 

Article

# Renaming Objective-C APIs for Swift

Use the `NS_SWIFT_NAME` macro to customize API names for Swift.

## Overview

If you want to import an Objective-C API into Swift with a different name, use the `NS_SWIFT_NAME` macro. The macro preserves the Objective-C name for use with Objective-C code, so the API has appropriate names in each language.

You apply the `NS_SWIFT_NAME` macro to an individual type, method, or function declaration in Objective-C. After applying the macro, the name you use in your Swift code will be what you’ve chosen by using the macro.

### Rename APIs

The example below renames a class and one of its properties:

```
NS_SWIFT_NAME(Sandwich.Preferences)
@interface SandwichPreferences : NSObject

@property BOOL includesCrust NS_SWIFT_NAME(isCrusty);

@end

@interface Sandwich : NSObject
@end
```

The `SandwichPreferences` class and its `includesCrust` property are renamed to `Sandwich.Preferences` and `isCrusty` for Swift:

```
var preferences = Sandwich.Preferences()
preferences.isCrusty = true
```

You use the `NS_SWIFT_NAME` macro as a prefix for classes and protocols. For all other kinds of declaration—such as properties, enumeration cases, and type aliases—you use the macro as a suffix. The following example uses the macro as a suffix to rename an enumeration:

```
typedef NS_ENUM(NSInteger, SandwichBreadType) {
    brioche, pumpernickel, pretzel, focaccia
} NS_SWIFT_NAME(SandwichPreferences.BreadType);
```

## See Also

### Customizing Objective-C APIs

Designating Nullability in Objective-C APIs

Use nullability annotations or mark regions as annotated to control how Objective-C declarations are imported into Swift.

Improving Objective-C API Declarations for Swift

Use the `NS_REFINED_FOR_SWIFT` macro to change how an API is imported into Swift.

Grouping Related Objective-C Constants

Add macros to your Objective-C types to group their values in Swift.

Marking API Availability in Objective-C

Use `a` macro to denote the availability of an Objective-C API.

Making Objective-C APIs Unavailable in Swift

Use the `NS_SWIFT_UNAVAILABLE` macro to prevent an API from being used in Swift.

