

- Metal
- GPU Devices and Work Submission
-  Detecting GPU Features and Metal Software Versions 

Article

# Detecting GPU Features and Metal Software Versions

Use the device object’s properties to determine how you perform tasks in Metal.

## Overview

GPUs don’t support a single common feature set. Instead, different GPUs support different capabilities. Newer, more powerful GPUs support more advanced features, letting you perform more complex tasks or perform the same task using a different technique the GPU can process more efficiently.

You need to determine which Metal features that a specific device object supports and use that information to choose your app’s behavior. For example, you might:

- Create multiple rendering or compute paths, and have your app dynamically choose the best option for each GPU.

- Restrict some features to specific GPUs or implement different levels of functionality. For example, in a game, you might remove shadows or reduce the complexity of shadows on older GPUs.

- Restrict your app so that it only runs when some GPUs are available; however, you should only use this option in extreme cases.

The version of Metal running on the system and the GPU you’re targeting determine which features are available. The MTLDevice object provides information about the software and hardware capabilities for a specific GPU. To see a summary of the features available in each family, see the Metal Feature Set Tables:

- Metal feature set tables (PDF)

- Metal feature set tables (Numbers)

A new version of Metal adds multiple features to device object at the same time. You should design your app around collections of common functionality. For example, on iOS, you might design two major rendering paths: one for current and future GPUs, and one for earlier GPUs.

### Determine GPU Feature Support

Metal organizes GPUs into four major families:

- Use the **Common** family to create apps that target a range of GPUs on multiple platforms.

- Use the **Apple** family to create apps that target Apple GPUs.

- Use the **Mac** family to create apps that target GPUs on macOS systems.

- Use the **Mac Catalyst** family when building an iPadOS app to run on macOS.

A GPU can be a member of more than one family; in most cases, a GPU supports one of the Common families and then one or more families specific to the build target.

More recent GPUs have higher version numbers and support larger feature sets. A higher GPU version is always a superset of an earlier version in the same GPU family. For details on the individual families and version numbers, see MTLGPUFamily.

The code below shows how to test whether a GPU supports a particular GPU family:

- Swift
- Objective-C

```
if #available(macOS 10.15, *) {
    if self.device.supportsFamily(.familyMac2) {
        // Enable features that require Mac family 2.
    }
}
else {
    // Fallback on earlier OS versions.
}
```

```
if (@available(macOS 10.15, *)) {
    if ([device supportsFamily:MTLGPUFamilyMac2])
    {
        // Enable features that require Mac family 2.
    }
}
else
{
    // Fallback on earlier OS versions.
}
```

### Determine Metal Version Availability

Each new Metal release adds new features for supported GPUs. In addition to checking for a GPU with the correct family, ensure that the features your app needs are also there. Use `available` statements to query whether the framework supports the features you need, as shown in the code below.

- Swift
- Objective-C

```
if #available(macOS 10.15, iOS 13, tvOS 13, *) {
     // Enable newer features.
}
else
{
    // Fallback on earlier OS versions.
}
```

```
if (@available(macOS 10.15, iOS 13, tvOS 13, *)) {
    // Enable newer features.
}
else
{
    // Fallback on earlier OS versions.
}
```

### Find Variations in a GPU Family

GPUs in the same family can vary in small ways. Some features aren’t supported uniformly across a family. Use the device object to test for the existence of these features using an API specific to each feature.

For example, Metal’s argument buffer feature has two tiers of support; the second tier is significantly better than the first. The code below shows how to test for tier 2 support:

- Swift
- Objective-C

```
if self.device.argumentBuffersSupport == .tier2
{
    // Enable tier 2 argument buffer support in renderer.
}
```

```
if (device.argumentBuffersSupport == MTLArgumentBuffersTier2)
{
    // Enable tier 2 argument buffer support in renderer.
}
```

### Discover Feature Availability in Earlier Operating Systems

If the GPU Family API isn’t available, test for features using *feature sets*. A feature set combines a Metal GPU family number with a software revision number. For example, to test for the first release of Metal that supported Apple family 4 GPUs, use MTLFeatureSet.iOS_GPUFamily4_v1, as shown here:

- Swift
- Objective-C

```
if self.device.supportsFeatureSet(.iOS_GPUFamily4_v1)
{
    // Enable family 4 rendering path.
}
```

```
if ([device supportsFeatureSet: MTLFeatureSet_iOS_GPUFamily4_v1])
{
    // Enable family 4 rendering path.
}
```

Metal added new feature set enumerations in new versions of Apple operating systems to support new software features and GPU families, so there are many different enumeration values representing different collections of features. If a GPU supports a feature set, it supports all features provided by earlier members of the same family, and all features in earlier software revisions. For example, MTLFeatureSet.iOS_GPUFamily4_v2 is version 2 of family 4, so it supports the same features as version 1, as well as all features supported by families 1, 2, and 3. You don’t need to test for those feature sets separately. Test for feature sets, from newest to oldest, until you successfully find a feature set that your app and the GPU both support.

## See Also

### Locating and Inspecting a GPU Device

Getting the Default GPU

Select the system’s default GPU device on which to run your Metal code.

func MTLCreateSystemDefaultDevice() -> (any MTLDevice)?

Returns the device instance Metal selects as the default.

protocol MTLDevice

The main Metal interface to a GPU that apps use to draw graphics and run computations in parallel.

Multi-GPU Systems

Locate and work with internal and external GPUs and their displays, video memory, and performance tradeoffs.

