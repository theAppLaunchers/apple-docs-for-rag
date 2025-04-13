

- AVFAudio
- AVAudioSession
-  setPreferredInputNumberOfChannels(\_:) 

Instance Method

# setPreferredInputNumberOfChannels(\_:)

Sets the preferred number of input channels for the current route.

iOS 7.0+iPadOS 7.0+Mac Catalyst 13.1+tvOS 9.0+visionOS 1.0+

``` source
func setPreferredInputNumberOfChannels(_ count: Int) throws
```

## Parameters 

`count`  

The number of input channels you want to use.

## Discussion

This method requests a change to the number of input channels. To determine whether the change has taken effect, query or key-value observe the inputNumberOfChannels property.

Requesting input channels less than one or greater than that returned by the maximumInputNumberOfChannels results in an error.

Set the preferred number of input channels only after setting the audio session’s category and mode, and activating the session.

## See Also

### Setting the number of input channels

var preferredInputNumberOfChannels: Int

The preferred number of input channels for the current route.

var inputNumberOfChannels: Int

The number of audio input channels for the current route.

var maximumInputNumberOfChannels: Int

The maximum number of input channels available for the current audio route.

