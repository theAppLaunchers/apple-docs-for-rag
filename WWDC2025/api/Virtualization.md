Framework

# Virtualization

Create virtual machines and run macOS and Linux-based operating systems.

macOS 11.0+

## [Overview](/documentation/Virtualization#overview)

The Virtualization framework provides high-level APIs for creating and managing virtual machines (VM) on Apple silicon and Intel-based Mac computers. Use this framework to boot and run macOS or Linux-based operating systems in custom environments that you define. The framework supports the [Virtual I/O Device (VIRTIO)](https://docs.oasis-open.org/virtio/virtio/v1.1/csprd01/virtio-v1.1-csprd01.html) specification, which defines standard interfaces for many device types, including network, socket, serial port, storage, entropy, and memory-balloon devices.

To set up a VM, configure a [`VZVirtualMachineConfiguration`](/documentation/virtualization/vzvirtualmachineconfiguration). If you’re creating a macOS guest also configure a [`VZMacPlatformConfiguration`](/documentation/virtualization/vzmacplatformconfiguration), and then add the devices you want to expose to the guest operating system. Then, create a [`VZVirtualMachineConfiguration`](/documentation/virtualization/vzvirtualmachineconfiguration) object with your configuration data, and use that VM object to start, pause, and resume the VM environment. To interact with the guest, you create a [`VZVirtualMachineView`](/documentation/virtualization/vzvirtualmachineview) with the [`VZVirtualMachine`](/documentation/virtualization/vzvirtualmachine) object to display and interact with the graphical content in a window.

## [Topics](/documentation/Virtualization#topics)

### [Essentials](/documentation/Virtualization#Essentials)

[

Adding the Virtualization Entitlement to Your Project](/documentation/virtualization/adding-the-virtualization-entitlement-to-your-project)

Configure your project to use the Virtualization framework.

[`com.apple.security.virtualization`](/documentation/BundleResources/Entitlements/com.apple.security.virtualization)

A Boolean value that indicates whether your app can use the Virtualization framework.

[

Using iCloud with macOS virtual machines](/documentation/virtualization/using-icloud-with-macos-virtual-machines)

Access iCloud from macOS guest virtual machines.

### [Virtual machine setup](/documentation/Virtualization#Virtual-machine-setup)

Configure and boot different guest operating systems.

[

Running macOS in a virtual machine on Apple silicon](/documentation/virtualization/running-macos-in-a-virtual-machine-on-apple-silicon)

Install and run macOS in a virtual machine using the Virtualization framework.

[

Running Linux in a Virtual Machine](/documentation/virtualization/running-linux-in-a-virtual-machine)

Run a Linux operating system on your Mac using the Virtualization framework.

[

Running GUI Linux in a virtual machine on a Mac](/documentation/virtualization/running-gui-linux-in-a-virtual-machine-on-a-mac)

Install and run GUI Linux in a virtual machine using the Virtualization framework.

[

Installing macOS on a Virtual Machine](/documentation/virtualization/installing-macos-on-a-virtual-machine)

Download a macOS restore image and install it in a new VM.

[

Creating and Running a Linux Virtual Machine](/documentation/virtualization/creating-and-running-a-linux-virtual-machine)

Design and run custom Linux guests on Apple silicon or Intel-based Mac Computers.

[

API Reference

Virtualize macOS on a Mac](/documentation/virtualization/virtualize-macos-on-a-mac)

Configure and run macOS guests on Apple silicon.

[

API Reference

Virtualize Linux on a Mac](/documentation/virtualization/virtualize-linux-on-a-mac)

Configure and run Linux guests on Apple silicon and Intel-based Mac computers.

[

Running Intel Binaries in Linux VMs with Rosetta](/documentation/virtualization/running-intel-binaries-in-linux-vms-with-rosetta)

Run x86\_64 Linux binaries under ARM Linux on Apple silicon.

[

Accelerating the performance of Rosetta](/documentation/virtualization/accelerating-the-performance-of-rosetta)

Improve Rosetta performance by adding support for the total store ordering (TSO) memory model to your Linux kernel.

### [Runtime](/documentation/Virtualization#Runtime)

View or control guest operating systems.

```swift
```swift
```swift
class VZVirtualMachine
```
```

An object that manages the overall state and configuration of your VM.
```
```swift
```swift
```swift
class VZVirtualMachineView
```
```

A view that allows user interaction with a VM.
```
```swift
```swift
```swift
class VZLinuxRosettaDirectoryShare
```
```

The Linux directory share for Rosetta.
```

### [Devices](/documentation/Virtualization#Devices)

Configure and connect devices to guest operating system instances.

[

API Reference

Audio](/documentation/virtualization/audio)

Configure audio devices that enable the guest operating system to perform audio playback and capture through the host’s audio devices.

[

API Reference

Graphics](/documentation/virtualization/graphics)

Configure a device for a guest to display its UI.

[

API Reference

Keyboards and pointing devices](/documentation/virtualization/keyboards-and-pointing-devices)

Configure devices that connect a mouse and keyboard to the guest system.

[

API Reference

Memory](/documentation/virtualization/memory)

Configure a memory balloon device to change the allocated memory for the guest system.

[

API Reference

Network](/documentation/virtualization/network)

Configure the devices that connect the guest system to the network.

[

API Reference

Randomization](/documentation/virtualization/randomization)

Configure a device for the guest system to use to generate random numbers.

[

API Reference

Serial ports](/documentation/virtualization/serial-ports)

Configure the serial devices that you use to communicate with the guest system.

[

API Reference

Shared directories](/documentation/virtualization/shared-directories)

Configure devices that share directories from the host into the guest system.

[

API Reference

Sockets](/documentation/virtualization/sockets)

Configure a device that manages port-based communication with the guest system.

[

API Reference

Storage](/documentation/virtualization/storage)

Configure the block-storage devices that represent the disks of the guest system.

[

API Reference

Consoles](/documentation/virtualization/consoles)

Configure a device that manages multiport console communication with the guest system.

[

API Reference

Clipboard sharing](/documentation/virtualization/clipboard-sharing)

Share the pasteboard between the host and guest system.

[

API Reference

USB Devices](/documentation/virtualization/usb-devices)

### [Enumerations](/documentation/Virtualization#Enumerations)

[

API Reference

Virtualization enumerations](/documentation/virtualization/virtualization-enumerations)

Control the caching modes, disk synchronization, and macOS auxiliary storage options of VMs.

### [Errors](/documentation/Virtualization#Errors)

```swift
```swift
```swift
```swift
let VZErrorDomain: String
```
```

The error domain for the Virtualization framework.
```
```swift
```swift
```swift
struct VZError
```
```

Errors that you might encounter when configuring or using a VM.
```
```