

- Xcode
- Debugging
- Metal debugger
-  Analyzing Apple GPU performance with performance heat maps 

Article

# Analyzing Apple GPU performance with performance heat maps

Gain insights to SIMD group performance by inspecting source code execution.

## Overview

Metal organizes the threads of your shader into single-instruction, multiple-data (SIMD) groups. The performance heat maps feature provides a way to quickly find SIMD groups that are expensive or divergent. You can graphically inspect how Apple GPUs execute the shader source code in those groups, and gain insights of potential performance bottlenecks.

Important

The performance heat maps feature is available for iOS devices with A17 Pro or later, and Mac computers with M3 or later.

### View the performance heat maps

To open the performance heat maps, click the Performance button in the Metal debugger’s Debug navigator, and then click the Heat Map tab above the Performance timeline.

When you select an encoder, pipeline state, or GPU command in the Timeline navigator, the heat maps for the corresponding work appear on the right.

Note

Performance heat maps are available for render command encoders, render pipeline states, and compute dispatches. However, they don’t support compute command encoders or compute pipeline states.

In addition, performance heat maps are available for the following shader types:

| Shader type     | Heatmap pixel location |
|-----------------|------------------------|
| Fragment shader | Fragment position      |
| Object shader   | Thread location        |
| Mesh shader     | Thread location        |
| Compute shader  | Thread location        |

Note

For compute, object, and mesh shaders, when the maximum compute thread location in the x-axis or y-axis exceeds 8192, each pixel in the heat map represents a SIMD group instead of a thread.

### Switch between shader types

By default, selecting a render command encoder, a render pipeline state, or a draw command shows the fragment shader heat maps. Selecting a compute dispatch command shows the compute shader heat maps.

You can switch between different shader types using the Vertex and Fragment tabs above the heat maps.

### Display more types of performance heat maps

By default, the Shader Execution Cost heat map and the Attachments display for render command encoders, pipeline states, and draws.

Click the Add button (+) in the heat map control bar to open a popover of all available performance heat maps. You can customize which heat maps to display by selecting the checkboxes.

Available performance heat map options include the following:

| Type | Description |
|----|----|
| Shader Execution Cost | Visualizes the shader execution cost by combining shader execution time and latency hiding. |
| ALU Cost | Visualizes the ALU portion of the shader execution cost. |
| Non-ALU Cost | Visualizes the non-ALU portion of the shader execution cost. |
| Thread Divergence | Visualizes the amount of GPU thread divergence in the SIMD groups. |
| Control Flow Divergence | Visualizes the GPU thread divergence that controls flow differences, like `IF` conditions, cause. |
| Inactive Threads | Visualizes the GPU thread divergence that inactive threads cause due to the shape of the geometry or the compute dispatch grid dimensions. |
| Overdraw | Visualizes the number of SIMD groups that write the pixel. |
| Instruction Count | Visualizes the number of instructions per pixel or per SIMD group. |
| Raytracing Latency | Visualizes the latency of ray-tracing instructions, which go through the ray-tracing unit. |
| Draw ID | Color codes different draws within a render pass. |

The color intensity in the heat maps represents the significance of the values. For example, red means *more expensive* in the Shader Execution Cost heat map, and *more divergent* in the Thread Divergence heat map.

### View and adjust the value range of performance heat maps

You can filter and tone-map a performance heat map by clicking the Histogram button in the title bar.

The histogram popover shows the value range of the heat map. You can drag the handles to adjust the range to filter smaller and larger values. This can be useful in situations when you want a certain value range, such as showing pixels in a render pass that executes more than 100 instructions.

### Inspect the execution history for a SIMD group

Selecting a pixel in the heat map allows you to inspect the underlying SIMD group.

If more than one SIMD group touches the pixel in a render pass, a list of SIMD groups in order of cost percentile appears so you can select the one to inspect. When you select a SIMD group in the list, its execution history appears below the heat maps.

The Execution History timeline shows the progress of the selected SIMD group from left to right, and lists the full shader call stack at each point of execution from top to bottom.

The Metal debugger also helps you better understand shader execution by detecting and visualizing loops in the shader instruction stream. You can select a node in the timeline, and the source editor jumps to the file and the line that contain the executed instructions of that node.

### Understand the number of instructions per line

The number of executed instructions appears next to the lines of code, in the gutter of the shader source code. This number is the total assembly code executions over the lifetime of the entire SIMD group for that line of code.

For example, if there’s a loop with 10 iterations, the number of instructions for the source lines within the loop is 10 times more than the source lines outside the loop, given the same amount of assembly code.

### Switch between per-line statistics modes

In the shader source code control bar, you can choose different modes for the per-line shader profiling statistics in the gutter. Options include the following:

| Mode | Description |
|----|----|
| Number of Instructions | The total number of assembly instructions that active threads execute. |
| Thread Divergence | 1 - the total number of instructions from active threads divided by the number of theoretical maximum instructions that the system can execute. |

You may find thread divergence to be 50% if there’s a conditional branch that only half of the threads enter within the selected SIMD group.

For more information about the Metal profiling tools for M3 and A17 Pro, see Discover new Metal profiling tools for M3 and A17 Pro.

## See Also

### Metal workload analysis

Analyzing your Metal workload

Investigate your app’s workload, dependencies, performance, and memory impact using the Metal debugger.

Analyzing resource dependencies

Avoid unnecessary work in your Metal app by understanding the relationships between resources.

Analyzing memory usage

Manage your Metal app’s memory usage by inspecting its resources.

Analyzing Apple GPU performance using a visual timeline

Locate performance issues using the Performance timeline.

Analyzing Apple GPU performance using counter statistics

Optimize performance by examining counters for individual passes and commands.

Analyzing Apple GPU performance using the shader cost graph

Discover potential shader performance issues by examining pipeline states.

Analyzing non-Apple GPU performance using counter statistics

Optimize performance by examining counters for individual passes and commands.

