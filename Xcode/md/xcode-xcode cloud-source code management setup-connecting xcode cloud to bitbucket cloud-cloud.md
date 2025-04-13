

- Xcode
- Xcode Cloud
- Source code management setup
-  Connecting Xcode Cloud to Bitbucket Cloud 

Article

# Connecting Xcode Cloud to Bitbucket Cloud

Allow Xcode Cloud to access your Bitbucket Cloud repository.

## Overview

When you first configure your project or workspace to use Xcode Cloud, you need to allow Xcode Cloud to access your Git repository. It uses this access to automatically build and test your code when you make changes to the codebase.

The person who first configures a project or workspace to use Xcode Cloud must have the *administrator* permission for the repository on Bitbucket Cloud. If you don’t have this permission, see Connect Xcode Cloud to an admin-managed Git repository.

To allow Xcode Cloud to access your repository on Bitbucket Cloud:

1.  Configure your project or workspace to use Xcode Cloud and create your first workflow as described in Configuring your first Xcode Cloud workflow. Xcode analyzes your project to learn which SCM provider you use and then indicates that you use Bitbucket Cloud on the Grant Access to Your Source Code sheet.

2.  Click Grant Access. Xcode opens your browser and takes you to the App Store Connect website.

3.  Click “Complete Step 1 in Bitbucket” to connect Xcode Cloud with your Bitbucket account. This takes you to your account on the Bitbucket Cloud website.

4.  Review the permissions Xcode Cloud requests and allow it to access your repository. This takes you back to the App Store Connect website, which indicates that you successfully connected Xcode Cloud to Bitbucket Cloud.

5.  Return to Xcode. It indicates that Xcode Cloud can access your source code.

6.  Click Next, complete the configuration of your first workflow, and start your first build.

## See Also

### Bitbucket Cloud and Bitbucket Server

Connecting Xcode Cloud to Bitbucket Server

Allow Xcode Cloud to access your Bitbucket Server repository.

