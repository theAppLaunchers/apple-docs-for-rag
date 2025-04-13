

- Kernel
- Kernel Functions
-  vDSP_biquadm_CreateSetup 

Function

# vDSP_biquadm_CreateSetup

Builds a data structure that contains precalculated data for use by a single-precision, multichannel cascaded biquadratic filter function.

macOS 10.9+

``` source
vDSP_biquadm_Setup vDSP_biquadm_CreateSetup(const double *__coeffs, vDSP_Length __M, vDSP_Length __N);
```

## Parameters 

`__Coefficients`  

The input array that contains the double-precision filter coefficients. The number of elements in the coefficients array must be `5 * __M * __N`.

`__M`  

The number of sections in the biquad filter.

`__N `  

The number of input-output channels.

## Return Value

A pointer to an allocated and initialized biquadratic filter object.

## Discussion

This function constructs and returns a biquadratic filter object from the coefficients that you specify. This function initializes the internal state of the setup object with all delay elements set to zero.

You define the `__Coefficients` array as a series of sections with each containing a set of five coefficients for each channel. Specify the order of the coefficients as three feedforward coefficients followed by two feedback coefficients.

The following code shows an example of creating a biquad setup object that contains two sections:

let section0 = (b0: 0.984764420,
                b1: -1.969528840,
                b2: 0.984764420,
                a1: -1.969331359,
                a2: 0.969726321)

let section1 = (b0: 0.984764420,
                b1: -1.969528840,
                b2: 0.984764420,
                a1: -1.955243388,
                a2: 0.969726321)

let sectionCount = vDSP_Length(2)
let channelCount = vDSP_Length(1)

let setup = vDSP_biquadm_CreateSetup([
    section0.b0, section0.b1, section0.b2, section0.a1, section0.a2,
    section1.b0, section1.b1, section1.b2, section1.a1, section1.a2
],
                                     sectionCount,
                                     channelCount)

This function allocates memory for its own use. You must call the vDSP_biquadm_DestroySetup function to free the allocated memory.

