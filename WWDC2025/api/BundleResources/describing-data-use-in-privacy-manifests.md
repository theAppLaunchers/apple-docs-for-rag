*   [Bundle Resources](/documentation/bundleresources)
*   [Privacy manifest files](/documentation/bundleresources/privacy-manifest-files)
*   Describing data use in privacy manifests

Article

# Describing data use in privacy manifests

Declare the data collected by your app or by third-party SDKs.

## [Overview](/documentation/BundleResources/describing-data-use-in-privacy-manifests#overview)

Record the categories of data that your app or third-party SDK collects about the person using the app, and the reasons it collects the data. App developers can use Xcode to create a privacy report, summarizing the information about collected data in their app and the third-party SDKs the app links to.

Important

Third-party SDKs need to provide their own privacy manifest files that record the types of data they collect. Your app’s privacy manifest file doesn’t need to cover data collected by third-party SDKs that your app links to.

### [Describe the data your app or third-party SDK collects](/documentation/BundleResources/describing-data-use-in-privacy-manifests#Describe-the-data-your-app-or-third-party-SDK-collects)

For each type of data your app or third-party SDK collects, add a dictionary to the [`NSPrivacyCollectedDataTypes`](/documentation/bundleresources/app-privacy-configuration/nsprivacycollecteddatatypes) array in your privacy information file. Add the following keys to the dictionary.

[`NSPrivacyCollectedDataType`](/documentation/bundleresources/app-privacy-configuration/nsprivacycollecteddatatypes/nsprivacycollecteddatatype)

A string that identifies the type of data your app or third-party SDK collects. Choose the value from the list of data types below that matches the data your app or third-party SDK collects.

[`NSPrivacyCollectedDataTypeLinked`](/documentation/bundleresources/app-privacy-configuration/nsprivacycollecteddatatypes/nsprivacycollecteddatatypelinked)

A Boolean that indicates whether your app or third-party SDK links this data type to the user’s identity. For more information, see Data linked to the user in [App privacy details on the App Store](https://developer.apple.com/app-store/app-privacy-details/#linked-data).

[`NSPrivacyCollectedDataTypeTracking`](/documentation/bundleresources/app-privacy-configuration/nsprivacycollecteddatatypes/nsprivacycollecteddatatypetracking)

A Boolean that indicates whether your app or third-party SDK uses this data type to track.

[`NSPrivacyCollectedDataTypePurposes`](/documentation/bundleresources/app-privacy-configuration/nsprivacycollecteddatatypes/nsprivacycollecteddatatypepurposes)

An array of strings that lists the reasons your app or third-party SDK collects the data. Choose values from the list of purposes below that match the reasons your app or third-party SDK collects this data type.

Xcode won’t generate a privacy report correctly if you define your own collected data types for the `NSPrivacyCollectedDataType` key, or provide your own reasons for the `NSPrivacyCollectedDataTypePurposes` key. Use values listed in the documentation for the keys.

### [Create your app’s privacy report](/documentation/BundleResources/describing-data-use-in-privacy-manifests#Create-your-apps-privacy-report)

Xcode can create a privacy report by aggregating the privacy manifests from your app and the third-party SDKs it links to. Use the privacy report to better understand all of the data collected by your app and whether it tracks. Create the privacy report for your app by doing the following:

1.  Open your project in Xcode.
    
2.  Choose Product > Archive. Xcode creates the archive and reveals it in the organizer.
    
3.  Control-click the archive in the organizer and choose Generate Privacy Report.
    
4.  Choose a location to save the privacy report.
    
5.  Switch to Finder.
    
6.  Navigate to the location where you saved the privacy report, and double-click to open the report in Preview.
    

The privacy report is organized in a similar way to Privacy Nutrition Labels. Refer to this report when you provide your app’s privacy details in App Store Connect. For more information on providing your app’s privacy details, see [App privacy details on the App Store](https://developer.apple.com/app-store/app-privacy-details/).

## [See Also](/documentation/BundleResources/describing-data-use-in-privacy-manifests#see-also)

### [Essentials](/documentation/BundleResources/describing-data-use-in-privacy-manifests#Essentials)

[

Adding a privacy manifest to your app or third-party SDK](/documentation/bundleresources/adding-a-privacy-manifest-to-your-app-or-third-party-sdk)

Report the data you collect and the required reasons API you use in your app or third-party SDK.

[

Describing use of required reason API](/documentation/bundleresources/describing-use-of-required-reason-api)

Ensure your use of covered API is consistent with policy.

[`App Privacy Configuration`](/documentation/bundleresources/app-privacy-configuration)

A data structure that represents the root object in a privacy manifest file.