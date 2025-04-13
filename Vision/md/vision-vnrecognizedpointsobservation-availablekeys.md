

- Vision
- VNRecognizedPointsObservation
-  availableKeys 

Instance Property

# availableKeys

The available point keys in the observation.

iOS 14.0+iPadOS 14.0+Mac Catalyst 14.0+macOS 11.0+tvOS 14.0+visionOS 1.0+

``` source
var availableKeys: [VNRecognizedPointKey] { get }
```

## See Also

### Inspecting the Observation

var availableGroupKeys: [VNRecognizedPointGroupKey]

The available point group keys in the observation.

func recognizedPoint(forKey: VNRecognizedPointKey) throws -> VNRecognizedPoint

Retrieves a recognized point for a key.

func recognizedPoints(forGroupKey: VNRecognizedPointGroupKey) throws -> [VNRecognizedPointKey : VNRecognizedPoint]

Retrieves the recognized points for a key.

