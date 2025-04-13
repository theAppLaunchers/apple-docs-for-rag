

- Xcode
- Testing
-  Improving code assessment by organizing tests into test plans 

Article

# Improving code assessment by organizing tests into test plans

Control the information you receive from your tests at different stages in the software engineering process by creating and configuring test plans.

## Overview

A mature project benefits from many tests that cover a variety of scenarios. Tests can verify code behavior or measure performance; they can test different products, or the same product on different targets or configurations. They can be long-running UI tests that exercise complex workflows or small unit tests that exercise individual functions, as described in Testing.

Control the information you receive from your tests at different stages in the software engineering process by organizing these tests into test plans, and configuring how Xcode executes the test plans. For example, you can create a test plan to run only the unit tests for a module while developing and debugging that module, and a second test plan to run all unit, integration, and UI tests before submitting your app to the App Store.

With Swift Testing, you can declare and add *tags*, annotations that identify tests that share common characteristics, to your tests.

You might add tags to specify:

- priority level (critical, normal, low)

- kind (unit, integration, performance)

- cadence (presubmission, daily, prerelease)

- functional area

- dependancies

In Xcode 16 and later, you can use tags in your test plans to specify which tests to include. For more information about declaring tags and adding tags to test, see Adding tags to tests. For more information about migrating your existing unit test to Swift Testing, see Migrating a test from XCTest.

Note

Tags aren’t a replacement for test suites. Suites impose hierarchical structure on test functions at the source level, while tags help you associate tests from different files, suites, and targets.

### Create schemes to associate test targets with products

A scheme instructs Xcode to use specific targets when you invoke the building, testing, running, analyzing, profiling, and archiving actions, shown in the figure below. In the test action for a scheme, include the target for the product under test along with the test targets that contain tests relevant to that product.

For information on creating Xcode schemes and assigning targets to schemes, see Customizing the build schemes for a project.

If your product has multiple targets — like an iOS app that contains a static library and a widget extension — create a scheme for each of the individual targets in addition to an “umbrella” scheme that builds the whole product suitable for release. Developers on your team can use the more specific scheme when working on tasks in each target, running only the tests relevant to that target to get faster feedback. When they are ready to integrate their changes, developers can get better assurance that they have not introduced regressions by running the complete collection of tests in the umbrella scheme.

### Create test plans to organize the tests for a scheme

A *test plan* is a document in your Xcode project that describes which tests Xcode should run when a developer invokes the test action, shown in the figure below, and the configurations Xcode uses to run the tests.

You can create multiple test plans for the same scheme and use any of them when running tests from Xcode or in Terminal. You must choose one test plan as the default plan for the scheme; Xcode uses this plan to run tests when none is explicitly specified. Xcode creates a default test plan that includes all of the tests from the test targets built by your scheme.

To edit this test plan, choose Product \> Scheme \> Edit Test Plan. Xcode prompts you for a location to save the test plan.

To create additional test plans:

1.  Choose Product \> Test Plan \> New Test Plan.

2.  Enter a name for the new test plan.

3.  Choose a location to save the test plan.

4.  Click Create.

To select the default test plan for the current scheme:

1.  Choose Product \> Test Plan \> Manage Test Plans.

2.  Select the radio button in the Default column next to the desired test plan.

### Include or exclude tests from a test plan

Specify the test targets to use, along with any tags Xcode should use to determine which tests to include or exclude from a test plan:

1.  Select the test plan in the Project navigator.

2.  In the Tests pane, click Choose Targets to add test targets to the test plan.

3.  To include tests annotated with a tag, click the Include Tags text field and type the symbol name of one or more tags. Select Any Tag from the filter button to include a test when it matches any the tags you enter, and All Tags to include it only when it matches all of the tags.

4.  To exclude tests annotated with a tag, enter the symbol name of one or more tags to exclude in the Exclude Tags field. Select Any Tag from the filter button to exclude a test when it matches any the tags you enter, and All Tags to exclude it only when it matches all of the tags.

To include all your tests in the test plan, leave the Include Tags and Exclude Tags fields empty.

### Choose the test suites and functions to run in a test plan

To further filter the tests that Xcode runs for a given test plan, select the checkbox in the Included column next to an item in the test plan’s outline view. You can select or deselect any item that matches the conditions from the Include Tags and Exclude Tags fields. The items represent targets, suites, functions, and specific input parameters passed to parameterized test functions. Xcode displays the symbol names for tags under the Tags column next to the suites and functions they annotate. Hold the pointer over an item to display a right arrow button. Click the button to display the source code for that item in the Source editor.

If you exclude a test function or test case from a test plan, Xcode skips over the test function or test case and doesn’t provide feedback on their status. The only effect an excluded test function has on the outcome of the test action is if the test contains a build error, in which case the whole test action fails.

Swift Testing and XCTest support ways to modify the effect a test has on the outcome of a test action while still running it. In Swift Testing you use traits to control the runtime conditions under which test should run, see Enabling and disabling tests and Known issues to indicate tests you expect to fail. To skip a test because the execution platform or configuration is inappropriate for the test in XCTest, use XCTSkipIf(_:_:file:line:) or XCTSkipUnless(_:_:file:line:). To indicate that a test is expected to fail in XCTest, use XCTExpectFailure(_:options:).

### Adjust configurations for test plans

