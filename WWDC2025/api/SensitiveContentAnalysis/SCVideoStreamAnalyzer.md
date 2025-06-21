*   [SensitiveContentAnalysis](/documentation/sensitivecontentanalysis)
*   SCVideoStreamAnalyzer Beta

Class

# SCVideoStreamAnalyzer

An object that monitors a stream of video by analyzing frames for sensitive content.

iOS 26.0+BetaiPadOS 26.0+Beta

```swift
```swift
```swift
```swift
```swift
```swift
```swift
```swift
class SCVideoStreamAnalyzer
```
```
```
```
```
```
```
```

## [Mentioned in](/documentation/SensitiveContentAnalysis/SCVideoStreamAnalyzer#mentions)

[

Detecting nudity in media and providing intervention options](/documentation/sensitivecontentanalysis/detecting-nudity-in-media-and-providing-intervention-options)

## [Overview](/documentation/SensitiveContentAnalysis/SCVideoStreamAnalyzer#overview)

Use this class to detect senstive content in a video stream, such as on a conference call that your app implements. The class detects senstive content in the video stream from either the device’s camera or the remote devices signed into the call, depending on how you configure the analyzer.

Create an instance of this class for each video stream in the call.

To begin analyzing the stream, pass it to either [`beginAnalysis(of:)`](/documentation/sensitivecontentanalysis/scvideostreamanalyzer/beginanalysis\(of:\)-78qm) ([`AVCaptureDeviceInput`](/documentation/AVFoundation/AVCaptureDeviceInput)) or [`beginAnalysis(of:)`](/documentation/sensitivecontentanalysis/scvideostreamanalyzer/beginanalysis\(of:\)-9ehkx) ([`VTDecompressionSession`](/documentation/VideoToolbox/VTDecompressionSession)), depending on your video playback implementation.

Important

This class works only when the Communication Safety parental control in Screen Time is enabled, or when the Sensitive Content Warnings setting is turned on. The initializers of this class throw an error if both settings are off.

### [React to sensitive content](/documentation/SensitiveContentAnalysis/SCVideoStreamAnalyzer#React-to-sensitive-content)

When the framework detects sensitive content in the stream, it calls [`analysisChangedHandler`](/documentation/sensitivecontentanalysis/scvideostreamanalyzer/analysischangedhandler) immediately with an [`SCSensitivityAnalysis`](/documentation/sensitivecontentanalysis/scsensitivityanalysis) object that includes information about the detection.

You implement the [`analysisChangedHandler`](/documentation/sensitivecontentanalysis/scvideostreamanalyzer/analysischangedhandler) callback to inspect the detection results, which includes confirmation that content is sensitve as well as guidance on next steps your app can take. The framework offers your app suggestions in the handler, which include:

*   Alerting the person to the presence of sensitive content ([`shouldIndicateSensitivity`](/documentation/sensitivecontentanalysis/scsensitivityanalysis/shouldindicatesensitivity))
    
*   Interrupting video playback ([`shouldInterruptVideo`](/documentation/sensitivecontentanalysis/scsensitivityanalysis/shouldinterruptvideo))
    
*   Muting audio ([`shouldMuteAudio`](/documentation/sensitivecontentanalysis/scsensitivityanalysis/shouldmuteaudio))
    

To stop analyzing the stream, call [`endAnalysis()`](/documentation/sensitivecontentanalysis/scvideostreamanalyzer/endanalysis\(\)). If your app implements a custom stream decoder, you can analyze individual frames by passing pixel buffers to [`analyze(_:)`](/documentation/sensitivecontentanalysis/scvideostreamanalyzer/analyze\(_:\)).

In the event of an error during analysis, the handler receives an error object that details what went wrong. For more information, see: [`SCVideoStreamAnalysisChangeHandler`](/documentation/sensitivecontentanalysis/scvideostreamanalysischangehandler).

### [Add the app entitlement](/documentation/SensitiveContentAnalysis/SCVideoStreamAnalyzer#Add-the-app-entitlement)

