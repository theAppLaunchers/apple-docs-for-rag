*   [Messages](/documentation/messages)
*   Adding Sticker packs and iMessage apps to the system Stickers app, Messages camera, and FaceTime

Article

# Adding Sticker packs and iMessage apps to the system Stickers app, Messages camera, and FaceTime

Enable your Sticker pack or iMessage app in the media context.

## [Overview](/documentation/Messages/adding-sticker-packs-and-imessage-apps-to-the-system-stickers-app-messages-camera-and-facetime#overview)

In iOS 12 and later, Sticker packs and iMessage apps can appear in multiple contexts.

[`MSMessagesAppPresentationContext.messages`](/documentation/messages/msmessagesapppresentationcontext/messages) context

The Sticker pack or iMessage app appears in the list of iMessage apps that appears when you press the plus button.

[`MSMessagesAppPresentationContext.media`](/documentation/messages/msmessagesapppresentationcontext/media) context

The sticker pack or iMessage app appears in the Stickers app throughout iOS, and in effect in FaceTime and the Messages camera.

People can access stickers throughout iOS through the emoji keyboard. To access effects in the Messages camera or FaceTime, a person taps the effects button. The system then displays all the iMessage apps and Sticker packs that support the media context. A person can launch an app, and use it to add images or stickers to the camera.

iMessage apps only appear in the `messages` context. To enable support for the `media` context, set the `MSSupportedPresentationContexts` key in your extension’s `Info.plist` file. If you indicate support for both `messages` and `media`, your Stickers only present in the `media` context including in Messages.

A Sticker pack or iMessage app’s context limits its available features. For example, In the [`MSMessagesAppPresentationContext.messages`](/documentation/messages/msmessagesapppresentationcontext/messages) context, a person can peel off stickers and attach them to any bubbles in the current conversation. Your app can also programatically send stickers, images, text, or interactive messages.

In the [`MSMessagesAppPresentationContext.media`](/documentation/messages/msmessagesapppresentationcontext/media) context, your app appears in effects in Messages and FaceTime. Therefore, the system limits your app to features that make sense over a photo or video. For instance, a person can’t play an interactive game while taking a photo; however, they can add stickers or images to the picture.

### [Specify the supported contexts](/documentation/Messages/adding-sticker-packs-and-imessage-apps-to-the-system-stickers-app-messages-camera-and-facetime#Specify-the-supported-contexts)

To specify the supported contexts:

1.  Open the `Info.plist` file for your Sticker pack or iMessage app extension.
    
2.  Add the `MSSupportedPresentationContexts` key, using an Array type.
    
3.  Add String values for the supported contexts. For the [`MSMessagesAppPresentationContext.messages`](/documentation/messages/msmessagesapppresentationcontext/messages) context, add the `MSMessagesAppPresentationContextMessages` value. For [`MSMessagesAppPresentationContext.media`](/documentation/messages/msmessagesapppresentationcontext/media), add `MSMessagesAppPresentationContextMedia`.
    

You must specify one of the contexts, but if you specify both contexts, they only present in the [`MSMessagesAppPresentationContext.media`](/documentation/messages/msmessagesapppresentationcontext/media) context.

