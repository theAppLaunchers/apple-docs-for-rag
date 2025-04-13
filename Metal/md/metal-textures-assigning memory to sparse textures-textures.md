

- Metal
- Textures
-  Assigning Memory to Sparse Textures 

Article

# Assigning Memory to Sparse Textures

Use a resource state encoder to allocate and deallocate sparse tiles for a sparse texture.

## Overview

A sparse texture has storage only when you explicitly provide it. Every mipmap in the texture is partitioned into tile-sized regions. Each region can be in one of three states:

- *Unmapped —* The region has no memory storage.

- *Uninitialized —* You’ve mapped a sparse tile to the region, but provided no texture data.

- *Initialized* — You’ve mapped a sparse tile and provided texture data.

Initially, all of the texture’s regions are unmapped. To provide data for a region, you ask the GPU to map regions in the texture to sparse tiles on the texture’s heap, and then copy or render data into those regions. When a region no longer needs memory, you unmap the region to free up its memory for future requests.

### Map or Unmap Sparse Tiles

To map or unmap sparse tiles, you issue commands to the GPU using a resource state command encoder (MTLResourceStateCommandEncoder). Encode a command for each update, specifying the texture, a slice and mipmap within that texture, and a region inside that mipmap. Specify the region in tile coordinates.

- Swift
- Objective-C

```
if let encoder = commandBuffer.makeResourceStateCommandEncoder() {
    encoder.updateTextureMapping(texture, mode: .map, region: tileRegion, mipLevel: 0, slice: 0)
    encoder.endEncoding()
}
```

```
id encoder = [commandBuffer resourceStateCommandEncoder];

[encoder updateTextureMapping:texture
                         mode:MTLSparseTextureMappingModeMap
                       region:tileRegion
                     mipLevel:0
                        slice:0];

[encoder endEncoding];
```

The GPU looks for free sparse tiles on the texture’s heap and assigns them to the texture. Once the mapping process is complete, future requests to read, write, or sample those regions access the assigned tiles. Metal doesn’t initialize the tiles with data, so to ensure that valid data is available, copy or render data into the newly mapped regions before you read or sample from them.

The GPU fulfills mapping requests in the order that you encoded the commands. Within each command, the GPU maps the tiles in a row-major order on a first-come, first-served basis. If the heap runs out of memory, Metal skips any remaining tiles in the request.

To free tiles and make additional memory available to satisfy other requests, encode commands using the MTLSparseTextureMappingMode.unmap mode instead.

Important

Before you release a sparse texture, unmap all of its sparse tiles. Otherwise, the sparse heap continues to mark those tiles as mapped. However, Metal frees all mapped tile memory when you release the heap.

### Map the Tail Mipmaps After You Create the Texture

If you create a complete mipmap chain for your texture, many of the lower-level mipmaps are smaller than the sparse tile size. To save memory, Metal packs all of these smaller mipmaps into one memory allocation, typically one sparse tile. To guarantee that a texture always has some data to sample, you usually want to map the tail mipmaps after you create the texture and keep the tail mapped until you’re ready to release the texture.

To map the tail mipmaps, ask the texture for the first mipmap in the tail and map any region within it. All of the tail mipmaps are mapped.

- Swift
- Objective-C

```
let tailRegion = MTLRegionMake2D(0, 0, 1, 1)

encoder.updateTextureMapping(texture, mode: .map, region: tailRegion, mipLevel: texture.firstMipmapInTail, slice: 0)
```

```
MTLRegion tailRegion = MTLRegionMake2D(0, 0, 1, 1);

[encoder updateTextureMapping:texture
                         mode:MTLSparseTextureMappingModeMap
                       region:tailRegion
                     mipLevel:texture.firstMipmapInTail
                        slice:0];
```

Similarly, if you unmap the first mipmap in the tail, all of the tail mipmaps are unmapped.

### Synchronize Access to Tile Mapping and Unmapping

Tile mapping is performed by the GPU, which means that it happens asynchronously at a future point after you commit the command buffer. Don’t change the memory assigned to a texture while the texture’s contents are being read or written. Use fences or events to ensure that these actions don’t overlap.

Important

If you use more than one resource state encoder to encode commands that access the same sparse heap, you must execute them sequentially, or your app may crash. For example, if you’ve two different command queues in your app, and both encode resource state commands for the same heap, synchronize access using shared events so that the updates happen sequentially.

For more information about synchronizing Metal commands, see Resource Synchronization.

## See Also

### Sparse Textures

Managing Sparse Texture Memory

Take direct control of memory allocation for texture data by using sparse textures.

Creating Sparse Heaps and Sparse Textures

Allocate memory for sparse textures by creating a sparse heap.

Converting Between Pixel Regions and Sparse Tile Regions

Learn how a sparse texture’s contents are organized in memory.

Reading and Writing to Sparse Textures

Decide how to handle access to unmapped texture regions.

Estimating How Often a Texture Region Is Accessed

Use texture access patterns to determine when you need to map a texture region.

class MTLResourceStatePassDescriptor

A configuration for a resource state pass, used to create a resource state command encoder.

class MTLResourceStatePassSampleBufferAttachmentDescriptor

A description of where to store GPU counter information at the start and end of a resource state pass.

class MTLResourceStatePassSampleBufferAttachmentDescriptorArray

An array of sample buffer attachments for a resource state pass.

protocol MTLResourceStateCommandEncoder

An encoder that encodes commands that modify resource configurations.

struct MTLMapIndirectArguments

The data layout for mapping sparse texture regions when using indirect commands.

