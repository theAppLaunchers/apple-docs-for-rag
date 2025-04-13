

- ARKit
- ARKit in iOS
-  Creating an immersive ar experience with audio 

Sample Code

# Creating an immersive ar experience with audio

Use sound effects and environmental sound layers to create an engaging AR experience.

Download

iOS 13.0+iPadOS 13.0+Xcode 16.0+

## Overview

This sample app uses SceneKit’s node-based audio API to associate environmental sounds with a virtual object that’s placed in the real world. Because audio is 3D positional in SceneKit by default, volume is automatically mixed based on the user’s distance from a node.

## Getting started

- This sample code supports `Relocalization` and therefore, it requires ARKit 1.5 (iOS 11.3) or greater

- ARKit is not available in the iOS Simulator

- Building the sample requires Xcode 9.3 or later

## Run an AR session and place virtual content

Before you can use audio, you need to set up a session and place the object from which to play sound. For simplicity, this sample runs a world tracking configuration and places a virtual object on the first horizontal plane that it detects. For more detail about this kind of session setup, see Tracking and visualizing planes. The object placement approach in this sample is similar to the one demonstrated in Placing objects and handling 3D interaction

## Add 3D audio to the scene

To play audio from a given position in 3D space, create an SCNAudioSource from an audio file. This sample loads the file from the bundle in `viewDidLoad`:

```
// As an environmental sound layer, audio should play indefinitely
audioSource.loops = true
// Decode the audio from disk ahead of time to prevent a delay in playback
audioSource.load()
```

Then, the audio source is configured and prepared:

```
// As an environmental sound layer, audio should play indefinitely
audioSource.loops = true
// Decode the audio from disk ahead of time to prevent a delay in playback
audioSource.load()
```

When you’re ready to play the sound, create an SCNAudioPlayer, passing it the audio source:

```
// Create a player from the source and add it to `objectNode`
objectNode.addAudioPlayer(SCNAudioPlayer(source: audioSource))
```

Note

For best results, use mono audio files. SceneKit’s audio engine uses panning to create 3D positional effects, so stereo audio sources produce less recognizable 3D audio effects.

