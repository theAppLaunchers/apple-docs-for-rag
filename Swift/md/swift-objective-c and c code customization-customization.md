

- Swift
-  Objective-C and C Code Customization 

# Objective-C and C Code Customization

Apply macros to your Objective-C APIs to customize how they’re imported into Swift.

## Topics

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

Making Objective-C APIs Unavailable in Swift

Use the `NS_SWIFT_UNAVAILABLE` macro to prevent an API from being used in Swift.

### Customizing C APIs

Customizing Your C Code for Swift

Use the `CF_SWIFT_NAME` macro to group functions that have related behavior.

## See Also

### Language Interoperability with Objective-C and C

Migrating Your Objective-C Code to Swift

Learn the recommended steps to migrate your code.

Cocoa Design Patterns

Adopt and interoperate with Cocoa design patterns in your Swift apps.

Handling Dynamically Typed Methods and Objects in Swift

Cast instances of the Objective-C `id` type to a specific Swift type.

Using Objective-C Runtime Features in Swift

Use selectors and key paths to interact with dynamic Objective-C APIs.

Imported C and Objective-C APIs

Use native Swift syntax to interoperate with types and functions in C and Objective-C.

Calling Objective-C APIs Asynchronously

Learn how functions and methods that take a completion handler are converted to Swift asynchronous functions.

