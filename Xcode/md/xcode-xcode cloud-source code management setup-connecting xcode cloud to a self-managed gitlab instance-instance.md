

- Xcode
- Xcode Cloud
- Source code management setup
-  Connecting Xcode Cloud to a self-managed GitLab instance 

Article

# Connecting Xcode Cloud to a self-managed GitLab instance

Allow Xcode Cloud to access your self-managed GitLab repository.

## Overview

When you first configure your project or workspace to use Xcode Cloud, you need to allow Xcode Cloud to access your Git repository. It uses this access to automatically build and test your code when you make changes to the codebase.

The person who first configures a project to use Xcode Cloud must have the *maintainer* role for the GitLab repository. If you don’t have this role, see Connect Xcode Cloud to an admin-managed Git repository.

To allow Xcode Cloud to access your self-managed GitLab repository:

1.  Configure your project or workspace to use Xcode Cloud and create your first workflow as described in Configuring your first Xcode Cloud workflow. Xcode analyzes your project to learn which SCM provider you use and then displays the URL of your self-managed GitLab instance on the Grant Access to Your Source Code sheet.

2.  Click Grant Access. Xcode opens your browser and takes you to the App Store Connect website.

3.  Choose self-managed GitLab to create a GitLab app that manages access to your GitLab repository.

4.  Copy the redirect URI, then click “your GitLab Self-hosted host” to open your GitLab instance’s website. It displays the page to create a new GitLab app.

5.  Enter a name for the GitLab app that’s easy to recognize; for example, `Xcode Cloud`.

6.  Paste the Xcode Cloud redirect URI into the field on the GitLab webpage for creating the GitLab app.

7.  Select the checkboxes next to *api*, *read_repository*, and *read_user* to allow the app to access these scopes.

8.  Save the app.

9.  Copy the GitLab app’s Application ID and paste it into the corresponding field on the App Store Connect website, and then repeat this step for the Application Secret.

10. Click Register on the App Store Connect website to connect Xcode Cloud to the GitLab app.

11. Click “Authorize in GitLab” top open your GitLab instance’s website and install the GitLab app for your repository.

12. Review the permissions that Xcode Cloud requests and allow it to access your account. This takes you back to the App Store Connect website, which indicates that you successfully connected Xcode Cloud to your self-managed GitLab instance.

13. Return to Xcode. It indicates that Xcode Cloud can access your source code.

14. Click Next, complete the configuration of your first workflow, and start your first build.

## See Also

### GitLab

Connecting Xcode Cloud to GitLab

Allow Xcode Cloud to access your GitLab repository.

