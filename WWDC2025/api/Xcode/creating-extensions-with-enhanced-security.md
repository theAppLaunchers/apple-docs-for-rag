*   [Xcode](/documentation/xcode)
*   [Build system](/documentation/xcode/build-system)
*   Creating extensions with enhanced security

Article

# Creating extensions with enhanced security

Reduce opportunities for an attacker to target your app through its extensions.

## [Overview](/documentation/Xcode/creating-extensions-with-enhanced-security#Overview)

Separating sensitive calculations, such as handling data from untrusted sources, into extensions that the system runs as separate processes from your app reduces the opportunity for attackers to target the sensitive calculation and gain access to other parts of your app or the system. Create enhanced security extensions on iOS, iPadOS, and macOS to enforce tighter sandbox restrictions, and enable compiler and runtime security protections.

### [Define the extension point in your app](/documentation/Xcode/creating-extensions-with-enhanced-security#Define-the-extension-point-in-your-app)

Add the `EX_ENABLE_EXTENSION_POINT_GENERATION` user-defined build setting with the value `YES` to your app target’s build setting. In your app’s source code, create an extension to [`AppExtensionPoint`](/documentation/ExtensionFoundation/AppExtensionPoint) that defines your app’s extension point. Give the extension point the [`AppExtensionPoint.Name`](/documentation/ExtensionFoundation/AppExtensionPoint/Name) of your choosing, and the [`AppExtensionPoint.EnhancedSecurity`](/documentation/ExtensionFoundation/AppExtensionPoint/EnhancedSecurity) attribute to tell the system to run your extension in the enhanced security runtime:

```swift

```swift
import ExtensionFoundation
extension AppExtensionPoint {
  @Definition
  static var exampleExtension: AppExtensionPoint {
    Name("exampleExtension")
    EnhancedSecurity()
  }
}
```

```

### [Create the extension](/documentation/Xcode/creating-extensions-with-enhanced-security#Create-the-extension)

Follow these steps to create the extension:

1.  In Xcode, choose File > New > Target, and select the Generic Extension template.
    
2.  Select the Enhanced Security Extension extension type, and click Finish.
    
3.  In the Xcode project navigator, delete the extension target’s `Info.plist` file.
    
4.  In the target build settings editor, delete the `INFOPLIST_FILE` build setting for the extension target.
    

Edit the main source file for the extension, so that the [`AppExtensionPoint.Identifier`](/documentation/ExtensionFoundation/AppExtensionPoint/Identifier) for the extension point it binds to has your app’s bundle ID as the host identifier, and the name you gave the extension point in the previous section:

```swift

```swift
import ExtensionFoundation
@main
```swift
```swift
struct MyAppHelper: ExampleExtension {
```
```
  @AppExtensionPoint.Bind
  var boundExtensionPoint: AppExtensionPoint {
    AppExtensionPoint.Identifier(host: "com.example.my-app", name: "exampleExtension")
  }
}
```

```

Write the code to implement your extension’s behavior. The system runs your extension in a sandbox that restricts access to most system services and frameworks. In particular, your extension can’t present UI. Instead, it must communicate with its host app, and ask the app to present UI and interact with other system services on the extension’s behalf.

### [Discover and launch the extension](/documentation/Xcode/creating-extensions-with-enhanced-security#Discover-and-launch-the-extension)

In your app, create an [`AppExtensionPoint.Monitor`](/documentation/ExtensionFoundation/AppExtensionPoint/Monitor) to discover the enhanced security extension:

```swift
```swift
```swift
```swift
```swift
```swift
let monitor = try await AppExtensionPoint.Monitor(appExtensionPoint: AppExtensionPoint.exampleExtension)
```
```
guard let identity = monitor.identities.first else {     
   fatalError("Extension not found")
}
```
```
```
```

The `identity` represents the bundle for the enhanced security extension you created in the previous section. Create an [`AppExtensionProcess`](/documentation/ExtensionFoundation/AppExtensionProcess) with that bundle to launch the extension:

```swift

```swift
do {
  self.process = try await AppExtensionProcess(configuration: .init(appExtensionIdentity: identity, onInterruption: {
    // The system calls this closure when the extension exits.
  }))
  // Communicate with the extension.
}
catch let error {
  // The system can't launch the extension.
}
```

```

