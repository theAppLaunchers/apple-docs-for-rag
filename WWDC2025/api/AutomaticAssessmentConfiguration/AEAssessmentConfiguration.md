*   [Automatic Assessment Configuration](/documentation/automaticassessmentconfiguration)
*   AEAssessmentConfiguration

Class

# AEAssessmentConfiguration

Configuration information for an assessment session.

iOS 13.4+iPadOS 13.4+Mac Catalyst 14.0+macOS 10.15.4+

```swift
```swift
```swift
```swift
```swift
```swift
```swift
```swift
class AEAssessmentConfiguration
```
```
```
```
```
```
```
```

## [Overview](/documentation/AutomaticAssessmentConfiguration/AEAssessmentConfiguration#overview)

Create a configuration instance and pass it to the [`init(configuration:)`](/documentation/automaticassessmentconfiguration/aeassessmentsession/init\(configuration:\)) initializer of an [`AEAssessmentSession`](/documentation/automaticassessmentconfiguration/aeassessmentsession) instance to create a new assessment session. Before using the configuration, indicate which exceptions you want to allow for the assessment session’s restrictions by setting values on the configuration instance. For example, you can set values to allow dictation and certain aspects of autocorrect:

```swift
```swift
```swift
```swift
```swift
```swift
```swift
```swift
```swift
```swift
```swift
let config = AEAssessmentConfiguration()
```
```
#if os(iOS) // These exceptions available only on iOS and iPadOS.
config.allowsDictation = true
config.autocorrectMode = [.punctuation, .spelling]
#endif
```swift
```swift
let session = AEAssessmentSession(configuration: config)
```
```
```
```
```
```
```

```

```
AEAssessmentConfiguration *config = [AEAssessmentConfiguration new];
#if TARGET_OS_IPHONE || TARGET_IPHONE_SIMULATOR // These exceptions available only on iOS and iPadOS.
config.allowsDictation = YES;
config.autocorrectMode = AEAutocorrectModePunctuation | AEAutocorrectModeSpelling;
#endif
AEAssessmentSession *session = [[AEAssessmentSession alloc] initWithConfiguration:config];
```

```
```
```
```
```

While you provide a configuration instance when creating a session on iOS, iPadOS, and macOS, specific exceptions apply only to certain platforms. In particular, on macOS, you can selectively make specific apps besides your own available during an assessment — for example, to allow users to access a calculator or a dictionary. All other exceptions apply only to iOS and iPadOS.

## [Topics](/documentation/AutomaticAssessmentConfiguration/AEAssessmentConfiguration#topics)

### [Allowing access to other apps](/documentation/AutomaticAssessmentConfiguration/AEAssessmentConfiguration#Allowing-access-to-other-apps)

```swift
```swift
```swift
```swift
func setConfiguration(AEAssessmentParticipantConfiguration, for: AEAssessmentApplication)
```
```

Adds an app to the list of apps available during an assessment.
```
```swift
```swift
```swift
var configurationsByApplication: [AEAssessmentApplication : AEAssessmentParticipantConfiguration]
```
```

The collection of apps available during an assessment, along with their associated configurations.
```
```swift
```swift
```swift
func remove(AEAssessmentApplication)
```
```

Removes the availability of a previously allowed app.
```
```swift
```swift
```swift
var mainParticipantConfiguration: AEAssessmentParticipantConfiguration
```
```

The app-specific configuration for the app that invokes the assessment.
```
```swift
```swift
```swift
class AEAssessmentApplication
```
```

A representation of an app that users can access during an assessment.
```
```swift
```swift
```swift
class AEAssessmentParticipantConfiguration
```
```

Configuration information for an app that’s available during an assessment.
```
```

### [Allowing accessibility](/documentation/AutomaticAssessmentConfiguration/AEAssessmentConfiguration#Allowing-accessibility)

```swift
```swift
```swift
```swift
var allowsAccessibilitySpeech: Bool
```
```

A Boolean value that indicates whether to allow the speech-related accessibility features during an assessment.
```
```swift
```swift
```swift
var allowsDictation: Bool
```
```

A Boolean value that indicates whether to allow the use of dictation during an assessment.
```
```

### [Allowing typing assistance](/documentation/AutomaticAssessmentConfiguration/AEAssessmentConfiguration#Allowing-typing-assistance)

```swift
```swift
```swift
```swift
var allowsContinuousPathKeyboard: Bool
```
```

A Boolean value that indicates whether to allow Slide to Type to operate during an assessment.
```
```swift
```swift
```swift
var allowsKeyboardShortcuts: Bool
```
```

A Boolean value that indicates whether to allow keyboard shortcuts during an assessment.
```
```swift
```swift
```swift
var allowsPredictiveKeyboard: Bool
```
```

A Boolean value that indicates whether to enable the predictive keyboard during an assessment.
```
```swift
```swift
```swift
var allowsPasswordAutoFill: Bool
```
```

A Boolean value that indicates whether to allow password autofill during an assessment.
```
```

### [Allowing corrections](/documentation/AutomaticAssessmentConfiguration/AEAssessmentConfiguration#Allowing-corrections)

```swift
```swift
```swift
```swift
var allowsSpellCheck: Bool
```
```

A Boolean value that indicates whether to allow spell check during an assessment.
```
```swift
```swift
```swift
var autocorrectMode: AEAssessmentConfiguration.AutocorrectMode
```
```

A Boolean value that indicates whether to allow Autocorrect during an assessment.
```
```swift
```swift
```swift
struct AutocorrectMode
```
```

The set of autocorrect features that you can enable during an assessment.
```
```

### [Allowing handoff](/documentation/AutomaticAssessmentConfiguration/AEAssessmentConfiguration#Allowing-handoff)

```swift
```swift
```swift
```swift
var allowsActivityContinuation: Bool
```
```

A Boolean value that indicates whether to allow Handoff during an assessment.
```
```

## [Relationships](/documentation/AutomaticAssessmentConfiguration/AEAssessmentConfiguration#relationships)

### [Inherits From](/documentation/AutomaticAssessmentConfiguration/AEAssessmentConfiguration#inherits-from)

*   [`NSObject`](/documentation/ObjectiveC/NSObject-swift.class)

### [Conforms To](/documentation/AutomaticAssessmentConfiguration/AEAssessmentConfiguration#conforms-to)

*   [`CVarArg`](/documentation/Swift/CVarArg)
*   [`CustomDebugStringConvertible`](/documentation/Swift/CustomDebugStringConvertible)
*   [`CustomStringConvertible`](/documentation/Swift/CustomStringConvertible)
*   [`Equatable`](/documentation/Swift/Equatable)
*   [`Hashable`](/documentation/Swift/Hashable)
*   [`NSCopying`](/documentation/Foundation/NSCopying)
*   [`NSObjectProtocol`](/documentation/ObjectiveC/NSObjectProtocol)

## [See Also](/documentation/AutomaticAssessmentConfiguration/AEAssessmentConfiguration#see-also)

### [Sessions](/documentation/AutomaticAssessmentConfiguration/AEAssessmentConfiguration#Sessions)

[

Preparing an educational assessment app for distribution](/documentation/automaticassessmentconfiguration/preparing-an-educational-assessment-app-for-distribution)

Ensure your app maintains academic integrity by reviewing assessment practices and managing system capabilities.

[

Build an Educational Assessment App](/documentation/automaticassessmentconfiguration/build-an-educational-assessment-app)

Ensure the academic integrity of your assessment app by using Automatic Assessment Configuration.

```swift
```swift
```swift
class AEAssessmentSession
```
```

A session that your app uses to protect an assessment.
```