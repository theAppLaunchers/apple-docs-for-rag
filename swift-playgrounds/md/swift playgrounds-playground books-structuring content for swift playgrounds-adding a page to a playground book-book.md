

- Swift Playgrounds
- Playground Books
- Structuring Content for Swift Playgrounds
-  Adding a Page to a Playground Book 

Article

# Adding a Page to a Playground Book

Create a subfolder, a manifest file, and a content file.

## Overview

Playground pages are the primary content of a playground book. They contain the code, prose, and optional live view that make up the primary Swift Playgrounds interface that’s displayed when viewing a book.

### Add a Subfolder to a Chapter Folder

Add a page by selecting a chapter folder and adding a subfolder to it. The subfolder’s name must end in the suffix .playgroundpage.

In Xcode, create a property list file called `Manifest.plist` in the new page’s subfolder. Choose File \> New \> File, then choose the Property List template from iOS \> Resources. Use the manifest property list to list the page’s name and configuration metadata.

### Add Code and Prose

For each page in your playground book, create a `main.swift` file. This file is where you write most of the content—code and prose—that learners see in a playground book. The code and prose you write in this file appears on the left side of a page when it’s displayed in Swift Playgrounds.

Important

If you’re writing a book that targets a version of the Swift Playgrounds book format earlier than `6.0`, use the name `Contents.swift` instead of `main.swift`.

By default, everything you write in `main.swift` is treated as normal Swift code that runs when a learner taps the Run button. Playground pages support rich annotions that you use to write prose and add functionality. For more information about annotations, see *Annotations* and Writing Prose for a Playground Page.

### Add an Always-On Live View

To display the results of running the code on a page, you can add an always-on live view. When present, it’s displayed on the right side of a page. Add an always-on live view by creating a file named `LiveView.swift` and placing it in a page’s .playgroundpage folder.

For the view to appear on the page, you must set the liveView property of the current page within `LiveView.swift`.

```
PlaygroundPage.current.liveView = 
```

### Specify the Page Name and Metadata

A page’s manifest property list determines both the page name and metadata for presenting the page in Swift Playgrounds. Configure the following property list keys in the manifest:

`CodeCopySetup`  
A dictionary you use to specify the instructions learners read when they’re copying content between playground pages. For information about the keys and values you use in this dictionary, see Mark Editable Areas as Copyable.

`LiveViewEdgeToEdge`  
**Required.** A Boolean value you use to control the initial size of the live view. Set to `true` to fill the whole live view area, which includes the Run and Hints buttons that overlay the live view.

`LiveViewMode`  
**Required.** A string you use to control the display of the live view area when the live view isn’t running. Set to `VisibleByDefault` to show the live view when the playground opens. Otherwise, set to `HiddenByDefault` to hide the live view until a learner runs the playground.

`Name`  
**Required.** A string you use to specify the page name displayed to learners in Swift Playgrounds.

`PlaygroundLoggingMode`  
A string you use to specify whether the results of running Swift statements on the page are displayed beside each statement. Set to `Normal` to display results; otherwise, set to `Off`.

`PosterReference`  
A string you use to reference an image file that’s shown centered and unscaled in the live view area before the live view runs. The image file can be in any Resources folder in the playground book.

`UserModuleCodeCompletionDirectives`  
An array of strings you use to control which code completions from modules show up in the shortcut bar. The syntax for each completion is identical to the syntax you use within the `code-completion` delimiter in `main.swift` files. For more information, see Customizing the Completions in the Shortcut Bar.

`UserModuleSourceFileToActivate`  
A string you use to specify the active Swift file when a learner opens this page. Set to the path of a Swift file relative to the Contents folder in the playground book. For example: `UserModules/MyModule.playgroundmodule/Sources/MyModule.swift`.

`UserModuleSourceFilesToOpen`  
An array of strings you use to specify which Swift files should open when a learner opens this page. The order of the array elements determines the display order of the files in the Swift Playgrounds interface.

## See Also

### Book Structure

Adding a Chapter to a Playground Book

Create a folder with a manifest that describes the chapter’s name and page order.

Adding a Cutscene to a Playground Book

Create a subfolder, a manifest file, and cutscene metadata.

Using Modules to Share Code in a Playground Book

In Swift Playgrounds 3.0 and later, make code available across multiple chapters to teach the value of reusable code.

Sharing Resources in a Playground Book

Reuse common assets throughout a book to reduce its size.

