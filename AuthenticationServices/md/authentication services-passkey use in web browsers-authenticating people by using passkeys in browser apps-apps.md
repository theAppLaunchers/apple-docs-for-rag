

- Authentication Services
- Passkey use in web browsers
-  Authenticating people by using passkeys in browser apps 

Article

# Authenticating people by using passkeys in browser apps

Provide a secure and convenient alternative to passwords.

## Overview

Your browser app on macOS or iOS can authenticate people to websites by using passkeys stored in the keychain, and managed by third-party credential providers. It can also create passkeys that the operating system stores in the keychain, or that third-party credential providers store. Optionally, when someone authenticates with a website, present your own UI to list the passkeys available for the website so they can choose which passkey to use; otherwise, delegate to the operating system’s UI to choose passkeys or, on iOS, use AutoFill.

Use ASAuthorizationController when performing requests defined in the WebAuthentication standard. If you present your own passkey-selection UI, you can specify allowedCredentials to restrict the system UI to only show the selected passkey. Implement the authorization controller’s delegate callback to receive passkey request responses, which you return to the website that makes the request.

### Request access to passkeys

When someone wants to use a passkey to authenticate with a website, create an instance of ASAuthorizationWebBrowserPublicKeyCredentialManager and follow these steps:

- Get the credential manager’s authorizationStateForPlatformCredentials property to check whether your app can use passkeys stored in the keychain or in third-party credential managers.

- If the state is ASAuthorizationWebBrowserPublicKeyCredentialManager.AuthorizationState.authorized, then get the credentials associated with the relying party from the credential manager.

- If the state is ASAuthorizationWebBrowserPublicKeyCredentialManager.AuthorizationState.notDetermined, call requestAuthorizationForPublicKeyCredentials(_:), passing a completion handler that the operating system calls when someone grants or denies the request.

- If the state is ASAuthorizationWebBrowserPublicKeyCredentialManager.AuthorizationState.denied, the person doesn’t allow your app to use their passkeys.

```
class BrowserAuthorizationController {
  func authenticatePerson(for relyingParty: String) throws {
    // Check the authorization state.
    let credentialManager = ASAuthorizationWebBrowserPublicKeyCredentialManager()
    switch(credentialManager.authorizationStateForPlatformCredentials) {
    case .authorized:
      // Use the credentials.
      let credentials = credentialManager.platformCredentials(forRelyingParty: relyingParty)
      self.respondToChallenge(for: relyingParty, using: credentials)
    case .denied:
      // Your app doesn't have access to the credentials.
      throw BrowserError("Unable to access passkeys to authenticate with \(relyingParty)")
    case .notDetermined:
      // Request access to the credentials.
      credentialManager.requestAuthorizationForPublicKeyCredentials() { authorizationState in
        // Check the updated authorizationState, and use the credentials if possible.
      }
    }
  }
}
```

### Create an assertion request

The credentials you get from the credential manager don’t contain the key data; instead, they contain metadata that identifies the credentials to the operating system and to the authenticating person. If the array of credentials contains more than one credential, present them to the person so they can select which credential to use.

Create a credential assertion request, using the challenge data sent by the requesting website. If the person chose a credential to use, restrict the request to allow only that credential. Pass the request to an ASAuthorizationController instance to complete the challenge.

```
extension BrowserAuthorizationController {
  func startAuthenticationChallenge(for relyingParty: String,
    selectedCredential: ASAuthorizationWebBrowserPlatformPublicKeyCredential?,
    challengeData: Data) async {
    let clientData = ASPublicKeyCredentialClientData(challenge: challengeData,
      origin: self.requestOrigin)
    let request = ASAuthorizationPlatformPublicKeyCredentialProvider(relyingPartyIdentifier: relyingParty)
      .createCredentialAssertionRequest(clientData: clientData)
    if let selectedCredential {
      request.allowedCredentials = [ASAuthorizationPlatformPublicKeyCredentialDescriptor(credentialID: selectedCredential.credentialID)]
    }
    let controller = ASAuthorizationController(authorizationRequests: [request])
    controller.delegate = self
    controller.presentationContextProvider = self
    controller.performRequests()
  }
}
```

To start an authorization request using AutoFill presentation on iOS, call performAutoFillAssistedRequests() on the authorization controller instead of performRequests().

### Supply a presentation context provider

ASAuthorizationController might need to present UI to complete the authentication challenge. Conform to ASAuthorizationControllerPresentationContextProviding to provide a window in which the controller can display its UI.

```
extension BrowserAuthorizationController : ASAuthorizationControllerPresentationContextProviding {
  func presentationAnchor(for controller: ASAuthorizationController) -> ASPresentationAnchor {
    guard let window = self.view.window else {
      fatalError("Started a credential request when the browser view isn't presented in a window.")
    }
    return window
  }
}
```

### Implement authorization controller delegate callbacks

Conform to ASAuthorizationControllerDelegate to react to authorization completion. Implement methods to respond to successful authorization, and to get notified when errors occur.

```
extension BrowserAuthorizationController : ASAuthorizationControllerDelegate {
  func authorizationController(controller: ASAuthorizationController,
    didCompleteWithAuthorization authorization: ASAuthorization) {
    // The authorization was successful.
    // Use the authorization parameter to retrieve the credential, and send that to the relying party website.
  }

  func authorizationController(controller: ASAuthorizationController,
    didCompleteWithError error: Error) {
    // The authorization failed.
    // Use the error to find out what happened, and retry or notify someone.
  }
}
```

## See Also

### Website authorization

class ASAuthorizationWebBrowserPublicKeyCredentialManager

A class that you use to request access to a person’s passkeys in a web browser, and that reports on the access status.

