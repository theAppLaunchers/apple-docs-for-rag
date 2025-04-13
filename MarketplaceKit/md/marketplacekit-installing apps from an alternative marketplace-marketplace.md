

- MarketplaceKit
-  Installing apps from an alternative marketplace 

Article

# Installing apps from an alternative marketplace

Manage the installation of apps that developers distribute from your marketplace app.

## Overview

To install apps that others distribute on your marketplace, call the AppLibrary installation functions. The system enforces that calls displaying the install sheet need to source from the callback of an ActionButton. This ensures that app installation occurs as the result of a person’s interaction with your marketplace app.

In processing the request, the system retrieves a license from your web server. Provide the license by implementing the App License Delivery SDK on a Swift server with an endpoint that the device’s operating system discovers by looking up a standard URL scheme.

If your marketplace requires authentication to download apps — for example, a purchase or log in — implement an authentication service that the device can query to decorate the headers of its communication with your endpoints. To set the header, and handle any network failures, provide a MarketplaceExtension in your app and implement its callbacks.

When the system receives a license, it requests that licensed app from your web server. Publish two endpoints that field requests for apps, including restore requests for new apps, and update requests. Using MarketplaceKit, handle any errors that might occur as the system communicates with your server, and provide people with visual status during app management tasks that might be long-running, such as installing an app.

## Define the request header

Bundle an extension with your marketplace to define authorization headers for requests to your server. Implement the MarketplaceExtension method additionalHeaders(for:account:).

The system calls your implementation of `additionalHeaders` to add custom information that you choose in each communication it makes with your web server. MarketplaceKit doesn’t require a specific authentication method for the installation of an alternative marketplace’s apps. You can use OAuth 2.0 or add custom information to associate the communication with the person signed in, or the person’s unique device. This effectively authorizes the system to act on the person’s behalf on subsequent calls to your web server for app licenses or alternative distribution packages.

If an access token or subscription expires, return an HTTP failure code from your marketplace server. The system calls your MarketplaceExtension method requestFailed(with:) implementation to correct the issue. If the failure results from:

- An expired subscription, set a flag to present an e-commerce flow within your alternative marketplace app.

- An invalid access token, reauthenticate the person according to Reauthenticate a person in your marketplace app or extension.

## Request installation from an alternative app marketplace

Your app requests app installation using MarketplaceKit API. The system enforces that installation requests source from a person’s interaction with your app’s UI. In other words, your app can install another app only when a person requests it by tapping a button. MarketplaceKit provides the ActionButton class for this purpose.

The following code defines an action button that presents the app install sheet for an app identified by the argument AppleItemID. The code takes a `confirmInstall` closure, and confirms the installation with an install verification token and authentication context.

```
class ViewController: UIViewController {

override func viewDidLoad() {
    super.viewDidLoad()

    // Describe the app to install. 
    let installMetadata = InstallMetadata( 
        account: "Test", 
        appleItemID: 6476788646, 
        alternativeDistributionPackage: URL(
            string: "https://example.com/packages/6476788646/version/1")!, 
        isUpdate: false)

    // Define the app's landing page.  
    installMetadata.appShareURL = URL(
        string: "https://example.com/apps/6476788646")!

    // Pass the app info to an Install button.
    let button = ActionButton(
        action: .install(
            InstallConfiguration(
                install: installMetadata, 
                confirmInstall: {
                    // Perform e-commerce, if needed.
                    return .confirmed(
                        installVerificationToken: installVerificationToken, 
                           authenticationContext: myLAContext
                    )
                }
            )
        )
    )    

    // Configure the button. 
    button.addTarget(self, action: #selector(installAction), for: .touchUpInside)
    button.label = "Install"
    button.fontSize = 18
    button.tintColor = .white
    button.backgroundColor = .systemBlue
    button.size = CGSize(width: 200, height: 75)
    button.cornerRadius = 15
    button.isEnabled = true
    button.center = self.view.center
    self.view.addSubview(button)
```

If an app requires a purchase before installation, modify the `confirmInstall` closure to present a custom UI and external purchase flow that you implement in your app.

