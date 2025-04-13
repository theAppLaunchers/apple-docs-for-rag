

- Metal
- Buffers
-  Improving CPU Performance by Using Argument Buffers 

Article

# Improving CPU Performance by Using Argument Buffers

Optimize your app’s performance by grouping your resources into argument buffers.

## Overview

Use argument buffers to gather multiple resources into a single shader argument. An *argument buffer* is a Metal buffer that contains references to other Metal resources, including MTLBuffer, MTLTexture, MTLSamplerState, and MTLAccelerationStructure objects. Argument buffers use less overhead than assigning each resource individually. This is especially true for resources that don’t change between frames because you can assign the argument buffer once and reuse it many times.

Note

You need to use argument buffers to bind resources to pipelines composed of shaders that you compile with the Metal shader converter.

For more information on argument buffers, watch Go bindless with Metal 3 and Explore bindless rendering in Metal.

### Define Argument Buffer Formats in Metal Shading Language

Declare your argument buffers in a Metal Shading Language (MSL) source file as structures.

```
struct ArgumentBufferExample{
    texture2d a;
    depth2d b;
    sampler c;
    texture2d d;
    device float4* e;
    texture2d f;
    int g;
};

kernel void example(constant ArgumentBufferExample & argumentBuffer [[buffer(0)]])
{
    // 
    ...
}
```

Add the following types to the structures:

- Basic scalar data types, such as `half` and `float`

- Basic vector and matrix data types, such as `half4` and `float4x4`

- Textures, such as `texture2d`

- Samplers, such as a linear sampler

- Acceleration structures

- Indirect command buffers

- Arrays and structures that store the types above

- Other arrays and structures

Note

Argument buffers can’t contain union types, although objects that adopt the MTLBuffer protocol support unions.

### Encode Resources into Argument Buffers

Structures in regular Metal buffers define the exact layout of the data in memory. The memory layout for argument buffers depends on the GPU’s support for argument buffers and the device’s OS version. Metal divides argument buffer support into two tiers: Tier 1 and Tier 2. For Tier 2, argument buffers match the memory layout of an equivalent C structure on these OS releases:

- iOS 16.0 and later

- tvOS 16.0 and later

- macOS 13.0 and later

To directly encode the argument buffer resources on these Tier 2 devices, write the MTLBuffer`.`gpuAddress property — and for other resource types (samplers, textures, and acceleration structures), the gpuResourceID property — into the corresponding structure member. To encode offsets, treat these property values as `uint64` types and add the offset to them.

For Tier 1 devices and older OS versions on Tier 2 devices, buffers have a private memory layout that can vary by GPU. For these devices, use an MTLArgumentEncoder object to encode an argument buffer’s data into a destination MTLBuffer object. Then pass the argument buffer as a parameter to an MTLRenderCommandEncoder or MTLComputeCommandEncoder graphics or compute function, such as the following:

- setVertexBuffer(_:offset:index:)

- setFragmentBuffer(_:offset:index:)

- setMeshBuffer(_:offset:index:)

- setObjectBuffer(_:offset:index:)

- setTileBuffer(_:offset:index:)

- setBuffer(_:offset:index:)

You can encode resources into argument buffers using the following types:

- MTLBuffer

- MTLTexture

- MTLSamplerState

- simd_float1, simd_float4, and other inlined constant data

- MTLAccelerationStructure

- MTLIndirectCommandBuffer

- MTLComputePipelineState

- MTLRenderPipelineState

### Use Heaps to Improve Efficiency

Encoding resources into argument buffers eliminates the need for the Metal driver to capture state and track residency when it assigns individual resources to the indices of a function’s argument table. Argument buffers provide greater control over resource residency, which you must explicitly declare before issuing draw or dispatch calls.

When you combine resource heaps with argument buffers, you can further reduce overhead by making all read-only resources backed by a MTLHeap with a single call to the `useHeap` method. However, you still need to call the `useResource` method for each writable resource, even when your pass only intends to read from it.

Finally, argument buffers allow Metal to index resources dynamically at function execution time, which increases the limit on the number of resources that it can place inside the buffers.

