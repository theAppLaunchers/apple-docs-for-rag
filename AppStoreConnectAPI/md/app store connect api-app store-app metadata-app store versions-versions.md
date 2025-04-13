

- App Store Connect API
- App Store
- App Metadata
-  App Store Versions 

API Collection

# App Store Versions

Manage versions of your app that are available in App Store.

## Overview

The `appStoreVersions` resource represents the information related to an App Store version of your app. Using this resource, you can:

- Create, modify, or delete a version for your app.

- Read key details for your version, including its App Store state.

- Specify whether to release the version manually or automatically.

- Modify attributes such as your app’s copyright information.

For more information about versions, see Create a new version.

## Topics

### Getting App Store Versions

List All App Store Versions for an App

Get a list of all App Store versions of an app across all platforms.

Read App Store Version Information

Get information for a specific app store version.

### Getting App Store Version Experiments

List All Experiments for an App Store Version

Get a list of all experiments for an App Store version of an app across all platforms.

List All Experiments for an App Store Version v1

Get a list of all experiments for an App Store version of an app across all platforms.

Deprecated

### Creating and Modifying App Store Versions

Create an App Store Version

Add a new App Store version or platform to an app.

Modify an App Store Version

Update the app store version for a specific app.

Delete an App Store Version

Delete an app store version that is associated with an app.

### Attaching a Build to a Version

Read the Build Information of an App Store Version

Get the build that is attached to a specific App Store version.

Get the Build ID for an App Store Version

Get the ID of the build that is attached to a specific App Store version.

Modify the Build for an App Store Version

Change the build that is attached to a specific App Store version.

### Attaching a Default App Clip Experience to a Version

Get the Default App Clip Experience for an App Store Version

Get the default App Clip experience for an App Store version of your app.

Get the Default App Clip Experiences Resource ID for an App Store Version

Get the ID of an app’s related default App Clip experience.

Modify the Default App Clip Experience of an App Store Version

Update the relationship between an App Store version and a default App Clip experience.

### Reading Localization Information

List All App Store Version Localizations for an App Store Version

Get a list of localized, version-level information about an app, for all locales.

### Reading Release and Review Information

Read the App Store Version Submission Information of an App Store VersionDeprecated

Read the App Store Review Details Resource Information of an App Store Version

Get the details you provide to App Review so they can test your app.

Read the App Store Version Phased Release Information of an App Store Version

Read the phased release status and configuration for a version with phased release enabled.

### Reading Declarations

Read the Age Rating Declaration Information of an App Store Version

Get the age-related information declared for your app.

Deprecated

Read the Routing App Coverage Information of an App Store Version

Get the routing app coverage file that is associated with a specific App Store version

### Getting Customer Reviews

List All Customer Reviews for an App Store Version

Get a list of customer reviews for a specific version of your app.

### Getting Game Center app versions

Read Game Center app version information of an App Store version

Get the status of Game Center enablement for an App Store version.

### Reading Distribution Package Information

Read an App Store version’s alternative distribution package

Read the alternative distribution package for a specific App Store version.

### Objects and Data Types

object AppStoreVersionUpdateRequest

The request body you use to update an App Store Version.

object AgeRatingDeclaration

The data structure that represents an Age Rating Declarations resource.

object AgeRatingDeclarationWithoutIncludesResponse

object AppStoreVersion

The data structure that represent an App Store Versions resource.

object AppStoreVersionResponse

A response that contains a single App Store Versions resource.

object AppStoreVersionsResponse

A response that contains a list of App Store Version resources.

object AppStoreVersionCreateRequest

The request body you use to create an App Store Version.

object AppStoreVersionBuildLinkageRequest

The request body you use to attach a build to an App Store version.

object AppStoreVersionBuildLinkageResponse

A response body that contains the ID of a single related resource.

object AppStoreVersionAppClipDefaultExperienceLinkageRequest

The request body you use to attach a default App Clip experience to an App Store version.

object AppStoreVersionAppClipDefaultExperienceLinkageResponse

A response that contains the ID of a single related Default App Clip Experiences resource.

type AppStoreVersionState

String that represents the state of an app version in the App Store.

Deprecated

type AppVersionState

String that represents the state of an app version.

## See Also

### Managing App Information and Versions

App Infos

Manage or read the app metadata that applies across all versions of your app.

App Info Localizations

Manage the app metadata that is localized and appears on the App Store.

App Store Version Localizations

Create and maintain version-specific App Store metadata that’s localized.

Routing App Coverages

Manage geographic coverage files for apps that use location to provide routing information.

