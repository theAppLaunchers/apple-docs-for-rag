

- Core Services
- File Metadata
- MDQuery
-  MDQueryCreate(\_:\_:\_:\_:) 

Function

# MDQueryCreate(\_:\_:\_:\_:)

Creates a new query instance.

macOS 10.4+

``` source
func MDQueryCreate(
    _ allocator: CFAllocator!,
    _ queryString: CFString!,
    _ valueListAttrs: CFArray!,
    _ sortingAttrs: CFArray!
) -> MDQuery!
```

## Parameters 

`allocator`  

The CFAllocator object to be used to allocate memory for the new object. Pass `NULL` or `kCFAllocatorDefault` to use the current default allocator.

`queryString`  

The query expression string for this query.

`valueListAttrs`  

An optional array of attribute names. The query will collect the values of these attributes into uniqued lists that can be used to summarize the results of the query and allow the user to further qualify the search. This parameter may be `NULL` if no value lists are required. Value list collection increases CPU usage and significantly increases the memory usage of an MDQuery. The attribute names are CFStrings.

`sortingAttrs`  

A n array of attribute names used to sort the results, or `NULL` if no sorting is required. The first name in the array is used as the primary sort key, the second as the secondary key, and so on. The comparison of like-typed values is a simple, literal comparison. Sorting increases memory usage and significantly increases the CPU usage of an MDQuery. It is usually more efficient to allow the MDQuery to sort the results than retrieving the values and sorting the results yourself. The attribute names are CFStrings.

## Return Value

An MDQueryRef, or `NULL` on failure. If the query string is empty or malformed the function returns NULL.

## See Also

### Creating Queries

func MDQueryCreateSubset(CFAllocator!, MDQuery!, CFString!, CFArray!, CFArray!) -> MDQuery!

Creates a new query that is a subset of the specified parentquery.

func MDQuerySetSearchScope(MDQuery!, CFArray!, OptionBits)

Sets the search scope for a query instance.

func MDQuerySetDispatchQueue(MDQuery!, dispatch_queue_t!)

Sets the dispatch queue on which query results will be delivered by MDQueryExecute.

