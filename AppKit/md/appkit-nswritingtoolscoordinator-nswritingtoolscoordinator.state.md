

- AppKit
- NSWritingToolsCoordinator
-  NSWritingToolsCoordinator.State 

Enumeration

# NSWritingToolsCoordinator.State

The states that indicate the current activity, if any, Writing Tools is performing in your view.

macOS 15.2+

``` source
enum State
```

## Mentioned in 

Adding Writing Tools support to a custom AppKit view

## Overview

Making changes to your view requires several different levels of interaction. Initially, Writing Tools displays its UI and collects information about what the person wants to do. When the person selects an operation, Writing Tools sends the relevant details to a large language model (LLM) and processes the results. It then works with the custom view to integrate any changes into the view’s text storage. During each of these activities, the coordinator reflects what’s happening in its state property. You can use the current state as a guide to making decisions in other parts of your view.

## Topics

### Getting the animation types

case inactive

A state that indicates Writing Tools isn’t currently performing any work on your view’s content.

case noninteractive

A state that indicates Writing Tools is handling interactions in the system UI, instead of in your view.

case interactiveResting

A state that indicates Writing Tools is in the resting state for an inline editing experience.

case interactiveStreaming

A state that indicates Writing Tools is processing a request and incorporating changes interactively into your view.

### Initializers

init?(rawValue: Int)

## Relationships

### Conforms To

- BitwiseCopyable
- Equatable
- Hashable
- RawRepresentable
- Sendable

## See Also

### Managing the current state

func stopWritingTools()

Stops the current Writing Tools operation and dismisses the system UI.

var state: NSWritingToolsCoordinator.State

The current level of Writing Tools activity in your view.

