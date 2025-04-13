

- Kernel
- Kernel Functions
-  vDSP_vdbcon 

Function

# vDSP_vdbcon

Vector convert power or amplitude to decibels; single precision.

macOS 10.4+

``` source
void vDSP_vdbcon(const float *__A, vDSP_Stride __IA, const float *__B, float *__C, vDSP_Stride __IC, vDSP_Length __N, unsigned int __F);
```

## Parameters 

`__A`  

Single-precision real input vector

`__IA`  

Stride for `A`

`__B`  

Pointer to single-precision real input scalar: zero reference

`__C`  

Single-precision real output vector

`__IC`  

Stride for `C`

`__N`  

The number of elements to process

`__F`  

Power (0) or amplitude (1) flag

## Discussion

Performs the following operation. α is 20 if `F` is 1, or 10 if `F` is 0.

Converts inputs from vector `A` to their decibel equivalents, calculated in terms of power or amplitude according to flag `F`. As a relative reference point, the value of input scalar `*B` is considered to be zero decibels.

