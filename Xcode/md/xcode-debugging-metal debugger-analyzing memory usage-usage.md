

- Xcode
- Debugging
- Metal debugger
-  Analyzing memory usage 

Article

# Analyzing memory usage

Manage your Metal app’s memory usage by inspecting its resources.

## Overview

The Memory viewer provides comprehensive information about your app’s memory usage in Metal. The Memory viewer’s top section presents a breakdown of memory by categories, and the bottom section displays a table of resources. In the table, you can inspect resources for their memory size, configuration, and other characteristics.

Metal apps create many resources, and those resources consume a lot of memory. For example, to render an animated character using a physically based renderer, you might need buffers to hold vertex and animation data, and multiple textures to provide material attributes. When you scale these requirements to multiple characters and larger scenes, your app’s memory footprint grows significantly.

Additionally, when you create Metal resources, specifying their configuration precisely has a substantial effect on performance. The Metal debugger analyzes the configuration you provide and uses it to create the underlying GPU representation of a resource. For example, if you create a resource with a private storage mode, Metal can optimize the resource for GPU access, and doesn’t need to store data in a location or format directly accessible from the CPU.

### Examine the bar graphs

The categories in the top section of the Memory viewer organize memory usage data and provide memory totals based on the following criteria:

Volatility  
This category lists *volatile* and *nonvolatile* resources. Nonvolatile memory total is a good indicator of your app’s tracked memory usage for Metal. When you mark a resource as volatile, you give Metal permission to dispose of its contents when memory is scarce. The operating system doesn’t count volatile memory in your app’s total memory footprint. For example, in iOS, a lower footprint reduces the risk that you exceed the jetsam limit and have the operating system terminate your app. If you think that you might use a resource in the future that you’re not currently using, mark it as volatile rather than simply releasing it. That way, you only need to recreate the resource’s contents if Metal discards them. For more information, see setPurgeableState(_:).

Type  
This category lists resources by type — textures, buffers, and so on. Check this category to determine whether your app is using any particular kind of resource more than others.

Storage mode  
This category lists resources by the modes that you define in MTLStorageMode. Check this category to determine whether an excessive number of resources are marked as MTLStorageMode.shared or MTLStorageMode.managed.

Use  
This category tracks whether commands accessed resources in the captured frame. Examine this category for a large total of unused resources, which might indicate that you need to release some resources or mark them as volatile.

Each bar graph consists of segments representing the largest resources that it tracks. The final segment of each bar graph shows an aggregate total for its smaller resources. Move your pointer over a segment to view a popover with the name of the resource, its size, and other information. Click a segment to get more information about that specific resource.

### Inspect the resources table

To improve how your app creates and manages resources, you need data about how it uses them. The Memory viewer provides information about the resources that are live in your Metal app during a capture.

The resources table provides the following information for all resource types:

| Column | Property | Description |
|----|----|----|
| Label | label | The label you add when creating the resource. Use this information to identify specific resources in your app. To learn how to name your resources, see Naming resources and commands. |
| Insights |  | Possible problems or optimizations that might improve memory or resource usage. |
| Type |  | The type of resource. For a texture, this information includes the texture’s subtype. For a heap, it includes the heap’s subtype. |
| Allocated Size | allocatedSize | The allocated memory size for the resource. |
| Storage Mode | resourceOptions or storageMode | The storage mode you choose when creating the resource. |
| Purgeable State |  | The volatility of the resource. When you mark a resource as volatile, the system can purge it when free memory is low. The operating system doesn’t include volatile resources in the system memory total for your app. |
| Aliasable | isAliasable() | An indication of whether the resource shares its associated memory with another resource on the same heap. |
| CPU Access |  | An indication of whether your app has accessed the resource from the CPU. |
| Time Since Last Bound |  | The amount of time since last binding the resource to a Metal command encoder. If you’ve never bound the resource or haven’t bound it for a long time, you can probably release this resource or mark it as volatile. |

For textures, you can add the following columns:

| Column | Property | Description |
|----|----|----|
| Pixel Format | pixelFormat | The Metal pixel format you choose when creating the texture. |
| Width | width | The width, in pixels, of the texture’s base mipmap. |
| Height | height | The height, in pixels, of the texture’s base mipmap. |
| Depth | depth | The depth, in pixels, of the texture’s base mipmap. |
| Array Length | arrayLength | The number of slices in the texture array. |
| Mipmaps | mipmapLevelCount | The number of mipmap levels in the texture. |
| Samples | sampleCount | The number of samples in each pixel. |
| Usage | usage | Indicates the actions a shader or app can perform on the texture. The more restricted the list, the more optimizations Metal can apply to the texture. |
| Lossless Compression |  | Indicates whether the texture supports lossless compression. |

