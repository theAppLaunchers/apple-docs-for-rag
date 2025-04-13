

- Kernel
- Kernel Functions
-  vDSP_biquadm_SetTargetsDouble 

Function

# vDSP_biquadm_SetTargetsDouble

Sets target values for selected double-precision coefficients within a valid single-precision multichannel biquad IIR filter object.

macOS 10.11+

``` source
void vDSP_biquadm_SetTargetsDouble(vDSP_biquadm_Setup __setup, const double *__targets, float __interp_rate, float __interp_threshold, vDSP_Length __start_sec, vDSP_Length __start_chn, vDSP_Length __nsec, vDSP_Length __nchn);
```

## Parameters 

`__setup`  

The filter state object whose coefficients the function updates.

`__targets`  

An input array of double-precision target values to the function applies to selected coefficients.

`__rate`  

The rate constant that determines the size of increments to the coefficient values. The rate’s value must be greater than zero, otherwise the function’s behavior is undefined.

`__threshold`  

The threshold constant that determines how close a coefficient’s value must be to the target value before incrementation stops. The threshold’s value must be greater than zero, otherwise the function’s behavior is undefined.

`__start_sec`  

The first section to update in each channel.

`__start_chn`  

The first channel to update.

`__nsec`  

The number of sections to update in each channel.

`__nchn`  

The number of channels to update.

## Discussion

Provide the filter coefficient targets as double-precision values. The function increments each selected coefficient at each sample until the difference between its value and the target value is less than a specified threshold.

The last four parameters define which coefficients the function changes. The actual increment for each selected coefficient is a function of the `rate` constant and the difference between the target value and its initial value.

This function doesn’t allocate any additional memory.

