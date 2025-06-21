Collection

*   [UIKit](/documentation/uikit)
*   TextKit

API Collection

# TextKit

Manage text storage and perform custom layout of text-based content in your app’s views.

## [Overview](/documentation/UIKit/textkit#overview)

TextKit provides several classes to control the layout of text, such as [`NSTextContentStorage`](/documentation/uikit/nstextcontentstorage), [`NSTextLayoutManager`](/documentation/uikit/nstextlayoutmanager), and [`NSTextContainer`](/documentation/uikit/nstextcontainer).

Additionally, TextKit uses [`NSAttributedString`](/documentation/Foundation/NSAttributedString) objects extensively. The [`NSTextStorage`](/documentation/uikit/nstextstorage) class is a subclass of [`NSMutableAttributedString`](/documentation/Foundation/NSMutableAttributedString), and many of the TextKit classes, for example, the classes listed in `Formatted content`, focus on creating complex [`NSAttributedString`](/documentation/Foundation/NSAttributedString) instances. Use these classes to specify your text’s format.

Most of the time, you can use TextKit to fine tune the formatting and layout of a [`UITextView`](/documentation/uikit/uitextview) by modifying the view’s [`textContainer`](/documentation/AppKit/NSTextView/textContainer), [`layoutManager`](/documentation/AppKit/NSTextView/layoutManager), or [`textStorage`](/documentation/AppKit/NSTextView/textStorage) properties. If you need more control, you can also use TextKit to build custom text controls.

## [Topics](/documentation/UIKit/textkit#topics)

### [Text management](/documentation/UIKit/textkit#Text-management)

```swift
```swift
```swift
```swift
class NSTextContentStorage
```
```

A concrete object for managing your view’s text content and generating the text elements necessary for layout.
```
```swift
```swift
```swift
class NSTextContentManager
```
```

An abstract class that defines the interface and a default implementation for managing the text document contents.
```
```swift
```swift
```swift
class NSAttributedString
```
```

A string of text that manages data, layout, and stylistic information for ranges of characters to support rendering.
```
```swift
```swift
```swift
class NSMutableAttributedString
```
```

A mutable string with associated attributes (such as visual style, hyperlinks, or accessibility data) for portions of its text.
```
```

### [Formatting and attributes](/documentation/UIKit/textkit#Formatting-and-attributes)

```swift
```swift
```swift
```swift
class NSParagraphStyle
```
```

The paragraph or ruler attributes for an attributed string.
```
```swift
```swift
```swift
class NSMutableParagraphStyle
```
```

An object for changing the values of the subattributes in a paragraph style attribute.
```
```swift
```swift
```swift
class NSTextTab
```
```

A tab in a paragraph.
```
```swift
```swift
```swift
class NSTextList
```
```

A section of text that forms a single list.
```
```

### [Content elements](/documentation/UIKit/textkit#Content-elements)

[

Enriching your text in text views](/documentation/uikit/enriching-your-text-in-text-views)

Add exclusion paths, text attachments, and text lists to your text, and render it with text views.

```swift
```swift
```swift
class NSTextParagraph
```
```

A class that represents a single paragraph backed by an attributed string as the contents.
```
```swift
```swift
```swift
class NSTextListElement
```
```

A class that represents a text list node.
```
```swift
```swift
```swift
class NSTextElement
```
```

An abstract base class that represents the smallest units of text layout such as paragraphs or attachments.
```
```swift
```swift
```swift
protocol NSTextElementProvider
```
```

A protocol the text content manager and its concrete subclasses conform to, which defines the interface for interacting with custom content types of a text document.
```

### [Location and selection](/documentation/UIKit/textkit#Location-and-selection)

```swift
```swift
```swift
```swift
class NSTextRange
```
```

A class that represents a contiguous range between two locations inside document contents.
```
```swift
```swift
```swift
class NSTextSelection
```
```

A class that represents a single logical selection context that corresponds to an insertion point.
```
```swift
```swift
```swift
class NSTextSelectionNavigation
```
```

An interface you use to expose methods for obtaining results from actions performed on text selections.
```
```swift
```swift
```swift
protocol NSTextLocation
```
```

An interface you implement that represents an abstract location inside your document’s content.
```
```

### [Layout](/documentation/UIKit/textkit#Layout)

[

Using TextKit 2 to interact with text](/documentation/uikit/using-textkit-2-to-interact-with-text)

Interact with text by managing text selection and inserting custom text elements.

[

Display text with a custom layout](/documentation/uikit/display-text-with-a-custom-layout)

Lay out text in a custom-shaped container and apply glyph substitutions.

```swift
```swift
```swift
class NSTextLayoutManager
```
```

The primary class that you use to manage text layout and presentation for custom text displays.
```
```swift
```swift
```swift
class NSTextContainer
```
```

A region where text layout occurs.
```
```swift
```swift
```swift
class NSTextLayoutFragment
```
```

A class that represents the layout fragment typically corresponding to a rendering surface, such as a layer or view subclass.
```
```swift
```swift
```swift
class NSTextLineFragment
```
```

A class that represents a line fragment as a single textual layout and rendering unit inside a text layout fragment.
```
```swift
```swift
```swift
class NSTextViewportLayoutController
```
```

Manages the layout process inside the viewport interacting with its delegate.
```
```swift
```swift
```swift
protocol NSTextLayoutOrientationProvider
```
```

A set of methods that define the orientation of text for an object.
```

### [Attachments](/documentation/UIKit/textkit#Attachments)

```swift
```swift
```swift
```swift
class NSTextAttachment
```
```

The values for the attachment characteristics of attributed strings and related objects.
```
```swift
```swift
```swift
class NSTextAttachmentViewProvider
```
```

A container object that associates a text attachment at a particular document location with a view object.
```
```swift
```swift
```swift
class NSAdaptiveImageGlyph
```
```

A data object for an emoji-like image that can appear in attributed text.
```
```swift
```swift
```swift
protocol NSTextAttachmentContainer
```
```

A set of methods that defines the interface to text attachment objects from a layout manager.
```
```swift
```swift
```swift
protocol NSTextAttachmentLayout
```
```

A set of methods that defines the interface to attachment objects from a text layout manager.
```
```

### [TextKit 1](/documentation/UIKit/textkit#TextKit-1)

```swift
```swift
```swift
```swift
class NSTextStorage
```
```

The fundamental storage mechanism of TextKit that contains the text managed by the system.
```
```swift
```swift
```swift
class NSLayoutManager
```
```

An object that coordinates the layout and display of text characters.
```
```

## [See Also](/documentation/UIKit/textkit#see-also)

### [Text](/documentation/UIKit/textkit#Text)

[

API Reference

Text display and fonts](/documentation/uikit/text-display-and-fonts)

Display text, manage fonts, and check spelling.

[

API Reference

Keyboards and input](/documentation/uikit/keyboards-and-input)

Configure the system keyboard, create your own keyboards to handle input, or detect key presses on a physical keyboard.

[

API Reference

Writing Tools](/documentation/uikit/writing-tools)

Add support for Writing Tools to your app’s text views.

[

API Reference

Handwriting recognition](/documentation/uikit/handwriting-recognition)

Configure text fields and custom views that accept text to handle input from Apple Pencil.