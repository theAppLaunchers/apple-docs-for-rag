

- Xcode
- Xcode Cloud
-  Setting up your project to use Xcode Cloud 

Article

# Setting up your project to use Xcode Cloud

Review account, project, and source control requirements before configuring your project or workspace to use Xcode Cloud.

## Overview

Xcode helps you configure your project or workspace to use Xcode Cloud. For a smooth configuration process, review the requirements for using Xcode Cloud and make changes as needed. Then, configure your project or workspace to use Xcode Cloud and start practicing continuous integration and delivery (CI/CD).

### Set up your App Store Connect account

To use Xcode Cloud, you need to:

- Be enrolled in the Apple Developer Program.

- Use Xcode 15 or later.

- Add your Apple Account under Accounts in Xcode Settings.

- Have an app record for your app in App Store Connect or have the required role or permission to create one.

To create an app record, you need to have the App Manager, Admin, or Account Holder role for your team. If you have the Developer role, you need the Create Apps permission. If you don’t have the required role or permission, work with a team member who does. For more information, see Create an app record in App Store Connect.

Note

Depending on how much you use Xcode Cloud, you may need an optional Xcode Cloud subscription plan. To manage Xcode Cloud subscription plans, you need the Account Holder role. For more information on subscription plans, see Get started with Xcode Cloud.

For more information about roles in App Store Connect, see Role permissions.

### Configure your project and workspace

If you create a project from a template, the default settings automatically meet Xcode Cloud requirements. If you have an existing project, be sure it meets the following project and workspace requirements:

- Use a consistent Xcode project or workspace.

- Use shared schemes. For information on sharing a scheme, see Customizing the build schemes for a project.

- Enable the archive action for the scheme that builds your app or framework.

- Ensure your dependencies and additional third-party tools are available to Xcode Cloud. For more information, see Making dependencies available to Xcode Cloud.

- Allow Xcode to manage signing for you. To use automatic code signing, toggle the “Automatically manage signing” checkbox in the Signing & Capabilities pane in the project editor.

- Set the bundle identifier for your app target in the Signing & Capabilities pane of your Xcode project or workspace. If you use `.xcconfig` files to set the bundle identifier, see Review Xcode Cloud workflows for more information.

Important

Xcode Cloud requires a consistent Xcode project or workspace that’s continuously present. If you use a third-party tool that dynamically generates or edits your project or workspace, the initial configuration of Xcode Cloud and subsequent builds may fail.

### Use a remote source control repository

You need a remote repository using Git to use Xcode Cloud. To learn more about using source control with Git in Xcode, see Source control management.

Xcode Cloud supports the following source code management (SCM) providers:

- Bitbucket Cloud and Bitbucket Server

- GitHub and GitHub Enterprise

- GitLab and self-managed GitLab instances

Note

If you use an IP allow list either on a self-hosted or cloud SCM provider — such as Bitbucket Server or GitHub Enterprise — make sure Xcode Cloud has access to your Git server. Check your firewall’s inbound HTTPS allow list and grant Xcode Cloud access to your Git server by adding the IP address ranges `17.58.0.0/18`, `17.58.192.0/18`, and `57.103.0.0/22`.

Additionally, you need a certain permission or role to connect Xcode Cloud to your Git repository. The exact permission depends on the SCM provider you use:

- If you host your code on Bitbucket Cloud or Bitbucket Server, you need the administrator permission.

- If you host your code on GitHub or GitHub Enterprise, you need to be an organization owner, or need the admin permission if you don’t use a GitHub organization.

- If you host your code on GitLab, or on a self-managed GitLab instance, you need the maintainer permission.

If you don’t have the required role or permission, work with a team member who does. For more information, see Connect Xcode Cloud to an admin-managed Git repository.

## See Also

### Essentials

About continuous integration and delivery with Xcode Cloud

Learn how continuous integration and delivery with Xcode Cloud helps you create high-quality apps and frameworks.

Configuring your first Xcode Cloud workflow

Set up your project or workspace to use Xcode Cloud and adopt continuous integration and delivery.