For more information on setting I`nfo.plist` keys, see [Edit property lists](https://help.apple.com/xcode/mac/9.3/#/dev3f399a2a6).

### [Work with the media context](/documentation/Messages/adding-sticker-packs-and-imessage-apps-to-the-system-stickers-app-messages-camera-and-facetime#Work-with-the-media-context)

The [`MSMessagesAppPresentationContext.media`](/documentation/messages/msmessagesapppresentationcontext/media) context supports only a subset of the features provided by the Messages framework. People can peel stickers from a sticker browser view, and place them in the Messages camera or FaceTime. They can reposition, resize, rotate, or remove stickers from the viewfinder.

iMessage apps can also insert stickers or images into the viewfinder using the [`insert(_:completionHandler:)`](/documentation/messages/msconversation/insert\(_:completionhandler:\)-7fpdd) or [`insertAttachment(_:withAlternateFilename:completionHandler:)`](/documentation/messages/msconversation/insertattachment\(_:withalternatefilename:completionhandler:\)) methods. However, if the attachment isn’t an image supported by [`MSSticker`](/documentation/messages/mssticker), then the [`insertAttachment(_:withAlternateFilename:completionHandler:)`](/documentation/messages/msconversation/insertattachment\(_:withalternatefilename:completionhandler:\)) method fails with an [`MSMessageErrorCode.apiUnavailableInPresentationContext`](/documentation/messages/msmessageerrorcode/apiunavailableinpresentationcontext) error.

Additionally, you can’t insert interactive messages or text into the media context. You also can’t send items automatically. Therefore, the following methods from the [`MSConversation`](/documentation/messages/msconversation) class aren’t available:

*   [`insert(_:completionHandler:)`](/documentation/messages/msconversation/insert\(_:completionhandler:\)-3g248)
    
*   [`insertText(_:completionHandler:)`](/documentation/messages/msconversation/inserttext\(_:completionhandler:\))
    
*   [`sendAttachment(_:withAlternateFilename:completionHandler:)`](/documentation/messages/msconversation/sendattachment\(_:withalternatefilename:completionhandler:\))
    
*   [`send(_:completionHandler:)`](/documentation/messages/msconversation/send\(_:completionhandler:\)-9krz)
    
*   [`send(_:completionHandler:)`](/documentation/messages/msconversation/send\(_:completionhandler:\)-4kje0)
    
*   [`sendText(_:completionHandler:)`](/documentation/messages/msconversation/sendtext\(_:completionhandler:\))
    

If you call these methods, they fail with an [`MSMessageErrorCode.apiUnavailableInPresentationContext`](/documentation/messages/msmessageerrorcode/apiunavailableinpresentationcontext) error.

Additionally, because you can’t send or receive interactive messages, the system never calls the following methods in the [`MSMessagesAppPresentationContext.media`](/documentation/messages/msmessagesapppresentationcontext/media) context:

*   [`willSelect(_:conversation:)`](/documentation/messages/msmessagesappviewcontroller/willselect\(_:conversation:\))
    
*   [`didSelect(_:conversation:)`](/documentation/messages/msmessagesappviewcontroller/didselect\(_:conversation:\))
    
*   [`didReceive(_:conversation:)`](/documentation/messages/msmessagesappviewcontroller/didreceive\(_:conversation:\))
    
*   [`didStartSending(_:conversation:)`](/documentation/messages/msmessagesappviewcontroller/didstartsending\(_:conversation:\))
    
*   [`didCancelSending(_:conversation:)`](/documentation/messages/msmessagesappviewcontroller/didcancelsending\(_:conversation:\))
    

Finally, the [`MSMessagesAppPresentationContext.media`](/documentation/messages/msmessagesapppresentationcontext/media) context is already inside the Messages camera or FaceTime; therefore, you can’t display another camera inside the current viewfinder.

### [Detect the current context](/documentation/Messages/adding-sticker-packs-and-imessage-apps-to-the-system-stickers-app-messages-camera-and-facetime#Detect-the-current-context)

Use the [`MSMessagesAppViewController`](/documentation/messages/msmessagesappviewcontroller) object’s [`presentationContext`](/documentation/messages/msmessagesappviewcontroller/presentationcontext) property to determine your iMessage app’s current context. Enable only the features that make sense in that context.

```

```
if presentationContext == .messages {
    // The system is presenting your iMessage app inside the Messages app.
    // You have full access to the Messages framework.
    // You can insert or send stickers, text, attachments, or interactive messages.
} else if presentationContext == .media {
    // The system is presenting your iMessage app in effects.
    // You can only insert stickers and images.
}
```

```

## [See Also](/documentation/Messages/adding-sticker-packs-and-imessage-apps-to-the-system-stickers-app-messages-camera-and-facetime#see-also)

### [Custom sticker packs](/documentation/Messages/adding-sticker-packs-and-imessage-apps-to-the-system-stickers-app-messages-camera-and-facetime#Custom-sticker-packs)

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