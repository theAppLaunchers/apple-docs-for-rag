

- Speech
-  Asking Permission to Use Speech Recognition 

Article

# Asking Permission to Use Speech Recognition

Ask the user’s permission to perform speech recognition using Apple’s servers.

## Overview

The speech recognition process involves capturing audio of the user’s voice and sending that data to Apple’s servers for processing. The audio you capture constitutes sensitive user data, and you must make every effort to protect it. You must also obtain the user’s permission before sending that data across the network to Apple’s servers. You request authorization using the APIs of the Speech framework.

### Add the Privacy Key to Your Info.plist File

In Xcode, add the `“Privacy - Speech Recognition Usage Description”` key to your app’s `Info.plist` file. The raw name of this key is NSSpeechRecognitionUsageDescription. Set the value of this key to a string that explains how you plan to use any recognized speech. When your app request authorization later, the system displays the value of this key to the user as part of the system prompt.

Take the opportunity to build trust with the user through your usage description. The quality of your usage description can significantly impact the user’s decision. For example, users are more likely to deny authorization if the usage description is unclear or misleading. Good descriptions explain precisely how you intend to use speech recognition, and may also include a link to your app’s privacy policy. For example:

- “The app uses speech recognition for dictating notes.”

- “Lets you mark an item as finished by saying Done.”

- “The app listens for specific verbal commands, such as “Start”, “Stop”, and “Pause”. For a complete list of commands, see http://myapp.example.com”.

Important

You must include the NSSpeechRecognitionUsageDescription key in your app’s `Info.plist` file. If this key is not present, your app will crash when it attempts to request authorization or use the APIs of the Speech framework.

### Request Authorization at First Use

Before using the APIs of the Speech framework, you must call requestAuthorization(_:) on the SFSpeechRecognizer object. The method executes asynchronously and delivers the results to a block you provide. Use that block to determine whether the user granted or rejected your request.

Note

Do not request access to speech recognition if you do not intend to use the feature right away. Instead, delay requests until the user interacts with the portion of your app that uses such features.

The first time your app requests authorization to use speech recognition, the system prompts the user to accept or deny that request. The system records the user’s selection so that subsequent requests do not prompt the user again. Instead, subsequent requests return almost immediately with the previously recorded results.

The following example shows the authorization request for an app that transcribes spoken phrases and displays them onscreen. Because the app’s interface is dependent on speech recognition, it requests authorization as soon as that interface is visible. In addition, the app disables portions of the interface if the user or system prevents access to speech recognition.

```
```

## See Also

### Essentials

class SFSpeechRecognizer

An object you use to check for the availability of the speech recognition service, and to initiate the speech recognition process.

