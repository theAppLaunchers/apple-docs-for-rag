

- Bundle Resources
- Information Property List
-  OSBundleCompatibleVersion 

Property List Key

# OSBundleCompatibleVersion

The backward limit of compatibility for the current driver.

macOS 10.0+

## Details 

Type  

string

## Discussion

Specify a previous version for the current driver, or the driver’s current version. Format this string the same way you format the value of the CFBundleVersion key. The combination of this value and the value in the CFBundleVersion key define the range of versions that offers the same level of compatibility. Dependent drivers use this information to determine if they are compatible with the driver. For example, if the driver’s current version is `10.0`, and you set the value of this key to `5.0`, a driver that depends on version `7.0` can successfully use the current driver.

When you change your driver in a way that breaks compatibility with your old code, update the value of this key. At that time, set the new value to the current version of your driver.

## See Also

### Kext dependencies

OSBundleLibraries

The drivers that the system must load before your driver.

