

- Media Player
- MPRemoteCommandCenter
-  enableLanguageOptionCommand 

Instance Property

# enableLanguageOptionCommand

The command object for enabling a language option.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.1+macOS 10.12.2+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
var enableLanguageOptionCommand: MPRemoteCommand { get }
```

## Discussion

Use the object in this property to register your app’s handler for enabling the language option for the media item. In your handler, change the language option to the new value. You can disable the command if your app does not support it.

## See Also

### Enabling language options

var disableLanguageOptionCommand: MPRemoteCommand

The command object for disabling a language option

