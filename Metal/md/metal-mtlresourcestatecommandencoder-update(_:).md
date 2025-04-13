

- Metal
- MTLResourceStateCommandEncoder
-  update(\_:) 

Instance Method

# update(\_:)

Encodes a command that instructs the GPU to update a fence, which signals passes waiting on the fence.

iOS 13.0+iPadOS 13.0+Mac Catalyst 14.0+macOS 11.0+tvOS 16.0+visionOS 1.0+

**iOS, iPadOS, tvOS, visionOS**

``` source
func update(_ fence: any MTLFence)
```

**Mac Catalyst, macOS**

``` source
optional func update(_ fence: any MTLFence)
```

**Required**

## Parameters 

`fence`  

An MTLFence instance to update.

## Discussion

Fences maintain order to prevent GPU data hazards as the GPU runs various passes within the same command queue. This encoded command notifies any passes waiting for `fence`.

The GPU driver evaluates the pass’s fences and the commands that depend on them when your app commits the enclosing MTLCommandBuffer.

## See Also

### Performing Fence Operations

func wait(for: any MTLFence)

Encodes a command that instructs the GPU to pause before starting the resource state commands until another pass updates a fence.

**Required**

