

- Xcode
- Xcode Cloud
-  Including notes for testers with a beta release of your app 

Article

# Including notes for testers with a beta release of your app

Add text files to your Xcode project to provide notes to beta testers about what to test.

## Overview

You can include notes when you distribute a beta version of your app from Xcode Cloud through TestFlight to give testers details about the changes the update includes, and to provide guidance for the areas of your app to test. Use these notes to focus testing on the areas of your app that need attention. The notes appear in the “What to test” field in the TestFlight app. The information you provide can be language- and locale-specific.

For more information about distributing a beta version of your app, see Creating a workflow that builds your app for distribution.

Related sessions from WWDC23

Session 10224: Simplify distribution in Xcode and Xcode Cloud

### Create a TestFlight folder

Xcode Cloud uses text files that you add to your Xcode project to create the notes for testers. The text files reside in a folder named TestFlight located in the same folder as your Xcode project or workspace.

To create the TestFlight folder:

- Open your project or workspace in Xcode.

- In the Project navigator, Control-click your project and choose New Group to create the group and its corresponding folder.

- Name the new group TestFlight.

### Add text files to the folder to include notes

Add text files to the TestFlight folder to provide notes to your testers. Provide notes in multiple languages by creating a file per language. For a list of the locales TestFlight supports, see BetaBuildLocalizationCreateRequest.Data.Attributes. For general information on language and region codes, see Choosing localization regions and scripts.

To add the text files to your project:

- Add a new Empty file to the TestFlight folder. For instructions, see Managing files and folders in your Xcode project.

- Name the file using the format `WhatToTest..txt`. For `LOCALE`, use the language and region code for the content you provide in the file. For example, use `WhatToTest.en-US.txt` for U.S. English.

- Commit and push the file to your remote repository.

The next time Xcode Cloud builds and uploads your app to TestFlight, it automatically finds this file and includes the text in your app’s “What to test” field in TestFlight.

### Provide useful and appropriate content

Include information that is useful to testers and relevant to the current release, such as the following:

- Features you add to your app.

- Issues you resolve in your code.

- The commit message for the commit that triggers the build, or the past few commit messages.

Note

When Xcode Cloud deploys your app, the information you provide is available to all testers in all groups who have access to the build.

### Write a script to generate content dynamically

You can use a custom build script to generate the notes during an Xcode Cloud build. The following example provides the last three commit messages from the GIT log as the tester notes:

```
#!/bin/zsh
#  ci_post_xcodebuild.sh

if [[ -d "$CI_APP_STORE_SIGNED_APP_PATH" ]]; then
  TESTFLIGHT_DIR_PATH=../TestFlight
  mkdir $TESTFLIGHT_DIR_PATH
  git fetch --deepen 3 && git log -3 --pretty=format:"%s" >! $TESTFLIGHT_DIR_PATH/WhatToTest.en-US.txt
fi
```

For more information, see Writing custom build scripts.

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

Removing your project from Xcode Cloud

Remove your project from Xcode Cloud to delete app and workflow data, disconnect your Git repository, and remove the Slack integration.

