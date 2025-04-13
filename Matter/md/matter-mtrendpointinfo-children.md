

- Matter
- MTREndpointInfo
-  children 

Instance Property

# children

The direct children of this endpoint. This excludes indirect descendants even if they are listed in the PartsList attribute of this endpoint due to the Full-Family Pattern being used. Refer to Endpoint Composition Patterns in the Matter specification for details.

iOS 18.4+iPadOS 18.4+Mac Catalyst 18.4+macOS 15.4+tvOS 18.4+visionOS 2.4+watchOS 11.4+

``` source
var children: [MTREndpointInfo] { get }
```

