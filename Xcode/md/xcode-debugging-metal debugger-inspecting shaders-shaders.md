

- Xcode
- Debugging
- Metal debugger
-  Inspecting shaders 

Article

# Inspecting shaders

Improve your app’s shader performance by examining and editing your shaders.

## Overview

The Metal debugger allows you to view and edit shaders with the Shader editor. After opening a shader, you can view and edit its source code, or the source code of any other file within the Metal library that the executed function requires. For more information, see Inspecting the bound resources for a command.

When you profile the Metal workload, you can see per-line performance metrics. As you make changes, you can reload the shader to update the Metal workload and performance numbers.

Important

Include source code when you capture a Metal workload because the Shader editor needs it to function correctly. For more information, see Building your project with embedded shader sources.

### Navigate your shader

The Shader editor shows your source code in the context of an executed function, and includes familiar Xcode source-editing abilities, like Fixing issues in your code as you type.

In addition to the source containing the executed function, you can also edit other files within the Metal library that the executed function requires. Click the Toggle Left Sidebar button on the bottom left to reveal the source files outline. Then, select another file.

### View per-line performance metrics

You can view per-line performance metrics in the Shader editor after profiling finishes. This happens automatically if you select Profile after Replay in the Metal Capture popover (see Capturing a Metal workload in Xcode) or Profile GPU Trace in the Replay window (see Replaying a GPU trace file). Alternatively, you can profile directly within the Shader editor by clicking the Generate button in the top right corner.

Then, wait for profiling to finish. You can see its status in the activity bar at the top of your Xcode window.

After profiling your Metal workload, the Shader editor shows statistics on each line. For devices with a GPU in the Apple 4 family or later, there’s a pie chart to the right of the numeric statistics to help you improve the performance for a function or a line of code. For more information on Apple GPU family 4 devices, see Tailor Your Apps for Apple GPUs and Tile-Based Deferred Rendering and Metal feature set tables.

You can hover the pointer over the pie chart to enlarge it and show more detail about the work that the GPU performed while executing the line of code. The work a GPU performs can be categorized as memory, ALU, synchronization, or control flow.

By understanding the activities that the GPU executes for each line in your shader, you can infer any necessary code changes to improve the shader performance.

| GPU activity | Explanation and recommendations |
|----|----|
| ALU | The amount of time that the GPU spends in the arithmetic logic unit. Change floats to half-floats where possible to reduce the time in the ALU. Also, try to minimize your use of complex instructions like `sqrt`, `sin`, `cos`, and `recip`. |
| Memory | The amount of time that the GPU spends waiting for access to your app’s buffers or texture memory. Reduce time by downsampling textures, or, if you’re not spending much time in memory, improve your texture resolution instead. |
| Control flow | The amount of time that the GPU spends in conditional, increment, or jump instructions as a result of branches or loops in your shader. Use a constant iteration count to minimize control flow time for loops because the Metal compiler can generate optimized code in those cases. |
| Synchronization | The amount of time that the GPU spends waiting for a required resource or event before execution can begin. Synchronization types are described below. |
| Synchronization (wait memory) | The amount of time that the GPU spends waiting for dependent memory accesses, such as texture sampling or buffer read/write. |
| Synchronization (wait pixel) | The amount of time that the GPU spends waiting for underlying pixels to release resources. In addition to color attachments, pixels can come from depth or stencil buffers or user-defined resources. Blending is a common cause of pixel waiting. Use raster order groups to reduce the wait time. |
| Synchronization (barrier) | The amount of time that the GPU spends when a thread reaches a barrier and the GPU waits for remaining threads in the same group to arrive at the barrier before proceeding. |
| Synchronization (atomics) | The amount of time that the GPU spends on atomic instructions. |

To ensure you see the most up-to-date profiling numbers, set your app’s deployment target to the matching OS version, even if temporarily. The Shader editor displays a warning at the top if the deployment target doesn’t match your OS version.

You can change the deployment target in the Xcode project settings. If you change the deployment target temporarily, don’t forget to change it back before deploying your app.

### Update your shader

After changing a shader, you can update the captured frame with the new source code by clicking the Reload Shaders button in the debug bar.

After updating the captured frame, Xcode does the following:

- Redraws the app window.

- Updates the profiler statistics and pie charts.

- Redraws attachments in the assistant editor.

- Maintains your place in the captured frame, providing an interactive environment to enhance your shader performance tuning.

Important

To avoid getting misleading results between different runs, using a consistent performance state is useful when iterating on your shader.

You can profile using a specific performance state by clicking the GPU Profiler button in the debug bar.

Then, select your desired performance state.

If your shader is producing incorrect results, you can also debug it. For more information, see Debugging the shaders within a draw command or compute dispatch.

## See Also

### Metal resource inspection

Inspecting acceleration structures

Reveal ray intersection bottlenecks by examining your acceleration structures.

Inspecting buffers

Confirm your buffer formats by examining buffer content.

Inspecting pipeline states

Determine how your render and compute passes behave by examining their properties.

Inspecting sampler states

Verify your sampler state configurations by examining their properties.

Inspecting textures

Discover issues in your textures by examining their content.

