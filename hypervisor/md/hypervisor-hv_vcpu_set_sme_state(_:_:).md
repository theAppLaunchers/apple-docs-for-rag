

- Hypervisor
-  hv_vcpu_set_sme_state(\_:\_:) 

Function

# hv_vcpu_set_sme_state(\_:\_:)

Sets the SME state consisting of the streaming Scalable Vector Extension (SVE) mode and ZA storage enable.

macOS 15.2+

``` source
func hv_vcpu_set_sme_state(
    _ vcpu: hv_vcpu_t,
    _ sme_state: UnsafePointer
) -> hv_return_t
```

## Parameters 

`vcpu`  

The ID of the vCPU instance.

`sme_state`  

The pointer to the SME state to set.

## Return Value

`HV_SUCCESS` on success, `HV_UNSUPPORTED` if SME is not supported on the platform, or an error code otherwise.

## Discussion

Important

You need to call this on the owning thread

For any entry or exit from streaming SVE mode, all Z vector and P predicate registers are set to zero, and all FPSR flags are set; you need to save this state if you need to retain it across streaming SVE mode transitions.

In streaming SVE mode, the system aliases the SIMD Q registers to the bottom `128` bits of the corresponding Z register, and any modification reflects on the Z register state.

If the optional `FEAT_SME_FA64` is implemented, the full SIMD instruction set is supported in streaming SVE mode; otherwise many legacy SIMD instructions are illegal in this mode.

When finished, disable streaming SVE mode and ZA storage; this serves as a power-down hint for SME-related hardware.

## See Also

### Functions

func hv_sme_config_get_max_svl_bytes(UnsafeMutablePointer&lt;Int>) -> hv_return_t

func hv_vcpu_apic_ctrl(hv_vcpuid_t, hv_apic_ctrl_t) -> hv_return_t

func hv_vcpu_apic_get_state(hv_vcpuid_t, UnsafeMutablePointer&lt;hv_apic_state_ext_t>) -> hv_return_t

func hv_vcpu_apic_lsc_enter_imm32(hv_vcpuid_t, UInt64, UInt32, UInt16, UInt32, UnsafeMutablePointer&lt;UInt64>?, UInt32) -> hv_return_t

func hv_vcpu_apic_lsc_enter_r32(hv_vcpuid_t, Bool, UInt64, UInt32, UInt16, hv_x86_reg_t, UnsafeMutablePointer&lt;UInt64>?, UInt32) -> hv_return_t

func hv_vcpu_apic_lsc_invalidate(hv_vcpuid_t) -> hv_return_t

func hv_vcpu_apic_put_state(hv_vcpuid_t, UnsafePointer&lt;hv_apic_state_ext_t>) -> hv_return_t

func hv_vcpu_apic_read(hv_vcpuid_t, UInt32, UnsafeMutablePointer&lt;UInt32>) -> hv_return_t

func hv_vcpu_apic_trigger_lvt(hv_vcpuid_t, hv_apic_lvt_flavor_t) -> hv_return_t

func hv_vcpu_apic_write(hv_vcpuid_t, UInt32, UInt32, UnsafeMutablePointer&lt;Bool>) -> hv_return_t

func hv_vcpu_exit_apic_access_read(hv_vcpuid_t, UnsafeMutablePointer&lt;UInt32>) -> hv_return_t

func hv_vcpu_exit_info(hv_vcpuid_t, UnsafeMutablePointer&lt;hv_vm_exitinfo_t>) -> hv_return_t

func hv_vcpu_exit_init_ap(hv_vcpuid_t, UnsafeMutablePointer&lt;Bool>, UInt32) -> hv_return_t

func hv_vcpu_exit_inject_excp(hv_vcpuid_t, UnsafeMutablePointer&lt;UInt8>, UnsafeMutablePointer&lt;Bool>, UnsafeMutablePointer&lt;UInt32>, UnsafeMutablePointer&lt;Bool>) -> hv_return_t

func hv_vcpu_exit_ioapic_eoi(hv_vcpuid_t, UnsafeMutablePointer&lt;UInt8>) -> hv_return_t

