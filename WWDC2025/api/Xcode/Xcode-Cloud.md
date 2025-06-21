Collection

*   [Xcode](/documentation/xcode)
*   Xcode Cloud

# Xcode Cloud

Automatically build, test, and distribute your apps with Xcode Cloud to verify changes and create high-quality apps.

## [Overview](/documentation/xcode/xcode-cloud#Overview)

Xcode Cloud lets you adopt _continuous integration and delivery_ (CI/CD), a standard software development practice that helps you develop and maintain your code and deliver apps to testers and users. Xcode Cloud is a CI/CD system that combines the tools you use to create apps and frameworks for Apple platforms: [Xcode](https://developer.apple.com/xcode/), [TestFlight](https://developer.apple.com/testflight/), and [App Store Connect](https://appstoreconnect.apple.com).

![A conceptual illustration that shows how Xcode Cloud builds a project and distributes an app to all kinds of devices.](https://docs-assets.developer.apple.com/published/83d5c07a9e6a7ebcf6780c5e25d0947a/Xcode-Cloud-Hero%402x.png)

With Xcode Cloud, you can automatically and frequently:

*   Build your project.
    
*   Run tests and perform verifications.
    
*   Distribute builds to testers and gather their feedback with [TestFlight](https://developer.apple.com/testflight/) while protecting user privacy.
    

After successfully verifying a new version of your app with Xcode Cloud and TestFlight, you can quickly release it on the App Store.

For more information about continuous integration and delivery, see [About continuous integration and delivery with Xcode Cloud](/documentation/xcode/about-continuous-integration-and-delivery-with-xcode-cloud). To learn more about configuring your project or workspace to use Xcode Cloud, see [Configuring your first Xcode Cloud workflow](/documentation/xcode/configuring-your-first-xcode-cloud-workflow).

Note

For additional information about Xcode Cloud that includes videos from WWDC21 and WWDC22, see [The Xcode Cloud toolkit](https://developer.apple.com/news/?id=076p6dmy).

## [Topics](/documentation/xcode/xcode-cloud#topics)

### [Essentials](/documentation/xcode/xcode-cloud#Essentials)

[

About continuous integration and delivery with Xcode Cloud](/documentation/xcode/about-continuous-integration-and-delivery-with-xcode-cloud)

Learn how continuous integration and delivery with Xcode Cloud helps you create high-quality apps and frameworks.

[

Setting up your project to use Xcode Cloud](/documentation/xcode/setting-up-your-project-to-use-xcode-cloud)

Review account, project, and source control requirements before configuring your project or workspace to use Xcode Cloud.

[

Configuring your first Xcode Cloud workflow](/documentation/xcode/configuring-your-first-xcode-cloud-workflow)

Set up your project or workspace to use Xcode Cloud and adopt continuous integration and delivery.

### [Setup and maintenance](/documentation/xcode/xcode-cloud#Setup-and-maintenance)

[

Making dependencies available to Xcode Cloud](/documentation/xcode/making-dependencies-available-to-xcode-cloud)

Review dependencies and make them available to Xcode Cloud before you configure your project to use Xcode Cloud.

[

Configuring Xcode Cloud for your team](/documentation/xcode/configuring-xcode-cloud-for-your-team)

Start using continuous integration and delivery with Xcode Cloud as a team.

[

Sharing macOS and Xcode versions across Xcode Cloud workflows](/documentation/xcode/sharing-custom-aliases-across-xcode-cloud-workflows)

Use custom aliases to share configurations with multiple workflows.

[

Sharing environment variables across Xcode Cloud workflows](/documentation/xcode/sharing-environment-variables-across-xcode-cloud-workflows)

Apply common configurations to multiple workflows by using shared environment variables.

[

Building Swift packages and Swift Playgrounds app projects with Xcode Cloud](/documentation/xcode/building-swift-packages-or-swift-playground-app-projects-with-xcode-cloud)

Add your Swift package or Swift Playgrounds app project to an Xcode project to build it in Xcode Cloud.

[

Setting the next build number for Xcode Cloud builds](/documentation/xcode/setting-the-next-build-number-for-xcode-cloud-builds)

Start numbering builds from a custom build number for your existing Mac app to avoid version collisions.

[

Including notes for testers with a beta release of your app](/documentation/xcode/including-notes-for-testers-with-a-beta-release-of-your-app)

Add text files to your Xcode project to provide notes to beta testers about what to test.

[

Removing your project from Xcode Cloud](/documentation/xcode/removing-your-project-from-xcode-cloud)

Remove your project from Xcode Cloud to delete app and workflow data, disconnect your Git repository, and remove the Slack integration.

### [Usage data](/documentation/xcode/xcode-cloud#Usage-data)

[

Reviewing Xcode Cloud usage data](/documentation/xcode/reviewing-xcode-cloud-usage-data)

Access Xcode Cloud usage information to understand how you and your team use Xcode Cloud.

### [Workflows](/documentation/xcode/xcode-cloud#Workflows)

[

Developing a workflow strategy for Xcode Cloud](/documentation/xcode/developing-a-workflow-strategy-for-xcode-cloud)

Review how you can best create custom Xcode Cloud workflows to refine your continuous integration and delivery practice.

[

API Reference

Xcode Cloud workflow reference](/documentation/xcode/xcode-cloud-workflow-reference)

Configure metadata, start conditions, actions, post-actions, and more to create custom Xcode Cloud workflows.

[

Creating a workflow that builds your app for distribution](/documentation/xcode/creating-a-workflow-that-builds-your-app-for-distribution)

Configure a workflow to build and sign your app for distribution to testers with TestFlight, in the App Store, or as a notarized app.

### [Source code management](/documentation/xcode/xcode-cloud#Source-code-management)

[

API Reference

Source code management setup](/documentation/xcode/source-code-management-setup)

Allow Xcode Cloud to access your Git repository.

[

Configuring requirements for merging a pull request](/documentation/xcode/configuring-requirements-for-merging-a-pull-request)

Protect stable branches by requiring a successful Xcode Cloud build or action before it’s possible to merge a pull request.

### [Custom build scripts](/documentation/xcode/xcode-cloud#Custom-build-scripts)

[

Writing custom build scripts](/documentation/xcode/writing-custom-build-scripts)

Extend your Xcode Cloud workflows with custom build scripts that perform custom tasks or install additional tools.

[

Environment variable reference](/documentation/xcode/environment-variable-reference)

Review predefined environment variables you use in custom build scripts.

### [Troubleshooting](/documentation/xcode/xcode-cloud#Troubleshooting)

[

Resolving common configuration and build issues](/documentation/xcode/resolving-common-configuration-and-build-issues)

Review common configuration and build issues and learn how you can resolve them.

[

Resolve GitHub Enterprise connection issues](/documentation/xcode/resolve-github-enterprise-connection-issues)

Verify that Xcode Cloud can access your GitHub Enterprise repository and fix configuration issues.

[

Reporting feedback for Xcode Cloud](/documentation/xcode/reporting-feedback-for-xcode-cloud)

Provide feedback on issues you encounter when building with Xcode Cloud.

### [Notifications](/documentation/xcode/xcode-cloud#Notifications)

[

Configuring webhooks in Xcode Cloud](/documentation/xcode/configuring-webhooks-in-xcode-cloud)

Configure webhooks that connect Xcode Cloud to other services and tools.

[

Xcode Cloud webhook payload reference](/documentation/xcode/webhook-payload)

Review details of the webhook payload that Xcode Cloud sends, including the product, workflow, build, actions, results, and SCM metadata associated with it.

[

Connecting Xcode Cloud to Slack](/documentation/xcode/connecting-xcode-cloud-to-slack)

Connect Xcode Cloud to Slack to keep your team informed about the latest Xcode Cloud builds.

### [REST API](/documentation/xcode/xcode-cloud#REST-API)

[

Xcode Cloud Workflows and Builds](/documentation/AppStoreConnectAPI/xcode-cloud-workflows-and-builds)

Automate reading Xcode Cloud data, managing workflows, and starting builds.

## [See Also](/documentation/xcode/xcode-cloud#see-also)

### [Distribution and continuous integration](/documentation/xcode/xcode-cloud#Distribution-and-continuous-integration)

[

API Reference

Distribution](/documentation/xcode/distribution)

Prepare your app and share it with your team, beta testers, and customers.