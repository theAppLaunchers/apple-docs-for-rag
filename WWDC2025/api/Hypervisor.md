Framework

# Hypervisor

Build virtualization solutions on top of a lightweight hypervisor, without third-party kernel extensions.

macOS 10.10+

## [Overview](/documentation/Hypervisor#overview)

Hypervisor provides C APIs so you can interact with virtualization technologies in user space, without writing kernel extensions (KEXTs). As a result, the apps you create using this framework are suitable for distribution on the [Mac App Store](https://www.appstore.com/).

Use this framework to create and control hardware-facilitated virtual machines and virtual processors (VMs and vCPUs) from your entitled, sandboxed, user-space process. Hypervisor abstracts virtual machines as processes, and virtual processors as threads.

### [Requirements](/documentation/Hypervisor#Requirements)

The Hypervisor framework has the following requirements:

Supported hardware

The Hypervisor framework requires hardware support to virtualize hardware resources. On Apple silicon, that includes the Virtualization Extensions. On Intel-based Mac computers, the framework supports machines with an Intel VT-x feature set that includes Extended Page Tables (EPT) and Unrestricted Mode.

At runtime, determine whether the Hypervisor APIs are available on a particular machine with the sysctl command, passing `kern.hv_support` as an argument.

Entitlements

All process must have the [`com.apple.security.hypervisor`](/documentation/BundleResources/Entitlements/com.apple.security.hypervisor) entitlement to use Hypervisor API.

### [Virtual Resource Mapping](/documentation/Hypervisor#Virtual-Resource-Mapping)

A guest is an operating system that runs on top of the virtual hardware. The operating system and processes that run the virtualized hardware are together called the host. Virtual hardware in the guest maps to specific resources on the host.

Each virtual machine corresponds to a process on the host. There can only be one virtual machine at a time per process; the virtual machine creates it with [`hv_vm_create(_:)`](/documentation/hypervisor/hv_vm_create\(_:\)).

Virtual CPUs (vCPUs) in a virtual machine map to POSIX threads. Create a new vCPU for the current thread with [`hv_vcpu_create(_:_:_:)`](/documentation/hypervisor/hv_vcpu_create\(_:_:_:\)). The vCPU runs when the thread calls [`hv_vcpu_run(_:)`](/documentation/hypervisor/hv_vcpu_run\(_:\)).

Hypervisor maps the physical memory in the guest to virtual memory of the host process. Create a new memory mapping with [`hv_vm_map(_:_:_:_:)`](/documentation/hypervisor/hv_vm_map\(_:_:_:_:\)). Access to memory outside the mapped range causes [`hv_vcpu_run(_:)`](/documentation/hypervisor/hv_vcpu_run\(_:\)) to exit. Emulate memory-mapped hardware by emulating the memory access on exit and re-enter the guest with [`hv_vcpu_run(_:)`](/documentation/hypervisor/hv_vcpu_run\(_:\)).

### [Example VM Life Cycle](/documentation/Hypervisor#Example-VM-Life-Cycle)

The following figure illustrates a simplified life cycle of creating and running a virtual machine with one or more virtual CPUs using the Hypervisor API.

![A flow diagram that represents the life cycle of a virtual machine.](https://docs-assets.developer.apple.com/published/bfee1ebf262231d5c3c11994026b7023/media-2916425%402x.png)

At the start of a task:

*   Create a VM with [`hv_vm_create(_:)`](/documentation/hypervisor/hv_vm_create\(_:\)).
    
*   Map a region in the virtual address space of the current task into the guest physical address space of the VM with [`hv_vm_map(_:_:_:_:)`](/documentation/hypervisor/hv_vm_map\(_:_:_:_:\)).
    
*   Create one or more POSIX threads with `pthread_create(_:_:_:_:)`.
    

In each thread:

*   Create a virtual CPU with [`hv_vcpu_create(_:_:_:)`](/documentation/hypervisor/hv_vcpu_create\(_:_:_:\)).
    
*   Call [`hv_vcpu_run(_:)`](/documentation/hypervisor/hv_vcpu_run\(_:\)) to run the vCPU.
    

When a thread receives an exit event:

*   Handle the event.
    
*   Re-enter the guest with [`hv_vcpu_run(_:)`](/documentation/hypervisor/hv_vcpu_run\(_:\)) or destroy the vCPU with [`hv_vcpu_destroy(_:)`](/documentation/hypervisor/hv_vcpu_destroy\(_:\)).
    

After all threads finish:

*   Unmap the memory region with [`hv_vm_unmap(_:_:)`](/documentation/hypervisor/hv_vm_unmap\(_:_:\)).
    
*   Destroy the VM with [`hv_vm_destroy()`](/documentation/hypervisor/hv_vm_destroy\(\)).
    

## [Topics](/documentation/Hypervisor#topics)

### [Platforms](/documentation/Hypervisor#Platforms)

[

API Reference

Apple Silicon](/documentation/hypervisor/apple-silicon)

Create and run virtual machines on Apple silicon.

[

API Reference

Intel-based Mac](/documentation/hypervisor/intel-based-mac)

Create and run virtual machines on Intel-based Mac computers.

### [Entitlements](/documentation/Hypervisor#Entitlements)

[`com.apple.security.hypervisor`](/documentation/BundleResources/Entitlements/com.apple.security.hypervisor)

A Boolean value that indicates whether the app creates and manages virtual machines.

[`com.apple.vm.hypervisor`](/documentation/BundleResources/Entitlements/com.apple.vm.hypervisor)

A Boolean value that indicates whether the app creates and manages virtual machines.

Deprecated

[`com.apple.vm.networking`](/documentation/BundleResources/Entitlements/com.apple.vm.networking)

A Boolean that indicates whether the app manages virtual network interfaces without escalating privileges to the root user.

[`com.apple.vm.device-access`](/documentation/BundleResources/Entitlements/com.apple.vm.device-access)

A Boolean value that indicates whether the app captures USB devices and uses them in the guest-operating system.

### [Reference](/documentation/Hypervisor#Reference)

[

API Reference

Hypervisor Structures](/documentation/hypervisor/hypervisor-structures)

[

API Reference

Hypervisor Constants](/documentation/hypervisor/hypervisor-constants)

[

API Reference

Hypervisor Functions](/documentation/hypervisor/hypervisor-functions)

[

API Reference

Hypervisor Data Types](/documentation/hypervisor/hypervisor-data-types)

### [Structures](/documentation/Hypervisor#Structures)

```swift
```swift
```swift
```swift
struct hv_ipa_granule_t
```
```
Beta
```
```

### [Variables](/documentation/Hypervisor#Variables)

```swift
```swift
```swift
```swift
var HV_IPA_GRANULE_16KB: hv_ipa_granule_t
```
```
```
```swift
```swift
```swift
var HV_IPA_GRANULE_4KB: hv_ipa_granule_t
```
```
```
```

### [Functions](/documentation/Hypervisor#Functions)

```swift
```swift
```swift
```swift
func hv_vm_config_get_default_ipa_granule(UnsafeMutablePointer<hv_ipa_granule_t>) -> hv_return_t
```
```
Beta
```
```swift
```swift
```swift
func hv_vm_config_get_ipa_granule(hv_vm_config_t, UnsafeMutablePointer<hv_ipa_granule_t>) -> hv_return_t
```
```
Beta
```
```swift
```swift
```swift
func hv_vm_config_set_ipa_granule(hv_vm_config_t, hv_ipa_granule_t) -> hv_return_t
```
```
Beta
```
```