

- Accelerate
-  bnns_graph_realloc_fn_t 

Type Alias

# bnns_graph_realloc_fn_t

The workspace and output allocation function.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+tvOS 18.0+visionOS 2.0+watchOS 11.0+

``` source
typealias bnns_graph_realloc_fn_t = (UnsafeMutableRawPointer?, Int, UnsafeMutablePointer, Int, Int) -> Int32
```

## Return Value

`0` on success, nonzero on failure.

## Discussion

BNNS may call this function for either an initial allocation, or to resize an existing allocation.

Typically, on the first execution of a graph all calls to this function are for allocation. Subsequent calls with the same context are for reallocation.

An optimized implementation should track sizes and avoid reallocating if the size is the same or smaller.

## See Also

### Specifying a context’s allocation callbacks

func BNNSGraphContextSetWorkspaceAllocationCallback(bnns_graph_context_t, bnns_graph_realloc_fn_t?, bnns_graph_free_all_fn_t?, Int, UnsafeMutableRawPointer?) -> Int32

Sets the allocation and deallocation callbacks for internal workspace.

func BNNSGraphContextSetOutputAllocationCallback(bnns_graph_context_t, bnns_graph_realloc_fn_t?, bnns_graph_free_all_fn_t?, Int, UnsafeMutableRawPointer?) -> Int32

Sets the allocation and deallocation callbacks for function outputs.

typealias bnns_graph_free_all_fn_t

The workspace and output deallocation function.

