*   [Speech](/documentation/speech)
*   SpeechAnalyzer Beta

Class

# SpeechAnalyzer

Analyzes spoken audio content in various ways and manages the analysis session.

iOS 26.0+BetaiPadOS 26.0+BetaMac Catalyst 26.0+BetamacOS 26.0+BetavisionOS 26.0+Beta

```swift
```swift
```swift
```swift
```swift
```swift
```

```
final actor SpeechAnalyzer
```

```
```
```
```
```
```
```

## [Overview](/documentation/Speech/SpeechAnalyzer#overview)

Analysis is asynchronous. Input, output, and session control are decoupled and may (and typically will) occur over several different tasks created by you or by the session.

The analyzer can only analyze one input sequence at a time.

### [Autonomous analysis](/documentation/Speech/SpeechAnalyzer#Autonomous-analysis)

You can and usually should perform analysis using the [`analyzeSequence(_:)`](/documentation/speech/speechanalyzer/analyzesequence\(_:\)) or [`analyzeSequence(from:)`](/documentation/speech/speechanalyzer/analyzesequence\(from:\)) methods; those methods work well with Swift structured concurrency techniques.

However, you may prefer that the analyzer proceed independently of those methods and perform its analysis autonomously as audio input becomes available in a task managed by the analyzer itself.

To use this capability, create the analyzer with one of the initializers that has an input sequence or file parameter, or call [`start(inputSequence:)`](/documentation/speech/speechanalyzer/start\(inputsequence:\)) or [`start(inputAudioFile:finishAfterFile:)`](/documentation/speech/speechanalyzer/start\(inputaudiofile:finishafterfile:\)). To end the analysis when the input ends, call [`finalizeAndFinishThroughEndOfInput()`](/documentation/speech/speechanalyzer/finalizeandfinishthroughendofinput\(\)). To end the analysis of that input and start analysis of different input, call one of the `start` methods.

### [Analyzer states](/documentation/Speech/SpeechAnalyzer#Analyzer-states)

Several methods cause the analysis session to _finish_. When an analysis session is finished, the analyzer will not take any additional input from the input sequence and will not accept a different input sequence or accept module changes. Most methods will do nothing. Modules’ results streams terminate; a module will not publish additional results to its result stream, but the application can continue to iterate over already-published results.

You may terminate the input sequence with a method such as `AsyncStream.Continuation.finish()`. This “finish” does not cause the analysis session to become finished, as you may continue the session with a different input sequence. Therefore, do not expect the analysis to end when the input sequence does. You can call one of this class’s `finish` methods to achieve that expectation.

### [Responding to errors](/documentation/Speech/SpeechAnalyzer#Responding-to-errors)

When the analyzer or its modules’ result streams throw an error, the analysis session becomes _finished_ as described above and the same error (or a `CancellationError`) is thrown from all waiting methods and result streams.

## [Topics](/documentation/Speech/SpeechAnalyzer#topics)

### [Creating an analyzer](/documentation/Speech/SpeechAnalyzer#Creating-an-analyzer)

[`convenience init(modules: [any SpeechModule], options: SpeechAnalyzer.Options?)`](/documentation/speech/speechanalyzer/init\(modules:options:\))

Creates an analyzer.

[`convenience init<InputSequence>(inputSequence: InputSequence, modules: [any SpeechModule], options: SpeechAnalyzer.Options?, analysisContext: AnalysisContext, volatileRangeChangedHandler: sending ((CMTimeRange, Bool, Bool) -> Void)?)`](/documentation/speech/speechanalyzer/init\(inputsequence:modules:options:analysiscontext:volatilerangechangedhandler:\))

Creates an analyzer and begins analysis.

[`convenience init(inputAudioFile: AVAudioFile, modules: [any SpeechModule], options: SpeechAnalyzer.Options?, analysisContext: AnalysisContext, finishAfterFile: Bool, volatileRangeChangedHandler: sending ((CMTimeRange, Bool, Bool) -> Void)?) async throws`](/documentation/speech/speechanalyzer/init\(inputaudiofile:modules:options:analysiscontext:finishafterfile:volatilerangechangedhandler:\))

Creates an analyzer and begins analysis on an audio file.

```swift
```swift
```swift
struct Options
```
```

Analysis processing options.
```

### [Managing modules](/documentation/Speech/SpeechAnalyzer#Managing-modules)

```swift
```swift
```swift
```swift
func setModules([any SpeechModule]) async throws
```
```

Adds or removes modules.
```
```swift
```swift
```swift
var modules: [any SpeechModule]
```
```

The modules performing analysis on the audio input.
```
```

### [Performing analysis](/documentation/Speech/SpeechAnalyzer#Performing-analysis)

```swift
```swift
```swift
```swift
func analyzeSequence<InputSequence>(InputSequence) async throws -> CMTime?
```
```

Analyzes an input sequence, returning when the sequence is consumed.
```
```swift
```swift
```swift
func analyzeSequence(from: AVAudioFile) async throws -> CMTime?
```
```

