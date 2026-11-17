- NowPlaying  
- Now Playing  
  
Framework  
  
# Now Playing  
  
Make your app’s media playback controls available on the Lock Screen, Control Center, and connected accessories.  
  
iOS 27.0+ iPadOS 27.0+ Mac Catalyst 27.0+ macOS 27.0+ tvOS 27.0+ visionOS 27.0+ watchOS 27.0+  
  
## Overview  
  
The Now Playing framework makes it easy for people to quickly access your app’s media controls across Apple platforms. The Now Playing interface integrates the controls on the Lock Screen, in Control Center, on Apple Watch, and in CarPlay. Use it to publish playback for music, audiobooks, podcasts, movies, TV shows, and other content. You describe your media content and supported commands with an Observable model, and the framework updates the system whenever your model changes.  
  
Now Playing supports two kinds of sessions:  
  
- Local sessions: Publish playback that happens on the current device. Create a type that conforms to MediaSessionRepresentable and use MediaSession to register it with the system. The framework observes your Observable model and publishes changes to the system as they happen.  
- Remote sessions: Publish playback that happens on external devices, such as speakers, streaming sticks, or smart TVs. Create an app extension that conforms to RemoteMediaSessionExtension and provide sessions conforming to RemoteMediaSessionRepresentable. Start remote sessions from your app using RemoteMediaSession, or from your server using push notifications when your app isn’t running.  
  
Important  
  
Don’t mix the Now Playing framework with the MPNowPlayingInfoCenter and MPRemoteCommandCenter APIs from the Media Player framework for local playback. Doing so results in undefined behavior.  
  
## Topics  
  
### Local sessions  
  
Publishing media sessions  
  
Show your app’s media on the Lock Screen and Control Center.  
  
protocol MediaSessionRepresentable  
  
A protocol that provides content metadata, playback state, and commands for a Now Playing session.  
  
class MediaSession  
  
A local Now Playing session that publishes metadata and commands to the system.  
  
enum MediaSessionError  
  
Errors that can occur during local session operations.  
  
### Remote sessions  
  
Publishing remote media sessions  
  
Show media from an external device on the Lock Screen and Control Center.  
  
protocol RemoteMediaSessionRepresentable  
  
A session that plays remotely, potentially across multiple devices.  
  
class RemoteMediaSession  
  
A session that manages remote media playback across devices.  
  
protocol RemoteMediaSessionExtension  
  
An app extension that provides remote media sessions.  
  
class RemoteMediaSessionExtensionConfiguration  
  
The configuration object for a remote playback extension.  
  
protocol RemoteMediaSessionAttributes  
  
A type that represents attributes for remote sessions.  
  
enum RemoteMediaSessionError  
  
Errors that can occur during remote session operations.  
  
struct MediaDevice  
  
A device that plays media in a remote session.  
  
### Playback  
  
struct MediaPlaybackSnapshot  
  
A snapshot of playback state and timing for a Now Playing session.  
  
Content types and metadata  
  
Describe the media your app is playing.  
  
Playback commands  
  
Declare the playback controls your app supports.  
