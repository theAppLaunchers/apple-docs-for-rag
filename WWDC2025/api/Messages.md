Framework

# Messages

Create app extensions that allow users to send text, stickers, media files, and interactive messages.

iOS 10.0+iPadOS 10.0+Mac Catalyst 14.0+

## [Overview](/documentation/Messages#overview)

You can use the Messages framework to create sticker packs and iMessage apps. You can create sticker packs and iMessage apps as either standalone apps or as app extensions within a containing iOS app. For more information on creating and working with app extensions, see [App extensions](https://developer.apple.com/app-extensions/).

iMessage apps and stickers help people interact and communicate in the context of a Messages conversation. For design guidance, see [Human Interface Guidelines > iMessage apps and stickers](https://developer.apple.com/design/human-interface-guidelines/imessage-apps-and-stickers).

### [iMessage apps](/documentation/Messages#iMessage-apps)

iMessage apps leverage the full framework to interact with the Messages app.

Note

To avoid a crash, an iMessage app linked on or after iOS 10 must include usage description keys for the device features it needs to access in its `Info.plist` file. Specifically, it must include [`NSCameraUsageDescription`](/documentation/BundleResources/Information-Property-List/NSCameraUsageDescription) to access the device’s camera, and it must include [`NSMicrophoneUsageDescription`](/documentation/BundleResources/Information-Property-List/NSMicrophoneUsageDescription) to access the device’s microphones.

Use iMessage apps to:

*   Present a custom user interface inside the Messages app; see [`MSMessagesAppViewController`](/documentation/messages/msmessagesappviewcontroller).
    
*   Create a custom or dynamic sticker browser; see [`MSStickerBrowserViewController`](/documentation/messages/msstickerbrowserviewcontroller).
    
*   Insert text, stickers, or media files into the Messages app’s input field; see [`MSConversation`](/documentation/messages/msconversation).
    
*   Create interactive messages that carry app-specific data; see [`MSMessage`](/documentation/messages/msmessage).
    
*   Update interactive messages (for example, to create games or collaborative apps); see [`MSSession`](/documentation/messages/mssession).
    

For more information on submitting iMessage Apps to the App Store, see [Preparing Your iMessage App for Submission](https://developer.apple.com/app-store/imessage-app-submissions/).

In iOS 17, Messages allows you to interactively resize iMessage apps with a vertical pan gesture. Messages handles any conflicts between resize gestures and your custom gestures. If your app uses manual touch handling such as [`touchesBegan(_:with:)`](/documentation/UIKit/UIGestureRecognizer/touchesBegan\(_:with:\)), [`touchesMoved(_:with:)`](/documentation/UIKit/UIGestureRecognizer/touchesMoved\(_:with:\)), and [`touchesEnded(_:with:)`](/documentation/UIKit/UIGestureRecognizer/touchesEnded\(_:with:\)), you can do either of the following:

*   Change your manual touch handling code to use a gesture recognizer instead.
    
*   Use your [`UIView`](/documentation/UIKit/UIView) to override [`gestureRecognizerShouldBegin(_:)`](/documentation/UIKit/UIGestureRecognizerDelegate/gestureRecognizerShouldBegin\(_:\)) and return `NO` when your iMessage app doesn’t own the gesture.
    

### [Become the default messaging app](/documentation/Messages#Become-the-default-messaging-app)

In iOS and iPadOS 18.2 and later, a person may select an app other than the Messages app to send instant messages. If you wish to make your app the default messages app, see [Preparing your app to be the default messaging app](/documentation/messages/preparing-your-app-to-be-the-default-messaging-app).

## [Topics](/documentation/Messages#topics)

### [Default messaging app](/documentation/Messages#Default-messaging-app)

[

Preparing your app to be the default messaging app](/documentation/messages/preparing-your-app-to-be-the-default-messaging-app)

Configure your messaging app so people can set it as the default on their device.

### [Custom sticker packs](/documentation/Messages#Custom-sticker-packs)

[

Adding Sticker packs and iMessage apps to the system Stickers app, Messages camera, and FaceTime](/documentation/messages/adding-sticker-packs-and-imessage-apps-to-the-system-stickers-app-messages-camera-and-facetime)

Enable your Sticker pack or iMessage app in the media context.

[

Adding your sticker packs to Messages](/documentation/messages/adding-your-sticker-packs-to-messages)

Drag and drop your sticker pack into the Stickers asset catalog to let people access your stickers from Messages.

```swift
```swift
```swift
class MSStickerBrowserViewController
```
```

A view controller that provides dynamic content to the standard sticker browser.
```
```swift
```swift
```swift
class MSStickerBrowserView
```
```

A browser view that displays a dynamically generated list of stickers.
```
```swift
```swift
```swift
class MSStickerView
```
```

A view for displaying a sticker.
```
```swift
```swift
```swift
enum MSStickerSize
```
```

The size of the stickers in the browser view.
```

### [Custom iMessage app interface](/documentation/Messages#Custom-iMessage-app-interface)

[

IceCreamBuilder: Building an iMessage Extension](/documentation/messages/icecreambuilder-building-an-imessage-extension)

Allow users to collaborate on the design of ice cream sundae stickers.

[

Creating a Sticker App with a Custom Layout](/documentation/messages/creating-a-sticker-app-with-a-custom-layout)

Expand on the Messages sticker app template to create an app with a customized user interface.

```swift
```swift
```swift
class MSMessagesAppViewController
```
```

The principal view controller for iMessage apps.
```
```swift
```swift
```swift
protocol MSMessagesAppTranscriptPresentation
```
```

A protocol that provides support for displaying live messages in the transcript of the Messages app.
```
```swift
```swift
```swift
enum MSMessagesAppPresentationStyle
```
```

Presentation styles that describe your iMessage app’s appearance.
```

### [Message content](/documentation/Messages#Message-content)

```swift
```swift
```swift
```swift
class MSConversation
```
```

An object that represents a conversation in the Messages app.
```
```swift
```swift
```swift
class MSSticker
```
```

A sticker that can be sent as a new message or attached to an existing balloon in the Messages app’s transcript.
```
```

### [Interactive messages](/documentation/Messages#Interactive-messages)

```swift
```swift
```swift
```swift
class MSMessage
```
```

A custom message object.
```
```swift
```swift
```swift
class MSSession
```
```

A session object used to create and update messages.
```
```swift
```swift
```swift
class MSMessageLayout
```
```

An abstract base class that defines the appearance of [`MSMessage`](/documentation/messages/msmessage) objects in the conversation transcript.
```
```swift
```swift
```swift
class MSMessageTemplateLayout
```
```

A template-based layout for custom messages.
```
```swift
```swift
```swift
class MSMessageLiveLayout
```
```

A layout that provides a custom, interactive view inside the transcript.
```
```

### [Critical messages](/documentation/Messages#Critical-messages)

[

Sending SMS messages from an app](/documentation/messages/critical-messaging-api)

Send critical messages from inside your app using the Critical Messaging API.

```swift
```swift
```swift
class MSCriticalSMSMessenger
```
```

The user interface for the Critical Messaging API.
```
```swift
```swift
```swift
struct MSRecipient
```
```

A structure that describes the recipient of a critical message.
```
```swift
```swift
```swift
struct MSCriticalMessage
```
```

MSCriticalMessage A simple struct to encapsulate the message string.
```
```swift
```swift
```swift
enum MSCriticalMessagingAuthorizationStatus
```
```

Values that describe the authorization status for the Critical Messaging API.
```

### [Errors](/documentation/Messages#Errors)

```swift
```swift
```swift
```swift
let MSStickersErrorDomain: String
```
```

The error domain for stickers.
```
```swift
```swift
```swift
let MSMessagesErrorDomain: String
```
```

The error domain for iMessage apps.
```
```swift
```swift
```swift
enum MSMessageErrorCode
```
```

The error codes that the Messages framework generates.
```
```swift
```swift
```swift
enum MSCriticalMessagingError
```
```

Values that describe errors the Critical Messaging API returns.
```
```