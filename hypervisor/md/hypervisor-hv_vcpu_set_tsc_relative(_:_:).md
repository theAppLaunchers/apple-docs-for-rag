

- Hypervisor
-  hv_vcpu_set_tsc_relative(\_:\_:) 

Function

# hv_vcpu_set_tsc_relative(\_:\_:)

Sets the offset of the guest timestamp-counter (TSC) relative to the Hypervisor’s TSC clock.

macOS 11.0+

``` source
func hv_vcpu_set_tsc_relative(
    _ vcpu: hv_vcpuid_t,
    _ offset: Int64
) -> hv_return_t
```

## Parameters 

`vcpu`  

The vCPU ID.

`offset`  

The relative offset value to apply to VMCS TSC-offset field.

## Return Value

`0` on success, or an hv_return_t error code.

## Discussion

Use this function to set the TSC-offset field in the VMCS so that the TSC value in the guest is the value of hv_tsc_clock() plus the given offset. The examples below show simple ways to calculate and set the TSC offset:

```
// initialization - set guest TSC to zero
int64_t vtsc_offset = - scale * hv_tsc_clock();
hv_vcpu_tsc_relative_offset(vcpu, vtsc_offset);

// compute the guest TSC at runtime from the host
uint64_t vtsc = scale * hv_tsc_clock() + vtsc_offset;

// guest writing to the IA32_TSC MSR
vtsc_offset = newTSCvalue - scale * hv_tsc_clock();
hv_vcpu_tsc_relative_offset(vcpu, vtsc_offset);

// guest writing to the IA32_TSC_ADJUST MSR
vtsc_offset += adjustment;
hv_vcpu_tsc_relative_offset(vcpu, vtsc_offset);

// at entry to inner hypervisor
hv_vcpu_tsc_relative_offset(vcpu, vtsc_offset);

// at entry to inner guest
hv_vcpu_tsc_relative_offset(vcpu, vtsc_offset + nested_offset);
```

## See Also

### Time-stamp counter functions

func hv_tsc_clock() -> UInt64

Returns the value of an abstract clock.