## Retrieve a license for the app from your web server

If your website doesn’t require authentication or the system is already successfully authorized to act on behalf of the page visitor, the system requests an app license from your web server. To process license requests, your web server implements an endpoint that serves generated licenses by using App License Delivery SDK.

## Serve a restore request

When your server responds with a license, the system then requests the app. To determine the endpoint to call, the system checks your `marketplace-kit` configuration file at the following relative URL:

```
/.well-known/marketplace-kit
```

Inside the file, define an endpoint to handle `restore` requests that the system makes to retrieve a specific app version:

```
"restore": "/PATH",
```

The system calls your restore endpoint with the following example POST:

```
{ 
    "apps": [
        { "appleItemId": "",
        "appleVersionId" : "" }
    ], 
    "platform" : "iOS" | "iPadOS",
    "osVersion" : "17.4"
}
```

The POST contains the following fields:

| Request field | description |
|----|----|
| `apps` | An array that contains an object for each app in the request. Each object in the array consists of an identifier (AppleItemID) and version (AppleVersionID) for the requested app. |
| `platform` | A string that identifies the platform of the installing device. |
| `osVersion` | A string that identifies the operating system version of the installing device. |

Compare the `platform` and `osVersion` fields to those contained within the app’s manifest to confirm that your alternative distribution package supports the device attempting to install it.

Important

Host the file using `https://` with a valid certificate. Don’t use redirects. For more information, see Supporting associated domains.

If downloading your app requires authorization and the system communicates with your endpoint without a valid access token, respond to the call with a status that requests reauthentication. An invalid access token can result from token expiration, or the restoration of a device from a backup. For more information, see Reauthenticating a person to manage apps.

Otherwise, send your app in response by supplying a URL in the `restores` element to the alternative distribution package for the requested app version:

```
{
    "restores": [
        { "appleItemId": "",
        "appleVersionId": "",
        "alternativeDistributionPackage": "/PATH",
        "installVerificationToken" : 
        "appShareURL" :  }
    ]
}
```

The `"restores"` array in the response contains an object for each requested app. Each object in the array contains the following fields:

| Response field | description |
|----|----|
| `appleItemId` | An identifier for a requested app. For more information, see AppleItemID. |
| `appleVersionId` | A version number that corresponds to the alternative distribution package. For more information, see AppleVersionID. |
| `alternativeDistributionPackage` | The app’s alternative distribution package in the assembled format described in Ingesting an alternative distribution package. This value has unique domain-matching requirements; for more information, see MarketplaceKitURIScheme. |
| `installVerificationToken` | A JSON web signature that MarketplaceKit requires for installations. For more information, see Supplying an install verification token. |
| `appShareURL` | An optional URL to a product landing page for the app on your marketplace website. The operating system populates the value in the Share Sheet when a person touches and holds the app’s icon on the Home Screen. |

## Serve an app update request

When a person requests an update to an installed app, or when Automatic Updates are on, the system sends a request similar to a restore. Add the `updates` endpoint in your server’s `marketplace-kit` configuration:

```
/.well-known/marketplace-kit
```

Set `url` to your server’s endpoint that handles app update requests:

```
"updates": {
    "url" : "/PATH",
    "pollingInterval": 24
```

The `pollingInterval` property is required. Set it to the minimum number of hours that the system waits to check for app updates. For example, if you set `pollingInterval` to `48`, the system calls your `updates` endpoint at most every 48 hours. In any case, the system calls your `updates` endpoint at most once every 24 hours.

The system sends an update POST to your endpoint, such as:

```
{
    "apps" : [
        {
            "appleItemId" : "",
            "appleVersionId" : "",
        },
        {
            "appleItemId" : "",
            "appleVersionId" : ""
        }
    ],
    "platform" : "iOS" | "iPadOS",
    "osVersion" : "17.0"    
}
```

The request contains the same fields as the POST for serving a restore request. For more information see the table above in Serve a restore request.

In response, your endpoint gives the alternative distribution package(s) in the `updates` element for apps matching the request criteria:

