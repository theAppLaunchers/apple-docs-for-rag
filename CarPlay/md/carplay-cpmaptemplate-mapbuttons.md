

- CarPlay
- CPMapTemplate
-  mapButtons 

Instance Property

# mapButtons

An array of map buttons on the trailing bottom corner of the map template.

iOS 12.0+iPadOS 12.0+Mac Catalyst 13.1+

``` source
var mapButtons: [CPMapButton] { get set }
```

## Discussion

When the array contains more than three buttons, the map template displays only the first three, ignoring the remaining buttons.

## See Also

### Managing Map Buttons

class CPMapButton

A button that represents an action that a map template displays on the CarPlay screen.

