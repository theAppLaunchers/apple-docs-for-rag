

- Xcode
- Debugging
- Metal debugger
-  Analyzing your Metal workload 

Article

# Analyzing your Metal workload

Investigate your app’s workload, dependencies, performance, and memory impact using the Metal debugger.

## Overview

The Metal debugger provides useful tools for analyzing many aspects of how your app uses the GPU.

After capturing a Metal workload (see Capturing a Metal workload in Xcode) or replaying a GPU trace (see Replaying a GPU trace file), the Metal debugger presents the Summary viewer. The Summary viewer includes a preview of the last presented drawable in your app on the left, several statistics on the right, and a list of automatically generated recommendations, called Insights, at the bottom.

To the left of the Summary viewer is the Debug navigator, which enables quick access to top-level information about your Metal workload. You can explore all of the GPU commands in your capture, as well as all of the pipeline states it uses.

### View statistics for your Metal workload

The Metal debugger automatically calculates several statistics and displays them on the right side of the Summary viewer.

The Overview section includes the number of command buffers, command encoders, and draw commands or compute dispatches. It takes CPU time to encode commands, and GPU time to execute them. If your app is creating too many command buffers or command encoders that start to have a significant impact on performance, consider reducing the workload. You can click the Show Dependencies button to open the Dependencies viewer and learn how your command encoders connect with one another (see Analyzing resource dependencies).

The Performance section includes the total GPU time and the number of vertices. If your workload has a high GPU time, consider optimizing its performance (see Optimizing GPU performance). You can also click the Show Performance button to display the Performance timeline and discover which aspects of your Metal workload are taking the most time (see Analyzing Apple GPU performance using a visual timeline).

Note

If you don’t select the Profile after Replay checkbox in the Metal Capture popover (see Capturing a Metal workload in Xcode) or the Profile GPU Trace checkbox in the Replay window (see Replaying a GPU trace file), the performance section doesn’t show any statistics. To see the statistics, click the Profile button and wait for profiling to finish.

The Memory section includes a brief overview of GPU memory for various resource types, such as textures and buffers. If your Metal workload is using a large amount of memory, consider optimizing the memory use. You can also click the Show Memory button to open the Memory viewer and discover which aspects of your Metal workload are using the most memory (see Analyzing memory usage).

### Browse API calls

By default, the Metal debugger shows an outline of captured Metal commands — grouped by command buffers, passes, and debug groups — in the Debug navigator. In addition, for render passes, the outline includes a list of render attachment thumbnail images.

It’s common for a render pass to issue a massive number of draw commands. You can skim through the draw commands by moving your pointer over the rows to quickly locate a draw command of interest. The Metal debugger shows a preview of the first attachment in the popover.

### Browse pipeline states

Instead of viewing the hierarchy of Metal commands, you can begin exploring your captured Metal workload from pipeline states. Click the Outline popup menu and select Group by Pipeline State.

The Metal debugger shows a list of pipeline states. Expanding a pipeline state allows you to see its shaders. Further expansion shows all the draw commands and compute dispatches that use that pipeline state.

With profiling data, the Debug navigator displays the percentage of samples from the shaders of each pipeline state when running the workload with overlap. In a shader-bound workload, this sorted list of pipeline states is helpful in identifying the most expensive pipeline state.

### Improve your Metal workload with Insights

The Metal debugger automatically generates a number of recommendations, called Insights, and includes them at the bottom of the Summary viewer to help you improve your Metal workload. The Insights information includes the following categories:

Memory  
Memory insights provide recommendations to reduce the amount of GPU memory that your workload uses. By default, Xcode sorts the recommendations by the amount of memory saved, so you can focus on the biggest potential wins first. In the following example, setting the wrong storage mode results in an additional 10.2 MB of GPU memory usage. The developer of this app can save that memory by following the advice and switching to memoryless.

Bandwidth  
Bandwidth insights provide recommendations to reduce the amount of memory bandwidth, which is particularly important on Apple GPUs. Transfers to and from external memory often result in decreased power efficiency and slower performance. To learn more, see Tailor Your Apps for Apple GPUs and Tile-Based Deferred Rendering.

Performance  
Performance insights provide recommendations to increase your app’s performance by avoiding expensive and redundant operations in the rendering pipeline.

API Usage  
API Usage insights provide recommendations to improve your Metal API usage. Fewer API calls can lead to less CPU time. In the following example, you can see that the vertex and fragment buffers are redundantly bound for each draw command:

Click the Insights button next to the command in the Debug navigator to see in-depth details and recommendations that may improve your command.

### Limit your scope with filters

Use the filter bar at the bottom of the Debug navigator to adjust filtering criteria. You can type filter terms into the filter bar’s text field, and the outline in the Debug navigator shows only rows with labels that match those filter terms.

When there are two or more filter terms, you can click the filter button to choose whether to match any or all of the terms. For any filter term, you can click it to choose to include or exclude resources that match that term.

The following additional filter tools appear to the right:

Show only related stack frames  
After capturing a fresh GPU trace, you can inspect the call stack for each Metal command. This allows filtering for the stack frames in your project.

Show only calls with issues  
This allows filtering for just the Metal commands with insights from the Metal debugger.

Show only markers and commands  
This allows filtering for Metal commands like draw commands, compute dispatches, and blit operations.

## See Also

### Metal workload analysis

Analyzing resource dependencies

Avoid unnecessary work in your Metal app by understanding the relationships between resources.

Analyzing memory usage

Manage your Metal app’s memory usage by inspecting its resources.

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

