

- GLKit
-  GLKBaseEffect Deprecated

Class

# GLKBaseEffect

A simple lighting and shading system for use in shader-based OpenGL rendering.

iOS 5.0–12.0DeprecatediPadOS 5.0–12.0DeprecatedmacOS 10.8–10.14DeprecatedtvOS 9.0–12.0Deprecated

``` source
class GLKBaseEffect
```

Deprecated

OpenGLES API deprecated. (Define GLES_SILENCE_DEPRECATION to silence these warnings)

## Overview

The GLKBaseEffect class provides shaders that mimic many of the behaviors provided by the OpenGL ES 1.1 lighting and shading model, including materials, lighting and texturing. The base effect allows up to three lights and two textures to be applied to a scene.

At initialization time, your application first creates a compatible OpenGL or OpenGL ES context and makes it current. Then, it allocates and initializes a new effect object, configures its properties, and calls its prepareToDraw() method. Binding an effect causes a shader to be compiled and bound to the current context. The base effect also requires vertex data to be supplied by your application. To supply vertex data, create one or more vertex array objects. For each attribute required by the shader, the vertex array object should enable the attribute and point to data stored in a vertex buffer object.

At rendering time, your application calls the effect’s prepareToDraw() method to prepare the effect. Then, it binds a vertex array object and submits one or more drawing commands.

Lighting calculations for the base effect are done in eye-space coordinates.  The light0, light1 and light2 properties hold the position and spot direction of the base effect’s lights. The transform property contains the model view matrix assigned to the scene. When a light is assigned a new position or spot direction, those values are immediately modified by the current model view matrix. Thus, it is important to sequence changes to the model view matrix and changes to the lights to achieve the desired light positioning.  Light positions that need to be transformed in a manner similar to scene geometry should be set after the model view matrix is updated.

### Subclassing

Although this class can be subclassed, there are no methods your subclass can use to directly override the underlying shader generation. Instead, your subclass should implement its functionality by changing the values of existing properties declared by the base class.

## Topics

### Naming the Effect

var label: String?

A string used to name your effect.

### Configuring the Modelview Transform

var transform: GLKEffectPropertyTransform

The modelview, projection and texture transformations applied to the vertex data when the effect is bound.

### Configuring Lights

var lightingType: GLKLightingType

The strategy the effect uses to calculate light values at each fragment. See GLKLightingType.

var lightModelTwoSided: GLboolean

A Boolean value that indicates whether lighting is calculated for both sides of a primitive.

var material: GLKEffectPropertyMaterial

The material properties used when calculating the light values for a rendered primitive.

var lightModelAmbientColor: GLKVector4

The ambient color applied to all primitives rendered by the effect.

var light0: GLKEffectPropertyLight

The lighting properties for the first light in the scene.

var light1: GLKEffectPropertyLight

The lighting properties for the second light in the scene.

var light2: GLKEffectPropertyLight

The lighting properties for the third light in the scene.

### Configuring Textures

var texture2d0: GLKEffectPropertyTexture

The properties for the first texture.

var texture2d1: GLKEffectPropertyTexture

The properties for the second texture.

var textureOrder: [GLKEffectPropertyTexture]?

The order in which textures are applied to rendered primitives.

### Configuring Fog

var fog: GLKEffectPropertyFog

The fog properties to apply to the scene.

### Configuring Color Information

var colorMaterialEnabled: GLboolean

A Boolean value that indicates whether or not to use the color vertex attribute when calculating the light’s interaction with the material.

var useConstantColor: GLboolean

A Boolean value that indicates whether or not to use the constant color.

var constantColor: GLKVector4

A constant color, used when per-vertex color data is not provided.

### Preparing the Effect for Drawing

func prepareToDraw()

Prepares an effect for rendering.

### Type Aliases

typealias GLKEffectPropertyPrvPtr

## Relationships

### Inherits From

- NSObject

### Inherited By

- GLKReflectionMapEffect

### Conforms To

- CVarArg
- CustomDebugStringConvertible
- CustomStringConvertible
- Equatable
- GLKNamedEffect
- Hashable
- NSObjectProtocol

## See Also

### Shader-Based Rendering Effects

protocol GLKNamedEffect

A standard interface for objects that provide shader-based OpenGL rendering effects.

class GLKReflectionMapEffect

A lighting and shading system that supports reflection mapping for use in shader-based OpenGL rendering.

Deprecated

class GLKSkyboxEffect

A simple skybox visual effect for use in shader-based OpenGL rendering.

Deprecated

