

- Bundle Resources
- applinks
- applinks.Details
-  applinks.Details.Components 

Object

# applinks.Details.Components

Patterns that define the universal links an app can open.

iOS 13.0+iPadOS 13.0+macOS 10.15+tvOS 13.0+visionOS 1.0+watchOS 7.0+

``` source
object applinks.Details.Components
```

## Properties

`#`

`string`

`/`

`string`

`?`

`(string | `applinks.Details.Components.Query`)`

Possible types: `string``, `applinks.Details.Components.Query

`caseSensitive`

`boolean`

`comment`

`string`

`exclude`

`boolean`

`percentEncoded`

`boolean`

## Discussion

Use this object to define whether an associated app can open specific URLs in this domain as universal links.

The object optionally contains any of these keys:

`/`  
The pattern to match with the URL path component. The default is `*`, which matches everything.

`?`  
The pattern or dictionary to match with the URL query component. The default is `*`, which matches everything.

`#`  
The pattern to match with the URL fragment component. The default is `*`, which matches everything.

`exclude`  
A Boolean value that indicates whether to stop pattern matching and prevent the universal link from opening if the URL matches the associated pattern. The default is `false`.

`comment`  
Text that the system ignores. Use this to provide information about the URLs a pattern matches.

`caseSensitive`  
A Boolean value that indicates whether pattern matching is case-sensitive. The default is `true`.

`percentEncoded`  
A Boolean value that indicates whether URLs are percent-encoded. The default is `true`.

The order that you use to specify the patterns in the array determines the order the system follows when looking for a match. The first match wins, allowing you to designate one app to handle specified URLs in your website, and another app to handle the rest.

You can also use the following wildcards in your URL pattern-matching definitions:

`*` — Matches zero or more characters. This performs a greedy match and matches as many characters as possible.

`?` — Matches any single character.

In addition, you can use `?*` to match one or more characters (that is, at least one character).

A match occurs when a URL matches *all* the components that a `components` object specifies. The following example code matches all URLs with a path of `abc` and a query of `def`.

```
{
  "/": "abc",
  "?": "def",
  "#": "*"
}
```

The URL `https://www.example.com/abc?def` matches with the above code, but `https://www.example.com/abc` and `https://www.example.com?def` don’t. The fragment part of the code matches everything, so the system ignores it.

This example code shows another components object in an association file:

```
{
  "/": "/help/website/*",
  "exclude": true,
  "comment": "Matches any URL whose path starts with /help/website/ and instructs the system not to open it as a universal link"
}
```

## Topics

### Query dictionaries

object applinks.Details.Components.Query

A dictionary of names and values to match with query items in a URL.

