

- Metal
- Shader Libraries
- Metal Binary Archives
-  Manipulating Metal Binary Archives 

Article

# Manipulating Metal Binary Archives

Split precompiled binaries into individual slices, and combine them back together for targeted distribution.

## Overview

When distributing Metal binary archives, it’s useful to maintain individual slices for each GPU and only include binaries relevant for an individual targeted device. This allows for you to maintain the performance of a precompiled Metal binary while reducing it to a minimal size. Using this strategy in a build system allows you to distribute slim binaries over the air from a larger precompiled binary, or to ship a larger set of precompiled binaries for a platform that supports multiple GPUs.

The code examples in this article use the following files:

- `shaders.metallib,`a Metal library you compile from Xcode or the `metal` command-line tool. To learn how to compile from the command-line, see Building a Shader Library by Precompiling Source Files.

- `shaders.mtlp-json`, a Metal translator configuration script for use with the `shaders.metallib` library. To learn about creating configuration scripts, see Creating Binary Archives from Device-Built Pipeline State Objects or Compiling Binary Archives from a Custom Configuration Script.

### Extract Slices from an Existing Binary Archive

Unless the configuration script or command-line options specify otherwise, the Metal translator builds for all supported GPU architectures, including those your app may not even target. For example, building a complete binary archive for the shaders in Using a Render Pipeline to Render Primitives, and then inspecting it, shows both a large number of binary slices and a significant size increase.

```
% xcrun -sdk macosx metal-tt shaders.metallib shaders.mtlp-json -o shaders.binary.metallib
% xcrun metal-lipo -archs render.binary.metallib
applegpu_g15g applegpu_g13g applegpu_g14g applegpu_g15s applegpu_g14s applegpu_g14d applegpu_g13s applegpu_g13d amdgpu_gfx803 amdgpu_gfx802 amdgpu_gfx900 amdgpu_gfx904 amdgpu_gfx906 amdgpu_gfx1010_nsgc amdgpu_gfx1010 amdgpu_gfx1011 amdgpu_gfx1012 amdgpu_gfx1030 amdgpu_gfx1032 intelgpu_icl_1x6x8r7 intelgpu_icl_1x8x8r7 intelgpu_kbl_gt2r0 intelgpu_kbl_gt2r2 intelgpu_kbl_gt2r4 intelgpu_kbl_gt3r1 intelgpu_kbl_gt3r6
% du -h render.binary.metallib
696K    render.binary.metallib
% du -h render.metallib
8.0K    render.metallib

```

Use the `metal-lipo` command-line tool for inspection and manipulation of Metal libraries, similar to the `lipo` tool for LLVM-compiled libraries. The `metal-lipo` command-line tool uses the parameter `-thin` to extract one specific GPU binary slice by architecture name. You can also extract every slice from the archive in Terminal by using the `tr` and `xargs` commands.

```
% mkdir -p shaders/macos
% xcrun metal-lipo -archs render.binary.metallib | tr ' ' '\n' | xargs -n 1 -I{} xcrun metal-lipo -thin {} -output shaders/macos/{}.binary.metallib render.binary.metallib
% ls shaders/macos
amdgpu_gfx1010.binary.metallib       amdgpu_gfx802.binary.metallib        applegpu_g15s.binary.metallib        applegpu_g14s.binary.metallib        intelgpu_kbl_gt3r1.binary.metallib
amdgpu_gfx1010_nsgc.binary.metallib  amdgpu_gfx803.binary.metallib        applegpu_g13d.binary.metallib        intelgpu_icl_1x6x8r7.binary.metallib intelgpu_kbl_gt3r6.binary.metallib
amdgpu_gfx1011.binary.metallib       amdgpu_gfx900.binary.metallib        applegpu_g13g.binary.metallib        intelgpu_icl_1x8x8r7.binary.metallib
amdgpu_gfx1012.binary.metallib       amdgpu_gfx904.binary.metallib        applegpu_g13s.binary.metallib        intelgpu_kbl_gt2r0.binary.metallib
amdgpu_gfx1030.binary.metallib       amdgpu_gfx906.binary.metallib        applegpu_g14d.binary.metallib        intelgpu_kbl_gt2r2.binary.metallib
amdgpu_gfx1032.binary.metallib       applegpu_g15g.binary.metallib        applegpu_g14g.binary.metallib        intelgpu_kbl_gt2r4.binary.metallib
```

Note

Using `metal-lipo -thin` doesn’t remove the architectures from the original binary archive.

### Combine Individual Slices into a New Binary Archive

The `metal-lipo` command-line tool also has a `-create` flag that performs the opposite of thinning. It combines binary archives to create a Metal library that contains each individual binary slice. Using this approach, you can create three new binary archives from a full set of binary archives: one for Intel-based Mac computers, one for AMD GPUs in an expansion slot, and one for Apple silicon.

```
% mkdir -p shaders/macos/lib
% xcrun -sdk macosx metal-lipo $(ls shaders/macos/applegpu*) -create -output shaders/macos/lib/applegpu.binary.metallib
% xcrun -sdk macosx metal-lipo $(ls shaders/macos/intelgpu*) -create -output shaders/macos/lib/intelgpu.binary.metallib
% xcrun -sdk macosx metal-lipo $(ls shaders/macos/amdgpu*) -create -output shaders/macos/lib/amdgpu.binary.metallib
% du -h shaders/macos/lib/*
180K    shaders/macos/lib/amdgpu.binary.metallib
124K    shaders/macos/lib/applegpu.binary.metallib
396K    shaders/macos/lib/intelgpu.binary.metallib
```

Tip

The `metal-lipo` command-line tool only works for combining binaries that are part of the same pipelines. To combine multiple binaries for different pipelines into a single library, use the `metal-pack` command-line tool. For information on `metal-pack`, run the command `man metal-pack` in Terminal.

## See Also

### Working with Metal Binary Archives

Creating Binary Archives from Device-Built Pipeline State Objects

Write your Metal pipeline states to a binary archive at app runtime, and build binaries for any supported GPU.

Compiling Binary Archives from a Custom Configuration Script

Define how the Metal translator builds binary archives without precompiled binaries as a starting source.

