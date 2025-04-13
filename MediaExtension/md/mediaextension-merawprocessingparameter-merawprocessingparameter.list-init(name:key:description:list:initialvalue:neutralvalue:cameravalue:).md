

- MediaExtension
- MERAWProcessingParameter
- MERAWProcessingParameter.List
-  init(name:key:description:list:initialValue:neutralValue:cameraValue:) 

Initializer

# init(name:key:description:list:initialValue:neutralValue:cameraValue:)

Creates a list parameter object.

macOS 15.0+

``` source
convenience init(
    name: String,
    key: String,
    description: String,
    list listElements: [MERAWProcessingParameter.ListElement],
    initialValue: Int,
    neutralValue: Int? = nil,
    cameraValue: Int? = nil
)
```

## Parameters 

`name`  

A localized human-readable name for the parameter, suitable for displaying in application UI.

`key`  

A unique key string identifying this parameter.

`description`  

A localized description of the parameter, suitable for displaying in a tool tip or similar explanatory UI.

`listElements`  

The ordered array of `MERAWProcessingListElementParameter` objects which make up this list.

`initialValue`  

The initial value of this parameter as defined in the sequence metadata.

`neutralValue`  

The neutral value of this parameter.

`cameraValue`  

The camera value for this parameter.

