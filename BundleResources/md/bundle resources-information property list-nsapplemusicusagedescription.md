

- Bundle Resources
- Information Property List
-  NSAppleMusicUsageDescription 

Property List Key

# NSAppleMusicUsageDescription

A message that tells the user why the app is requesting access to the user’s media library.

iOS 2.0+iPadOS 2.0+macOS 15.0+visionOS 1.0+

## Details 

Name  
Privacy - Media Library Usage Description

Type  

string

## Discussion

Set the value of this key to a user-readable description of how your app intends to use a person’s media library. The first time your app attempts to access their library, the system prompts the user to grant or deny access to your app. The system includes this key’s description in the dialog it displays to the user.

Important

Your app must provide a value for this key to access a person’s media library. This requirement applies to iOS, iPadOS, visionOS, and macOS apps that link against the macOS 15 SDK or later.

## See Also

### MediaPlayer

Requesting Access to Apple Music Library

Prompt the customer to authorize access to Apple Music library.

