

- Xcode
- Performance and metrics
-  Analyzing the performance of your Metal app 

Article

# Analyzing the performance of your Metal app

Ensure consistent, smooth rendering by profiling your app’s frame time.

## Overview

A low-performing frame rate can cause an app to seem sluggish or disruptive to its users, so it’s important to remove temporary interruptions, or *stutters*, to optimize your app’s user experience. To get information about the cause of slowness in your app’s frame rate, you can use the Game Performance template in Instruments, which combines threading and system call information with the Metal system trace instrument. By presenting important app states and rendering activities, the Game Performance template helps you infer the changes that are necessary to achieve consistent, smooth rendering.

### Open the Game Performance template

Start the performance analysis from your Xcode project by choosing Product \> Profile, or by pressing Command-I. Alternatively, you can launch Instruments and choose a target app.

In the Template Selection window, select Game Performance and click Choose.

### Get to know the instruments

The Game Performance template includes the following instruments:

Points of Interest  
Indicates locations in the trace that a developer might want to pay special attention to.

System Load  
Tracks the performance and current load of the system.

Thread State Trace  
Traces each time the OS scheduler makes a decision that might impact your app’s threads.

System Call Trace  
Records system calls and their duration.

Virtual Memory Trace  
Tracks virtual memory activity per thread.

Time Profiler  
Profiles the running threads on all cores at regular intervals for the app.

Thermal State  
Records the device thermal state.

Metal Resource Events  
Records Metal GPU resource allocations, such as textures and buffers.

Metal Application  
Records Metal app events.

GPU  
Records GPU events.

Display  
Records display and vertical synchronization events.

### Include performance limiter or utilization counters

By default, Instruments doesn’t collect performance counters data. You can optionally include this for the instruments. Click and hold the Record button and choose Recording Options.

Then, in the Recording Options popover, choose the Performance Limiters option from the Counter Set menu.

When you record the Instruments trace, it collects performance limiter and utilization counters data.

### Record an Instruments capture

Begin collecting the data by clicking the Record button.

Within your app, perform the actions that reproduce a slow frame rate, and then click the Record button to stop recording.

### Identify performance anomalies

To expedite your review of the capture results, narrow your focus to around the time the frame rate was slow. Sometimes a frame rate anomaly is a result of infrequently skipped frames, and other times it’s due to a consistently poor frame rate. In either case, you identify frame rate anomalies by finding unexpected delay in your app’s display times.

In the display results, hover the pointer over a frame to check its duration. For example, in the screenshot below, the display instance is 50 milliseconds (ms). Below the display instance, you can inspect how many vertical synchronization (vsync) events the app skipped during that time.

Because the display instance of 50 ms is significantly longer than the display instances around it, you can consider the delay in frame delivery a stutter. In contrast, the following screenshot shows an app that maintained a consistent frame rate:

A duration of 16.67 ms is one 60 fps frame, and because all other frames consistently achieve this frame duration, there’s no performance anomaly to observe.

Not all displays use a frame interval of ~16 ms. For example, vertical synchronization can happen on ~4 ms intervals. It isn’t a requirement that display instances align with vertical synchronization for a healthy frame rate. An app that uses a 20 ms frame interval is a healthy frame rate as long as it consistently achieves 50 fps. However, a delay of 50 ms is much too long for smooth animations.

### Check GPU utilization

After finding a performance anomaly, look for the cause by examining the GPU activities occurring around that time. The GPU Hardware track shows your shader pipeline stages that run on the shader cores. Any long-running stages or inconsistent durations in the track timeline can indicate a utilization issue. For example, the following screenshot shows a case where a display instance spanned multiple frame intervals, meaning that the app unintentionally skipped frames:

To begin investigating shader core utilization as a potential cause of poor frame rate, do the following:

1.  Observe the performance anomaly. In this case, the display instance spanned multiple frame intervals.

2.  Check the vertex shader. In this case, the vertex shader is healthy because it completes in a small percentage of the frame interval.

3.  Hover the pointer over the fragment shader to see its duration. In this case, it ran for 74.64 ms, which is too long.

Because the combined duration of the vertex and the fragment shader is more than the duration of a 60 fps frame interval (16.67 ms), the app skipped a frame. The vertex shader ran quickly in this case, which means the app’s frame rate issues are solely due to fragment shader overutilization.

The following are additional reasons for overutilization of the shader cores:

- **Too many render passes:** Indicated by the renderer depriving the GPU of downtime. Check the number of render passes that occur at the time of the poor frame rate by using the Dependencies viewer. For more information, see Analyzing resource dependencies.

- **High resolution:** Inidicated by critically more fragment shader activity per the same number of submitted vertices, as compared to when your viewport is set to the smaller size. To ensure your app’s viewport isn’t related to the slowdown, temporarily reduce the viewport size to see if performance improves.

