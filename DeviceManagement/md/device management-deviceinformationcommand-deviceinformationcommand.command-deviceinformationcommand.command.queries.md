

- Device Management
- DeviceInformationCommand
- DeviceInformationCommand.Command
-  DeviceInformationCommand.Command.Queries 

Device Management Command

# DeviceInformationCommand.Command.Queries

A query dictionary to get information about a device.

iOS 4.0+iPadOS 4.0+macOS 10.7+tvOS 9.0+visionOS 1.1+watchOS 10.0+Device Assignment ServicesVPP License Management

``` source
object DeviceInformationCommand.Command.Queries
```

## Properties

`AccessibilitySettings`

`string`

The key to get the current state of settable accessibility settings. Available in iOS 16 and later.

`ActiveManagedUsers`

`string`

The key to get an array of directory GUIDs for logged-in managed users. Requires the Device Information access right. Available in macOS 10.11 and later.

`AppAnalyticsEnabled`

`string`

The key to determine whether the device is sharing app analytics. Requires the Device Information access right. Available in iOS 4 and later, and macOS 10.7 and later.

`AutoSetupAdminAccounts`

`string`

The key to get the contents of DeviceInformationResponse.QueryResponses.AutoSetupAdminAccountsItem, which Setup Assistant automatically creates during enrollment. Requires the Device Information access right. Available in macOS 10.11 and later.

`AvailableDeviceCapacity`

`string`

The key to get the available capacity. Requires the Device Information access right. Available in iOS 4 and later, and macOS 10.7 and later.

`AwaitingConfiguration`

`string`

The key to determine whether the device is waiting for a DeviceConfiguredCommand to continue through Setup Assistant.

`BatteryLevel`

`string`

The key to get the battery level. Requires the Device Information access right. Available in iOS 5 and later.

`BluetoothMAC`

`string`

The key to get the Bluetooth media access control (MAC) address. Requires the Network Information access right.

`BuildVersion`

`string`

The key to get the operating system version. This value requires the Device Information access right.

`CellularTechnology`

`string`

The key to get the cellular technology type. Requires the Device Information access right. Available in iOS 4.2.6 and later.

`DataRoamingEnabled`

`string`

The key to determine whether the system enabled data roaming on the device. Requires the Network Information access right. Available in iOS 5 and later.

`DeviceCapacity`

`string`

The key to get the device’s total capacity. Requires the Device Information access right. Available in iOS 4 and later, and macOS 10.7 and later.

`DeviceID`

`string`

The key to get the device ID. Requires the Device Information access right. Available in tvOS 6 and later.

`DeviceName`

`string`

The key to get the device name. Requires the Device Information access right.

`DevicePropertiesAttestation`

`string`

The key to get an attestation of the device’s properties. Available in iOS 16 and later, macOS 14 and later, tvOS 16 and later, and watchOS 10 and later.

`DiagnosticSubmissionEnabled`

`string`

The key to determine whether the system enabled the diagnostic submission setting on the device. Requires the Device Information access right. Available in iOS 9.3 and later.

`EACSPreflight`

`string`

The key to determine whether the device can perform an EraseDeviceCommand using Erase All Content and Settings (EACS).

`EASDeviceIdentifier`

`string`

The key to get the device identifier for Exchange ActiveSync (EAS). Requires the Device Information access right. Available in iOS 7 and later.

`EstimatedResidentUsers`

`string`

The key to get the estimated number of users that can use this Shared iPad device, according to the available space of the device and each user’s quota. Requires the Device Information access right. Available in iOS 14 and later.

`EthernetMAC`

`string`

The key to get the primary Ethernet MAC address. Requires the Network Information access right. Available in macOS 10.7 and later.

`HasBattery`

`string`

The key to determine whether the device has an internal battery.

`HostName`

`string`

The key to get the hostname. Available in macOS 10.11 and later.

`IsActivationLockSupported`

`string`

The key to determine whether the device supports Activation Lock. Also see `IsActivationLockManageable` in SecurityInfoResponse.SecurityInfo.ManagementStatus. Available in macOS 10.9 and later.

`IsAppleSilicon`

`string`

The key to determine whether the device is a Mac with Apple silicon (for example, an Apple M1 chip). Available in macOS 12 and later.

`IsCloudBackupEnabled`

`string`

The key to determine whether the system enabled iCloud Backup on the device. Requires the Device Information access right. Available in iOS 7.1 and later.

`IsDeviceLocatorServiceEnabled`

`string`

The key to determine whether the system enabled a device locator service such as Find My on the device. Requires the Device Information access right. Available in iOS 7 and later.

`IsDoNotDisturbInEffect`

