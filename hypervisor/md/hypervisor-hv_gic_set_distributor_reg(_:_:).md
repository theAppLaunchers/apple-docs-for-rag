

- Hypervisor
-  hv_gic_set_distributor_reg(\_:\_:) 

Function

# hv_gic_set_distributor_reg(\_:\_:)

Writes the provided value to a generic interrupt controller (GIC) distributor register you specify.

macOS 15.0+

``` source
func hv_gic_set_distributor_reg(
    _ reg: hv_gic_distributor_reg_t,
    _ value: UInt64
) -> hv_return_t
```

## Parameters 

`reg`  

The enumeration value that represents the distributor register.

`value`  

The distributor register value to be write.

## Return Value

HV_SUCCESS on success; otherwise, an error code.

## Discussion

GIC distributor register enumeration values are equal to the device register offsets that the ARM GIC v3 specification defines. Alternatively, the client can use the offset while looping through large register arrays.

## See Also

### Getting and setting registers

func hv_gic_get_distributor_reg(hv_gic_distributor_reg_t, UnsafeMutablePointer&lt;UInt64>) -> hv_return_t

Reads a generic interrupt controller (GIC) distributor register.

func hv_gic_get_msi_reg(hv_gic_msi_reg_t, UnsafeMutablePointer&lt;UInt64>) -> hv_return_t

Reads a generic interrupt controller (GIC) distributor message signaled interrupt (MSI) register.

func hv_gic_get_icc_reg(hv_vcpu_t, hv_gic_icc_reg_t, UnsafeMutablePointer&lt;UInt64>) -> hv_return_t

Reads a generic interrupt controller’s ICC CPU system register.

func hv_gic_get_ich_reg(hv_vcpu_t, hv_gic_ich_reg_t, UnsafeMutablePointer&lt;UInt64>) -> hv_return_t

Reads a generic interrupt controller’s (GIC) ICH virtualization control system register.

func hv_gic_get_icv_reg(hv_vcpu_t, hv_gic_icv_reg_t, UnsafeMutablePointer&lt;UInt64>) -> hv_return_t

Writes a generic interrupt controller’s (GIC) ICV system register.

func hv_gic_get_redistributor_reg(hv_vcpu_t, hv_gic_redistributor_reg_t, UnsafeMutablePointer&lt;UInt64>) -> hv_return_t

Read a generic interrupt controller (GIC) redistributor register.

func hv_gic_set_icc_reg(hv_vcpu_t, hv_gic_icc_reg_t, UInt64) -> hv_return_t

Writes to a generic interrupt controller (GIC) ICC cpu system register.

func hv_gic_set_ich_reg(hv_vcpu_t, hv_gic_ich_reg_t, UInt64) -> hv_return_t

Writes to a generic interrupt controller (GIC) ICH virtualization control system register.

func hv_gic_set_icv_reg(hv_vcpu_t, hv_gic_icv_reg_t, UInt64) -> hv_return_t

Writes to a generic interrupt controller (GIC) ICV system register.

func hv_gic_set_msi_reg(hv_gic_msi_reg_t, UInt64) -> hv_return_t

Writes to a generic interrupt controller distributor message signaled interrupt (MSI) register.

func hv_gic_set_redistributor_reg(hv_vcpu_t, hv_gic_redistributor_reg_t, UInt64) -> hv_return_t

Writes to a GIC redistributor register.

