

- Swift Playgrounds
- Playground Books
-  Hiding Code from a Playground Page 

Article

# Hiding Code from a Playground Page

Use special Swift comments to hide code from display but continue to run it.

## Overview

You can hide code that’s unrelated to the main content of a playground page, like calls to page setup functions, code for assessing the learner’s progress, and functions in editable examples. Hidden code is still executed when the learner runs the playground.

Place code you want to hide between the `hidden-code` and `end-hidden-code` delimiters.

The following shows the raw syntax for a playground page with hidden code.

```
//#-hidden-code
import UIKit
import PlaygroundSupport
let viewRect = CGRect(x: 0, y: 0, width: 100 , height: 400)
let theView = CustomView(frame: viewRect)
PlaygroundPage.current.liveView = theView
//#-end-hidden-code
//#-editable-code
theView.markColor = UIColor.darkGray
theView.isChecked = true
//#-end-editable-code
```

The following shows how the previous code appears when it’s rendered in the playground page source editor.

```
theView.markColor = UIColor.darkGray
theView.isChecked = true
```

## See Also

### Annotations

Writing Prose for a Playground Page

Add comment markers in your Swift code to mark text as prose.

Specifying Editable Regions in a Playground Page

Guide learning by marking code that learners can change or copy forward.

Customizing the Completions in the Shortcut Bar

Guide learners toward a solution by hiding some symbols and showing others.

Localizing Code Comments and String Literals

In Swift Playgrounds 3.0 and later, mark up code zones to replace them with code that’s localized for the current user.

