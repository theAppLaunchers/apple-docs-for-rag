

- Quartz
-  QCCompositionParameterView Deprecated

Class

# QCCompositionParameterView

A class that allows users to edit the input parameters of a composition in real time. The composition can be rendering in any of the following objects: QCRenderer, QCView, or QCCompositionLayer.

macOS 10.4–10.15Deprecated

``` source
@MainActor
class QCCompositionParameterView
```

Deprecated

QuartzComposer API deprecated. (Define QC_SILENCE_DEPRECATION to silence these warnings)

## Topics

### Getting and Setting the Renderer

func setCompositionRenderer((any QCCompositionRenderer)!)

Sets the composition parameter view for editing the input parameters of the provided renderer object.

func compositionRenderer() -> (any QCCompositionRenderer)!

Returns the renderer object associated with the composition parameter view.

### Checking for Input Parameters

func hasParameters() -> Bool

Checks whether the composition that is currently edited by the composition parameter view has any input parameters.

### Setting and Retrieving the Delegate

func setDelegate(Any!)

Sets the composition parameter view delegate.

func delegate() -> Any!

Returns the composition parameter view delegate.

### Managing Background Drawing

func setDrawsBackground(Bool)

Sets whether the composition parameter view draws its background.

func drawsBackground() -> Bool

Returns whether the composition parameter view draws its background.

### Setting and Getting the Background Color

func setBackgroundColor(NSColor!)

Sets the background color of the composition parameter view.

func backgroundColor() -> NSColor!

Retrieves the background color of the composition parameter view.

## Relationships

### Inherits From

- NSView

### Conforms To

- CVarArg
- CustomDebugStringConvertible
- CustomStringConvertible
- Equatable
- Hashable
- NSAccessibilityElementProtocol
- NSAccessibilityProtocol
- NSAnimatablePropertyContainer
- NSAppearanceCustomization
- NSCoding
- NSDraggingDestination
- NSObjectProtocol
- NSStandardKeyBindingResponding
- NSTouchBarProvider
- NSUserActivityRestoring
- NSUserInterfaceItemIdentification
- Sendable

## See Also

### Classes

class QCComposition

The `QCComposition` class represents a Quartz Composer composition that either:

Deprecated

class QCCompositionLayer

A layer that loads, plays, and controls Quartz Composer compositions in a Core Animation layer hierarchy.

Deprecated

class QCCompositionPickerPanel

The `QCCompositionPickerPanel` class represents a utility window that allows users to browse compositions that are in the Quartz Composer composition repository and, if supported, preview the composition. The `QCCompositionPickerPanel` class cannot be subclassed.

Deprecated

class QCCompositionPickerView

The `QCCompositionPickerView` class allows users to browse compositions that are in the Quartz Composer composition repository, and to preview them. You can set the default input parameters for a composition preview by using the method setDefaultValue:forInputKey:.

Deprecated

class QCCompositionRepository

The `QCCompositionRepository` class represents a system-wide centralized repository of built-in and installed Quartz Composer compositions (`/Library/Compositions` and `~/Library/Compositions`). The `QCCompositionRepository` class cannot be subclassed.

Deprecated

class QCPatchControllerDeprecated

class QCPlugIn

A base class to subclass for writing custom patches.

Deprecated

class QCPlugInViewController

The `QCPlugInViewController` class communicates (through Cocoa bindings) between a custom patch and the view used for the internal settings of the custom patch. Only custom patches that use internal settings exposed to the user need to use the `QCPlugInViewController` class.

Deprecated

class QCRenderer

A base class for low-level rendering.

Deprecated

class QCView

The `QCView` class is a custom `NSView` class that loads, plays, and controls Quartz Composer compositions. It is an autonomous view that is driven by an internal timer running on the main thread.

Deprecated

