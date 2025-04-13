

- Xcode
- Localization
-  Adding support for languages and regions 

Article

# Adding support for languages and regions

Select the resources that you want to localize for each language and region you support.

## Overview

Add the language and region combinations you want to support to your project. For each localization, select the resources, such as image and audio files, that you want to localize.

### Add localizations

In the project editor, select the project name under Project, and click Info. Under Localizations, click the Add button (+), then choose a language and region combination from the pop-up menu.

The pop-up menu contains the language name followed by the language ID in parentheses — for example, German (de), Japanese (ja), and Arabic (ar). For regional variants and scripts, the region appears in parentheses followed by the language ID in parentheses— for example, English (India) (en-IN) where en-IN is the language ID. The Other submenu (at the bottom of the menu) contains additional languages and regions to choose from. For guidance, see Choosing localization regions and scripts.

If you have localizable resources in the project, select the resource files that you want to localize in the sheet that appears, and click Finish. For example, select images, audio, strings, and `.stringsdict` files that you add to your project.

For storyboard and XIB interfaces, select the user interface files (files with a `.storyboard` or `.xib` filename extension). Xcode adds a strings file to the localization folder that contains the text to translate, as well as comments that describe the user interface components. For example, if you add German to an iOS app that uses storyboards, `LaunchScreen.storyboard` becomes a group containing a `LaunchScreen.storyboard (Base)` and `LaunchScreen.strings (German) `file.

Note

Xcode adds the `Base` and the development language to the localization table by default. Use the Base localization for resources that support string substitution at runtime, such as storyboard, XIB, and Siri intent definition files.

### View localizable resources

You can verify the resources for each localization in the Project navigator and Finder.

The first time you add a localization, Xcode changes every resource that you want to localize into a group containing the original file and a localization-specific version. The next time you add a localization, Xcode adds another localization-specific file to the group.

In the file system, Xcode creates a separate localization folder to store the localization-specific resources. The name of the folder is the language ID followed by the `.lproj` file extension — for example, `de.lproj `if you choose German (de) from the localization menu.

## See Also

### Languages and regions

Choosing localization regions and scripts

Add a language-only localization or localizations specific to regional variants and scripts.