- **Large textures:** Indicated by high synchronization time when profiling your fragment shader. The per-line profiling result shows a high percentage of time in wait memory. For more information, see Inspecting shaders.

- **Large meshes:** Indicated by a high number of vertices that your app submits. Check the affected frames using the Geometry viewer. For more information, see Inspecting the geometry of a draw command.

- **Unoptimized shader code:** Indicated by general shader sluggishness. If you’re able to modify your app’s shaders, profile them to identify hot spots. For example, you can optimize your shaders by downsizing data types, or by minimizing the use of control structures. You don’t necessarily know whether your shaders can benefit from optimization until you try it. For more information, see Inspecting shaders.

### Check CPU utilization

While checking your shader core utilization, also look for signs that indicate problems with your app’s CPU utilization. The screenshot below shows a case where frame skipping appears to result from something other than the shader core. Note the gap where the shader core was idle for multiple frames.

When the Display track spans multiple frame intervals and there are gaps in the shader core timeline, it indicates that your host app’s code is running long. Inspect your app’s CPU utilization to determine whether it’s responsible for poor frame rate.

To check your app’s CPU utilization, identify your rendering threads in the thread state tracks. In the case of healthy CPU utilization, your app’s rendering threads generally show a significant amount of blocked time. The following screenshot shows an app’s rendering thread selected, and its blocked time taking around 75% of each ~16 ms frame interval:

Blocked time indicates that your renderer finished submitting its draw commands with some time to spare in the frame interval. Because the amount of blocked time above encompasses about two-thirds of its frame interval, the host app has left enough time for the shader core to start and finish its work within the same frame interval.

By contrast, if your rendering threads don’t show much blocked time, it’s likely that your app is overutilizing the CPU. To identify whether your app is overutilizing the CPU, and to determine the reason, perform the following steps:

1.  Observe a stutter, as identified by a display duration longer than 16.67 ms.

2.  Ensure that shader code isn’t the cause of the low frame rate. For more information, see Check GPU utilization above.

3.  Check the thread states for Running that are blue in color.

4.  Click the thread’s track to select it.

5.  Choose Profile from the View Selection menu.

6.  Expand the results list items and look for the highest weight to find the methods that are spending the most time in your host app code.

Note

Option-click the disclosure triangle to automatically disclose your app’s symbols.

The time a thread spends running is represented by the collection of blue and orange areas in the timeline track. If a frame interval has little blocked time, it indicates CPU overutilization. To resolve the issue, focus your optimization efforts on improving slow-running code. Because the long-running methods are in your host app, you can easily determine whether — and how — you can optimize them to run faster.

### Check CPU thread prioritization

Other processes can preempt your app if you misconfigure thread priority. To consider these kinds of thread-related pipelining issues, check the System Load track.

The orange spikes in the System Load track indicate that runnable threads outnumbered the CPU cores available to process them. The green areas indicate the opposite — the healthy situation where enough CPU cores were available for processing. To deal with the problematic orange situations, you can use fewer threads and increase the priority of your app’s threads.

To confirm whether low thread-priority is affecting your app’s frame rate, follow these steps:

1.  Observe long-running display instances.

2.  Visually confirm there are a number of skipped frames. For an app that uses a 60 fps frame interval, you can find that vertical synchronizations don’t align with display.

3.  Select the System Load track.

4.  Select your app’s rendering thread in the bottom detail area.

5.  Move the inspection time around the identified performance anomaly in the timeline area, and observe the rendering thread’s state and priority at the inspection time in the bottom detail area.

In the above screenshot, the Preempted thread state indicates that other Runnable and Running threads starved the rendering thread of processing. Low thread-priority is an example of how misconfigured host app code relates to low frame rate.

A priority of 45 is recommended for rendering threads. To set your thread’s priority, call `pthread_attr_setschedparam(_:_:)` before creating your thread with `pthread_create(_:_:_:_:)`. For more information on thread priorities, see Tune CPU job scheduling for Apple silicon games. For more information on `pthread_create` and `pthread_attr_setschedparam`, see Reading UNIX Manual Pages.

### Check CPU-GPU overlap

In addition to shader core and CPU utilization, more subtle causes of low frame rate involve CPU-GPU pipelining. In this context, *pipelining* refers to how well your app coordinates the efforts of the CPU and the GPU while maintaining a consistent frame rate. By minimizing the amount of time the CPU and the GPU wait for each other, you maximize the amount of work each unit does in parallel. That’s called *CPU-GPU overlap*.

For example, if you have a rendering algorithm that needs the result from a compute pass before encoding rendering commands, Metal provides indirect command buffers (ICBs) to increase overlap. By generating rendering commands on the GPU using ICBs, you can avoid having the CPU wait for the compute results. For more information, see Encoding Indirect Command Buffers on the GPU.

## See Also

### Graphics

Analyzing the memory usage of your Metal app

Keep your app alive in the background by managing its memory footprint.

