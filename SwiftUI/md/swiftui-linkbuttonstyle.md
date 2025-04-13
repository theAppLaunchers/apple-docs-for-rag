

- SwiftUI
-  LinkButtonStyle 

Structure

# LinkButtonStyle

A button style for buttons that emulate links.

macOS 10.15+

``` source
struct LinkButtonStyle
```

## Overview

You can also use link to construct this style.

## Topics

### Creating the button style

init()

Creates a link button style.

### Supporting types

func makeBody(configuration: LinkButtonStyle.Configuration) -> some View

Creates a view that represents the body of a button.

## Relationships

### Conforms To

- PrimitiveButtonStyle

## See Also

### Supporting types

struct DefaultButtonStyle

The default button style, based on the button’s context.

struct AccessoryBarButtonStyle

A button style that you use for actions in an accessory toolbar that narrow the focus of a search or other operation.

struct AccessoryBarActionButtonStyle

A button style that you use for extra actions in an accessory toolbar.

struct BorderedButtonStyle

A button style that applies standard border artwork based on the button’s context.

struct BorderedProminentButtonStyle

A button style that applies standard border prominent artwork based on the button’s context.

struct BorderlessButtonStyle

A button style that doesn’t apply a border.

struct CardButtonStyle

A button style that doesn’t pad the content, and applies a motion effect when a button has focus.

struct PlainButtonStyle

A button style that doesn’t style or decorate its content while idle, but may apply a visual effect to indicate the pressed, focused, or enabled state of the button.

