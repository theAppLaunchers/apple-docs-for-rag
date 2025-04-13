

- iAd
-  Setting Up Apple Search Ads Attribution 

Article

# Setting Up Apple Search Ads Attribution

Retrieve the attribution dictionary.

## Overview

Warning

After February 7, 2023, all requests made to the Apple Search Ads iAd Attribution API will return with a value of `"iad-attribution"` `=` `false`, or errors. See requestAttributionDetails(_:). Use the AdServices framework for current attribution integration with the Apple Search Ads Campaign Management API for devices using iOS 14.3 and later. Attribution isn’t available for downloads and redownloads from devices using iOS 14.2 or earlier.

The attribution dictionary contains attribution data that the system retrieves from user interaction with ads originating from Apple Search Ads campaigns.

To retrieve the attribution dictionary, use the following process in sequence.

### Retrieve the Attribution Dictionary

See the requestAttributionDetails(_:) method for the conditions to retrieve the dictionary that contains the attribution object. Next, check for Apple Search Ads attribution, such as at app first open or when registration is complete. Store the data locally, so you don’t need to repeat the method call.

```
// Check for iOS 10 attribution implementation
if ([[ADClient sharedClient] respondsToSelector:@selector(requestAttributionDetailsWithBlock:)]) { 
NSLog(@"iOS 10 call exists"); 
[[ADClient sharedClient] requestAttributionDetailsWithBlock:^(NSDictionary *attributionDetails, NSError *error) { 
// Look inside of the returned dictionary for all attribution details
NSLog(@"Attribution Dictionary: %@", attributionDetails); 
}];
}
```

The following example shows the dictionary structure you receive when you call requestAttributionDetails(_:):

```
{ 
"Version3.1" = { 
"iad-attribution" = true; 
"iad-org-name" = "org name";
"iad-org-id" = "40669820";
"iad-campaign-id" = "542370539"; 
"iad-campaign-name" = "campaign name"; 
"iad-purchase-date" = "2020-08-04T17:18:07Z" 
"iad-conversion-date" = "2020-08-04T17:18:07Z"; 
"iad-conversion-type" = "newdownload"; 
"iad-click-date" = "2020-08-04T17:17:00Z"; 
"iad-adgroup-id" = "542317095"; 
"iad-adgroup-name" = "adgroup name"; 
"iad-country-or-region" = "US"; 
"iad-keyword" = "keyword";
"iad-keyword-id" = "87675432";
"iad-keyword-matchtype" = "Broad";
"iad-ad-id" = "542317136";
}
```

### Download Attribution Data

After your app retrieves the attribution dictionary, upload the attribution data to your server using the method of your choice. Next, check for Apple Search Ads attribution. Store the data locally, so you don’t need to repeat the method call.

The following list contains the data dictionary keys and data types the iAd framework returns:

`iad-attribution`  
Boolean. `True` if the user clicks an Apple Search Ads impression up to 30 days before app download or redownload.

`iad-org-name`  
String. The organization that owns the campaign that the corresponding ad belongs to.

`iad-org-id`  
Integer. The `Id` of the organization that owns the campaign that the corresponding ad belongs to.

`iad-campaign-id`  
Integer. The `Id` of the campaign that the corresponding ad belongs to.

`iad-campaign-name`  
String. The name of the campaign that the corresponding ad belongs to.

`iad-click-date`  
Date/Time string. The date and time when the user clicks a corresponding ad.

`iad-purchase-date`  
Date/Time string. The date and time when the user first downloads your app. When the value of `iad-conversion-type` is `redownload`, this string represents the original purchase date. The purchase may or may not be associated with an Apple Search Ad.

`iad-conversion-date`  
Date/Time string. The date and time when the user downloads or redownloads your app by clicking an Apple Search Ad.

`iad-conversion-type`  
String. The type of conversion is either a `newdownload` or a `redownload`. A `redownload` is a download of an app by users who have previously installed your app.

`iad-adgroup-id`  
Integer. The `Id` of the ad group that the corresponding ad belongs to.

`iad-adgroup-name`  
String. The name of the ad group that the corresponding ad belongs to. See Ad Groups for more information.

`iad-country-or-region`  
String. The country or region associated with the campaign that results in an installation.

`iad-keyword`  
String. The keyword for the ad impression that led to the corresponding ad click.

`iad-keyword-id`  
String. The `Id` of the keyword for the ad impression.

`iad-keyword-matchtype`  
String. The match type of the keyword for the ad impression. Values are `Broad`, `Exact`, or search match. See Ad Groups for more information.

`iad-ad-id`  
Integer. The `Id` of the ad that the corresponding ad belongs to.

#### Report Attribution Data

Attribution data reporting helps you track performance of your campaigns. The following conditions apply to attribution data:

- All actions need to occur on the same device.

- Attribution only applies to users running iOS 10 or later, and who have downloaded or redownloaded the app within the previous 30 days.

- Apple Search Ads reports a download or a redownload as it happens, and up to 30 days later.

- A download or a redownload needs to occur from an App Store listing or an Apple Search Ads impression.

If you integrate your data-reporting strategy with a Mobile Measurement Provider (MMP), note the differences with MMP methodology when compared to Apple Search Ads:

- Apple Search Ads uses a 30-day attribution window. Third-party attribution may only allow an attribution window of 7 to 28 days.

- *App open latency* may be one of the reasons for a difference in the total installation count. App open latency is the delay between an installation and first launch. MMPs typically report an installation when the app opens for the first time. Apple Search Ads reports an installation when a download or redownload is complete.

- Third parties may not count redownloads as installations. Third parties don’t have visibility to know whether an app has been previously removed from a device. They may attribute a redownload as another app open latency or user engagement.

## See Also

### Essentials

iAd Changelog

Learn what’s new in the Apple Search Ads iAd Attribution API.

class ADClient

The parent class you use to request an attribution response.

Deprecated

