

- Core Graphics
- CGEventFlags
-  maskNonCoalesced 

Type Property

# maskNonCoalesced

Indicates that mouse and pen movement events are not being coalesced.

Mac CatalystmacOS

``` source
static var maskNonCoalesced: CGEventFlags { get }
```

## See Also

### Constants

static var maskAlphaShift: CGEventFlags

Indicates that the Caps Lock key is down for a keyboard, mouse, or flag-changed event.

static var maskShift: CGEventFlags

Indicates that the Shift key is down for a keyboard, mouse, or flag-changed event.

static var maskControl: CGEventFlags

Indicates that the Control key is down for a keyboard, mouse, or flag-changed event.

static var maskAlternate: CGEventFlags

Indicates that the Alt or Option key is down for a keyboard, mouse, or flag-changed event.

static var maskCommand: CGEventFlags

Indicates that the Command key is down for a keyboard, mouse, or flag-changed event.

static var maskHelp: CGEventFlags

Indicates that the Help modifier key is down for a keyboard, mouse, or flag-changed event. This key is not present on most keyboards, and is different than the Help key found in the same row as Home and Page Up.

static var maskSecondaryFn: CGEventFlags

Indicates that the Fn (Function) key is down for a keyboard, mouse, or flag-changed event. This key is found primarily on laptop keyboards.

static var maskNumericPad: CGEventFlags

Identifies key events from the numeric keypad area on extended keyboards.

