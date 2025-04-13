

- Swift
- RegexComponent
-  url(scheme:user:password:host:port:path:query:fragment:) 

Type Method

# url(scheme:user:password:host:port:path:query:fragment:)

Creates a regex component that matches a URL substring, capturing it as a Foundation URL.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+tvOS 16.0+visionOS 1.0+watchOS 9.0+

``` source
static func url(
    scheme: URL.ParseStrategy.ComponentParseStrategy = .required,
    user: URL.ParseStrategy.ComponentParseStrategy = .optional,
    password: URL.ParseStrategy.ComponentParseStrategy = .optional,
    host: URL.ParseStrategy.ComponentParseStrategy = .required,
    port: URL.ParseStrategy.ComponentParseStrategy = .optional,
    path: URL.ParseStrategy.ComponentParseStrategy = .optional,
    query: URL.ParseStrategy.ComponentParseStrategy = .optional,
    fragment: URL.ParseStrategy.ComponentParseStrategy = .optional
) -> Self
```

Available when `Self` is `URL.ParseStrategy`.

## Parameters 

`scheme`  

A URL.ParseStrategy.ComponentParseStrategy for matching the URL scheme component.

`user`  

A URL.ParseStrategy.ComponentParseStrategy for matching the user component.

`password`  

A URL.ParseStrategy.ComponentParseStrategy for matching the password component.

`host`  

A URL.ParseStrategy.ComponentParseStrategy for matching the host component.

`port`  

A URL.ParseStrategy.ComponentParseStrategy for matching the port component.

`path`  

A URL.ParseStrategy.ComponentParseStrategy for matching the path component.

`query`  

A URL.ParseStrategy.ComponentParseStrategy for matching the query component.

`fragment`  

A URL.ParseStrategy.ComponentParseStrategy for matching the fragment component.

## Return Value

A `RegexComponent` that matches a URL.

## Discussion

All the parameters to this method take a URL.ParseStrategy.ComponentParseStrategy value to configure the matching behavior for one component of the URL. The three possible values are:

- URL.ParseStrategy.ComponentParseStrategy.required — The URL component needs to be present for matching to succeed.

- URL.ParseStrategy.ComponentParseStrategy.optional — The URL component doesn’t need to be present for matching to succeed.

- URL.ParseStrategy.ComponentParseStrategy.defaultValue(_:) — If the URL component is absent, the captured URL contains the provided default value for the component.

The following example creates a Regex that matches a URL, when it contains a scheme and a host. It then matches against a source string that contains a date formatted in the `en_US` locale, some whitespace, and a valid URL. The regex defines a default value for the port with URL.ParseStrategy.ComponentParseStrategy.defaultValue(_:), and because the source URL doesn’t include a port, the captured URL adds it.

```
let source = "7/31/2022, 5:15:12 AM  https://www.example.com/productList?query=slushie"
let matcher = Regex {
    One(.dateTime(date: .numeric,
                  time: .standard,
                  locale: Locale(identifier: "en_US"),
                  timeZone: TimeZone(identifier: "PST")!))
    OneOrMore(.horizontalWhitespace)
    Capture {
        One(.url(scheme: .required,
                 user: .optional,
                 password: .optional,
                 host: .required,
                 port: .defaultValue(8088),
                 path: .optional,
                 query: .optional,
                 fragment: .optional))
    }
}
guard let match = source.firstMatch(of: matcher) else { return }
let url = match.1 // url = https://www.example.com:8088/productList?query=slushie
```

