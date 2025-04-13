

- Metal
- MTLIndirectCommandBufferDescriptor
-  inheritBuffers 

Instance Property

# inheritBuffers

A Boolean value that determines where commands in the indirect command buffer get their buffer arguments from when you execute them.

iOS 12.0+iPadOS 12.0+Mac Catalyst 13.1+macOS 10.14+tvOS 12.0+visionOS 1.0+

``` source
var inheritBuffers: Bool { get set }
```

## Discussion

Always set this property explicitly.

If you set the value to true, don’t set buffer arguments when you encode commands into the indirect command buffer. The commands use (inherit) the buffer arguments that you set on the parent encoder.

If you set the value to false, set the buffer arguments when you encode the commands into the indirect command buffer. The commands ignore any buffer arguments set on the parent encoder.

## See Also

### Declaring Command Inheritance

var inheritPipelineState: Bool

A Boolean value that determines where commands in the indirect command buffer get their pipeline state from when you execute them.

