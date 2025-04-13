

- Apple News Format
-  Color 

Type

# Color

The strings for defining colors in Apple News Format.

Apple News Format 1.7+

``` source
string Color
```

## Mentioned in 

Supported Color Names

## PossibleValues:

`/^(\#\w{3})|(\#\w{6})|(\#\w{8})|([a-z]{0,20})$/`

## Discussion

You can define colors in different ways in Apple News Format.

### 3-character RGB

Use three characters to define red, green, and blue (RGB). For example, a value of `#c00` is short for `#cc0000` and makes red.

### 4-character RGBA

Use four characters to define RGB and alpha (opacity). For example, a value of `#fc0a` is short for `#ffcc00aa`.

### 6-character RGB

Use six characters to define two-character values for each of red, green, and blue. For example, a value of `#0000ff` makes blue.

### 8-character RGBA

Use eight characters to define RGBA. For example, in a value of `#000000aa`, the first six characters define RGB, and the last characters define alpha. `#00000000` represents black but fully transparent, while `#000000ff` is fully opaque.

### Color Names

Use any of the available color names like `red`, `lightgreen,` or `rebeccapurple`. See Supported Color Names.

## See Also

### Styles

Enhancing Your Articles with Styles

Improve the appearance of the text and components in your article by using Apple News Format styles.

Supporting Dark Mode for Your Article

Update your article template so that your article adapts when Dark Mode is active.

object DocumentStyle

The object for setting the background color for your article.

Text Styles

Learn about text styles and how to apply them to your text and text components.

Component Styles

Learn to use component styles to add borders, set background colors, and apply background images to components and to set the styling for tables.

Supported Color Names

Learn the color names supported in Apple News Format.

