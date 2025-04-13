

- Hypervisor
-  hv_vmx_vcpu_get_cap_write_vmcs(\_:\_:\_:\_:) 

Function

# hv_vmx_vcpu_get_cap_write_vmcs(\_:\_:\_:\_:)

Returns the allowed_0 and allowed_1 masks for a VMCS field of a vCPU.

macOS 11.0+

``` source
func hv_vmx_vcpu_get_cap_write_vmcs(
    _ vcpu: hv_vcpuid_t,
    _ field: UInt32,
    _ allowed_0: UnsafeMutablePointer,
    _ allowed_1: UnsafeMutablePointer
) -> hv_return_t
```

## Parameters 

`vcpu`  

The vCPU ID.

`field`  

The ID of the VMCS field for which to return capabilities.

`allowed_0`  

The pointer to the VMCS allowed_0 mask (written on success).

`allowed_1`  

The pointer to the VMCS allowed_1 mask (written on success).

## Return Value

HV_SUCCESS if the operation was successful, otherwise an error code specified in hv_return_t.

## Discussion

Returns the constraints imposed by the Hypervisor framework on the given VMCS field, in the form of `allowed_0` and `allowed_1` masks, that indicate what bit values may be set when writing the given VMCS field.

When writing to a VMCS field, the caller is allowed to set bits that are 0 in its `allowed_0` mask to 0, and bits that are 1 in its `allowed_1` mask to 1. This means:

- If allowed_0 = 0, allowed_1 = 0 -\> must be `NOT SET`.

- If allowed_0 = 0, allowed_1 = 1 -\> can be either `SET` or `NOT SET.`

- If allowed_0 = 1, allowed_1 = 0 -\> undefined (shouldn’t happen).

- If allowed_0 = 1, allowed_1 = 1 -\> must be `SET`.

Important

This function must be called by the owning thread.

## See Also

### Field management

Virtual Machine Control Structure (VMCS) Field IDs

Fields you can read or change using the Hypervisor framework’s read and write functions.

func hv_vmx_vcpu_read_vmcs(hv_vcpuid_t, UInt32, UnsafeMutablePointer&lt;UInt64>) -> hv_return_t

Returns, by reference, the current value of a virtual machine control structure (VMCS) field of a vCPU.

func hv_vmx_vcpu_write_vmcs(hv_vcpuid_t, UInt32, UInt64) -> hv_return_t

Sets the value of a virtual machine control structure (VMCS) field of a vCPU.

func hv_vmx_vcpu_set_apic_address(hv_vcpuid_t, hv_gpaddr_t) -> hv_return_t

Sets the address of the guest Advanced Programmable Interrupt Controller (APIC) for a vCPU in the guest physical address space of the VM.

Virtual Machine control structure (VMCS) Field IDs

Identify the fields of the virtual machine control structure.