For buffers, you can add the following column:

| Column | Property | Description |
|----|----|----|
| Length | length | The logical length, in bytes, of the buffer. Compare this value to the allocated size. To make memory available to the GPU, Metal sometimes needs to allocate more memory than you request. If you see many small buffers, consolidate those that the system uses together into a single buffer, or allocate the buffers on a heap. These alternative allocation strategies save memory and require less work to track dependencies between commands accessing those resources. |

For heaps, you can add the following columns:

| Column | Property | Description |
|----|----|----|
| Size | size | The logical size, in bytes, of the heap. |
| Used Size | usedSize | The number of bytes the heap allocates for other resources. |
| Hazard Tracking Mode | resourceOptions or hazardTrackingMode | The hazard tracking mode of the allocated resources on the heap. |

For indirect command buffers, you can add the following column:

| Column | Property | Description |
|----|----|----|
| Size | size | The number of bytes the system uses to hold encoded commands. This total doesn’t include memory for any commands that the system resets. Compare this size to the allocated size of the indirect command buffers. Choose the size of an indirect command buffer based on the number of commands you expect to execute inside it. |

For acceleration structures, you can add the following column:

| Column | Property | Description |
|----|----|----|
| Size | size | The logical length, in bytes, of the acceleration structure. |

### Improve your Metal workload with Insights

Click the Insights button in the bottom right corner to open a popover of recommendations for the resources.

### Limit your scope with filters

Use the filter field at the bottom of the Memory viewer to adjust filtering criteria. Type filter terms into the field, and the resources table displays any resources with labels that match those filter terms.

You can also click the filter button to add filters for specific kinds of resources, to limit the table to resources that the captured frame uses, and to limit the table to just volatile resources.

When there are two or more filter terms, you can click the filter button to choose whether to match any or all of the terms. For any filter term, you can click it to choose to include or exclude resources that match that term.

### Group and sort resources to detect patterns

By default, the resources table shows all resources in a single list. You can click a column header to sort the table by that column in ascending or descending order. You can also group the resources by certain criteria.

Control-click an entry in the table to group the resources by any of the following criteria:

None  
Restores the behavior to the default, which shows all resources in the table without grouping them.

Type  
Groups the resources into buffers, textures, heaps, or indirect command buffers.

Allocated Size  
Groups the resources by their actual size. The groupings are based on a logarithmic scale. Use this criteria to find the largest resources in your app.

Storage Mode  
Groups the resources by the storage mode you select when creating each resource.

Command Buffer  
Groups the resources based on which command buffers reference them. Use this criteria to determine which commands are referencing which resources.

Command Encoder  
Groups the resources according to commands that use a specific command encoder. Use this criteria to understand the behavior of your specific compute and render passes.

From this same context menu, you can also choose to sort by a specific criteria, which is equivalent to clicking a column heading for sorting.

### Get more information about a specific resource

You can also get more information about a specific resource by Control-clicking it and selecting Get Info.

For example, for a texture, the additional information shows details specific to that texture, such as its pixel format and dimensions. To see the contents of the texture, double-click it.

### Export a memory report

To share the data in the Memory viewer, you can export it in the following ways:

- Export a GPU trace: Choose File \> Export and select a location to save the GPU trace file. You can then open the trace file later.

- Export a comma-separated values (CSV) file: Choose Editor \> Export Memory Report to generate the CSV file. The resulting file has all of the columns you see in the resource view. You can open this file in Numbers or another spreadsheet app.

## See Also

### Metal workload analysis

Analyzing your Metal workload

Investigate your app’s workload, dependencies, performance, and memory impact using the Metal debugger.

Analyzing resource dependencies

Avoid unnecessary work in your Metal app by understanding the relationships between resources.

Analyzing Apple GPU performance using a visual timeline

Locate performance issues using the Performance timeline.

Analyzing Apple GPU performance using counter statistics

Optimize performance by examining counters for individual passes and commands.

Analyzing Apple GPU performance with performance heat maps

Gain insights to SIMD group performance by inspecting source code execution.

Analyzing Apple GPU performance using the shader cost graph

Discover potential shader performance issues by examining pipeline states.

Analyzing non-Apple GPU performance using counter statistics

Optimize performance by examining counters for individual passes and commands.

