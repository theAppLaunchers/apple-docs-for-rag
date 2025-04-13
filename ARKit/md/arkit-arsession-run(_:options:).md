

- ARKit
- ARSession
-  run(\_:options:) 

Instance Method

# run(\_:options:)

Starts AR processing for the session with the specified configuration and options.

iOS 11.0+iPadOS 11.0+Mac Catalyst 13.1+

``` source
func run(
    _ configuration: ARConfiguration,
    options: ARSession.RunOptions = []
)
```

## Parameters 

`configuration`  

An object that defines motion and scene tracking behaviors for the session.

`options`  

Options affecting how existing session state (if any) transitions to the new configuration.

If the session is running for the first time, this parameter has no effect.

## Mentioned in 

Managing Session Life Cycle and Tracking Quality

## Discussion

The session tracks device motion, captures and processes scene imagery from the device camera, and coordinates with your delegate object or ARSCNView or ARSKView view only when running.

Calling this method on a session that has already started transitions immediately to the new session configuration. The `options` parameter determines how existing session state transitions to the new configuration. By default, the session resumes device position tracking from the last known state and keeps any anchors already included in the session (those you’ve added manually with add(anchor:), as well as those added automatically by ARKit features such as plane detection or face tracking).

This method returns immediately when called, but the session continues to run.

## See Also

### Configuring and running a session

var identifier: UUID

A unique identifier of the running session.

struct RunOptions

Options for transitioning an AR session’s current state when you change its configuration.

var configuration: ARConfiguration?

An object that defines motion and scene tracking behaviors for the session.

func pause()

Pauses processing in the session.

