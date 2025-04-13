

- DeveloperToolsSupport
-  ColorResource 

Structure

# ColorResource

A color resource.

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+macOS 14.0+tvOS 17.0+visionOS 1.0+watchOS 10.0+

``` source
struct ColorResource
```

## Topics

### Operators

static func == (ColorResource, ColorResource) -> Bool

Returns a Boolean value indicating whether two values are equal.

### Initializers

init(name: String, bundle: Bundle)

Creates a color from a resource with the specified name in the given bundle.

### Instance Properties

var hashValue: Int

The hash value.

### Instance Methods

func hash(into: inout Hasher)

Hashes the essential components of this value by feeding them into the given hasher.

### Default Implementations

Equatable Implementations

## Relationships

### Conforms To

- Equatable
- Hashable
- Sendable

## See Also

### Resource Definition

struct ImageResource

An image resource.

