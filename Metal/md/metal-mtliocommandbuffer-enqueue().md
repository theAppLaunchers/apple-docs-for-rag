

- Metal
- MTLIOCommandBuffer
-  enqueue() 

Instance Method

# enqueue()

Reserves a place for the input/output command buffer in the input/output command queue without committing the command buffer.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+tvOS 16.0+visionOS 1.0+

``` source
func enqueue()
```

**Required**

## Discussion

The method saves the next position for the command buffer in the input/output command queue. You can call enqueue() at any time relative to encoding commands, but you can only enqueue a command buffer once. To submit a command buffer to GPU for execution, call its commit() method.

For example, to fill multiple command buffers asynchronously that execute in a specific order:

1.  Call each command buffer’s enqueue() method in order.

2.  Encode commands into each command buffer on its own, separate thread.

3.  Call each command buffer’s commit() in any order.

## See Also

### Submitting a Command Buffer

func commit()

Submits the command buffer to the queue for execution on the GPU.

**Required**