`string`

The key to determine whether the device is in Do Not Disturb (DND) mode. Requires the Device Information access right. Available in iOS 7 and later.

`IsMDMLostModeEnabled`

`string`

The key to determine whether the system enabled Managed Lost Mode on the device. Requires the Device Information access right. Available in iOS 9.3 and later.

`IsMultiUser`

`string`

The key to determine whether the device is in ephemeral multiuser mode. Requires the Device Information access right. Available in iOS 9.3 and later.

`IsNetworkTethered`

`string`

The key to determine whether the device is network-tethered. Requires the Network Information access right. Available in iOS 10.3 and later.

`IsRoaming`

`string`

The key to determine whether the device is roaming. Requires the Network Information access right. Available in iOS 4.2 and later.

`IsSupervised`

`string`

The key to determine whether the device is supervised. Requires the Device Information access right. Available in iOS 6 and later, macOS 10.15 and later, and tvOS 9 and later.

`iTunesStoreAccountHash`

`string`

The key to get a hash of the logged-in iTunes Store account. Also see GetVppUserRequest. This value requires the App Installation access right.

`iTunesStoreAccountIsActive`

`string`

The key to determine whether iTunes Store account is active. Requires the App Installation access right.

`LastCloudBackupDate`

`string`

The key to get the date of the most recent iCloud backup. Available in iOS 8 and later.

`LocalHostName`

`string`

The key to get the local hostname from Bonjour. Available in macOS 10.11 and later.

`ManagedAppleIDDefaultDomains`

`string`

The key to get the list of domains that the device suggests on the Shared iPad login screen. Available in iOS 16 and later.

`MaximumResidentUsers`

`string`

The key to get the maximum number of users that can use this Shared iPad device. In iOS 13.4 and later, this value is always `32`. Requires the Device Information access right. Available in iOS 9.3 and later.

`MDMOptions`

`string`

The key to get the contents of SettingsCommand.Command.Settings.MDMOptions.MDMOptions.

`Model`

`string`

The key to get the model. Requires the Device Information access right.

`ModelName`

`string`

The key to get the model name, such as *iPhone*. Requires the Device Information access right.

`ModemFirmwareVersion`

`string`

The key to get the modem firmware version. Requires the Device Information access right. Available in iOS 4 and later.

`ModelNumber`

`string`

The key to get the device’s hardware model number including region info, such as `MK1A3LL/A`. Requires the Device Information access right. Requires Apple silicon on macOS.

`OnlineAuthenticationGracePeriod`

`string`

The key to get the grace period for Shared iPad online authentication (in days). Available in iOS 16 and later.

`OrganizationInfo`

`string`

The key to get the contents of SettingsCommand.Command.Settings.OrganizationInfo.OrganizationInfo.

`OSUpdateSettings`

`string`

The key to get the contents of DeviceInformationResponse.QueryResponses.OSUpdateSettings. Requires the Device Information access right. Available in macOS 10.11 and later.

`OSVersion`

`string`

The key to get the operating system version. Requires the Device Information access right.

`PersonalHotspotEnabled`

`string`

The key to determine whether the system enabled Personal Hotspot on the device, which isn’t available for all carriers. Requires the Network Information access right. Available in iOS 7 and later.

`PINRequiredForDeviceLock`

`string`

The key to determine whether the DeviceLockCommand requires a PIN. Available in macOS 11 and later.

`PINRequiredForEraseDevice`

`string`

The key to determine whether the EraseDeviceCommand requires a PIN. Available in macOS 11 and later.

`ProductName`

`string`

The key to get the product name, such as *iPad8,12*. This value requires the Device Information access right.

`ProvisioningUDID`

`string`

The key to get the device identifier for provisioning profiles. This value differs from the UDID for Apple silicon. Available in macOS 11.3 and later.

`PushToken`

`string`

The key to get the push token for the current user-channel connection. The MDM server ignores this query for the device channel. Requires the Device Information access right. Available in iOS 9.3 and later, and macOS 10.12 and later.

`QuotaSize`

`string`

The key to get the quota size for each user on this Shared iPad device. Requires the Device Information access right. Available in iOS 13.4 and later.

`ResidentUsers`

`string`

The key to get the number of users currently on this Shared iPad device. Requires the Device Information access right. Available in iOS 13.4 and later.

`SerialNumber`

`string`

The key to get the serial number. Requires the Device Information access right.

`ServiceSubscriptions`

`string`

The key to get the contents of DeviceInformationResponse.QueryResponses.ServiceSubscriptionProperty. Requires the Network Information access right.

`SkipLanguageAndLocaleSetupForNewUsers`

`string`

