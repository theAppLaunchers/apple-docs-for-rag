

- Foundation
- NSXPCConnection
-  setCodeSigningRequirement(\_:) 

Instance Method

# setCodeSigningRequirement(\_:)

Sets the code signing requirement for this connection.

macOS 13.0+

``` source
func setCodeSigningRequirement(_ requirement: String)
```

## Parameters 

`requirement`  

A string that describes requirements expected of the connection peer. See Code Signing Guide for more information on the code signing format.

## Discussion

Use this method to enforce a code-signing requirement on the peer process of an XPC connection.

The following example shows how a client can ensure that the XPC service on the other end of a connection has a specific entitlement.

- Swift
- Objective-C

```
let c = NSXPCConnection(serviceName: "com.example.ExampleService")
c.remoteObjectInterface = getServerInterface()
c.setCodeSigningRequirement("entitlement [com.example.testentitlement] exists")
c.resume()

if let proxy = c.remoteObjectProxyWithErrorHandler { error in
    // Handle error.
} as? MyServerInterface {
    proxy.myMessageWithReply() { reply in
        // Handle success case with "reply" from service.
    }
}
```

```
NSXPCConnection *c = [[NSXPCConnection alloc] initWithServiceName:@"com.example.ExampleService"];
c.remoteObjectInterface = getServerInterface();    
[c setCodeSigningRequirement:@"entitlement [com.example.testentitlement] exists"];
[c resume];

[[c remoteObjectProxyWithErrorHandler:^(NSError *error) {
    // If there is a code signing error, this block receives NSXPCConnectionCodeSigningRequirementFailure here.
}] myMessageWithReply:^(BOOL arg) {
    // Handle success case here.
}];

```

Calling this method with a malformed `requirement` results in a fatal error in Swift, or throws an exception in Objective-C. If new messages don’t match the requirement, the connection becomes invalidated.

Call this method before calling resume(), since it’s an XPC error to call this method more than once.

