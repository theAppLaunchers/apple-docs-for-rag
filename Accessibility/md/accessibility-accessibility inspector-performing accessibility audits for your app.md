

- Accessibility
- Accessibility Inspector
-  Performing accessibility audits for your app 

Article

# Performing accessibility audits for your app

Audit your app for common accessibility issues with Accessibility Inspector.

## Overview

In Accessibility Inspector, the *Audits pane* provides the ability to audit your app for a few of the most common accessibility issues. An *audit* inspects a particular screen in your app and provides feedback about the issues it encounters in your UI, such as insufficient contrast, text clipping, or missing element descriptions. Use this pane to perform audits, view audit results with explanations, view fix suggestions, or save audit results for later.

### Target your app

In Accessibility Inspector, the *target menu* displays a list of connected devices and apps you can inspect. To begin an audit, choose your app from this menu.

Selecting an app to audit causes the *Run Audit button* and *Options menu* to appear in the Audits pane.

### Choose which types of audits to perform

The *Options menu* lets you configure the types of audits to run depending on the platform you test on. Select the checkbox next to the corresponding type of test to include it in the audit. Listed below are the platform-specific types of tests you can select from the Options menu.

#### All platforms

**Element description**. This test checks each element’s accessibility label. All accessible elements must provide some context-specific, descriptive label.

**Hit region**. This test checks whether the size of an element is too small for a person to interact with.

**Contrast**. This test checks for sufficient color contrast between overlapping elements.

**Element detection**. This test checks whether any elements contain inaccessible content that your app might need to be expose as separate accessibility children.

#### iOS, watchOS, and tvOS

**Clipped text**. This test checks whether clipping might occur for any text labels at larger Dynamic Type sizes.

**Traits**. This test verifies that an accessibility object implements all the properties and methods required for the accessibility traits it possesses.

**Dynamic Type**. This test checks whether the text in your app supports Dynamic Type, letting people adjust the size of the text in your app according to their system preference for font size.

#### macOS

**Parent/child**. This test checks the integrity of the accessibility hierarchy by making sure each parent-child pair forms a closed loop. For example, if parent object lists a child as part of its accessibility children, but the child object doesn’t refer to that object as its parent, this parent-child pair is invalid. Invalid parent-child pairs can prevent an assistive app from correctly traversing an app’s accessibility hierarchy.

**Action**. This test checks whether an element’s accessibility action is valid for that type of element.

### Run an audit for every screen

After you choose which types of tests to perform, you can begin auditing your UI. To test the accessibility of every workflow in your app, make sure to run an audit for each of the screens in your app. For example, a to-do list app might audit each of the following screens: first launch experience, login screen, empty to-do list, to-do list with tasks, and the screen for adding a new task.

Click the *Run Audit button* to begin an audit for the current screen. Accessibility Inspector runs the tests and displays the results for each. Every time you run an audit for the same app, a new audit result name with a corresponding number appears. Next to the audit result name is a summary of the issues, reporting the number of issues for each type of test.

### Interact with the audit issues

Each audit issue identifies a particular element in the UI that raises a potential accessibility concern. You can interact with these issues in Accessibility Inspector to get more details.

- To read a detailed explanation of the audit issue, click the dropdown next to the issue.

- To draw a highlight over the element in question, click the issue.

- To inspect the element in question in the *Inspection pane*, double-click the issue.

### Capture a screenshot of each audit issue

The Audits pane lets you quickly capture a screenshot of any audit issue from the most recent audit. Click the *Capture icon* next to an audit issue to show a screenshot of the current screen with a blue highlight over the element in question.

### View fix suggestions for audit issues

Each audit issue presents a corresponding fix suggestion to help you resolve that issue in your app. Click the *Fix suggestions icon* next to an audit issue to receive a fix suggestion for the element in question. For example, a fix suggestion might provide guidance for specific colors, font sizes, or APIs to use to address the audit issue.

### Export and save audit results

You might want to keep a record of audit results to share with app designers or reference later while resolving audit issues. To generate an HTML document with audit results for your app, choose File \> Save Audit Report As…

This export provides a single HTML file that contains a summary of every audit result from the Audits pane. You can navigate through the details of each result, including screenshots, descriptions, and fix suggestions for each audit issue.

### Add audits to your UI tests

In addition to performing accessibility audits manually in Accessibility Inspector, you can automate these audits in your UI tests. Calling performAccessibilityAudit(for:_:) on your XCUIApplication audits the current screen for accessibility issues the same way that running an audit in Accessibility Inspector does. If the UI test finds any audit issues, it automatically fails.

For more information about automating audits, see Perform accessibility audits for your app.

Performing accessibility audits is an excellent start to improving the accessibility of your app, but eliminating all audit issues that Accessibility Inspector reports doesn’t guarantee a fully accessible app. Always test your app with various assistive apps, such as VoiceOver, to make sure there are no problems.

