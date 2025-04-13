

- Core Text
- CTRubyPosition
-  CTRubyPosition.interCharacter 

Case

# CTRubyPosition.interCharacter

The ruby text is positioned to the right of the base text, regardless of whether it’s horizontal or vertical.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.1+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
case interCharacter
```

## Discussion

This is the way that Bopomofo annotations are attached to Chinese text in Taiwan.

## See Also

### Constants

case before

The ruby text is positioned before the base text, appearing above horizontal text and to the right of vertical text.

case after

The ruby text is positioned after the base text, appearing below horizontal text and to the left of vertical text.

case inline

The ruby text follows the base text with no special styling.

case count

A constant that accounts for all ruby positions during ruby annotation creation.

