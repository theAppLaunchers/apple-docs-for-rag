

- Foundation
- NSURLComponents
-  queryItems 

Instance Property

# queryItems

The query URL component as an array of name/value pairs.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.1+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
var queryItems: [URLQueryItem]? { get set }
```

## Discussion

When you get this property’s value, the NSURLComponents class parses the query string and returns an array of NSURLQueryItem objects, each of which represents a single key-value pair, in the order in which they appear in the original query string. Because a name may appear more than once in a single query string, the name properties of query items are not guaranteed to be unique. If the query property is an empty string, the queryItems property is an empty array. If the query property is `nil`, the queryItems property is also `nil`.

When you set this property’s value, the NSURLComponents class joins each name/value pair with a `=` delimiter and joins the array with a `&` delimiter, then sets the query property to the resulting string. Setting the queryItems property to an empty array sets the query property to an empty string, and setting the queryItems property to `nil` sets the query property to `nil`.

Note

RFC 3986 specifies which characters must be percent-encoded in the query component of a URL, but not how those characters should be interpreted. The use of delimited key-value pairs is a common convention, but isn’t standardized by a specification. Therefore, you may encounter interoperability problems with other implementations that follow this convention.

One notable example of potential interoperability problems is how the plus sign (`+`) character is handled:

According to RFC 3986, the plus sign is a valid character within a query, and doesn’t need to be percent-encoded. However, according to the W3C recommendations for URI addressing, the plus sign is reserved as shorthand notation for a space within a query string (for example, `?greeting=hello+world`).

If a URL query component contains a date formatted according to RFC 3339 with a plus sign in the timezone offset (for example, `2013-12-31T14:00:00+00:00`), interpreting the plus sign as a space results in an invalid time format. RFC 3339 specifies how dates should be formatted, but doesn’t advise whether the plus sign must be percent-encoded in a URL. Depending on the implementation receiving this URL, you may need to preemptively percent-encode the plus sign character.

As an alternative, consider encoding complex and/or potentially problematic data in a more robust data-interchange format, such as JSON or XML.

To ensure you can compose and decompose URL queries even with empty components, the NSURLComponents class has the following behavior for cases where no name or value is present:

- If a name-value pair has nothing before its equals sign, the `name` property of the corresponding query item is a zero-length string.

- If a name-value pair has nothing after its equals sign, the `value` property of the corresponding query item is a zero-length string.

- If a name-value pair has no equals sign, the `value` property of the corresponding query item is `nil`.

- If a name-value pair is empty (that is, the `query` string starts with `&`, ends with `&`, or contains ``` &``& ```), the corresponding query item has a zero-length `name` and `nil` `value`.

For example, in the URL `http://www.example.com/index.php?key1=value1&key2=value2`, this property’s value is an array of two NSURLQueryItem objects: one whose name property is `key1` and whose value property is `value1`, and one whose name property is `key2` and whose value property is `value2`.

## See Also

### Accessing components in native format

var fragment: String?

The fragment URL component (the part after a `#` symbol), or nil if not present.

var host: String?

The host URL subcomponent, or nil if not present.

var encodedHost: String?

The host subcomponent, percent-encoded.

var password: String?

The password URL subcomponent, or nil if not present.

var path: String?

The path URL component, or nil if not present.

var port: NSNumber?

The port number URL component, or nil if not present.

var query: String?

The query URL component as a string, or nil if not present.

var scheme: String?

The scheme URL component, or nil if not present.

var user: String?

The username URL subcomponent, or nil if not present.

