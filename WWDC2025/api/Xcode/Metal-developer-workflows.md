Collection

*   [Xcode](/documentation/xcode)
*   [Debugging](/documentation/xcode/debugging)
*   Metal developer workflows

# Metal developer workflows

Locate and fix issues related to your app’s use of the Metal API and GPU functions.

## [Overview](/documentation/Xcode/Metal-developer-workflows#Overview)

Metal comes with a comprehensive suite of advanced developer tools to help you debug and optimize your Metal apps.

### [Runtime diagnostics](/documentation/Xcode/Metal-developer-workflows#Runtime-diagnostics)

You can enable API Validation when running your app to check for incorrect Metal API usage. For more information, see [Validating your app’s Metal API usage](/documentation/xcode/validating-your-apps-metal-api-usage).

Enable Shader Validation when running your app to check for issues like out-of-bounds memory access, missing `useResource` calls, and stack overflows. For more information, see [Validating your app’s Metal shader usage](/documentation/xcode/validating-your-apps-metal-shader-usage).

The Metal Performance HUD offers a visual overlay to catch performance issues while your app is running. For more information, see [Monitoring your Metal app’s graphics performance](/documentation/xcode/monitoring-your-metal-apps-graphics-performance).

### [Runtime performance analysis](/documentation/Xcode/Metal-developer-workflows#Runtime-performance-analysis)

The Metal system trace tool in Instruments provides a visual timeline of the parallel work on the CPU and the GPU, and the memory usage of your Metal app.

![An Instruments screenshot displaying a capture in the Game Performance template.](https://docs-assets.developer.apple.com/published/3e6e41b0f0c4a82c893f9f86a4d8bf2e/gputools-instruments-game-performance-hero.png)

You can begin profiling with the Game Performance template (see [Analyzing the performance of your Metal app](/documentation/xcode/analyzing-the-performance-of-your-metal-app)) or the Game Memory template (see [Analyzing the memory usage of your Metal app](/documentation/xcode/analyzing-the-memory-usage-of-your-metal-app)).

### [Advanced Metal debugging and profiling](/documentation/Xcode/Metal-developer-workflows#Advanced-Metal-debugging-and-profiling)

The Metal debugger in Xcode provides advanced tools for debugging and profiling your Metal app.

![A screenshot of the Metal debugger showing the Bound Resources viewer and attachments for a draw command.](https://docs-assets.developer.apple.com/published/41dec1ced249f9f0b2c733fc369c1260/gputools-metal-debugger-hero.png)

You can get summaries of your Metal workload with the Dependencies viewer and the Memory viewer, inspect individual resources, and selectively debug your shaders. For more information on debugging, see [Investigating visual artifacts](/documentation/xcode/investigating-visual-artifacts).

In addition, you can optimize your Metal app by drilling down performance bottlenecks with the Performance timeline and the per-line shader profiling results. For more information on profiling, see [Optimizing GPU performance](/documentation/xcode/optimizing-gpu-performance).

Learn more about [Metal debugger](/documentation/xcode/metal-debugger).

## [Topics](/documentation/Xcode/Metal-developer-workflows#topics)

### [Project preparation for debugging](/documentation/Xcode/Metal-developer-workflows#Project-preparation-for-debugging)

Make your Metal app easier to debug by taking a few extra steps as you develop your code.

[

Building your project with embedded shader sources](/documentation/xcode/building-your-project-with-embedded-shader-sources)

Prepare to debug your project’s shaders by including source code in the build.

[

Naming resources and commands](/documentation/xcode/naming-resources-and-commands)

Enhance the debugging of your Metal app using labels and grouping.

[

Creating and using custom capture scopes](/documentation/xcode/creating-and-using-custom-capture-scopes)

Capture specific GPU commands by using custom capture scopes.

### [Runtime diagnostics](/documentation/Xcode/Metal-developer-workflows#Runtime-diagnostics)

Learn how to use runtime tools to discover potential issues in your Metal app.

[

Inspecting live resources at runtime](/documentation/xcode/inspecting-live-resources-at-runtime)

Validate your resources by viewing the contents of your textures and buffers while debugging your Metal app.

[

Validating your app’s Metal API usage](/documentation/xcode/validating-your-apps-metal-api-usage)

Catch runtime issues in your Metal app using API Validation.

[

Validating your app’s Metal shader usage](/documentation/xcode/validating-your-apps-metal-shader-usage)

Catch common shader runtime issues using Shader Validation while your app is running.

[

Monitoring your Metal app’s graphics performance](/documentation/xcode/monitoring-your-metal-apps-graphics-performance)

Catch performance issues using the Metal Performance HUD while your app is running.

### [Counters](/documentation/Xcode/Metal-developer-workflows#Counters)

Get references for the set of performance metrics available across Metal tools.

[

Finding your Metal app’s GPU occupancy](/documentation/xcode/finding-your-metal-apps-gpu-occupancy)

Understand the GPU usage for executing shaders by using occupancy.

[

Reducing shader bottlenecks](/documentation/xcode/reducing-shader-bottlenecks)

Identify and minimize congestion points in a GPU’s subsystems by checking its limiter and utilization counters.

[

Measuring the GPU’s use of memory bandwidth](/documentation/xcode/measuring-the-gpus-use-of-memory-bandwidth)

Check whether your Metal app correctly reads and writes to memory by measuring the GPU’s memory bandwidth.

## [See Also](/documentation/Xcode/Metal-developer-workflows#see-also)

### [Graphics](/documentation/Xcode/Metal-developer-workflows#Graphics)

[

API Reference

Metal debugger](/documentation/xcode/metal-debugger)

Debug and profile your Metal workload with a GPU trace.