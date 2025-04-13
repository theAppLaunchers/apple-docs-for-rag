

- WatchKit
-  NowPlayingView 

Structure

# NowPlayingView

A view that displays the system’s Now Playing interface so that the user can control audio.

WatchKitSwiftUIwatchOS 7.0+

``` source
@MainActor @preconcurrency
struct NowPlayingView
```

## Mentioned in 

Adding a Now Playing View

## Overview

With a Now Playing view, users can control current or recently played audio without leaving your app. The Now Playing view displays information about the current audio source, such as another app on the user’s Apple Watch or iPhone. For example, users can play and pause music from their Apple Watch’s Music app or control the volume of a podcast on their iPhone.

The system automatically selects the source. If the user is listening to audio on their watch or phone, the system selects that audio source. Otherwise, the system selects the most recently used source.

Always present the Now Playing view so that it fills the screen in a nonscrolling container. Don’t add any other elements to the view.

## Topics

### Creating a Now Playing View

init()

Creates a view that displays the system’s Now Playing interface.

## Relationships

### Conforms To

- Sendable
- View

## See Also

### User interface

Storyboard support

Connect your code to storyboard elements using interface controllers, interface objects, and event handlers.

