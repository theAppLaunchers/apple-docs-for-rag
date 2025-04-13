

- Bundle Resources
- Information Property List
-  ENDeveloperRegion 

Property List Key

# ENDeveloperRegion

A string that specifies the region that the app supports.

iOS 13.7+iPadOS 13.7+

## Details 

Type  

string

## Discussion

Important

This type is available in iOS 12.5, and in iOS 13.7 and later.

All ExposureNotification apps must specify the region for which they work by adding this key to the app’s `Info.plist` file. The value is a string that represents the app’s region. This value can be an ISO 3166-1 country code (e.g. “CA” for Canada), or the ISO 3166-1/3166-2 country code plus subdivision code (“US-CA” for California).

## See Also

### Exposure notification

ENAPIVersion

A number that specifies the version of the API to use.

