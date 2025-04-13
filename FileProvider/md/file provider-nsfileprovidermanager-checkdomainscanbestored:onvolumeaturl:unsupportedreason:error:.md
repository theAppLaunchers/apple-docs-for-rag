

- File Provider
- NSFileProviderManager
-  checkDomainsCanBeStored:onVolumeAtURL:unsupportedReason:error: 

Type Method

# checkDomainsCanBeStored:onVolumeAtURL:unsupportedReason:error:

Check if a URL is eligible for storing a domain.

macOS 15.0+

``` source
+ (BOOL) checkDomainsCanBeStored:(BOOL *) eligible 
                   onVolumeAtURL:(NSURL *) url 
               unsupportedReason:(NSFileProviderVolumeUnsupportedReason *) unsupportedReason 
                           error:(NSError * *) error;
```

## Discussion

This returns whether the check has been performed succesfully - NOT whether the drive is eligible.

If an error was encountered while checking, this method returns FALSE and an error describing the problem will be set.

The eligible parameter will contain the result of the check and indicate whether the volume can be used to store FP domains. Its value is only defined if the call returns YES.

The url can be any existing and accessible URL on the volume for which you want to assess eligibility. The checks are volume-wide and the exact location on the volume doesn’t impact them.

If a drive is eligible, unsupportedReason will be empty (0). Otherwise it will contain the list of identified conditions that currently prevent this drive from being used to store FP domains.

## See Also

### Working with external volumes

func stateDirectoryURL() throws -> URL

Returns a URL for a directory for storing state information for the domain.

protocol NSFileProviderExternalVolumeHandling

A protocol that defines the interface for handling external volumes.

