

- Bundle Resources
- Information Property List
-  OSBundleLibraries 

Property List Key

# OSBundleLibraries

The drivers that the system must load before your driver.

macOS 10.0+

## Details 

Type  

object

## Discussion

Use this key to specify other drivers that your driver depends on. For example, specify any drivers that contain symbols your driver creates or uses at startup. The system loads the drivers in this list before it attempts to load your driver. If the system fails to resolve the dependencies or load the corresponding libraries, the kernel doesn’t load your driver.

Each key in the dictionary is the bundle identifier of another driver, and the value is a string that contains the minimum version of the driver you require. Your driver must be compatible with the specified version of the other driver.

Don’t include this key for codeless kexts.

## See Also

### Kext dependencies

OSBundleCompatibleVersion

The backward limit of compatibility for the current driver.

