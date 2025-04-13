

- MailKit
- MEComposeSessionHandler
-  additionalHeaders(for:) 

Instance Method

# additionalHeaders(for:)

Provides custom headers to include in the outgoing message.

macOS 12.0+

``` source
@MainActor
optional func additionalHeaders(for session: MEComposeSession) -> [String : [String]]
```

## Parameters 

`session`  

The session that represents the properties of the message in the compose window.

## Return Value

A dictionary that maps header keys to arrays of string values.

## Discussion

To add custom headers to an outgoing message, return a dictionary that contains the header key and an array of one or more values.

Note

MailKit ignores entries in the dictionary for standard headers such as Subject.

The following code shows an example of adding two custom headers: one with a single value, and another with multiple values.

```
func additionalHeaders(for session: MEComposeSession) -> [String : [String]] {
    // To insert custom headers into a message, return a dictionary with
    // the key and an array of one or more values.
    return [
        "X-CustomHeader": ["This is a custom header."],
        "X-CustomColors": ["Red", "Green", "Blue"]
    ]
}
```

The resulting message contains the following headers:

```
X-Customcolors: Red
X-Customcolors: Green
X-Customcolors: Blue
X-Customheader: This is a custom header.
```

Note

Header keys in mail messages are case-insensitive, so don’t make assumptions about the capitalization of header.

