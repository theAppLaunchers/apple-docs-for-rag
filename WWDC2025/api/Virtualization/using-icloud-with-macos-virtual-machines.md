*   [Virtualization](/documentation/virtualization)
*   Using iCloud with macOS virtual machines

Article

# Using iCloud with macOS virtual machines

Access iCloud from macOS guest virtual machines.

## [Overview](/documentation/Virtualization/using-icloud-with-macos-virtual-machines#overview)

In macOS 15 and later, Virtualization supports access to iCloud accounts and resources when running macOS in a virtual machine (VM) on Apple silicon. When you create a VM in macOS 15 from a macOS 15 software image (an `.ipsw` file) using a [`VZMacHardwareModel`](/documentation/virtualization/vzmachardwaremodel) that you obtain from a [`VZMacOSRestoreImage`](/documentation/virtualization/vzmacosrestoreimage), Virtualization configures an identity for the VM that it derives from security information in the host’s Secure Enclave. Just as individual physical devices have distinct identities based on their Secure Enclaves, this identity is distinct from other VMs.

If someone moves a VM to a different Mac host and restarts it, the Virtualization framework automatically creates a new identity for the VM using the information from the Secure Enclave of the new Mac host. This identity change requires the person using the VM to reauthenticate to allow iCloud to restart syncing data to the VM.

Additionally, the Virtualization framework detects attempts to start multiple copies of the same VM simultaneously on the same Mac host. For example, when someone duplicates the files that make up a VM, the framework treats the copy of the VM as a clone of the first one. Starting a second clone while another clone is already running causes the Virtualization framework to automatically construct a new identity for the second clone. This preserves the integrity that different VMs have distinct identities, and requires that the person using the VM reauthenticate to use iCloud services.

### [Migrate data from older VMs to new VMs to access iCloud](/documentation/Virtualization/using-icloud-with-macos-virtual-machines#Migrate-data-from-older-VMs-to-new-VMs-to-access-iCloud)

iCloud support for VMs is available in macOS 15 and later. Be sure to let anyone using your virtualization-enabled app know that they need to migrate their data from older VMs to a macOS 15 or later VM. Using a macOS 15 installer to upgrade an older VM doesn’t provide support for iCloud.

### [Let people know where to look for additional iCloud support](/documentation/Virtualization/using-icloud-with-macos-virtual-machines#Let-people-know-where-to-look-for-additional-iCloud-support)

Adding information to your app about additional [iCloud support resources](https://support.apple.com/icloud), such as in your app’s help and tips, can help people using your app understand how to troubleshoot any issues when accessing iCloud from the VMs your app supports.

## [See Also](/documentation/Virtualization/using-icloud-with-macos-virtual-machines#see-also)

### [Related Documentation](/documentation/Virtualization/using-icloud-with-macos-virtual-machines#Related-Documentation)

[

TipKit](/documentation/TipKit)

Display tips that help people discover features in your app.

[`@MainActor class NSHelpManager`](/documentation/AppKit/NSHelpManager)

An object for displaying online help for an app.

### [Essentials](/documentation/Virtualization/using-icloud-with-macos-virtual-machines#Essentials)

[

Adding the Virtualization Entitlement to Your Project](/documentation/virtualization/adding-the-virtualization-entitlement-to-your-project)

Configure your project to use the Virtualization framework.

[`com.apple.security.virtualization`](/documentation/BundleResources/Entitlements/com.apple.security.virtualization)

A Boolean value that indicates whether your app can use the Virtualization framework.