```
{
    "updates": [
        { "appleItemId": "",
        "appleVersionId": "",
        "alternativeDistributionPackage": "/PATH",
        "bundleVersion" : "1",
        "shortVersionString" : "1.0.14",
        "installVerificationToken" : 
        "appShareURL" :  }
    ]
}
```

The `"restores"` array in the response contains an object for each requested app. Each object in the array contains the following fields:

| Response field | description |
|----|----|
| `appleItemId` | An identifier for an app to update. For more information, see AppleItemID. |
| `appleVersionId` | A version number that corresponds to the alternative distribution package. For more information, see AppleVersionID. |
| `alternativeDistributionPackage` | The requested app’s alternative distribution package in the assembled format described in Ingesting an alternative distribution package. This value has unique domain-matching requirements; for more information, see MarketplaceKitURIScheme. |
| `bundleVersion` | The app’s bundle version. |
| `shortVersionString` | The app’s short version string. |
| `installVerificationToken` | A JSON web signature that MarketplaceKit requires for installations. For more information, see Supplying an install verification token. |
| `appShareURL` | An optional URL to a product landing page for the app on your marketplace website. The operating system populates the value in the Share Sheet when a person touches and holds the app’s icon on the Home Screen. |

## Indicate app unavailability

If a device requests an app that’s not available on your alternative marketplace, then your marketplace responds with a `"failures"` array that includes the unavailable apps:

```
{
    "restores": [ { ... } ],
    "updates": [ { ... } ],
    "failures": [
        { "appleItemId": "10737747186",
        "appleVersionId": "2000004563",
        "failure": { "code" : 404, "description": "App unavailable." } }
    ]
}
```

The `"failures"` array in the response contains an object for each requested app you fail to provide:

| failures field | description |
|----|----|
| `appleItemId` | An identifier for the app your server fails to provide. For more information, see AppleItemID. |
| `appleVersionId` | The version of the app your server fails to provide. For more information, see AppleVersionID. |

For a description of the `"restore"` and `"update"` fields, see Serve a restore request and Serve an app update request.

An app might be unavailable if the developer removes it from sale or if Apple sends an app take-down request. A device that’s restoring from a backup might be uninformed of the removal as it requests the app as part of the restore process.

To indicate the app isn’t available in the response, set `"code"` to `404`. If the request intiates from someone’s actions, such as tapping a darkened app icon while restoring their device from a backup, the system displays an informative prompt on the Home Screen that reads:

```
App Not Available 
"App 1" not available from Megabyte Mart.
```

## Override the MarketplaceKit endpoint for an app

To handle a specific app differently, modify the `marketplace-kit` file to add a configuration just for that app using the `"overridesByAppleItemID"` element. Inside, define an `"appleItemId"` element that contains a copy of the `marketplace-kit` configuration, differing in just the ways necessary to process the specific app.

```
{
    "overridesByAppleItemID":
    {
        "":
        {
            "restore": "/PATH",
            "updates":
            {
                "url": "/PATH",
                "pollingInterval": 
            },
            "license": "..."
        }
    }
    // The default configuration follows: 
    "restore": "/PATH",
    "updates":
    {
        "url": "/PATH",
        "pollingInterval": 
    },
    "license": "..." 
}
```

Add the `"overridesByAppleItemID"` element to the bottom of your `marketplace-kit` configuration file.

You can override the `marketplace-kit` endpoint for many reasons. For example, to route requests for a specific app on your marketplace to a different endpoint for processing.

## Show progress for app downloads

To provide a responsive installation experience, give visual feedback while installation is in progress. Display your own custom UI according to the progress object to provide visual feedback on the state of a given installation. Convey the progress in a way that works for your app; MarketplaceKit doesn’t provide a predetermined UI for progress.

## See Also

### Web services

Processing alternative app marketplace notifications

Manage the addition and removal of apps available on your alternative marketplace.

Ingesting an alternative distribution package

Process an available app version from App Store Connect and store it for download from your server.

Installing your app from your website

Manage the installation of an app that you develop and distribute through your website.

Supplying an install verification token

Support the installation of alternative distribution apps by creating signed JSON web tokens.

