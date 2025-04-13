

- Swift
- Objective-C and C Code Customization
-  Making Objective-C APIs Unavailable in Swift 

Article

# Making Objective-C APIs Unavailable in Swift

Use the `NS_SWIFT_UNAVAILABLE` macro to prevent an API from being used in Swift.

## Overview

If parts of an Objective-C API aren’t suitable for Swift, you can make those parts unavailable in Swift. You make part of an API unavailable in Swift as part of introducing new Swift APIs that supersede parts of the existing Objective-C API. For example, you might replace an Objective-C constant with a Swift constant that’s nested inside a containing Swift type.

### Prevent an Objective-C API from Being Imported

To prevent a declaration in an Objective-C API from being imported, pass a single parameter to the `NS_SWIFT_UNAVAILABLE` macro. The parameter indicates what a developer using Swift should do instead of using the part of the API you’re making unavailable.

In this example, an Objective-C class that provides a convenience initializer that takes variadic arguments for key-value pairs suggests using a dictionary literal instead:

```
+ (instancetype)collectionWithValues:(NSArray *)values
                             forKeys:(NSArray *)keys
NS_SWIFT_UNAVAILABLE("Use a dictionary literal instead.");
```

Attempting to call the `collectionWithValues:forKeys:` method in Swift results in a compiler error.

### Make an API Unavailable in Both Languages

To make an Objective-C declaration unavailable at compile time in both Swift and Objective-C, use the `NS_UNAVAILABLE` macro. The macro behaves just like the `NS_SWIFT_UNAVAILABLE` macro except that it doesn’t support the customizable error message and it restricts compile-time access to the declaration in Objective-C code.

## See Also

### Customizing Objective-C APIs

Designating Nullability in Objective-C APIs

Use nullability annotations or mark regions as annotated to control how Objective-C declarations are imported into Swift.

Renaming Objective-C APIs for Swift

Use the `NS_SWIFT_NAME` macro to customize API names for Swift.

Improving Objective-C API Declarations for Swift

Use the `NS_REFINED_FOR_SWIFT` macro to change how an API is imported into Swift.

Grouping Related Objective-C Constants

Add macros to your Objective-C types to group their values in Swift.

Marking API Availability in Objective-C

Use `a` macro to denote the availability of an Objective-C API.

