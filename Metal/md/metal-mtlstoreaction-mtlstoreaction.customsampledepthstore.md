

- Metal
- MTLStoreAction
-  MTLStoreAction.customSampleDepthStore 

Case

# MTLStoreAction.customSampleDepthStore

The GPU stores depth data in a sample-position–agnostic representation.

iOS 11.0+iPadOS 11.0+Mac Catalyst 13.1+macOS 10.13+tvOS 11.0+visionOS 1.0+

``` source
case customSampleDepthStore
```

## Discussion

You can only set this action on a MTLRenderPassDepthAttachmentDescriptor object.

Set this action when you need to read the depth data in a subsequent render pass or blit operation that is unaware of the programmable sample positions used to generate the data.

If you specify this action, Metal may decompress the depth render target and store the resulting data in its decompressed form. If you don’t change programmable sample positions in a subsequent render pass, use MTLStoreAction.store instead to improve performance.

## See Also

### Constants

case dontCare

The GPU has permission to discard the rendered contents of the attachment at the end of the render pass, replacing them with arbitrary data.

case store

The GPU stores the rendered contents to the texture.

case multisampleResolve

The GPU resolves the multisampled data to one sample per pixel and stores the data to the resolve texture, discarding the multisample data afterwards.

case storeAndMultisampleResolve

The GPU stores the multisample data to the multisample texture, resolves the data to a sample per pixel, and stores the data to the resolve texture.

case unknown

The system selects a store action when it encodes the render pass.

