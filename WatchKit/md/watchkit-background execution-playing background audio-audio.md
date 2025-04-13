

- WatchKit
- Background execution
-  Playing Background Audio 

Article

# Playing Background Audio

Enable background audio in your app to provide a seamless playback experience.

## Overview

While most watchOS apps are optimized for quick interactions, apps that play audio content should continue playing even after the user lowers their wrists or navigates to a new app. Your app needs to play audio in the background in order to provide this seamless playback experience.

To play background audio:

1.  Enable the Audio Background Mode.

2.  Configure and Activate the audio session.

3.  Start playing.

### Enable the Audio Background Mode

First, you must enable the Audio Background Mode capability for your WatchKit extension, as shown in Figure 1.

This step sets the UIBackgroundModes key in your extension’s `Info.plist` file.

### Configure and Activate the Audio Session

Before you can play audio, you need to set up and activate the audio session.

Start by setting the session’s category to playback, and the route policy to longForm.

```
session.setCategory(AVAudioSession.Category.playback,
                        mode: .default,
                        policy: .longForm,
                        options: [])
```

Next, activate the session, by calling the activate(options:completionHandler:) method.

```
session.activate(options: []) { (success, error) in
    // Check for an error and play audio.
}
```

This method sets up the audio route asynchronously before activating your session. watchOS requires a Bluetooth audio route for long-form audio. If necessary, the system presents an audio route picker to the user, letting them choose the Bluetooth route (see Figure 2).

In general, if the user has previously selected a Bluetooth route or if AirPods or other W1-equipped Bluetooth headphones are nearby, the system picks the audio route automatically without displaying a picker view to the user. If no applicable Bluetooth route is selected (either automatically or by the user), the system passes an error to the completion handler.

### Start Playing

The activate(options:completionHandler:) method calls its completion handler as soon as a Bluetooth route is selected or when an error occurs. Check for errors in the completion handler. If no errors occurred, you can begin playing your audio content.

The code listing below shows all the steps needed to set up the session, activate it, and begin playing.

```
// Set up the session.
let session = AVAudioSession.sharedInstance()

do {
    try session.setCategory(AVAudioSession.Category.playback,
                            mode: .default,
                            policy: .longForm,
                            options: [])
} catch let error {
    fatalError("*** Unable to set up the audio session: \(error.localizedDescription) ***")
}

// Set up the player.
let player: AVAudioPlayer
do {
    player = try AVAudioPlayer(data: audioData)
} catch let error {
    print("*** Unable to set up the audio player: \(error.localizedDescription) ***")
    // Handle the error here.
    return
}

// Activate and request the route.
session.activate(options: []) { (success, error) in
    guard error == nil else {
        print("*** An error occurred: \(error!.localizedDescription) ***")
        // Handle the error here.
        return
    }

    // Play the audio file.
    player.play()
}
```

## See Also

### Background sessions

Enabling Background Sessions

Enable the background mode for audio, location updates, remote notifications, or workouts.

WKBackgroundModes

The services a watchOS app provides that require it to continue running in the background.

UIBackgroundModes

Services provided by an app that require it to run in the background.

