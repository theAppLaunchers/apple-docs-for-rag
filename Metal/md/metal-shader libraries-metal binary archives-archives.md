

- Metal
- Shader Libraries
-  Metal Binary Archives 

# Metal Binary Archives

Distribute precompiled GPU-specific binaries as part of your app to avoid runtime compilation of Metal shaders.

## Overview

Metal supports the widest range of devices available by compiling to Metal intermediate representation (Metal IR), but this comes with a tradeoff. Metal IR libraries are smaller and more flexible, but your app still needs to compile shader functions for the device’s GPU at runtime. This isn’t always desirable; for example, you might want to precompile shaders you use for visual presentation while your app performs other loading or setup. When you’re ready to increase the size of your application bundle in exchange for avoiding runtime compilation, you can precompile shaders to *binary archives*. Binary archives are GPU-specific slices you ship individually or as part of a larger Metal library.

The Metal translator is part of the Metal compiler that produces binary archives from a combination of Metal IR and a JSON representation of your app’s pipeline state. You run the Metal translator with the `metal-tt` command in Terminal.

To get the most out of binary archives and the Metal translator, read the articles below in order, starting with Creating Binary Archives from Device-Built Pipeline State Objects.

## Topics

### Working with Metal Binary Archives

Creating Binary Archives from Device-Built Pipeline State Objects

Write your Metal pipeline states to a binary archive at app runtime, and build binaries for any supported GPU.

Manipulating Metal Binary Archives

Split precompiled binaries into individual slices, and combine them back together for targeted distribution.

Compiling Binary Archives from a Custom Configuration Script

Define how the Metal translator builds binary archives without precompiled binaries as a starting source.

## See Also

### Shader Compilation

Metal Libraries

Compile and manage Metal libraries from the command line.

Metal Dynamic Libraries

Create a single Metal library containing reusable code to reduce library size and avoid repeated shader compilation at runtime.

