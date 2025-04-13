

- MarketplaceKit
-  Creating an alternative app marketplace 

Article

# Creating an alternative app marketplace

Enable the distribution of other third-party apps from within your marketplace app.

## Overview

An *alternative app marketplace* is an iOS or iPadOS app from which someone can install other third-party apps. To create a marketplace, fill out a webform that outlines the qualifications. If approved, Apple enables a code-signing entitlement on your account to distribute your marketplace app on the web. Apple also provides you with a framework that facilitates the secure installation of apps that your marketplace distributes.

The architecture of an alternative marketplace includes an app, a webpage, from which people download your app, and a web server that stores app data it regularly receives from App Store Connect. When people download an app through your alternative app marketplace, your web server communicates with the device’s operating system directly by providing authentication services, app licenses, and app data to facilitate a secure app installation experience.

Important

If you’re interested in publishing an alternative app marketplace, review the criteria and submit a request using the web form here: Getting started as an alternative app marketplace in the European Union.

## Design a marketplace app

For an alternative app marketplace:

- Build a new app; only new bundle IDs qualify for marketplace provisioning.

- Add a code-signing configuration that the system requires to launch your app on devices. Marketplace apps require the com.apple.developer.marketplace.app-installation entitlement, which is a *managed entitlement*. To provision managed entitlements, see Provisioning with managed capabilities.

- Build with Xcode 15.3 or later, to accommodate MarketplaceKit framework availability. MarketplaceKit lets people install apps from an alternative marketplace on supported devices.

- Use APIs that vary from App Store apps. Specifically, use AdAttributionKit for ads, Background Assets to download large files, and a custom e-commerce solution.

Note

Don’t use StoreKit or the App Store’s In-App Purchase system, or On Demand Resources in your marketplace app.

## Set up your marketplace app for alternative distribution

To set up a marketplace, provide your web domain and a distribution key to App Store Connect, which facilitates the secure distribution of your app over the web.

The domain ensures that your marketplace app installs only from your website, and the *distribution key*:

- Regularly verifies the agreement, or *relationship*, you make with other developers that distribute their app on your marketplace.

- Signs a token that the system uses to verify each installation request of your app, or the apps that your marketplace distributes.

For more information, see Distributing your app from your website.

## Facilitate the life cycle of your apps

When a developer prepares to distribute their app on your marketplace, provide them a *marketplace token*. They upload the token in App Store Connect, which enables them to choose your marketplace as a distributor. The process of generating and exchanging the token occurs between just your app marketplace and the inquring app developer. For more information, see Creating keys and establishing alternative marketplace connections.

To handle other regular requests, implement a web server that:

- Manages available apps by communicating with App Store Connect. When an app that your maketplace distributes completes Notarization, App Store Connect sends the app to your server. App Store Connect also notifies your server when a developer removes an app from sale or when Apple issues an app take-down request. To receive notifications and perform the actions they require, see Processing alternative app marketplace notifications.

- Provides apps and app licenses to a person’s device. When a person attempts to download an app from your marketplace, the system requests a license from your server followed by the app itself. The system calls various endpoints that you publish on your server to process license requests and app requests. For more information, see Installing apps from an alternative marketplace.

Although you store apps on — and serve apps from — your web server, people install the apps only from within your alternative app marketplace app, not your website.

Tip

People can find an app on your alternative app marketplace using Spotlight search if you maintain a list of available apps and upload it to a location known to Apple. For more information, see Marketplace Search Configurations.

## Test the app during development

App marketplace development can occur anywhere in the world, as Xcode allows running a development-signed or Ad-Hoc signed app marketplace on Simulator and all supported physical devices running iOS or iPadOS 18.2 and later. Through the development build, apps that the marketplace distributes can also install and run.

However, workflows that involve submission to App Store Connect, such as beta testing your app through internal TestFlight and web distribution of your marketplace app, need to occur on a device in the EU, signed in with an Apple Account that has an EU country or region.

You can test the installation of the apps that your marketplace distributes on a physical device when:

- A relationship exists with the app in App Store Connect. See Manage distribution on an alternative app marketplace.

- The developer manually sends you an alternative distribution package for the app that they retrieve from App Store Connect or your webhook receives a notification from App Store Connect. See Processing alternative app marketplace notifications.

- Your marketplace server ingests the app’s alternative distribution package; see Ingesting an alternative distribution package.

To test distribution over the web, ensure:

- Your marketplace app completes Notarization in App Store Connect; see Create a marketplace app.

- Your webpage contains a properly formatted download link to your app’s alternative distribution package; see Design a webpage suitable for app download.

Note

To test system-wide search, upload your app catalog. Apple ingests the upload and enables its contents to show up in Lookup, Safari, and Spotlight search on a device within 24 hours. For more information, see Building a searchable catalog for your marketplace app for inclusion in Spotlight.

## See Also

### Essentials

Distributing your app from your website

Configure your app and website to enable people to install your app on their devices from your website.

Distributing your app on an alternative app marketplace

Design your app for alternative distribution from an alternative app marketplace.