The key to determine whether the system skips the language and country/region panes for new users on Shared iPad.

`SoftwareUpdateDeviceID`

`string`

The key to get the device identifier that you use to look up available OS updates through https://gdmf.apple.com/v2/pmv. Available in iOS 15 and later, and macOS 12 and later.

`SoftwareUpdateSettings`

`string`

The key to get the device settings that control which updates appear in the Software Update pane in Settings. Available in iOS 14.5 and later.

`SupplementalBuildVersion`

`string`

The key to get the build version for the currently installed rapid security response. If there’s no installed rapid security response, this value is the same as `BuildVersion`. Requires the Device Information access right.

`SupplementalOSVersionExtra`

`string`

The key to get the OS update rapid security response version letter, if a rapid security response update is installed. This value requires the Device Information access right.

`SupportsiOSAppInstalls`

`string`

The key to determine whether the macOS device supports iOS or iPadOS app installs. Available in macOS 11 and later.

`SupportsLOMDevice`

`string`

The key to determine whether the device can receive `PowerON`, `PowerOFF`, and `Reset` commands from a lights-out management (LOM) controller. Available in macOS 11 and later.

`SystemIntegrityProtectionEnabled`

`string`

The key to determine whether the system enabled System Integrity Protection on the device. This value requires the Device Information access right, and is available in macOS 10.12 and later.

`TemporarySessionOnly`

`string`

The key to determine whether the device only allows temporary sessions.

`TemporarySessionTimeout`

`string`

The key to get the timeout interval for the temporary session.

`TimeZone`

`string`

The key to get the current Internet Assigned Numbers Authority (IANA) time zone database name. Requires the Device Information access right. Available in iOS 14 and later, and tvOS 14 and later.

`UDID`

`string`

The key to get the unique identifier of the device.

`UserSessionTimeout`

`string`

The key to get the timeout interval for the user session.

`WiFiMAC`

`string`

The key to get the Wi-Fi MAC address. Requires the Network Information access right.

`CarrierSettingsVersion`

`string`

Deprecated 

The key to get the version of the carrier settings. Requires the Network Information access right. Available as of iOS 4 and deprecated in iOS 16.

`CurrentCarrierNetwork`

`string`

Deprecated 

The key to get the name of the current carrier network. Requires the Network Information access right. Available as of iOS 4 and deprecated in iOS 16.

`CurrentMCC`

`string`

Deprecated 

The key to get the current mobile country code (MCC). Requires the Network Information access right. It’s available as of iOS 4 and deprecated in iOS 16.

`CurrentMNC`

`string`

Deprecated 

The key to get the current mobile network code (MNC). Requires the Network Information access right. Available as of iOS 4 and deprecated in iOS 16.

`IMEI`

`string`

Deprecated 

The key to get the International Mobile Equipment Identity (IMEI) number. Requires the Device Information access right. Available as of iOS 4 and deprecated in iOS 16.

`ICCID`

`string`

Deprecated 

The key to get the integrated circuit card (ICC) identifier for the installed SIM card. Requires the Network Information access right. Available as of iOS 4 and deprecated in iOS 16.

`IsActivationLockEnabled`

`string`

Deprecated 

The key to determine whether the system enabled Activation Lock on the device. Requires the Device Information access right. Available as of iOS 7 and macOS 10.15, and deprecated in iOS 16 and macOS 13.

`MEID`

`string`

Deprecated 

The key to get the mobile equipment ID (MEID). Requires the Device Information access right. Available as of iOS 4 and deprecated in iOS 16.

`PhoneNumber`

`string`

Deprecated 

The key to get the raw phone number, without punctuation, and including the country code. Requires the Network Information access right. Available as of iOS 4 and deprecated in iOS 16.

`SIMCarrierNetwork`

`string`

Deprecated 

Apple no longer supports this query. Use `SubscriberCarrierNetwork` instead.

`SubscriberCarrierNetwork`

`string`

Deprecated 

The key to get the home carrier network. Requires the Network Information access right. Available as of iOS 5 and deprecated in iOS 16.

`SubscriberMCC`

`string`

Deprecated 

The key to get the home mobile country code. Requires the Network Information access right. Available as of iOS 4.2.6 and deprecated in iOS 16.

`SubscriberMNC`

`string`

Deprecated 

The key to get the home mobile network code. Requires the Network Information access right. Available as of iOS 4.2.6 and deprecated in iOS 16.

`VoiceRoamingEnabled`

`string`

Deprecated 

The key to determine whether the system enabled voice roaming on the device, which isn’t available for all carriers. Requires the Network Information access right. Available as of iOS 5 and deprecated in iOS 16.

