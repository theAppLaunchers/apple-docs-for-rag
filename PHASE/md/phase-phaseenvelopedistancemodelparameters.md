

- PHASE
-  PHASEEnvelopeDistanceModelParameters 

Class

# PHASEEnvelopeDistanceModelParameters

A graph of points and curves that shapes the volume of a sound over distance.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 17.0+visionOS 1.0+

``` source
class PHASEEnvelopeDistanceModelParameters
```

## Overview

This class provides an envelope that the app configures to dissipate the volume of a source’s sound with distance. The envelope describes a graph that the app configures using points and curves, where the input value is the distance between a sound source and the listener, and the output value is the sound’s volume.

### Dissipate Sound by Using an Envelope

The framework interprets this class’s envelope as a *gain curve*, which determines the sound’s volume over a distance. An envelope offers more precise control over sound dissipation than a geometric rolloffFactor. For example, the following code defines slow sound dissipation followed by a sharp decrease:

- Swift
- Objective-C

```
var envelopeSegments : [PHASEEnvelopeSegment]!
envelopeSegments.append(PHASEEnvelopeSegment(endPoint: simd_make_double2(6.0, 1.0),
 curveType: PHASECurveType.sigmoid))
envelopeSegments.append(PHASEEnvelopeSegment(endPoint: simd_make_double2(9.0, 0.0),
 curveType:PHASECurveType.inverseCubed))
let distanceModelEnvelope = PHASEEnvelope(startPoint: simd_make_double2(0.0, 0.125),
 segments:envelopeSegments)

let piecewiseModel = PHASEEnvelopeDistanceModelParameters(envelope: distanceModelEnvelope!)

spatialMixer.distanceModelParameters = piecewiseModel
```

```
NSMutableArray* envelopeSegments = [NSMutableArray new];
[envelopeSegments addObject: [[PHASEEnvelopeSegment alloc] initWithEndPoint:simd_make_double2(6.0f, 1.0f) curveType:PHASECurveTypeSigmoid];
[envelopeSegments addObject: [[PHASEEnvelopeSegment alloc] initWithEndPoint:simd_make_double2(9.0f, 0.0f) curveType:PHASECurveTypeInverseCubed];
PHASEEnvelope* distanceModelEnvelope = [[PHASEEnvelope alloc] initWithStartPoint:simd_make_double2(0.0f, 0.125f) segments:envelopSegments];

PHASEEnvelopeDistanceModelParameters* piecewiseModel = [[PHASEEnvelopeDistanceModelParameters alloc] initWithEnvelope:distanceModelEnvelope];

spatialMixer.distanceModelParameters = piecewiseModel;
```

## Topics

### Creating the Distance Model Parameters

init(envelope: PHASEEnvelope)

Creates the distance model parameters with an envelope.

### Shaping the Volume Over a Distance

var envelope: PHASEEnvelope

An envelope that shapes sound dissipation over distance.

## Relationships

### Inherits From

- PHASEDistanceModelParameters

### Conforms To

- CVarArg
- CustomDebugStringConvertible
- CustomStringConvertible
- Equatable
- Hashable
- NSObjectProtocol

## See Also

### Distance Modeling

class PHASEGeometricSpreadingDistanceModelParameters

An object that dissipates sound frequencies over distance.

class PHASEDistanceModelFadeOutParameters

A distance over which the framework fades out sound.

class PHASEDistanceModelParameters

A base class for a sound’s rate of change over distance.

