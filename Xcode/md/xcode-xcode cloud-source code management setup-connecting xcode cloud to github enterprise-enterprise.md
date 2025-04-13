

- Xcode
- Xcode Cloud
- Source code management setup
-  Connecting Xcode Cloud to GitHub Enterprise 

Article

# Connecting Xcode Cloud to GitHub Enterprise

Allow Xcode Cloud to access your GitHub Enterprise repository.

## Overview

When you first configure your project or workspace to use Xcode Cloud, you need to allow Xcode Cloud to access your Git repository. It uses this access to automatically build and test your code when you make changes to the codebase.

If you host your code as part of a GitHub organization, the person who first configures a project to use Xcode Cloud must be an *organization owner*. If you don’t use a GitHub organization, the person who first configures a project to use Xcode Cloud must have the *admin* permission. If you don’t have the required role or permission, see Connect Xcode Cloud to an admin-managed Git repository.

If your GitHub Enterprise instance settings have an IP allow list, make sure that you have added our IP address ranges to it before proceeding.

To allow Xcode Cloud to access your repository on GitHub Enterprise:

1.  Configure your project or workspace to use Xcode Cloud and create your first workflow as described in Configuring your first Xcode Cloud workflow. Xcode analyzes your project to learn which SCM provider you use and then displays the URL of your GitHub Enterprise instance on the Grant Access to Your Source Code sheet.

2.  Click Grant Access. Xcode opens your browser and takes you to the App Store Connect website.

3.  Choose GitHub Enterprise.

4.  Register the host name of your GitHub Enterprise host. The corresponding field should already contain your instance’s URL. Check if it’s correct; for example, make sure it contains a required port.

5.  Click Complete Step 1 in GitHub Enterprise to navigate to the website of your GitHub Enterprise host.

6.  Review the name of the GitHub app, then create it. GitHub Enterprise uses this app to grant Xcode Cloud access to your repository.

7.  Review and authorize the permissions that the GitHub app requests.

8.  Authorize Xcode Cloud to verify your identity on GitHub Enterprise to link your GitHub Enterprise account to your Apple Account.

9.  Choose to only install the GitHub app for your project’s repository. Don’t install it for every repository. When the installation finishes, GitHub Enterprise takes you back to the App Store Connect website. App Store Connect now indicates that you successfully connected Xcode Cloud to GitHub Enterprise.

10. Return to Xcode. It indicates that Xcode Cloud can access your source code.

11. Click Next, complete your first workflow, and start your first build.

## See Also

### GitHub and GitHub Enterprise

Connecting Xcode Cloud to GitHub

Allow Xcode Cloud to access your GitHub repository.

