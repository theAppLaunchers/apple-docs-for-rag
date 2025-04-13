

- Core Animation
- CALayer
-  autoresizingMask 

Instance Property

# autoresizingMask

A bitmask defining how the layer is resized when the bounds of its superlayer changes.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.1+macOS 10.5+

``` source
var autoresizingMask: CAAutoresizingMask { get set }
```

## Discussion

If your app does not use a layout manager or constraints to handle layout changes, you can assign a value to this property to adjust the layer’s size in response to changes in the superlayer’s bounds. For a list of possible values, see CAAutoresizingMask.

The default value of this property is kCALayerNotSizable.

## See Also

### Managing Layer Resizing and Layout

var layoutManager: (any CALayoutManager)?

The object responsible for laying out the layer’s sublayers.

func setNeedsLayout()

Invalidates the layer’s layout and marks it as needing an update.

func layoutSublayers()

Tells the layer to update its layout.

func layoutIfNeeded()

Recalculate the receiver’s layout, if required.

func needsLayout() -> Bool

Returns a Boolean indicating whether the layer has been marked as needing a layout update.

func resize(withOldSuperlayerSize: CGSize)

Informs the receiver that the size of its superlayer changed.

func resizeSublayers(withOldSize: CGSize)

Informs the receiver’s sublayers that the receiver’s size has changed.

func preferredFrameSize() -> CGSize

Returns the preferred size of the layer in the coordinate space of its superlayer.