### [Communicate between the app and the extension](/documentation/Xcode/creating-extensions-with-enhanced-security#Communicate-between-the-app-and-the-extension)

Use [`XPCSession`](/documentation/XPC/XPCSession) to handle communication between your app and its enhanced security extension. For more information, see [Creating XPC services](/documentation/XPC/creating-xpc-services).

Define structures that conform to [`Codable`](/documentation/Swift/Codable) in code you share between the app and extension, and create instances of those structures to send over XPC using the session you create:

```swift
```swift
```swift
```swift
```swift
```swift
struct Message: Identifiable, Codable {
```
```
  var id: String
  // Add properties that represent data your app sends to its extension.
  struct Response: Codable {
    // Define another structure that the extension sends back to the app in its reply.
  }
}
```
```
```
```

Call [`makeXPCSession()`](/documentation/ExtensionFoundation/AppExtensionProcess/makeXPCSession\(\)) in your app to create an `XPCSession` you use to send messages to the extension:

```swift

```swift
do {
  self.xpcSession = try process.makeXPCSession()
  try xpcSession.activate()
  // Send messages to the extension.
}
catch let error {
  // The system can't create the XPC session.
}
```

```

Use the session you create to send messages to the extension, and receive responses:

```swift
```swift
```swift
```swift
```swift
```swift
let response = try await withCheckedThrowingContinuation { continuation in
```
```
  do {
    // Construct the message the app sends to the extension.
    let message = Message()
    try xpcSession.send(Message()) { result in
      switch result {
      case .success(let reply):
        let response = (try? reply.decode(as: Message.Response.self)) ?? /* Create a default response. */
        continuation.resume(returning: response)
      case .failure(let error):
        continuation.resume(throwing: error)
      }
    }
  }
  catch {
    continuation.resume(throwing: error)
  }
}
// Interpret the response from the extension.
```
```
```
```

In the extension, create a [`ConnectionHandler`](/documentation/ExtensionFoundation/ConnectionHandler) to accept incoming connections from the app. Call the [`init(onSessionRequest:)`](/documentation/ExtensionFoundation/ConnectionHandler/init\(onSessionRequest:\)) initializer, and use the closure to accept the XPC connection and create a session.

```swift

```swift
extension ExampleExtension {
    var configuration: some AppExtensionConfiguration {
        // Return your extension's configuration upon request.
        return ConnectionHandler(onSessionRequest: { request in
            let handler = MessageHandler(appExtension: self)
            return request.accept { session in
                return handler
            }
        })
    }
}
 
fileprivate struct MessageHandler<E: ExampleExtension>: XPCPeerHandler, Sendable {
    let appExtension: E
     
    func handleIncomingRequest(_ message: Message) -> (any Encodable)? {
        // Process the incoming message.
        return Message.Response()
    }
}
```

```

### [Adopt other security hardening features](/documentation/Xcode/creating-extensions-with-enhanced-security#Adopt-other-security-hardening-features)

Enhanced security extensions use the same compiler and runtime security features as apps that adopt the Enhanced Security capability. For more information, see [Enabling enhanced security for your app](/documentation/xcode/enabling-enhanced-security-for-your-app).

## [See Also](/documentation/Xcode/creating-extensions-with-enhanced-security#see-also)

### [Security and privacy](/documentation/Xcode/creating-extensions-with-enhanced-security#Security-and-privacy)

[

Verifying the origin of your XCFrameworks](/documentation/xcode/verifying-the-origin-of-your-xcframeworks)

Discover who signed a framework, and take action when that changes.

[

Enabling enhanced security for your app](/documentation/xcode/enabling-enhanced-security-for-your-app)

Detect out-of-bounds memory access, use of freed memory, and other potential vulnerabilities.

[

Adopting type-aware memory allocation](/documentation/xcode/adopting-type-aware-memory-allocation)

Reduce the opportunities to treat pointers as data in your code.

[

Conforming to Mach IPC security restrictions](/documentation/xcode/conforming-to-mach-ipc-security-restrictions)

Avoid crashes and potentially insecure situations associated with Mach messages.