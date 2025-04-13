

- TipKit
-  TipNSView 

Class

# TipNSView

A user interface element that represents a tip in AppKit applications.

macOS 14.0+

``` source
@MainActor @objc @preconcurrency
final class TipNSView
```

## Overview

You create a tip view by providing a tip and an optional arrow edge. The tip is a type that conforms to the Tip protocol. The arrow edge is a directional arrow pointing away from the tip.

Use this view to create a tip you want to display and lay out as a NSView.

Adding and removing TipNSView from your app is done by listening to a tip’s shouldDisplayUpdates or statusUpdates.

```
import Cocoa
import TipKit

struct CatTracksFeatureTip: Tip {
    var title: Text {
        Text("Sample tip title")
    }

    var message: Text? {
        Text("Sample tip message")
    }

    var image: Image? {
        Image(systemName: "globe")
    }
}

class CatTracksViewController: NSViewController {
    private var catTracksFeatureTip = CatTracksFeatureTip()
    private var tipObservationTask: Task?
    private weak var tipView: TipNSView?

    override func viewDidAppear() {
        super.viewDidAppear()

        tipObservationTask = tipObservationTask ?? Task { @MainActor in
            for await shouldDisplay in catTracksFeatureTip.shouldDisplayUpdates {
                if shouldDisplay {
                    let tipHostingView = TipNSView(catTracksFeatureTip)
                    view.addSubview(tipHostingView)

                    view.addConstraints([
                        tipHostingView.centerYAnchor.constraint(equalTo: view.centerYAnchor),
                        tipHostingView.leadingAnchor.constraint(equalTo: view.leadingAnchor, constant: 20.0),
                        tipHostingView.trailingAnchor.constraint(equalTo: view.trailingAnchor, constant: -20.0)
                    ])

                    tipView = tipHostingView
                }
                else {
                    tipView?.removeFromSuperview()
                    tipView = nil
                }
            }
        }
    }

    override func viewDidDisappear() {
        super.viewDidDisappear()

        tipObservationTask?.cancel()
        tipObservationTask = nil
    }
}
```

## Topics

### Initializers

convenience init(any Tip, arrowEdge: Edge?, actionHandler: (Tips.Action) -> Void)

Creates a tip view with an optional arrow.

### Instance Properties

var backgroundColor: NSColor?

The background color to use for the tip view.

var cornerRadius: CGFloat

Corner radius for the tip view.

var imageSize: CGSize

Size of the image displayed in the tip view.

var imageStyle: (any ShapeStyle)?

Foreground style for the tip’s image.

var viewStyle: any TipViewStyle

The given style for TipView within the view hierarchy

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

## See Also

### AppKit Views

class TipNSPopover

A subclass of NSPopover that displays a popover tip in AppKit applications.

