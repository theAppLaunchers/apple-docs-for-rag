

- Messages
-  MSSession 

Class

# MSSession

A session object used to create and update messages.

iOS 10.0+iPadOS 10.0+Mac Catalyst 13.1+

``` source
class MSSession
```

## Overview

Note

The MSSession class does not declare any instance methods or properties. iMessage apps use MSSession objects to identify and track updatable messages.

MSMessage objects associated with a session receive the following treatment in the transcript:

- The first time a session is used, the message appears normally in the transcript.

- If a later message is sent using the same session, the previous message is removed from the transcript. The new message, with the updated content, is added to the bottom of the transcript, as normal.

- If the previous message has a non-`nil` summaryText property, the Messages app creates a summary message from the text and inserts it in the message’s previous location.

### Create New, Updatable Messages

Use the following workflow to create a new, updatable message.

1.  Create the following:

- A new URL that encodes the message’s initial state. For example, you could encode data as key-value pairs in the URL’s query string. For more information, see the MSMessage class’s url property.

- A new layout object that describes the initial message’s appearance. For more information, see the MSMessage class’s layout property.

- A string that describes the message’s current state. For more information, see the MSMessage class’s summaryText property.

2.  Instantiate a new MSSession object by calling its init() method.

3.  Instantiate a new MSMessage object by calling its init(session:) method and passing the session object. Set the message’s url, layout, and summaryText properties.

4.  Send the message by calling the conversation’s insert(_:completionHandler:) method. Pass `nil` for the change description.

The Messages app adds the message to the transcript as soon as the user taps the send button.

### Update Messages

Use the following workflow to receive and update a message.

1.  When the user taps on one of your MSMessage entries, the conversation’s selectedMessage property is changed to the tapped message. Use key-value observing to respond to these changes. Extract the current state from the message’s url property, and present it to the user. For more information on receiving messages, see MSMessage.

2.  After the user responds, create the following:

- A new URL that encodes the updated message state. For example, you could encode the data as key-value pairs in the URL’s query string. For more information, see the MSMessage class’s url property.

- A new layout object that describes the updated message’s appearance. For more information, see the MSMessage class’s layout property.

- A string that describes the message’s current state. For more information, see the MSMessage class’s summaryText property.

3.  Instantiate a new MSMessage object by calling its init(session:) method and passing the currently selected message’s MSSession object. Set the message’s url, layout, and summaryText properties.

4.  Send the updated message by calling the conversation’s insert(_:completionHandler:) method.

The Messages app updates the message in the transcript as soon as the user taps the send button.

## Relationships

### Inherits From

- NSObject

### Conforms To

- CVarArg
- CustomDebugStringConvertible
- CustomStringConvertible
- Equatable
- Hashable
- NSCoding
- NSObjectProtocol
- NSSecureCoding

## See Also

### Interactive messages

class MSMessage

A custom message object.

class MSMessageLayout

An abstract base class that defines the appearance of MSMessage objects in the conversation transcript.

class MSMessageTemplateLayout

A template-based layout for custom messages.

class MSMessageLiveLayout

A layout that provides a custom, interactive view inside the transcript.

