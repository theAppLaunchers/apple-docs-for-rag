

- TipKit
- Tips
-  Tips.Parameter 

Structure

# Tips.Parameter

A type that monitors the state of its wrapped value to reevaluate any dependent tip rules when the value changes.

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+macOS 14.0+tvOS 17.0+visionOS 1.0+watchOS 10.0+

``` source
struct Parameter where Value : Decodable, Value : Encodable, Value : Sendable
```

## Overview

You create a parameter by wrapping a conforming type with the `@Parameter` macro. An `id` is generated based on the parameter’s enclosing instance and the name of the property it is wrapping.

Note

Parameters are persistent by default. Wrapping a property with `@Parameter` will persist its value between app launches within the tips datastore. Passing transient as an option will allow the parameter to reset to a default value the first time it is referenced.

Tips must be configured using configure(_:) before a parameter’s value will be updated.

Pair parameters with the tip properties you want to monitor.

For example, to track whether someone has previously used a feature in your app, define a property wrapper, along with the parameter with the value you want to track in your tip as follows:

```
struct LandmarksUser {
    // Define the user interaction you want to use for a display rule.
    @Parameter
    static var hasFavoritedLandmark: Bool = false
}
```

Then construct a rule for your tip based on that parameter:

```
struct FavoriteLandmarkTip: Tip {
    var rules: [Rule] {
        // Tip will only display when `hasFavoritedLandmark` is false.
        #Rule(LandmarksUser.hasFavoritedLandmark) {
            $0 == false
        }
    }
}
```

## Topics

### Creating rules

struct Rule

A condition to meet before displaying a tip.

### Parameter options

static var transient: Tips.ParameterOption

An option that resets the parameter value the first time it is referenced.

## Relationships

### Conforms To

- Identifiable
- Sendable

