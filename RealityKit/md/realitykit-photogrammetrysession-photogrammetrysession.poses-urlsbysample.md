

- RealityKit
- PhotogrammetrySession
- PhotogrammetrySession.Poses
-  urlsBySample 

Instance Property

# urlsBySample

Mapping from the sample ID to the image URL in the input folder corresponding to that sample ID. This simplifies the visualization of which image in the input folder corresponds to a given computed pose.

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+macOS 14.0+

``` source
var urlsBySample: [Int : URL] { get }
```

## Discussion

Note: the dictionary is empty unless a folder of images was used to create this session. If the session is created from a custom `Sequence` it is expected that the caller has maintained the map from provided sample ID to original image location.

