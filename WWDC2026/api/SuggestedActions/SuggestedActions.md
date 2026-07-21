# SuggestedActions  
  
- SuggestedActions  
-  Suggested Actions  
  
Framework  
  
# Suggested Actions  
  
Offer quick actions next to messages in your messaging app, based on context you provide.  
  
iOS 27.0+ iPadOS 27.0+ Mac Catalyst 27.0+ macOS 27.0+ visionOS 27.0+  
  
## Overview  
  
When people send each other messages in your messaging app, they share information like dates, reminders, or other actionable content. To let people complete a message-related task in your messaging app with Suggested Actions, add a SuggestedActionsView below a message and provide the view with message content. To preserve user privacy, the framework analyzes the message content you provide on-device and doesn’t send it to Apple servers.  
  
By default, the SuggestedActionsView doesn’t take up space or affect your layout. When you provide it with message content, Suggested Actions identifies the suggested actions that apply to the message, then shows the SuggestedActionsView inline, filled with actions a person can take. For example, Suggested Actions can detect and suggest actions such as:  
  
- Creating an event in Calendar from a proposed meeting time  
- Adding an entry in Reminders  
- Opening a location in Maps  
  
Note  
  
To use the Suggested Actions framework, add the Suggested Actions entitlement to your app target.  
  
## Topics  
  
### Essentials  
  
Suggested Actions  
  
A Boolean value that indicates whether a messaging app displays suggested actions for a message.  
  
### Suggested actions for messages  
  
struct SuggestedActionsView  
  
A view that displays suggested actions for a message.  
