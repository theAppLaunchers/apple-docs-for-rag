

- Device Management
- ExtensibleSingleSignOnKerberos
-  ExtensibleSingleSignOnKerberos.ExtensionData 

Device Management Profile

# ExtensibleSingleSignOnKerberos.ExtensionData

The additional data to pass to the app extension.

iOS 13.0+iPadOS 13.0+macOS 10.15+visionOS 1.1+Device Assignment ServicesVPP License Management

``` source
object ExtensibleSingleSignOnKerberos.ExtensionData
```

## Properties

`allowAutomaticLogin`

`boolean`

If `false`, the system doesn’t allow saving passwords in the keychain.

Default: `true`

`allowPasswordChange`

`boolean`

If `false`, the system disables password changes. Available in macOS 10.15 and later.

Default: `true`

`allowPlatformSSOAuthFallback`

`boolean`

If `true` and `usePlatformSSOTGT` is `true`, the system allows the user to manually sign in. Available in macOS 13 and later.

Default: `true`

`cacheName`

`string`

Deprecated 

The GSS name of the Kerberos cache to use. Rarely set by an administrator.

`certificateUUID`

`string`

The PayloadUUID of a PKINIT certificate.

`credentialBundleIdACL`

`[string]`

A list of bundle IDs allowed to access the ticket-granting ticket (TGT).

`credentialUseMode`

`string`

This setting affects how other processes use the Kerberos Extension credential. Allowed values:

`always`  
The system always uses the credential if the SPN matches the Kerberos Extension `Hosts` array and the caller hasn’t specified another credential. However, the system won’t use the credential if the calling app isn’t in the `credentialBundleIDACL`.

`whenNotSpecified`  
The system only uses the extension credential if the SPN matches the Kerberos Extension `Hosts` array. However, the system won’t use the credential if the calling app isn’t in the `credentialBundleIDACL`.

`kerberosDefault`  
The system uses the default Kerberos processes to select credentials, and normally uses the default Kerberos credential. This is the same as turning off this capabiliity.

Available in macOS 11 and later.

Default: `always`

Possible Values: `always, whenNotSpecified, kerberosDefault`

`customUsernameLabel`

`string`

The custom user name label used in the Kerberos extension instead of “Username,” such as “Company ID”. Available in macOS 11 and later.

`delayUserSetup`

`boolean`

If `true`, the system doesn’t prompt the user to setup the Kerberos extension until either the administrator enables it with the `app-sso` tool or the system receives a Kerberos challenge. Available in macOS 11 and later.

Default: `false`

`domainRealmMapping`

ExtensibleSingleSignOnKerberos.ExtensionData.DomainRealmMapping

A custom domain-realm mapping for Kerberos. The system uses this when the DNS name of hosts doesn’t match the realm name. Most administrators don’t need to customize this.

`helpText`

`string`

The text to display to the user at the bottom of the Kerberos login window. You can also use this to display help information or disclaimer text. Available in iOS 14 and later, and macOS 11 and later.

`includeKerberosAppsInBundleIdACL`

`boolean`

If `true`, the Kerberos extension allows the standard Kerberos utilities including `TicketViewer` and `klist` to access and use the credential. This is in addition to `includeManagedAppsInBundleIdACL` or the `credentialBundleIdACL`, if you specify those values. Available in macOS 12 and later.

Default: `false`

`includeManagedAppsInBundleIdACL`

`boolean`

If `true`, the Kerberos extension allows only managed apps to access and use the credential. This is in addition to the `credentialBundleIDACL`, if you specify that value. Available in iOS 14 and later, and macOS 12 and later.

Default: `false`

`isDefaultRealm`

`boolean`

Specifies whether this is the default realm if there’s more than one Kerberos extension configuration.

Default: `false`

`monitorCredentialsCache`

`boolean`

If `false`, the system requests the credential on the next matching Kerberos challenge or network state change. If the credential is expired or missing, the system creates a new one. Available in macOS 11 and later.

Default: `true`

`principalName`

`string`

The principal (username) to use. You don’t need to include the realm.

`preferredKDCs`

`[string]`

