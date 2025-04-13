

- Xcode
- Xcode Cloud
-  Removing your project from Xcode Cloud 

Article

# Removing your project from Xcode Cloud

Remove your project from Xcode Cloud to delete app and workflow data, disconnect your Git repository, and remove the Slack integration.

## Overview

When your app or framework is no longer under active development, you might want to do some general cleanup, like:

- Remove your app and any data from Xcode Cloud.

- Disconnect Xcode Cloud from your SCM provider.

- Disconnect Xcode Cloud from your team’s Slack workspace.

- Remove any webhooks that you’ve configured.

### Deleting your data from Xcode Cloud

When you delete your data from Xcode Cloud, you can’t restore it and it becomes immediately inaccessible.

Similarly, deleting a workflow deletes the workflow’s build history and artifacts. Only delete a workflow or your data from Xcode Cloud when you’re confident that you don’t need its build history or artifacts anymore. Instead, deactivate workflows you no longer need as described in Deactivate a workflow instead of deleting it.

To stop using Xcode Cloud for your app or framework and delete its associated data:

- In Xcode, navigate to the Report navigator, Control-click your app, choose Delete Xcode Cloud Data for,” and confirm that you want to permanently delete all Xcode Cloud data.

- In App Store Connect, go to your app’s page, select the Xcode Cloud tab, choose Settings \> Delete Xcode Cloud Data, click Delete, and confirm that you want to permanently delete all Xcode Cloud data.

For more information on the differences between deleting and deactivating a workflow, see Deactivate a workflow instead of deleting it.

### Disconnect your Git repository in Xcode Cloud

If you move your Git repositories to another source code management (SCM) provider, you’ll want to remove the old provider from your Xcode Cloud configuration.

To disconnect Xcode Cloud from Bitbucket Server, GitHub Enterprise, or a self-managed GitLab instances:

1.  Sign in to App Store Connect and go to Users and Access.

2.  Select the Xcode Cloud tab.

3.  Move the cursor over the SCM provider you want to remove, then click the Remove button (-) and confirm that you want to disconnect Xcode Cloud from your provider.

To disconnect Xcode Cloud from Bitbucket, GitHub, or GitLab:

1.  Sign in to App Store Connect and go to your profile settings by clicking your account in the top-right corner of the website and Edit Profile.

2.  Select the Xcode Cloud tab.

3.  Choose Integrations in the sidebar.

4.  Click Unlink next to the SCM provider you no longer use and confirm that you want to remove the connection between Xcode Cloud and your provider.

### Remove personal access tokens or apps

To completely remove all traces of Xcode Cloud from your SCM provider, you need to remove the app or personal access token that allowed Xcode Cloud access to the repository. The process to do this is different for each SCM provider:

Bitbucket Cloud  
Sign into your Bitbucket Cloud account and go to your personal settings. Choose “App authorization” in the Access Management group and revoke the application authorization for Xcode Cloud.

Bitbucket Server  
Sign in to your Bitbucket Server account and go to your account settings. Choose “HTTP access tokens” and revoke the token for Xcode Cloud using the Actions \> Revoke button.

GitHub  
Sign into your GitHub account. If you use a GitHub organization and the organization owns your Git repository, follow the steps described for GitHub Enterprise. If you don’t use a GitHub organization, go to your account settings. Choose Applications, click Configure next to the Xcode Cloud app, and then click Uninstall to remove the GitHub app from your account and repositories.

GitHub Enterprise  
Sign into your GitHub Enterprise account and go to your account settings. Choose Applications \> Configure, and then click Uninstall at the bottom of your GitHub app’s settings. This removes the GitHub app from your repositories. Next, choose Developer Settings \> GitHub Apps and click Edit for the Xcode Cloud GitHub app. Navigate to the Advanced section and delete your app from your GitHub Enterprise account or organization.

GitLab  
Sign into your GitLab account and navigate to your user preferences. Click Applications, and then scroll down to the list of authorized apps and revoke the authorization for the Xcode Cloud app.

Self-managed GitLab Instance  
Sign into your account for your self-managed GitLab instance and go to your account settings. Choose Applications and then delete the app for Xcode Cloud.

### Remove the Slack integration

If you connected your team’s Slack workspace to Xcode Cloud, the connection between Xcode Cloud and your Slack workspace remains when you delete a workflow or remove your project. To remove the Slack integration, you’ll need to uninstall the Slack app from your team’s Slack workspace:

1.  Open your Slack workspace in your browser and click Manage. Alternatively, click on your workspace’s name in the Slack app and choose “Settings & administration” \> “Manage apps”.

2.  Choose Installed Apps in the sidebar, then choose the Xcode Cloud app.

3.  Remove the app and confirm that you want to delete the Slack app for Xcode Cloud.

Note

Depending on the configuration of your team’s Slack workspace, you may need to ask your team’s Slack administrator to remove the Slack app.

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

Setting the next build number for Xcode Cloud builds

Start numbering builds from a custom build number for your existing Mac app to avoid version collisions.

Including notes for testers with a beta release of your app

Add text files to your Xcode project to provide notes to beta testers about what to test.

