

- Security
-  Authorization Plug-ins 

API Collection

# Authorization Plug-ins

Extend the authorization services API by creating plug-ins that can participate in authorization decisions.

## Overview

Use plug-ins to extend macOS authorization services to perform authorizations in a new way or to implement a new policy that is too complex to be implemented entirely with the authorization policy database.

You must import this API explicitly:

- Swift
- Objective-C

```
import Security.AuthorizationPlugin
```

```
#import        
```

Note

When your plug-in needs to interact with the user, subclass the SFAuthorizationPluginView class to maintain the look and feel of the system authentication dialogs.

## Topics

### First Steps

Extending authorization services with plug-ins

Modify the system’s authorization policy with custom code.

### Creating a Plug-in

AuthorizationCallbacks Version

The version of the interface implemented by the authorization engine.

AuthorizationPluginInterface Version

The version of the interface implemented by the plug-in.

