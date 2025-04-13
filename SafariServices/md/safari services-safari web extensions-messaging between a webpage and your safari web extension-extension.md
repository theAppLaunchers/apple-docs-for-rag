

- Safari Services
- Safari web extensions
-  Messaging between a webpage and your Safari web extension 

Article

# Messaging between a webpage and your Safari web extension

Configure your extension to enable messaging from webpages, and then update your extension to handle messages.

## Overview

With messaging, you can allow a webpage to control features in your extension based on events or data, or you can allow a webpage to request and use data from your extension.

First, configure your web extension to receive messages from a list of webpages that you specify. Then, add functionality to handle messages that a webpage sends to your extension, and respond to that webpage.

### Enable messaging from webpages in your manifest

To enable messaging from webpages, add `externally_connectable` to your extension’s `manifest.json` file. Include a list of webpages that you want to send messages to your extension in the `matches` attribute.

```
{ 
    "externally_connectable": {
        "matches": [ "*://*.apple.com/*" ]
    }
}
```

If you don’t provide the `matches` attribute or you provide an empty list, no webpages can send messages to your extension.

### Send messages from a webpage to your extension

Send a message from a webpage to your extension using `browser.runtime.sendMessage`. Provide your extension’s identifier, the message data, and a closure to handle the response from your extension.

```
browser.runtime.sendMessage("com.example.connectable-ext.Extension (team_identifier)", {greeting: "Hello!"}, function(response) {
    console.log("Received response from the background page:");
    console.log(response.farewell);
});
```

Your extension’s identifier is a string that consists of the bundle identifier for your extension, and your team identifier in parentheses. Find your team identifier in your developer account in the Membership tab under Account Settings. Note that extension identifiers can be different across browsers. For more information about finding the right extension identifier for Safari, see What’s new in Safari web extensions.

In your extension’s background page, listen for incoming messages webpages and send responses.

```
browser.runtime.onMessageExternal.addListener(function(message, sender, sendResponse) {
    console.log("Received message from the sender:");
    console.log(message.greeting);
    sendResponse({farewell: "Goodbye from the background page!"});
});
```

### Set up a port for messages between a webpage and your extension

If your extension needs to handle more continuous data from a webpage, establish a port connection between the webpage and your extension.

```
let port = browser.runtime.connect("extensionID");
```

In your extension’s background page, listen for incoming port connection requests.

```
browser.runtime.onConnectExternal.addListener(function(port) {
    console.log("Connection request received!");
});
```

Then, use `port.postMessage` to send a message through the port, and `port.onMessage` to receive a message from the port.

## See Also

### Messaging

Messaging between the app and JavaScript in a Safari web extension

Communicate about events and share data between the containing app and JavaScript by using native messaging and app groups.

let SFExtensionMessageKey: String

A string the system uses as a key in a user info dictionary to identify a message.

let SFExtensionProfileKey: String

A string the system uses as a key in a user info dictionary to identify a profile identifier.

Messaging a Web Extension’s Native App

Communicate between your Safari web extension and its containing app.

