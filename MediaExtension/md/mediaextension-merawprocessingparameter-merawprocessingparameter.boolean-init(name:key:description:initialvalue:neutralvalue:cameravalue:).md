

- MediaExtension
- MERAWProcessingParameter
- MERAWProcessingParameter.Boolean
-  init(name:key:description:initialValue:neutralValue:cameraValue:) 

Initializer

# init(name:key:description:initialValue:neutralValue:cameraValue:)

Creates a Boolean parameter object.

macOS 15.0+

``` source
convenience init(
    name: String,
    key: String,
    description: String,
    initialValue: Bool,
    neutralValue: Bool? = nil,
    cameraValue: Bool? = nil
)
```

## Parameters 

`name`  

A localized human-readable name for the parameter, suitable for displaying in application UI.

`key`  

A unique key string identifying this parameter.

`description`  

A localized description of the parameter, suitable for displaying in a tool tip or similar explanatory UI.

`initialValue`  

The initial value of this parameter as defined in the sequence metadata.

`neutralValue`  

The neutral value of this parameter.

`cameraValue`  

The camera value for this parameter.

