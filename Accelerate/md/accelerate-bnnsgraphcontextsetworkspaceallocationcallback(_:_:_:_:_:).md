

- Accelerate
-  BNNSGraphContextSetWorkspaceAllocationCallback(\_:\_:\_:\_:\_:) 

Function

# BNNSGraphContextSetWorkspaceAllocationCallback(\_:\_:\_:\_:\_:)

Sets the allocation and deallocation callbacks for internal workspace.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+tvOS 18.0+visionOS 2.0+watchOS 11.0+

``` source
func BNNSGraphContextSetWorkspaceAllocationCallback(
    _ context: bnns_graph_context_t,
    _ realloc: bnns_graph_realloc_fn_t?,
    _ free: bnns_graph_free_all_fn_t?,
    _ user_memory_context_size: Int,
    _ user_memory_context: UnsafeMutableRawPointer?
) -> Int32
```

## Parameters 

`context`  

The graph context.

`realloc`  

The memory allocation and reallocation function. If you pass `nil` for this parameter, you must also set `nil` for the `free` parameter. In this case, graph execution uses the default BNNS allocation mechanism.

`free`  

The memory allocation and reallocation function. If you pass `nil` for this parameter, you must also set `nil` for the `realloc` parameter. In this case, graph execution uses the default BNNS allocation mechanism.

`user_memory_context_size`  

The size, in bytes, `user_memory_context`.

`user_memory_context`  

A pointer that that BNNS passes unmodified in all calls to `realloc` and `free`.

## Return Value

`0` on success, nonzero on failure.

## Discussion

If BNNS can’t bound the required workspace size prior to execution — for example, if the tensor sizes depend on input data — it allocates workspace during execution. Use this function to override the default memory allocation mechanisms.

Note that BNNS typically calls the `free` function when it destroys the context, but it only requires the workspace during execution. As such, you may wish to make the allocated memory purgable or free it between calls to BNNSGraphContextExecute(_:_:_:_:_:_:).

If you pass the same `user_memory_context` to BNNSGraphContextSetWorkspaceAllocationCallback(_:_:_:_:_:) and BNNSGraphContextSetOutputAllocationCallback(_:_:_:_:_:), BNNS only calls the `free` function once.

## See Also

### Specifying a context’s allocation callbacks

func BNNSGraphContextSetOutputAllocationCallback(bnns_graph_context_t, bnns_graph_realloc_fn_t?, bnns_graph_free_all_fn_t?, Int, UnsafeMutableRawPointer?) -> Int32

Sets the allocation and deallocation callbacks for function outputs.

typealias bnns_graph_realloc_fn_t

The workspace and output allocation function.

typealias bnns_graph_free_all_fn_t

The workspace and output deallocation function.

