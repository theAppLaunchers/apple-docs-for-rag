

- Multipeer Connectivity
- MCAdvertiserAssistant
-  discoveryInfo 

Instance Property

# discoveryInfo

The `info` dictionary that was passed when this object was initialized.

iOS 7.0+iPadOS 7.0+Mac Catalyst 13.1+macOS 10.10+tvOS 10.0+visionOS 1.0+

``` source
var discoveryInfo: [String : String]? { get }
```

## Discussion

You set this property’s value when you initialize the object. It cannot be changed later.

## See Also

### Initializing and Configuring

init(serviceType: String, discoveryInfo: [String : String]?, session: MCSession)

Initializes an advertiser assistant object.

var session: MCSession

The session into which new peers are added after accepting an invitation.

var delegate: (any MCAdvertiserAssistantDelegate)?

The delegate object that handles advertising-assistant-related events.

var serviceType: String

The service type that your app is advertising.

