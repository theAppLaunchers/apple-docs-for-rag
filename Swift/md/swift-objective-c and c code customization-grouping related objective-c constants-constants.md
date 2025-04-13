

- Swift
- Objective-C and C Code Customization
-  Grouping Related Objective-C Constants 

Article

# Grouping Related Objective-C Constants

Add macros to your Objective-C types to group their values in Swift.

## Overview

You use one of the following macros to declare that several Objective-C constants are related to each other:

- `NS_ENUM` for simple enumerations

- `NS_CLOSED_ENUM` for simple enumerations that can never gain new cases

- `NS_OPTIONS` for enumerations whose cases can be grouped into sets of options

- `NS_TYPED_ENUM` for enumerations with a raw value type that you specify

- `NS_TYPED_EXTENSIBLE_ENUM` for enumerations that you expect might gain more cases

### Declare Simple Enumerations

Use the `NS_ENUM` macro for simple groups of constants.

The example below uses the macro to declare a `UITableViewCellStyle` enumeration that groups several different view styles for table views:

```
typedef NS_ENUM(NSInteger, UITableViewCellStyle) {
    UITableViewCellStyleDefault,
    UITableViewCellStyleValue1,
    UITableViewCellStyleValue2,
    UITableViewCellStyleSubtitle
};
```

In Swift, the `UITableViewCellStyle` enumeration is imported like this:

```
enum UITableViewCellStyle: Int {
    case `default`
    case value1
    case value2
    case subtitle
}
```

Enumerations imported using the `NS_ENUM` macro won’t fail when you initialize one with a raw value that does not correspond to an enumeration case. This characteristic facilitates compatibility with C, which allows any value to be stored in an enumeration, including values used internally but not exposed in headers.

The `NS_ENUM` macro is the only enumeration macro that results in an actual enumeration type when imported to Swift. The other enumeration macros generate structures.

### Declare Closed Enumerations

Use the `NS_CLOSED_ENUM` macro for a simple group of constants that you can never add new cases to. Closed enumerations are useful for representing a finite set of states that you expect people to switch over using a switch statement. The three cases of ComparisonResult—ComparisonResult.orderedAscending, ComparisonResult.orderedSame, and ComparisonResult.orderedDescending—are an example of a finite set. They’re the only logical cases for performing an ordered comparison during tasks like sorting.

Don’t use the `NS_CLOSED_ENUM` macro if:

- You’ve ever added cases to an enumeration after its initial declaration

- You can think of additional cases you might add later

- The enumeration has any private cases

In these scenarios, use the `NS_ENUM` macro instead.

### Declare Option Sets

You use the `NS_OPTIONS` macro when two or more constants in a grouping of constants can be combined. For example, the output formatting for a JSONEncoder instance can be sorted and can use ample white space at the same time, so it’s valid to specify both options in an option set: `[.sorted, .prettyPrinted]`.

The example below shows how to apply the `NS_OPTIONS` macro and assign raw values that are mutually exclusive:

```
typedef NS_OPTIONS(NSUInteger, UIViewAutoresizing) {
        UIViewAutoresizingNone                 = 0,
        UIViewAutoresizingFlexibleLeftMargin   = 1 

The increasing sequence of nonnegative integers used along with the bitwise left shift operator (`

```
public struct UIViewAutoresizing: OptionSet {
    public init(rawValue: UInt)

    public static var flexibleLeftMargin: UIViewAutoresizing { get }
    public static var flexibleWidth: UIViewAutoresizing { get }
    public static var flexibleRightMargin: UIViewAutoresizing { get }
    public static var flexibleTopMargin: UIViewAutoresizing { get }
    public static var flexibleHeight: UIViewAutoresizing { get }
    public static var flexibleBottomMargin: UIViewAutoresizing { get }
}
```

### Declare Typed Enumerations

You use the `NS_TYPED_ENUM` to group constants with a raw value type that you specify. Use `NS_TYPED_ENUM` for sets of constants that *can’t* logically have values added in a Swift extension, and use `NS_TYPED_EXTENSIBLE_ENUM` for sets of constants that *can* be expanded in an extension.

The example below uses the `NS_TYPED_ENUM` macro to declare the different colors used by a traffic light:

```
// Store the three traffic light color options as 0, 1, and 2.
typedef long TrafficLightColor NS_TYPED_ENUM;

TrafficLightColor const TrafficLightColorRed;
TrafficLightColor const TrafficLightColorYellow;
TrafficLightColor const TrafficLightColorGreen;
```

The number of colors that a traffic light uses isn’t expected to grow, so it’s not declared to be extensible.

Here’s how the `TrafficLightColor` type is imported to Swift:

```
struct TrafficLightColor: RawRepresentable, Equatable, Hashable {
    typealias RawValue = Int

    init(rawValue: RawValue)
    var rawValue: RawValue { get }

    static var red: TrafficLightColor { get }
    static var yellow: TrafficLightColor { get }
    static var green: TrafficLightColor { get }
}
```

#### Declare Typed Extensible Enumerations

Extensible enumerations are imported in a similar fashion to nonextensible ones, except that they receive an additional initializer.

The examples below show how a `FavoriteColor` type is declared, imported, and extended. The first one declares the `FavoriteColor` type and adds a single enumeration case for the color blue:

```
typedef long FavoriteColor NS_TYPED_EXTENSIBLE_ENUM;
FavoriteColor const FavoriteColorBlue;
```

The additional initializer omits the label requirement for its first parameter:

```
struct FavoriteColor: RawRepresentable, Equatable, Hashable {
    typealias RawValue = Int

    init(_ rawValue: RawValue)
    init(rawValue: RawValue)
    var rawValue: RawValue { get }

    static var blue: FavoriteColor { get }
}
```

You can add extensions to extensible enumerations later in your Swift code.

The example below adds another favorite color:

```
extension FavoriteColor {
    static var green: FavoriteColor {
        return FavoriteColor(1) // blue is 0, green is 1, and new favorite colors could follow
    }
}
```

Note

You might encounter Objective-C code that uses the older `NS_STRING_ENUM` and `NS_EXTENSIBLE_STRING_ENUM` macros, which were used to group string constants. Use `NS_TYPED_ENUM` and `NS_TYPED_EXTENSIBLE_ENUM` when grouping related constants of any type, including string constants.

## See Also

### Customizing Objective-C APIs

Designating Nullability in Objective-C APIs

Use nullability annotations or mark regions as annotated to control how Objective-C declarations are imported into Swift.

Renaming Objective-C APIs for Swift

Use the `NS_SWIFT_NAME` macro to customize API names for Swift.

Improving Objective-C API Declarations for Swift

Use the `NS_REFINED_FOR_SWIFT` macro to change how an API is imported into Swift.

Marking API Availability in Objective-C

Use `a` macro to denote the availability of an Objective-C API.

Making Objective-C APIs Unavailable in Swift

Use the `NS_SWIFT_UNAVAILABLE` macro to prevent an API from being used in Swift.

