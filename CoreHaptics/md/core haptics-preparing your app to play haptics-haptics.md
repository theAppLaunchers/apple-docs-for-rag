

- Core Haptics
-  Preparing your app to play haptics 

Article

# Preparing your app to play haptics

Set up your app to play haptics.

## Overview

This article describes the process of setting up your app to play haptics. You’ll check for device compatibility, create a haptic engine, and then configure the engine’s handler properties.

Note

Make sure you set the engine’s handler properties before starting it to play a haptic.

### Check for device compatibility

Before you create and configure a haptic engine, check the hardware capabilities to see what type of feedback the device supports. Some devices don’t support haptic feedback, including iPad, iPod touch, and Apple Vision Pro. Checking the hardware capabilities lets you adjust your app’s behavior to provide alternative types of feedback as needed. For example, you might play stronger audio or multimedia, or you might provide visual feedback instead.

The following example fetches the hardware capabilities and checks the value of the supportsHaptics property to determine whether haptic feedback is available. The app then saves the result to a variable, which it uses later to determine what type of feedback to provide.

- Swift
- Objective-C

```
var supportsHaptics: Bool = false
...
// Check if the device supports haptics.
let hapticCapability = CHHapticEngine.capabilitiesForHardware()
supportsHaptics = hapticCapability.supportsHaptics
```

```
@property (nonatomic, assign) BOOL supportsHaptics;
...
// Check if the device supports haptics.
self.supportsHaptics = CHHapticEngine.capabilitiesForHardware.supportsHaptics;
```

For an example of conditioning haptic playback, see Playing a Custom Haptic Pattern from a File.

### Create a haptic engine

The CHHapticEngine is your app’s interface to the haptic device. Use an instance of a haptic engine to perform these key tasks:

- Create players to play those haptic and audio patterns.

- Play haptic patterns directly from a file URL.

- Modulate haptic patterns during playback.

Create this engine early in your app’s life cycle—for example, in your main view controller’s viewDidLoad()—and store it in an instance variable or property so it doesn’t go out of scope during playback.

- Swift
- Objective-C

```
var engine: CHHapticEngine!
...
// Create and configure a haptic engine.
do {
    engine = try CHHapticEngine()
} catch let error {
    fatalError("Engine Creation Error: \(error)")
}
```

```
@property (nonatomic, strong) CHHapticEngine* engine;
...
NSError* error;
_engine = [[CHHapticEngine alloc] initAndReturnError:&error];
```

Note

The haptic engine isn’t a singleton; you can create multiple instances in different parts of your app or game, like different view controllers or levels. Each instance of the haptic engine behaves independently. Core Haptics is thread-safe, meaning you can execute player operations on separate threads.

### Set the reset handler to recover from failure

Core Haptics calls the reset handler after the media server has recovered from failure. When this occurs, inside the reset handler, your app should do the following:

- Restart the haptic engine, if it was running at the time reset happened, by calling start().

- Reregister any custom audio resources you had registered, using registerAudioResource(_:options:).

- Recreate all haptic pattern players you had created, using makePlayer(with:).

- Swift
- Objective-C

```
// The reset handler provides an opportunity to restart the engine.
engine.resetHandler = {

    print("Reset Handler: Restarting the engine.")

    do {
        // Try restarting the engine.
        try self.engine.start()

        // Register any custom resources you had registered, using registerAudioResource.
        // Recreate all haptic pattern players you had created, using createPlayer.

    } catch {
        fatalError("Failed to restart the engine: \(error)")
    }
}
```

```
__weak ViewController* weakViewController = self;
[_engine setResetHandler:^{

    NSLog(@"Engine RESET!");

    // Try restarting the engine again.
    NSError* startupError;
    [weakViewController.engine startAndReturnError:&startupError];

    if (startupError) {
        NSLog(@"ERROR: Engine couldn't restart!");
    }

    // Register any custom resources you had registered, using registerAudioResource.
    // Recreate all haptic pattern players you had created, using createPlayer.
}];
```

Your app could attempt to restart the engine inside the handler, allowing it to recover on its own. However, as shown in the code listing above, a restart may still fail if the external reason for the reset hasn’t subsided.

### Receive notification of haptic engine stoppage due to outside causes

When external factors cause the haptic engine to stop, like audio interruptions from a phone call or because the user has put your app in the background, Core Haptics calls the stoppedHandler. The reason for the stoppage is passed into the handler. Because stopping is a normal part of the life cycle, you need to restart the engine before it can play the next haptic.

As you’re testing your app, set the stoppedHandler to debug the precise cause of the engine stoppage, as shown below.

- Swift
- Objective-C

```
// The stopped handler alerts engine stoppage.
engine.stoppedHandler = { reason in
    print("Stop Handler: The engine stopped for reason: \(reason.rawValue)")
    switch reason {
    case .audioSessionInterrupt: print("Audio session interrupt")
    case .applicationSuspended: print("Application suspended")
    case .idleTimeout: print("Idle timeout")
    case .systemError: print("System error")
    @unknown default:
        print("Unknown error")
    }
}
```

```
// The stopped handler alerts engine stoppage.
[_engine setStoppedHandler:^(CHHapticEngineStoppedReason reason){
    NSLog(@"Engine STOPPED!");
    switch (reason)
    {
        case CHHapticEngineStoppedReasonAudioSessionInterrupt: {
            NSLog(@"REASON: Audio Session Interrupt");
            // A phone call or notification could have come in, so take note to restart the haptic engine after the call ends. Wait for user-initiated playback.
            break;
        }
        case CHHapticEngineStoppedReasonApplicationSuspended: {
            NSLog(@"REASON: Application Suspended");
            // The user could have backgrounded your app, so take note to restart the haptic engine when the app reenters the foreground. Wait for user-initiated playback.
            break;
        }
        case CHHapticEngineStoppedReasonIdleTimeout: {
            NSLog(@"REASON: Idle Timeout");
            // The system stopped an idle haptic engine to conserve power, so restart it before your app must play the next haptic pattern.
            break;
        }
        case CHHapticEngineStoppedReasonSystemError: {
            NSLog(@"REASON: System Error");
            // The system faulted, so either continue without haptics or terminate the app.
            break;
        }
    }
}];
```

In production, your app can handle each cause in a different way. For example, you could handle the case CHHapticEngine.StoppedReason.systemError by continuing the app without haptics, or by throwing a fatal error to terminate the app.

Note

The stopped handler defined in the code above is called only when external causes trigger an engine stoppage. The stopped handler isn’t called if you manually stop the engine through an explicit stop(completionHandler:) call. Instead, Core Haptics calls the completion handler passed as input to the explicit stop call.

### Define and play haptics

Once you’ve set up your app to play haptics, you can incorporate haptic patterns. See:

- Simple haptic patterns defined inline as dictionaries: Playing a single-tap haptic pattern

- Custom file-based haptic patterns: Playing a Custom Haptic Pattern from a File

- Programmatic haptics tied to real-time physics: Playing Collision-Based Haptic Patterns

## See Also

### Essentials

Playing a single-tap haptic pattern

Create and play a transient haptic pattern from a dictionary literal inline.

class CHHapticEngine

An object that represents the connection to the haptic server.

class CHHapticPattern

An object representing a haptic waveform.

protocol CHHapticPatternPlayer

A protocol that defines a standard pattern player capable of playing haptic patterns with fixed parameters.

protocol CHHapticAdvancedPatternPlayer

A protocol that defines an advanced pattern player capable of looping, seeking, pausing, and resuming haptic playback.

