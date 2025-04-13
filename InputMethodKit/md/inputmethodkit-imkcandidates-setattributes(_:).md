

- InputMethodKit
- IMKCandidates
-  setAttributes(\_:) 

Instance Method

# setAttributes(\_:)

Sets the style attributes for the candidates window.

macOS 10.5+

``` source
@MainActor
func setAttributes(_ attributes: [AnyHashable : Any]!)
```

## Parameters 

`attributes`  

A dictionary that contains keys and values for the styles to use. You can supply the keys and values listed in the following table:

| Key | Value |
|----|----|
| NSFontAttributeName | An `NSFont` object. Setting the font attribute sets the font that is used to draw Candidates. It does not effect the selection keys which are always drawn in the same font. Note that to set the font size you should use this key/value pair. |
| IMKCandidatesOpacityAttributeName | An `NSNumber` object that represents a floating-point value between `0.0` (transparent) and `1.0` (completely opaque. The default opacity is `1.0`. |
| NSForegroundColorAttributeName | An `NSColor` object to use for the candidate text color. The default color is black. |
| NSBackgroundColorDocumentAttribute | An `NSColor` object to use for the background color behind the candidate text. |

## See Also

### Managing Window Type and Text Attributes

func panelType() -> IMKCandidatePanelType

Returns the style of the candidates window.

func setPanelType(IMKCandidatePanelType)

Sets the style of the candidates window.

func attributes() -> [AnyHashable : Any]!

Returns a dictionary of the style attributes used for the candidates window..

