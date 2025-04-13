

- Device Management
- SecurityInfoResponse
-  SecurityInfoResponse.SecurityInfo 

Device Management Command

# SecurityInfoResponse.SecurityInfo

A dictionary that contains security-related information.

iOS 4.0+iPadOS 4.0+macOS 10.7+tvOS 9.0+visionOS 1.1+watchOS 10.0+Device Assignment ServicesVPP License Management

``` source
object SecurityInfoResponse.SecurityInfo
```

## Properties

`AuthenticatedRootVolumeEnabled`

`boolean`

If `true`, the system booted using an Authenticated Root Volume. This value is available in macOS 11 and later.

`AutoLockTime`

`integer`

The number of seconds before a device goes to sleep after being idle. This value is only available on Shared iPad in iOS 17 and later.

`BootstrapTokenAllowedForAuthentication`

`string`

This value specifies whether the Secure Enclave Processor (SEP) supports and allows secure operations to use the Bootstrap Token. The value is automatically set for devices enrolled through the Device Enrollment Program (DEP). The user can also manually set this value in the RecoveryOS.

This value is available for Apple silicon in macOS 11 and later. Not available for user enrollment.

Possible Values: `allowed, disallowed, not supported`

`BootstrapTokenRequiredForKernelExtensionApproval`

`boolean`

If `true`, the device can accept a Bootstrap Token from the MDM server instead of prompting for user authentication prior to enabling kernel extensions. This includes enabling kexts through the `com.apple.syspolicy.kernel-extension-policy` payload or triggering the `RestartDevice` command with `RebuildKernelCache` set to `true`. This only applies when `BootstrapTokenAllowedForAuthentication` is `true` in the SecurityInfoResponse.SecurityInfo response.

This value is available for Apple silicon in macOS 11 and later. Not available for user enrollment.

`BootstrapTokenRequiredForSoftwareUpdate`

`boolean`

If `true`, the device can accept a Bootstrap Token from the MDM server instead of prompting for user authentication prior to installation. This only applies when `BootstrapTokenAllowedForAuthentication` is `true` in the SecurityInfoResponse.SecurityInfo response.

This value is available for Apple silicon in macOS 11 and later. Not available for user enrollment.

`FDE_Enabled`

`boolean`

If `true`, the device has enabled FileVault full disk encryption (FDE). This value is available in macOS 10.9 and later.

`FDE_HasInstitutionalRecoveryKey`

`boolean`

If `true`, FileVault FDE has an institutional recovery key. This value is available in macOS 10.9 and later.

`FDE_HasPersonalRecoveryKey`

`boolean`

If `true`, FileVault FDE has a personal recovery key. This value is available in macOS 10.9 and later.

`FDE_PersonalRecoveryKeyCMS`

`data`

If the FileVault personal recovery key has enabled escrow with a recovery key, this value contains the key. The certificate from the FDERecoveryKeyEscrow profile encrypts the key and wraps it as CMS data. This value is available in macOS 10.13 and later.

`FDE_PersonalRecoveryKeyDeviceKey`

`string`

If the FileVault personal recovery key has enabled escrow with a recovery key, this value is the device serial number. This is the value that displays to the user at the EFI login window as part of the help message if they enter their password incorrectly three times. The server also uses this value as an index when saving the device personal recovery key. This replaces the `recordNumber` that the server returned in the previous escrow mechanism. This value is available in macOS 10.13 and later.

`FirewallSettings`

SecurityInfoResponse.SecurityInfo.FirewallSettings

A dictionary that contains the firewall settings. This value is available in macOS 10.12 and later.

`FirmwarePasswordStatus`

SecurityInfoResponse.SecurityInfo.FirmwarePasswordStatus

A dictionary that contains the status of the EFI firmware password. This value is available in macOS 10.13 and later.

`HardwareEncryptionCaps`

`integer`

An integer that indicates the underlying hardware encryption capabilities of the device, which is one of the following values:

- `1`: Block-level encryption

- `2`: File-level encryption

- `3`: Both block-level and file-level encryption

Important

`IsRecoveryLockEnabled`

`boolean`

`ManagementStatus`

SecurityInfoResponse.SecurityInfo.ManagementStatus

`PasscodeCompliant`

`boolean`

`PasscodeCompliantWithProfiles`

`boolean`

`PasscodeLockGracePeriod`

`integer`

`PasscodeLockGracePeriodEnforced`

`integer`

`PasscodePresent`

`boolean`

`RemoteDesktopEnabled`

`boolean`

`SecureBoot`

SecurityInfoResponse.SecurityInfo.SecureBoot

`SystemIntegrityProtectionEnabled`

`boolean`

## Overview

Note

For a device to have data protection, `HardwareEncryptionCaps` must be `3` and `PasscodePresent` must `true`.

```
This value is available in iOS 4 and later, and tvOS 6 and later.
```

- IsRecoveryLockEnabled: If `true`, a password is required to enter recovery (see SetRecoveryLockCommand). Available in macOS 11.5 and later and only on Apple silicon devices.

- ManagementStatus: A dictionary that contains the status of the device’s MDM enrollment.

- PasscodeCompliant: If `true`, the user’s passcode is compliant with all requirements on the device, including Exchange and other accounts. This value is available in iOS 4 and later, and tvOS 6 and later.

- PasscodeCompliantWithProfiles: If `true`, the user’s passcode is compliant with requirements from profiles. This key doesn’t apply to User-Enrolled devices. This value is available in iOS 4 and later, and tvOS 6 and later.

- PasscodeLockGracePeriod: The user preference for the number of seconds before a locked screen requires the device passcode to unlock it. This value is only available for Shared iPad.

- PasscodeLockGracePeriodEnforced: The enforced value for the number of seconds before a locked screen requires the device passcode to unlock it. If a device has a passcode, changing `PasscodeLockGracePeriod` to a larger value doesn’t take effect until the user logs out or removes the passcode. This value is only available for Shared iPad.

- PasscodePresent: If `true`, the device has a passcode. This key doesn’t apply to User-Enrolled devices. This value is available in iOS 4 and later, and tvOS 6 and later.

- RemoteDesktopEnabled: If `true`, Remote Desktop is active on the device. This value is available in macOS 10.14.4 and later.

- SystemIntegrityProtectionEnabled: If `true`, System Integrity Protection (SIP) is active on the device. This value is available in macOS 10.12 and later.

- SecureBoot: A dictionary that contains the device’s Secure Boot settings. This value is available in macOS 10.15 and later.

## Topics

### Commands

object SecurityInfoResponse.SecurityInfo.FirewallSettings

A dictionary that contains the firewall settings.

object SecurityInfoResponse.SecurityInfo.FirmwarePasswordStatus

A dictionary that contains the status of the EFI firmware password.

object SecurityInfoResponse.SecurityInfo.ManagementStatus

A dictionary that contains the status of the device’s MDM enrollment.

object SecurityInfoResponse.SecurityInfo.SecureBoot

The response object for the secure boot settings.

object SecurityInfoResponse.SecurityInfo.SecureBoot.ReducedSecurity

A dictionary that contains the device’s reduced security settings.

## See Also

### Commands

object SecurityInfoResponse.ErrorChainItem

A dictionary that describes an error chain item.

