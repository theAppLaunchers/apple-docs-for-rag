

- MapKit
-  MKOverlayRenderer 

Class

# MKOverlayRenderer

The shared infrastructure for drawing overlays on the map surface.

iOS 7.0+iPadOS 7.0+Mac Catalyst 13.1+macOS 10.9+tvOS 9.2+visionOS 1.0+

``` source
class MKOverlayRenderer
```

## Overview

An overlay renderer draws the visual representation of an overlay object — that is, an object that conforms to the MKOverlay protocol. This class defines the drawing infrastructure the map view uses. Subclasses need to override the draw(_:zoomScale:in:) method to draw the contents of the overlay.

The MapKit framework provides several concrete instances of overlay renderers. Specifically, it provides renderers for each of the concrete overlay objects. You can use one of these existing renderers or define your own subclasses if you want to draw the overlay contents differently.

You can subclass `MKOverlayRenderer` to create overlays based on custom shapes, content, or drawing techniques. The only method subclasses need to override is the draw(_:zoomScale:in:) method. However, if your class contains content that may not be ready for drawing right away, you need to also override the canDraw(_:zoomScale:) method and use it to report when your class is ready and able to draw.

The map view may tile large overlays and distribute the rendering of each tile to separate threads. Therefore, the implementation of your draw(_:zoomScale:in:) method needs to be safe to run from background threads and from multiple threads simultaneously.

## Topics

### Creating an overlay view

init(overlay: any MKOverlay)

Creates and returns the overlay renderer and associates it with the specified overlay object.

### Attributes of the overlay

var overlay: any MKOverlay

The overlay object containing the data for drawing.

var alpha: CGFloat

The amount of transparency to apply to the overlay.

var contentScaleFactor: CGFloat

The scale factor for drawing the overlay’s content.

var blendMode: CGBlendMode

The blend mode to apply to the overlay.

### Converting points on the map

func point(for: MKMapPoint) -> CGPoint

Returns the point in the overlay renderer’s drawing area corresponding to the specified point on the map.

func mapPoint(for: CGPoint) -> MKMapPoint

Returns the point on the map that corresponds to the specified point in the overlay renderer’s drawing area.

func rect(for: MKMapRect) -> CGRect

Returns the rectangle in the overlay renderer’s drawing area corresponding to the specified rectangle on the map.

func mapRect(for: CGRect) -> MKMapRect

Returns the rectangle on the map that corresponds to the specified rectangle in the overlay renderer’s drawing area.

### Drawing the overlay

func canDraw(MKMapRect, zoomScale: MKZoomScale) -> Bool

Returns a Boolean value that indicates whether the overlay view is ready to draw its content.

func draw(MKMapRect, zoomScale: MKZoomScale, in: CGContext)

Draws the overlay’s contents at the specified location on the map.

func setNeedsDisplay()

Invalidates the entire contents of the overlay for all zoom scales.

func setNeedsDisplay(MKMapRect)

Invalidates the specified portion of the overlay at all zoom scales.

func setNeedsDisplay(MKMapRect, zoomScale: MKZoomScale)

Invalidates the specified portion of the overlay, but only at the specified zoom scale.

### Types

typealias MKZoomScale

A scale factor to use in conjunction with a map.

func MKRoadWidthAtZoomScale(MKZoomScale) -> CGFloat

Returns the width (in screen points) of roads on a map at the specified zoom level.

## Relationships

### Inherits From

- NSObject

### Inherited By

- MKOverlayPathRenderer
- MKTileOverlayRenderer

### Conforms To

- CVarArg
- CustomDebugStringConvertible
- CustomStringConvertible
- Equatable
- Hashable
- NSObjectProtocol

## See Also

### Shared behavior

protocol MKOverlay

An interface for associating content with a specific map region.

class MKShape

An abstract class that defines the basic properties for all shape-based overlay objects.

class MKMultiPoint

An abstract class that defines the common behavior that open and closed polygon overlays share.

class MKPlacemark

A user-friendly description of a location on the map.