Each test plan contains one or more configurations that tell Xcode how to set up the runtime environment for the tests. In the Configurations tab of the test plan editor, shown in the figure below, you can set environment variables, enable additional checks such as the address sanitizer and memory management guards, and choose different localization settings for the code.

The values you can specify in a test plan configuration are:

Arguments Passed on Launch  
Command-line arguments to the product under test.

Environment Variables  
Values set in the tested product’s environment.

Target for Variable Expansion  
The target that Xcode should use as a basis for expanding build settings. For a list of the settings available, see Build settings reference.

Application Language  
The language used for localized strings in the product under test, or System Language to use the language specified in System Settings.

Application Region  
The region used for locale settings in the product under test, or System Region to use the region specified in System Settings.

Simulated Location  
The location returned when using location services during tests. Specify a location, None to use the location of the device running test, or a GPX file to simulate traveling a route during tests.

Automatic Screen Capture  
Specify whether the UI Automation test runner captures screenshots as it runs tests, and whether it deletes screenshots for passing tests.

Preferred Capture Format  
Specify whether the UI Automation test runner captures video or screenshots.

Localization Screenshots  
Gather screenshots of your app for localizers. For more information, see Creating screenshots of your app for localizers.

Distribution  
The method of distribution to use for the product under test.

Attachments  
Gather attachments with augmented information about test behavior. For more information, see attachments.

Collect Test Diagnostics on Failure  
Collect diagnostic information in any situation where a test fails, only when testing with `xcodebuild`, or never.

Execution Order  
Control whether Xcode runs tests in alphabetical order, or picks a random order each time. Running tests in a random order can uncover situations where your test’s behavior depends on actions taken in other tests.

Test Timeouts  
Control whether tests automatically fail after a set amount of time.

Default Test Execution Time Allowance(s)  
The number of seconds a test runs for by default before it automatically fails. The minimum value you can set is 60 seconds. Override this setting for an individual test by calling executionTimeAllowance. This value is ignored if Test Timeouts is set to No.

Maximum Test Execution Time Allowance(s)  
The maximum number of seconds a test can run for before it automatically fails. The minimum value you can set is 60 seconds. A test times out after the maximum test execution time allowance has elapsed, even if the test requests a longer execution time using executionTimeAllowance. This value is ignored if Test Timeouts is set to No.

Test Repetition Mode  
Choose whether tests are run once, repeated until they fail, repeated until they pass, or run a set number of times.

Maximum Test Repetitions  
The highest number of times a test is repeatedly run.

Relaunch Tests for Each Repetition  
Whether Xcode launches a new process for each test repetition.

Code Coverage  
Collect code coverage metrics during test runs.

Address Sanitizer  
Detect out-of-bounds access to memory, memory used after it has been freed, and other incorrect memory use.

Thread Sanitizer  
Detect thread-related race conditions.

Undefined Behavior Sanitizer  
Detect issues related to undefined behavior in the C programming language.

Main Thread Checker  
Detect issues caused by using API on background threads that should only be used on the main thread.

Malloc Scribble  
Write a specific value to freed memory, to support detecting incorrect use of freed memory.

Malloc Guard Edges  
Add guard pages before and after large allocations, to support detecting out-of-bounds memory use.

Guard Malloc  
Use a substitute version of the memory allocator with additional detection for incorrect memory uses.

Zombie Objects  
Replace deallocated objects with zombies that crash your app when they receive Objective-C messages.

Malloc Stack Logging  
Record the function call stack whenever memory is allocated.

For more information on the address sanitizer, thread sanitizer, undefined behavior sanitizer, and main thread checker, see Diagnosing memory, thread, and crash issues early.

To create additional test plan configurations, click the Add button. Xcode runs the tests specified in a test plan once for each of that plan’s configurations.

### Add a test plan to a scheme

You can associate a test plan with more than one scheme, to get the same test suites and functions included with the same configurations in multiple schemes. To add an existing test plan to a scheme, do the following:

1.  Choose Product \> Test Plan \> Manage Test Plans.

2.  Click the Add button below the list of test plans.

3.  Choose Add existing Test Plan.

4.  Select the test plan you want to add to the scheme.

### Run the tests specified in a test plan in Xcode

When Xcode runs the test action, it executes the tests in the active test plan once for each configuration in the test plan. To set the active test plan and run the tests specified in that plan, do the following:

1.  Choose Product \> Test Plan.

2.  Select the test plan you want to run.

3.  Choose Product \> Test.

For information about interpreting the results of tests in Xcode, see Running tests and interpreting results.

### Run tests from the command-line

To run tests using a specific test plan from the command-line, you must explicitly name the test plan to use. To discover the test plans for `SampleApp`, run the following:

```
```

To run the tests specified in the “Performance Tests” test plan, run the following:

```
```

To run the tests in the “Performance Tests” test plan, using only the configuration called “My Config”, run the following:

```
```

To run the tests in the “Performance Tests” test plan, using all configurations except “My Config”, run the following:

```
```

## See Also

### Test development

Adding tests to your Xcode project

Include test targets that build code to test the logic in your functions, check for integration issues, automate UI workflows, and measure performance.

Updating your existing codebase to accommodate unit tests

Remove coupling between components to increase test coverage and reliability.

Determining how much code your tests cover

Use code coverage to focus new test development on areas that lack adequate testing.

