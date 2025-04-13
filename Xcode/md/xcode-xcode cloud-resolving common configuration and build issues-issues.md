

- Xcode
- Xcode Cloud
-  Resolving common configuration and build issues 

Article

# Resolving common configuration and build issues

Review common configuration and build issues and learn how you can resolve them.

## Overview

Xcode guides you through the process of configuring your project to use Xcode Cloud and of creating workflows. However, there’s a chance that you run into issues. This is more likely for complex codebases and projects that have many dependencies. To help you diagnose build failure, view logs in the build report in Xcode or on the App Store Connect website and download build reports.

### View build logs

To understand why a build failed, open your project or workspace and navigate to the Report navigator. Select a build, expand a failed action, and select Logs to see the build logs. To download the build logs and any other build artifacts — for example, a result bundle — choose Artifacts for the failed action.

Alternatively, select a build in the Xcode Cloud tab on the App Store Connect website to view detailed information about the build.

### Reproduce a build failure locally

Reproducing a build failure locally is often key to fixing its cause. To quickly replicate a failing build’s source state locally:

1.  Open your Xcode project or workspace, navigate to the Report navigator, and select a build to view its Build Report overview.

2.  Click Switch To in the top-right corner of the overview and follow the on screen prompts to either switch to the latest commit of the branch or check out the specific commit of the failing build.

3.  Reproduce the issue locally by performing the action that failed in Xcode Cloud and resolve the issue.

If your workflow doesn’t automatically start a new build with the latest change, manually start a new build as described in Start a new build below.

### Resolve configuration issues

To resolve issues when first configuring your project or workspace to use Xcode Cloud:

- If Xcode doesn’t list your product, enable the archive action for the scheme that builds your app or framework in Xcode.

- If you can’t grant Xcode Cloud access to your Git repository, check if you have the required permission or role to connect Xcode Cloud to your Git repository. For more information, see Grant Xcode Cloud access to your source code.

- If a workflow’s action doesn’t list a scheme, make sure you shared the scheme. For information on sharing a scheme, see Xcode Help.

### Resolve build issues

To resolve build issues:

- Control-click your workflow in the Report navigator, click Edit Workflow, and verify that the environment setting uses the macOS and Xcode versions you require to build your project.

- Check if your project or workspace uses Xcode’s new build system. For more information about the new build system, see Build System Release Notes for Xcode 10. For details about how to turn on the new build system, see Choose the build system.

- Review your project’s dependencies and required additional tools to make sure they are accessible to Xcode Cloud. For more information, see Making dependencies available to Xcode Cloud.

- If you use CocoaPods to manage your dependencies, check if you committed your `Podfile` and your `Podfile.lock` files to Git and installed CocoaPods correctly as explained in Make CocoaPods dependencies available to Xcode Cloud.

- If a third-party tool indicates networking issues, configure it to respect the `HTTP_PROXY` and `HTTPS_PROXY` environment variables and adjust its proxy settings as needed.

- If your build fails with an error that indicates a missing app capability, check if the app ID you used when you configured your first Xcode Cloud workflow has all required capabilities enabled. For more information about capabilities, see Enable app capabilities.

### Resolve Swift package dependency issues

Xcode Cloud supports using Swift package dependencies in your project. Be sure to read Use Swift package dependencies and Git submodules if your project requires Swift package dependencies to build successfully.

A common cause of failing builds is that Xcode Cloud can’t access the `Package.resolved` file that it needs to resolve your Swift Package dependencies. To resolve issues related to the `Package.resolved` file, make sure:

- To commit and push the file to your Git repository.

- Your `.gitignore` file doesn’t include the file.

### Start a new build

When you’ve made changes to your project or workspace to resolve a build issue, start a new build to verify that the change resolved it:

- To manually start a new build that includes any new changes, Control-click the workflow in the Report navigator and click Start Build.

- To start a build from the same Git commit, Control-click the build in the Report navigator and choose Rebuild.

## See Also

### Troubleshooting

Resolve GitHub Enterprise connection issues

Verify that Xcode Cloud can access your GitHub Enterprise repository and fix configuration issues.

Reporting feedback for Xcode Cloud

Provide feedback on issues you encounter when building with Xcode Cloud.

