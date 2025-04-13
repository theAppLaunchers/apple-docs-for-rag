

- Xcode
- Xcode Cloud
-  Setting the next build number for Xcode Cloud builds 

Article

# Setting the next build number for Xcode Cloud builds

Start numbering builds from a custom build number for your existing Mac app to avoid version collisions.

## Overview

Xcode Cloud assigns a build number to each build it performs. A *build number* is an integer value that Xcode Cloud automatically increases with each build, starting from `1`. Your first Xcode Cloud build’s build number is `1`, the second build’s build number is `2`, the third build’s build number is `3`, and so on.

For all apps except existing macOS apps, use the default value of `1` for Xcode Cloud builds. For existing Mac apps, start the build number from a different value than `1`.

Important

Xcode Cloud build numbers are always integers; for example, `42`, `420`, or `420000` and so on. You can’t use build numbers that are hash values, timestamps, or other strings.

When you distribute an Xcode Cloud build with TestFlight or release it on the App Store, App Store Connect uses the build number of the Xcode Cloud build. This makes it easy to identify the Xcode Cloud build that correlates with an app’s version in TestFlight or the App Store. For example, say you use Xcode Cloud to create a workflow called `Weekly Build` that makes a new version available to external testers in TestFlight once per week. For your latest weekly build, it distributes version `1.2.1 (42)` where `42` is the build number that Xcode Cloud set. If you need to look at detailed build information for the version, look at the version’s build number — `42` — and navigate to the corresponding Xcode Cloud build in Xcode or App Store Connect.

### Review build number requirements

For a new app, starting with build number `1` makes sense. When you start using Xcode Cloud for an existing app, it assigns build number `1` to your first build. For iOS, iPadOS, tvOS, visionOS, and watchOS apps, this behavior meets build number requirements. Apps for those platforms can use a lower build number for a new version compared to a previous version because App Store Connect requires each app version to use a unique combination of CFBundleShortVersionString and CFBundleVersion.

For example, your latest app version in the App Store could be `1.2.1 (42)` before you start using Xcode Cloud. When you start using Xcode Cloud, your next app version would be `1.2.2 (1)` because Xcode Cloud build numbers start at `1`. It’s a unique combination of the version and the build number and, as a result, App Store Connect accepts it when you submit the new version for app review.

However, Mac apps must follow different build number requirements. To successfully submit a Mac app to app review, its build number must continuously increase, even across app versions. If the app in the previous example was a Mac app, version `1.2.2 (1)` would be invalid because the build number didn’t increase compared to the previous version `1.2.1 (42)`. A valid build number for this Mac app would be `1.2.2 (43)`.

To help cases where incrementing the Xcode Cloud build number starting with `1` isn’t possible — like for an existing Mac app — use App Store Connect to configure Xcode Cloud to increment the build number starting with a custom value.

### Set the next build number to a custom value

Setting the next build number to a custom integer value solves cases where incrementing Xcode Cloud build numbers starting with `1` leads to version collisions.

Important

Only members of your Apple Development Team with the Admin or App Manager role can set the next build number to a custom value.

To configure the next build number:

1.  Start using Xcode Cloud for your project or workspace.

2.  Navigate to your app’s page on the App Store Connect website.

3.  Click the Xcode Cloud tab and choose Settings in the sidebar.

4.  Click the Build Number tab below Settings.

5.  Click the Edit button next to Next Build Number.

6.  Enter a new build number and save your changes.

The screenshot below shows the form you use to edit the Build Number on the App Store Connect website.

## See Also

### Setup and maintenance

Making dependencies available to Xcode Cloud

Review dependencies and make them available to Xcode Cloud before you configure your project to use Xcode Cloud.

Configuring Xcode Cloud for your team

Start using continuous integration and delivery with Xcode Cloud as a team.

Sharing macOS and Xcode versions across Xcode Cloud workflows

Use custom aliases to share configurations with multiple workflows.

Sharing environment variables across Xcode Cloud workflows

Apply common configurations to multiple workflows by using shared environment variables.

Building Swift packages and Swift Playgrounds app projects with Xcode Cloud

Add your Swift package or Swift Playgrounds app project to an Xcode project to build it in Xcode Cloud.

Including notes for testers with a beta release of your app

Add text files to your Xcode project to provide notes to beta testers about what to test.

Removing your project from Xcode Cloud

Remove your project from Xcode Cloud to delete app and workflow data, disconnect your Git repository, and remove the Slack integration.

