

- SMS and Call Reporting
-  ILMessageFilterCapabilitiesQueryHandling 

Protocol

# ILMessageFilterCapabilitiesQueryHandling

A set of methods implemented by a Message Filter app extension to handle capabilities query requests.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+visionOS 1.0+

``` source
protocol ILMessageFilterCapabilitiesQueryHandling : NSObjectProtocol
```

## Topics

### Handling a Capabilities Query Request

func handle(ILMessageFilterCapabilitiesQueryRequest, context: ILMessageFilterExtensionContext, completion: (ILMessageFilterCapabilitiesQueryResponse) -> Void)

Evaluates a query request and provides a response describing how the system should handle the message it represents.

**Required**

## Relationships

### Inherits From

- NSObjectProtocol

## See Also

### Queries

class ILMessageFilterCapabilitiesQueryRequest

A request to query a Message Filter extension about sharing its sub-category capabilities.

