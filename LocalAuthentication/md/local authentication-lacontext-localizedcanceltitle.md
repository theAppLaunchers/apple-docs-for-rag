

- Local Authentication
- LAContext
-  localizedCancelTitle 

Instance Property

# localizedCancelTitle

The localized title for the cancel button in the dialog presented to the user during authentication.

iOS 10.0+iPadOS 10.0+Mac Catalyst 13.1+macOS 10.12+visionOS 1.0+

``` source
var localizedCancelTitle: String? { get set }
```

## Discussion

The system presents a cancel button during biometric authentication to let the user abort the authentication attempt. The button appears every time the system asks the user to present a finger registered with Touch ID. For Face ID, the button only appears if authentication fails and the user is prompted to try again. Either way, the user can stop trying to authenticate by tapping the button.

Use the localizedCancelTitle property to choose a title for the cancel button. If you set the property to `nil`—as it is by default—or assign an empty string, the system uses an appropriate default title, like “Cancel”. Otherwise, provide a localized string that’s short and clear.

## See Also

### Customizing authentication prompts

var localizedReason: String

The localized explanation for authentication shown in the dialog presented to the user.

var localizedFallbackTitle: String?

The localized title for the fallback button in the dialog presented to the user during authentication.

