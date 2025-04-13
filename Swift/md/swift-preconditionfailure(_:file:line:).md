

- Swift
-  preconditionFailure(\_:file:line:) 

Function

# preconditionFailure(\_:file:line:)

Indicates that a precondition was violated.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func preconditionFailure(
    _ message: @autoclosure () -> String = String(),
    file: StaticString = #file,
    line: UInt = #line
) -> Never
```

## Parameters 

`message`  

A string to print in a playground or `-Onone` build. The default is an empty string.

`file`  

The file name to print with `message`. The default is the file where `preconditionFailure(_:file:line:)` is called.

`line`  

The line number to print along with `message`. The default is the line number where `preconditionFailure(_:file:line:)` is called.

## Discussion

Use this function to stop the program when control flow can only reach the call if your API was improperly used and execution flow is not expected to reach the call—for example, in the `default` case of a `switch` where you have knowledge that one of the other cases must be satisfied.

This function’s effect varies depending on the build flag used:

- In playgrounds and `-Onone` builds (the default for Xcode’s Debug configuration), stops program execution in a debuggable state after printing `message`.

- In `-O` builds (the default for Xcode’s Release configuration), stops program execution.

- In `-Ounchecked` builds, the optimizer may assume that this function is never called. Failure to satisfy that assumption is a serious programming error.

## See Also

### Testing

func assert(@autoclosure () -> Bool, @autoclosure () -> String, file: StaticString, line: UInt)

Performs a traditional C-style assert with an optional message.

func assertionFailure(@autoclosure () -> String, file: StaticString, line: UInt)

Indicates that an internal consistency check failed.

func precondition(@autoclosure () -> Bool, @autoclosure () -> String, file: StaticString, line: UInt)

Checks a necessary condition for making forward progress.

