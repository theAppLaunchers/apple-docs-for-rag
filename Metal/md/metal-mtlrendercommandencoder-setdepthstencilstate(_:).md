

- Metal
- MTLRenderCommandEncoder
-  setDepthStencilState(\_:) 

Instance Method

# setDepthStencilState(\_:)

Configures the combined depth and stencil state.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.1+macOS 10.11+tvOSvisionOS 1.0+

``` source
func setDepthStencilState(_ depthStencilState: (any MTLDepthStencilState)?)
```

**Required**

## Parameters 

`depthStencilState`  

An instance that conforms to the MTLDepthStencilState protocol.

## Discussion

This method changes the combined depth and stencil state for the render command encoder that’s compatible with its depth and stencil attachment configuration. For example, if the new state enables depth testing or depth writing, the render pass needs to have a depth attachment. Similarly, if the new state enables stencil testing or stencil writing, the render pass’s stencil needs to have a stencil attachment. You create depth and stencil attachments for a render pass by assigning the depthAttachment and stencilAttachment properties of the MTLRenderPassDescriptor instance that creates it.

Pass `nil` to clear the state from the previous call, which restores a state that’s equivalent to the default values of an MTLDepthStencilDescriptor instance’s properties.

## See Also

### Configuring Depth and Stencil Behavior

func setDepthBias(Float, slopeScale: Float, clamp: Float)

Configures the adjustments a render pass applies to depth values from fragment functions by a scaling factor and bias.

**Required**

func setDepthClipMode(MTLDepthClipMode)

Configures how the render pipeline handles fragments outside the near and far planes of the view frustum.

**Required**

func setStencilReferenceValue(UInt32)

Configures the same comparison value for front- and back-facing primitives.

**Required**

func setStencilReferenceValues(front: UInt32, back: UInt32)

Configures different comparison values for front- and back-facing primitives.

**Required**

