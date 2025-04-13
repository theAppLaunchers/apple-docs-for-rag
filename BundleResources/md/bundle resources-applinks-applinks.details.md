

- Bundle Resources
- applinks
-  applinks.Details 

Object

# applinks.Details

A list of apps and the universal links they handle for a domain.

iOS 9.0+iPadOS 9.0+macOS 10.15+tvOS 10.0+visionOS 1.0+watchOS 7.0+

``` source
object applinks.Details
```

## Properties

`appID`

`string`

`appIDs`

`[string]`

`components`

`[`applinks.Details.Components`]`

`defaults`

applinks.Defaults

## Discussion

The object optionally contains any of these keys:

`appID`  
An application identifier that specifies the app that can handle the universal links in the `components` array.

`appIDs`  
An array of application identifiers that specify the apps that can handle the universal links in the `components` array.

`components`  
An array of components that define the universal link URLs an app can handle.

`defaults`  
A dictionary for defining the default settings to use for all universal links pattern matching in the components array.

Use `appID` or `appIDs` to specify the applications that can access the specific URLs you define in the associated `components` array. You specify each application identifier in the following format:

```
.
```

This example code shows a universal links details object in an association file:

```
{
  "appIDs": [ "ABCDE12345.com.example.app", "ABCDE12345.com.example.app2" ],
  "components": [
    {
      "/": "/buy/*",
      "#": "my_great_product_123",
      "comment": "Matches any URL whose path starts with /buy/ and fragment equals my_great_product_123, ignoring case"
    }
  ],
  "defaults": { "caseSensitive": false }
}
```

## Topics

### URL components

object applinks.Details.Components

Patterns that define the universal links an app can open.

