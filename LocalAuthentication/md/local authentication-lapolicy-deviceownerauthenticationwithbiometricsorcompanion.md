

- Local Authentication
- LAPolicy
-  deviceOwnerAuthenticationWithBiometricsOrCompanion 

Type Property

# deviceOwnerAuthenticationWithBiometricsOrCompanion

Device owner will be authenticated by biometry or a companion device e.g. Watch, Mac, etc.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+

``` source
static var deviceOwnerAuthenticationWithBiometricsOrCompanion: LAPolicy { get }
```

## Discussion

Companion or biometric authentication is required. If no nearby paired companion device can be found, it behaves as LAPolicyDeviceOwnerAuthenticationWithBiometrics. Similarly, if biometry is unavailable it behaves as LAPolicyDeviceOwnerAuthenticationWithCompanion.

```
        When both mechanisms are available, user is asked to use biometry and companion authentication
        will run in parallel. Users should follow instructions on the companion device to authenticate.
```

