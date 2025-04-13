

- Accelerate
-  vsincosf(\_:\_:) 

Function

# vsincosf(\_:\_:)

Simultaneously computes sine and cosine of values in a vector.

iOS 6.0+iPadOS 6.0+Mac Catalyst 13.1+macOS 10.5+tvOSvisionOS 1.0+watchOS 2.0+

``` source
func vsincosf(
    _: vFloat,
    _: UnsafeMutablePointer
) -> vFloat
```

## Return Value

Returns a vector that contains the result of `cos(x)` for each value (`x`) in the source vector.

### Parameters:

parameter 1  
the source vector.

parameter 2  
the output vector.

## See Also

### Trigonometric Functions (from vfp.h)

func vsinf(vFloat) -> vFloat

For each vector element, calculates the sine.

func vcosf(vFloat) -> vFloat

For each vector element, calculates the cosine.

func vtanf(vFloat) -> vFloat

For each vector element, calculates the tangent.

func vasinf(vFloat) -> vFloat

For each vector element, calculates the arcsine. Results are in the interval \[-pi/2, pi/2\].

func vacosf(vFloat) -> vFloat

For each vector element, calculates the arccosine. Results are in the interval \[0, pi\].

func vatanf(vFloat) -> vFloat

For each vector element, calculates the arctangent. Results are in the interval \[-pi/2, pi/2\].

func vatan2f(vFloat, vFloat) -> vFloat

For each vector element, calculates the arctangent of `arg2`/`arg1` in the interval \[-pi,pi\] using the sign of both arguments to determine the quadrant of the computed value.

func vvcbrt(UnsafeMutablePointer&lt;Double>, UnsafePointer&lt;Double>, UnsafePointer&lt;Int32>)

Calculates the cube root for each element of a vector.

func vvcbrtf(UnsafeMutablePointer&lt;Float>, UnsafePointer&lt;Float>, UnsafePointer&lt;Int32>)

Calculates the cube root for each element of a vector.