### Understand Argument Buffer Tier Limits and Capabilities

Use the argumentBuffersSupport property of the MTLDevice object to get its tier.

**Common Tier 1 and Tier 2 Limits**

On iOS and tvOS, the maximum number of unique samplers per app is `96`, and for macOS, `1024` or greater, depending on the device and OS version.These limits are only applicable to samplers that have their supportArgumentBuffers property set to true. Use the MTLDevice`.`maxArgumentBufferSamplerCount property to get the exact maximum number of unique samplers per app for a device.

Metal considers a MTLSamplerState object unique if the configuration of its originating MTLSamplerDescriptor properties is unique. For example, if two samplers have equal minFilter values but different magFilter values, Metal considers them different objects.

For the maximum number of entries in each function argument table, see Metal feature set tables.

**Tier 1 Limits**

For Tier 1, Metal imposes resource limits on the maximum combined number of resources set within an argument buffer and set individually, per graphics or compute function. Metal counts the argument buffer entries against the maximum buffer entries in each function argument table. For example, if a kernel function uses four individual textures and one argument buffer with eight textures, the total number of textures for that kernel function is 12. Tier 1 argument buffers can’t include writable textures.

Other Tier 1 limits on argument buffers are:

- Need to be immutable because the GPU can’t modify the contents of an argument buffer

- Need to be CPU-accessible, so set the buffer’s storage mode to either MTLStorageMode.shared or MTLStorageMode.managed

- Can’t be accessible through pointer indexing, or include pointers to other argument buffers, in MSL

**Tier 2 Limits**

GPUs that support Tier 2 argument buffers have significantly higher limits that enable more capabilities in your app.

For Tier 2, argument buffers can be mutable so that the GPU and CPU can both modify the contents of them at any time. However, Metal may perform certain optimizations if you specify that neither the CPU nor the GPU modifies a buffer’s contents between the time Metal sets the buffer in a function’s argument table and the time Metal completes execution of the associated command buffer. Metal considers these types of argument buffers immutable. To indicate that an argument buffer is immutable and let Metal perform optimizations, set its associated MTLPipelineBufferDescriptor`.`mutability property to MTLMutability.immutable.

In MSL, you access Tier 2 argument buffers by indexing a pointer.

```
struct ArgumentBufferTextures {
    texture2d diffuse;
    texture2d specular;
};

struct ArgumentBufferMaterial {
    device ArgumentBufferTextures *textures;
};

fragment float4 exampleFragment(device ArgumentBufferMaterial & material)
{
    return material.textures[4]->diffuse.read(uint2(0));
}
```

Because you can’t copy samplers from the thread address space to the device address space, you only copy argument buffer samplers between argument buffers. For example, if you create `constexpr` samplers in shaders by default in the thread address space, you can’t assign them to buffers in the device address space.

```
struct ArgumentBufferSampler {
    sampler sampler0;
};

kernel void exampleKernel(device ArgumentBufferSampler *source,
                          device ArgumentBufferSampler *destination,
                          sampler sampler1) {
    constexpr sampler sampler2;

    // Metal allows device-to-device copies.
    destination->sampler0 = source->sampler0;

    // Metal doesn't allow thread-to-device copies.
    destination->sampler0 = sampler1;
    destination->sampler0 = sampler2;
}
```

## See Also

### Argument Buffers

Managing groups of resources with argument buffers

Create argument buffers to organize related resources.

Tracking the Resource Residency of Argument Buffers

Optimize resource performance within an argument buffer.

Indexing Argument Buffers

Assign resource indices within an argument buffer.

Rendering Terrain Dynamically with Argument Buffers

Use argument buffers to render terrain in real time with a GPU-driven pipeline.

Encoding Argument Buffers on the GPU

Use a compute pass to encode an argument buffer and access its arguments in a subsequent render pass.

Using Argument Buffers with Resource Heaps

Reduce CPU overhead by using arrays inside argument buffers and combining them with resource heaps.

class MTLArgumentDescriptor

A representation of an argument within an argument buffer.

protocol MTLArgumentEncoder

An object used to encode data into an argument buffer.

let MTLAttributeStrideStatic: Int

