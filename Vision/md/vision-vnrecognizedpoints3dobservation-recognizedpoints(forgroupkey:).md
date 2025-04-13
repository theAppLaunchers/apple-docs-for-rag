

- Vision
- VNRecognizedPoints3DObservation
-  recognizedPoints(forGroupKey:) 

Instance Method

# recognizedPoints(forGroupKey:)

Returns a point for a group key you specify.

iOS 14.0+iPadOS 14.0+Mac Catalyst 14.0+macOS 11.0+tvOS 14.0+visionOS 1.0+

``` source
func recognizedPoints(forGroupKey groupKey: VNRecognizedPointGroupKey) throws -> [VNRecognizedPointKey : VNRecognizedPoint3D]
```

## Parameters 

`groupKey`  

The group key to retrieve points for.

## Return Value

A dictionary of labeled points for the group.

## See Also

### Inspecting the Observation

var availableKeys: [VNRecognizedPointKey]

The available point keys in the observation.

var availableGroupKeys: [VNRecognizedPointGroupKey]

The available point group keys in the observation.

func recognizedPoint(forKey: VNRecognizedPointKey) throws -> VNRecognizedPoint3D

Returns a point for a key you specify.

