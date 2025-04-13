

- Quartz
- QCPlugInContext
-  cglContextObj() Deprecated

Instance Method

# cglContextObj()

Returns the destination CGL context to use for OpenGL rendering from within the execution method.

macOS 10.5–10.14Deprecated

``` source
func cglContextObj() -> CGLContextObj!
```

**Required**

Deprecated

Quartz Composer OpenGL API deprecated. (Define QC_SILENCE_GL_DEPRECATION to silence these warnings)

## Return Value

The destination CGL context.

## Discussion

To send commands to the OpenGL context:

- Use CGL macros instead of changing the current OpenGL context.

- Save and restore all OpenGL states except those defines by `GL_CURRENT_BIT` (vertex position, color, texture, and so on)

The following code shows how you’d use the method `CGLContextObj`:

```
// Set up using CGL macros.
#import 

- (BOOL) execute:(id)context
              atTime:(NSTimeInterval)time
             withArguments:(NSDictionary *)arguments
{
    // Set the CGL context to a local variable.
    CGLContextObj cgl_ctx = [context CGLContextObj];
    if(cgl_ctx == NULL)
    return NO;

    // Save and set OpenGL states.
    // Put your OpenGL code here.
    // Restore the OpenGL states.
    return YES;
}
```

You can retrieve the corresponding OpenGL pixel format by calling the function `CGLGetPixelFormat(_:)`.

