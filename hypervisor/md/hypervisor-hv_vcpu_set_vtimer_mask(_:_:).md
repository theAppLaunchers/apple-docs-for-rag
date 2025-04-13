

- Hypervisor
-  hv_vcpu_set_vtimer_mask(\_:\_:) 

Function

# hv_vcpu_set_vtimer_mask(\_:\_:)

Sets or clears the virtual timer mask.

macOS 11.0+

``` source
func hv_vcpu_set_vtimer_mask(
    _ vcpu: hv_vcpu_t,
    _ vtimer_is_masked: Bool
) -> hv_return_t
```

## Parameters 

`vcpu`  

The ID of the vCPU instance.

`vtimer_is_masked`  

A Boolean value that indicates whether the vTimer has a mask set.

## Return Value

HV_SUCCESS if the operation was successful, otherwise an error code specified in hv_return_t.

## Discussion

After hv_vcpu_run(_:) returns with the exit reason `HV_EXIT_REASON_VTIMER_ACTIVATED`, the timer is masked automatically.

The vCPU won’t exit with this reason again until the mask is cleared even when calling hv_vcpu_run() with the vTimer interrupt in a pending state.

After receiving a HV_EXIT_REASON_VTIMER_ACTIVATED exit reason, the caller of `hv_vcpu_run`() needs to make the interrupts to the vTimer pending in the guest’s virtual interrupt controller. It also needs to detect when the guest has serviced this interrupt. For example, call this function when emulating a GIC when deactivating an interrupt whose ID matches that of the vTimer.

## See Also

### Timer functions

func hv_vcpu_get_vtimer_mask(hv_vcpu_t, UnsafeMutablePointer&lt;Bool>) -> hv_return_t

Gets the virtual timer mask.

func hv_vcpu_get_vtimer_offset(hv_vcpu_t, UnsafeMutablePointer&lt;UInt64>) -> hv_return_t

Returns the vTimer offset for the vCPU ID you specify.

func hv_vcpu_set_vtimer_offset(hv_vcpu_t, UInt64) -> hv_return_t

Sets the vTimer offset to a value that you provide.