The ordered list of perferred Key Distribution Centers (KDCs) to use for Kerberos traffic. Use this if the servers aren’t discoverable through DNS. If the servers are specified, then the system uses them for both connectivity checks and attempts to use them first for Kerberos traffic. If the servers don’t respond, the device falls back to DNS discovery. Format each entry the same as it would be in a `krb5.conf` file, for example:

- `adserver1.example.com`

- `tcp/adserver1.example.com:88`

- `kkdcp://kerberosproxy.example.com:443/kkdcp`

`pwChangeURL`

`string`

This URL will launch in the user’s default web browser when they initiate a password change. Available in macOS 10.15 and later.

`pwNotificationDays`

`integer`

The number of days prior to password expiration when the system sends a notification of password expiration to the user. Available in macOS 10.15 and later.

Default: `15`

`pwExpireOverride`

`integer`

Deprecated 

The number of days that the system allows using passwords on this domain. For most domains, this calculation is automatic. Available in macOS 10.15 and later.

`pwReqComplexity`

`boolean`

If `true`, the system requires passwords to meet Active Directory’s definition of “complex”. Available in macOS 10.15 and later.

Default: `false`

`pwReqHistory`

`integer`

The number of prior passwords that the system disallows reuse on this domain. Available in macOS 10.15 and later.

`pwReqLength`

`integer`

The minimum length of passwords on the domain.Available in macOS 10.15 and later.

`pwReqMinAge`

`integer`

The minimum age of passwords before the system allows changing them on this domain. Available in macOS 10.15 and later.

`pwReqText`

`string`

The text version of the domain’s password requirements. Only for use if `pwReqComplexity` or `pwReqLength` aren’t specified. Available in macOS 10.15 and later.

`replicationTime`

`integer`

Deprecated 

The time, in seconds, required to replicate changes in the Active Directory domain. The Kerberos extension uses this when checking password age after a change. Available in macOS 11 and later.

Default: `900`

`requireTLSForLDAP`

`boolean`

Require that LDAP connections use TLS. Available in macOS 11 and later.

Default: `false`

`requireUserPresence`

`boolean`

If `true`, the system requires the user to provide Touch ID, Face ID or their passcode to access the keychain entry.

Default: `false`

`performKerberosOnly`

`boolean`

If `true`, the Kerberos Extension handles Kerberos requests only. It doesn’t check for password expiration, show the password expiration in the menu, check for external password changes, perform password sync, or retrieve the home directory. Available in macOS 13 and later.

Default: `false`

`siteCode`

`string`

The name of the Active Directory site the Kerberos extension should use. Most administrators don’t need to modify this value, as the Kerberos extension can normally find the site automatically.

`syncLocalPassword`

`boolean`

If `false`, the system disables password sync. Note that this will not work if the user is logged in with a mobile account. Available in macOS 10.15 and later.

Default: `false`

`usePlatformSSOTGT`

`boolean`

If `true`, the system requires this configuration uses a TGT from Platform SSO instead of requesting a new one. Available in macOS 13 and later.

Default: `false`

`useSiteAutoDiscovery`

`boolean`

If `false`, the Kerberos extension doesn’t automatically use LDAP and DNS to determine its AD site name.

Default: `true`

`allowPassword`

`boolean`

If `true`, allow the user to switch the user interface to Password mode. Available in macOS 15 and later.

Default: `true`

`allowSmartCard`

`boolean`

If `true`, allow the user to switch the user interface to SmartCard mode. Available in macOS 15 and later.

Default: `true`

`identityIssuerAutoSelectFilter`

`string`

A string with wildcards that can use used to filter the list of available SmartCards by issuer. e.g “\*My CA2\*”. If there is one remaining, it will be auto-selected. If there more than one remaining, then the list is shorter. Available in macOS 15 and later.

`pwReqRTFData`

`data`

The RTF file formatted version of the domain’s password requirements. Only for use if `pwReqComplexity` or `pwReqLength` aren’t specified. Available in macOS 15 and later.

`startInSmartCardMode`

`boolean`

If `true`, the user interface will start in SmartCard mode. Available in macOS 15 and later.

Default: `false`

## Topics

### Profiles

object ExtensibleSingleSignOnKerberos.ExtensionData.DomainRealmMapping

The mapping of realms to their DNS suffixes.

