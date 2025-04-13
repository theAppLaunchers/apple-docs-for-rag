

- PHASE
- PHASEDucker
-  init(engine:sourceGroups:targetGroups:gain:attackTime:releaseTime:attackCurve:releaseCurve:) 

Initializer

# init(engine:sourceGroups:targetGroups:gain:attackTime:releaseTime:attackCurve:releaseCurve:)

Creates an object that manages competing sounds.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 17.0+visionOS 1.0+

``` source
init(
    engine: PHASEEngine,
    sourceGroups: Set,
    targetGroups: Set,
    gain: Double,
    attackTime: Double,
    releaseTime: Double,
    attackCurve: PHASECurveType,
    releaseCurve: PHASECurveType
)
```

## Parameters 

`engine`  

The app’s instance of the framework object.

`sourceGroups`  

The sounds that determine volume reduction.

`targetGroups`  

The sounds that reduce in volume.

`gain`  

The volume level of the sound.

`attackTime`  

The amount of time for sound reduction to reach maximum strength.

`releaseTime`  

The amount of time to transition from maximum sound reduction to no reduction.

`attackCurve`  

A mathematical curve that shapes transition progress during the time it takes to reach maximum sound reduction.

`releaseCurve`  

A mathematical curve that shapes signal progress during the time it takes to transition from maximum sound reduction to no reduction.

