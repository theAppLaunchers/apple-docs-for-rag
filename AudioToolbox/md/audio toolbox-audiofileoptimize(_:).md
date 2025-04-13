

- Audio Toolbox
-  AudioFileOptimize(\_:) 

Function

# AudioFileOptimize(\_:)

Consolidates audio data and performs other internal optimizations of the file structure.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.1+macOS 10.2+tvOS 9.0+visionOS 1.0+

``` source
func AudioFileOptimize(_ inAudioFile: AudioFileID) -> OSStatus
```

## Parameters 

`inAudioFile`  

The audio file you want to optimize.

## Return Value

A result code. See Result Codes.

## Discussion

This function optimizes the file so additional audio information can be appended to the existing data. Typically, this function consolidates the file’s audio data at the end of the file. This improves performance, such as when writing additional data to the file.

Do not use this potentially expensive and time-consuming operation during time-critical operations. Instead, use the kAudioFilePropertyIsOptimized property to check the optimization state of a file. You can then optimize when it won’t adversely affect your application.