To use this class, the system requires the [`com.apple.developer.sensitivecontentanalysis.client`](/documentation/BundleResources/Entitlements/com.apple.developer.sensitivecontentanalysis.client) entitlement in your app’s code signature. Calls to the framework fail to return positive results without it. You can can add this entitlement to your app by enabling the Sensitive Content Analysis capability in Xcode; see [Adding capabilities to your app](/documentation/Xcode/adding-capabilities-to-your-app).

For more information, see [Detecting nudity in media and providing intervention options](/documentation/sensitivecontentanalysis/detecting-nudity-in-media-and-providing-intervention-options).

## [Topics](/documentation/SensitiveContentAnalysis/SCVideoStreamAnalyzer#topics)

### [Creating a video stream analyzer](/documentation/SensitiveContentAnalysis/SCVideoStreamAnalyzer#Creating-a-video-stream-analyzer)

[`init(participantUUID: String, streamDirection: SCVideoStreamAnalyzer.StreamDirection) throws`](/documentation/sensitivecontentanalysis/scvideostreamanalyzer/init\(participantuuid:streamdirection:\))

Creates a video stream analyzer for the given call participant and stream option.

```swift
```swift
```swift
enum StreamDirection
```
```

Options for the different types of analyzed video streams.
```

### [Analyzing a video stream](/documentation/SensitiveContentAnalysis/SCVideoStreamAnalyzer#Analyzing-a-video-stream)

```swift
```swift
```swift
```swift
func analyze(CVPixelBuffer)
```
```

Analyzes individual video-stream frames for sensitive content.
```
```swift
```swift
```swift
func beginAnalysis(of: AVCaptureDeviceInput) throws
```
```

Analyzes video frames for the given capture device input.
```
```swift
```swift
```swift
func beginAnalysis(of: VTDecompressionSession) throws
```
```

Analyzes video frames for the given decompression session.
```
```swift
```swift
```swift
var analysisChanges: some AsyncSequence<SCSensitivityAnalysis, any Error>
```
```

A stream your app uses to receive video-stream analysis results.
```
```swift
```swift
```swift
func endAnalysis()
```
```

Stops stream analysis.
```
```

### [Responding to sensitive content](/documentation/SensitiveContentAnalysis/SCVideoStreamAnalyzer#Responding-to-sensitive-content)

```swift
```swift
```swift
```swift
var analysis: SCSensitivityAnalysis?
```
```

The results of the first detected sensitive video frame.
```
```swift
```swift
```swift
func continueStream()
```
```

Indicates that your app is ready to resume video stream analysis.
```
```

## [Relationships](/documentation/SensitiveContentAnalysis/SCVideoStreamAnalyzer#relationships)

### [Inherits From](/documentation/SensitiveContentAnalysis/SCVideoStreamAnalyzer#inherits-from)

*   [`NSObject`](/documentation/ObjectiveC/NSObject-swift.class)

### [Conforms To](/documentation/SensitiveContentAnalysis/SCVideoStreamAnalyzer#conforms-to)

*   [`CVarArg`](/documentation/Swift/CVarArg)
*   [`CustomDebugStringConvertible`](/documentation/Swift/CustomDebugStringConvertible)
*   [`CustomStringConvertible`](/documentation/Swift/CustomStringConvertible)
*   [`Equatable`](/documentation/Swift/Equatable)
*   [`Hashable`](/documentation/Swift/Hashable)
*   [`NSCoding`](/documentation/Foundation/NSCoding)
*   [`NSObjectProtocol`](/documentation/ObjectiveC/NSObjectProtocol)
*   [`NSSecureCoding`](/documentation/Foundation/NSSecureCoding)

Beta Software

This documentation contains preliminary information about an API or technology in development. This information is subject to change, and software implemented according to this documentation should be tested with final operating system software.

[Learn more about using Apple's beta software](https://developer.apple.com/support/beta-software/)