Analyzes an input sequence created from an audio file, returning when the file has been read.
```
```

### [Performing autonomous analysis](/documentation/Speech/SpeechAnalyzer#Performing-autonomous-analysis)

```swift
```swift
```swift
```swift
func start<InputSequence>(inputSequence: InputSequence) async throws
```
```

Starts analysis of an input sequence and returns immediately.
```
```swift
```swift
```swift
func start(inputAudioFile: AVAudioFile, finishAfterFile: Bool) async throws
```
```

Starts analysis of an input sequence created from an audio file and returns immediately.
```
```

### [Finalizing and cancelling results](/documentation/Speech/SpeechAnalyzer#Finalizing-and-cancelling-results)

```swift
```swift
```swift
```swift
func cancelAnalysis(before: CMTime)
```
```

Stops analyzing audio predating the given time.
```
```swift
```swift
```swift
func finalize(through: CMTime?) async throws
```
```

Finalizes the modules’ analyses.
```
```

### [Finishing analysis](/documentation/Speech/SpeechAnalyzer#Finishing-analysis)

```swift
```swift
```swift
```swift
func cancelAndFinishNow() async
```
```

Finishes analysis immediately.
```
```swift
```swift
```swift
func finalizeAndFinishThroughEndOfInput() async throws
```
```

Finishes analysis after an audio input sequence has been fully consumed and its results are finalized.
```
```swift
```swift
```swift
func finalizeAndFinish(through: CMTime) async throws
```
```

Finishes analysis after finalizing results for a given time-code.
```
```swift
```swift
```swift
func finish(after: CMTime) async throws
```
```

Finishes analysis once input for a given time is consumed.
```
```

### [Determining audio formats](/documentation/Speech/SpeechAnalyzer#Determining-audio-formats)

[`static func bestAvailableAudioFormat(compatibleWith: [any SpeechModule]) async -> AVAudioFormat?`](/documentation/speech/speechanalyzer/bestavailableaudioformat\(compatiblewith:\))

Retrieves the best-quality audio format that the specified modules can work with, from assets installed on the device.

[`static func bestAvailableAudioFormat(compatibleWith: [any SpeechModule], considering: AVAudioFormat?) async -> AVAudioFormat?`](/documentation/speech/speechanalyzer/bestavailableaudioformat\(compatiblewith:considering:\))

Retrieves the best-quality audio format that the specified modules can work with, taking into account the natural format of the audio and assets installed on the device.

### [Improving responsiveness](/documentation/Speech/SpeechAnalyzer#Improving-responsiveness)

```swift
```swift
```swift
```swift
func prepareToAnalyze(in: AVAudioFormat?) async throws
```
```

Prepares the analyzer to begin work with minimal startup delay.
```
```swift
```swift
```swift
func prepareToAnalyze(in: AVAudioFormat?, withProgressReadyHandler: sending ((Progress) -> Void)?) async throws
```
```

Prepares the analyzer to begin work with minimal startup delay, reporting the progress of that preparation.
```
```

### [Monitoring analysis](/documentation/Speech/SpeechAnalyzer#Monitoring-analysis)

```swift
```swift
```swift
```swift
func setVolatileRangeChangedHandler(sending ((CMTimeRange, Bool, Bool) -> Void)?)
```
```

A closure that the analyzer calls when the volatile range changes.
```
```swift
```swift
```swift
var volatileRange: CMTimeRange?
```
```

The range of results that can change.
```
```

### [Managing contexts](/documentation/Speech/SpeechAnalyzer#Managing-contexts)

```swift
```swift
```swift
```swift
func setContext(AnalysisContext) async throws
```
```

Sets contextual information to improve or inform the analysis.
```
```swift
```swift
```swift
var context: AnalysisContext
```
```

An object containing contextual information.
```
```

## [Relationships](/documentation/Speech/SpeechAnalyzer#relationships)

### [Conforms To](/documentation/Speech/SpeechAnalyzer#conforms-to)

*   [`Actor`](/documentation/Swift/Actor)
*   [`Sendable`](/documentation/Swift/Sendable)
*   [`SendableMetatype`](/documentation/Swift/SendableMetatype)

## [See Also](/documentation/Speech/SpeechAnalyzer#see-also)

### [Essentials](/documentation/Speech/SpeechAnalyzer#Essentials)

[

Bringing advanced speech-to-text capabilities to your app](/documentation/speech/bringing-advanced-speech-to-text-capabilities-to-your-app)

Learn how to incorporate live speech-to-text transcription into your app with SpeechAnalyzer.

```swift
```swift
```swift
class AssetInventory
```
```

Before using `SpeechAnalyzer`, you must install the assets required by the modules you use. These assets are machine-learning models downloaded from Apple’s servers.

Beta
```

Beta Software

This documentation contains preliminary information about an API or technology in development. This information is subject to change, and software implemented according to this documentation should be tested with final operating system software.

[Learn more about using Apple's beta software](https://developer.apple.com/support/beta-software/)