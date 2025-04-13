

- MetricKit
- MXCallStackTree
-  jsonRepresentation() 

Instance Method

# jsonRepresentation()

Returns the contents of the stack tree in JSON format.

iOS 14.0+iPadOS 14.0+Mac Catalyst 14.0+macOS 12.0+visionOS 1.0+

``` source
func jsonRepresentation() -> Data
```

## Return Value

A `Data` object containing the JSON representation of the stack tree.

## Discussion

The stack tree is returned as a JSON dictionary. The top level contains one key:

`callStackTree`  
A dictionary containing the call stacks.

The `callStackTree` dictionary contains two keys:

`callStacks`  
An array of call stacks for a process or thread.

`callStackPerThread`  
A Boolean specifying whether the stack trace is for a single process thread or for all process threads.

A call stack is a dictionary containing at most two keys:

`threadAttributed`  
A Boolean indicating that the crash or exception occurred in this call stack.

`callStackRootFrames`  
An array of stack frames.

A stack frame is a dictionary containing up to six keys:

`binaryName`  
The name of the binary associated with the stack frame.

`binaryUUID`  
A unique ID a developer uses to symbolicate a stack frame. For more information, see Adding identifiable symbol names to a crash report.

`address`  
The memory address of the stack frame.

`offsetIntoBinaryTextSegment`  
The offset of the stack frame into the text segment of the binary.

`sampleCount`  
For a CPU exception, the amount of time spent sampling the stack frame.

`subFrames`  
An array of stack frame dictionaries. There can be many levels of nested stack frames.

The following code shows a partial example of the JSON for a stack tree with one stack frame per thread:

```
```

