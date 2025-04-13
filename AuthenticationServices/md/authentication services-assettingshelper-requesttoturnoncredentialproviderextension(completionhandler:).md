

- Authentication Services
- ASSettingsHelper
-  requestToTurnOnCredentialProviderExtension(completionHandler:) 

Type Method

# requestToTurnOnCredentialProviderExtension(completionHandler:)

Call this method from your containing app to request to turn on a contained Credential Provider Extension. If the extension is not currently enabled, a prompt will be shown to allow it to be turned on. The completion handler is called with YES or NO depending on whether the credential provider is enabled. You need to wait 10 seconds in order to make additional request to this API.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+visionOS 2.0+

``` source
class func requestToTurnOnCredentialProviderExtension(completionHandler: @escaping (Bool) -> Void)
```

``` source
class func requestToTurnOnCredentialProviderExtension() async -> Bool
```

