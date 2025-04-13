

- RealityKit
- VirtualEnvironmentProbeComponent
-  VirtualEnvironmentProbeComponent.Probe 

Structure

# VirtualEnvironmentProbeComponent.Probe

A sample of the environment around a point in a scene the system uses for environment-based lighting.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+visionOS 2.0+

``` source
struct Probe
```

## Topics

### Initializers

init(environment: EnvironmentResource, intensityExponent: Float)

Creates a virtual-environment probe from an environment resource and intensity value.

### Instance Properties

var environment: EnvironmentResource

The resource that stores a representation of diffuse and specular environment lighting.

var intensityExponent: Float

The intensity value for the resource, which RealityKit defines on a logarithmic scale.

## See Also

### Environment

class EnvironmentResource

An environmental resource that contains background and lighting information for a scene.

struct EnvironmentLightingConfigurationComponent

A component that scales the amount of light that an entity receives from its environment.

struct VirtualEnvironmentProbeComponent

A component that provides environment lighting for entities you place within the same virtual world.

enum Source

Options that define the source of diffuse and specular lighting for environment lighting calculations.

