

- Foundation
- NSAttributedString
-  draw(with:options:context:) 

Instance Method

# draw(with:options:context:)

Draws the attributed string in the specified bounding rectangle using the provided options.

iOS 6.0+iPadOS 6.0+Mac Catalyst 13.1+macOS 10.11+tvOS 9.0+visionOS 1.0+watchOS 2.0+

**macOS**

``` source
func draw(
    with rect: CGRect,
    options: NSString.DrawingOptions = [],
    context: NSStringDrawingContext?
)
```

**iOS, iPadOS, Mac Catalyst, tvOS, visionOS, watchOS**

``` source
func draw(
    with rect: CGRect,
    options: NSStringDrawingOptions = [],
    context: NSStringDrawingContext?
)
```

## Parameters 

`rect`  

The bounding rectangle in which to draw the string.

`options`  

Additional drawing options to apply to the string during rendering. For a list of possible values, see NSStringDrawingOptions.

`context`  

A context object with information about how to adjust the font tracking and scaling information. On return, the specified object contains information about the actual values used to render the string. This parameter may be `nil`.

## Discussion

If usesLineFragmentOrigin is specified in `options`, it wraps the string text as needed to make it fit. If the string is too big to fit completely inside the rectangle, the method scales the font or adjusts the letter spacing to make the string fit within the given bounds.

If usesLineFragmentOrigin is not specified in `options`, the origin of the rectangle is the baseline of the only line. The text will be displayed above the rectangle and not inside of it. For example, if you specify a rectangle starting at 0,0 and draw the string ‘juxtaposed’, only the descenders of the ‘j’ and ‘p’ will be seen. The rest of the text will be on the top edge of the rectangle.

This method draws the line using the attributes specified in the attributed string itself. If newline characters are present in the string, those characters are honored and cause subsequent text to be placed on the next line underneath the starting point.

There must be either an active graphics context when you call this method.

### Special Considerations

This method uses the baseline origin by default, so it renders the string as a single line. To render the string in multiple lines, specify usesLineFragmentOrigin in `options`.

## See Also

### Drawing the attributed string

func draw(at: CGPoint)

Draws the attributed string starting at the specified point in the current graphics context.

func draw(in: CGRect)

Draws the attributed string inside the specified bounding rectangle in the current graphics context.

