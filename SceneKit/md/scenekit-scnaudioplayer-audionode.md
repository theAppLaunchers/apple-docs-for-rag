

- SceneKit
- SCNAudioPlayer
-  audioNode 

Instance Property

# audioNode

The audio node SceneKit uses for mixing audio from this player.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.1+macOS 10.11+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
var audioNode: AVAudioNode? { get }
```

## Discussion

SceneKit uses this AVAudioNode object to perform 3D positional mixing during playback. Use this object to vary parameters such as volume and reverb in real time during playback. To set default values for those parameters, use the audioSource property.

## See Also

### Working with Audio Sources

var audioSource: SCNAudioSource?

The source of audio played by this player.

