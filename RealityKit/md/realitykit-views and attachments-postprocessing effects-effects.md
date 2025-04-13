

- RealityKit
- Views and attachments
-  Postprocessing effects 

# Postprocessing effects

Create special rendering effects for your RealityKit scenes.

## Overview

In iOS 15 and later, and macOS 12 and later, you can apply postprocess effects to a RealityKit scene after RealityKit renders it, but before RealityKit displays it. If you register a postprocess callback function, RealityKit passes that function the complete, rendered frame so you can modify it before the viewer sees it. You can use any image processing or drawing APIs on the rendered frame but, as a practical matter, only APIs that execute on the GPU are fast enough to use every frame and maintain a good framerate.

Core Image, Metal kernal functions, Metal Performance Shaders, and SpriteKit all execute on the GPU and can be effectively used to implement postprocessing effects.

## Topics

### Core Image effects

Applying core image filters as a postprocess effect

Create special rendering effects for your RealityKit scenes using Core Image.

### Metal effects

Using Metal performance shaders to create custom postprocess effects

Leverage the Metal Performance Shaders framework to create special rendering effects for your RealityKit scenes.

Implementing Special Rendering Effects with RealityKit Postprocessing

Implement a variety of postprocessing techniques to alter RealityKit rendering.

Checking the pixel format of a postprocess effect’s output texture

Make sure your postprocess effect works on all devices.

Passing Structured Data to a Metal Compute Function

Send nontexture data from Swift to your Metal shaders using a shared header file.

Implementing postprocess effects using Metal compute functions

Create custom shaders to implement postprocess effects.

## See Also

### Postprocessing

struct PostProcessContext

An object the framework uses to pass data to a postprocess callback.

struct RenderCallbacks

A container that holds the view’s render callbacks.

