

- App Intents
- AssistantSchemas
-  AssistantSchemas.WhiteboardEnum 

Protocol

# AssistantSchemas.WhiteboardEnum

Assistant schema conformance for whiteboard types.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+tvOS 16.0+visionOS 1.0+watchOS 9.0+

``` source
protocol WhiteboardEnum : AssistantSchemas.Model
```

## Mentioned in 

Making whiteboard actions available to Siri and Apple Intelligence

## Topics

### Instance Properties

var color: some AssistantSchemas.Enum

The color of a whiteboard canvas.

var itemType: some AssistantSchemas.Enum

The type of an item on a whiteboard canvas.

## Relationships

### Inherits From

- AssistantSchemas.Model

### Conforming Types

- AssistantSchema.EnumSchema
- AssistantSchemas.EnumSchema

## See Also

### Whiteboard

Making whiteboard actions available to Siri and Apple Intelligence

Create app intents and entities that make your app’s whiteboard functionality available to Siri and Apple Intelligence.

protocol WhiteboardIntent

Assistant schema conformance for app intents that offer whiteboard functionality.

protocol WhiteboardEntity

Assistant schema conformance for app entities that describe data for whiteboard functionality.

