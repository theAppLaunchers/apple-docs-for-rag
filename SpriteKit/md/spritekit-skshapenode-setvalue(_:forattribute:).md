

- SpriteKit
- SKShapeNode
-  setValue(\_:forAttribute:) 

Instance Method

# setValue(\_:forAttribute:)

Sets an attribute value for an attached shader.

iOS 10.0+iPadOS 10.0+Mac Catalyst 13.1+macOS 10.12+tvOS 10.0+visionOS 1.0+watchOS 3.0+

**watchOS**

``` source
func setValue(
    _ value: SKAttributeValue,
    forAttribute key: String
)
```

**iOS, iPadOS, Mac Catalyst, macOS, tvOS, visionOS**

``` source
@MainActor
func setValue(
    _ value: SKAttributeValue,
    forAttribute key: String
)
```

## Parameters 

`value`  

An attribute value object containing the scalar or vector value to set in the attached shader.

`key`  

The attribute name.

## See Also

### Customizing Stroking or Fill Drawing

Controlling Shape Drawing with Shaders

Change a shape node’s appearance by supplying custom shader code.

var strokeShader: SKShader?

A custom shader used to determine the color of the stroked portion of the shape node.

var fillShader: SKShader?

A custom shader used to determine the color of the filled portion of the shape node.

var attributeValues: [String : SKAttributeValue]

The values of each attribute associated with the node’s attached shader.

func value(forAttributeNamed: String) -> SKAttributeValue?

The value of a shader attribute.

