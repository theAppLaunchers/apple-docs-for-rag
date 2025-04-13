

- Swift
-  precondition(\_:\_:file:line:) 

Function

# precondition(\_:\_:file:line:)

Checks a necessary condition for making forward progress.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func precondition(
    _ condition: @autoclosure () -> Bool,
    _ message: @autoclosure () -> String = String(),
    file: StaticString = #file,
    line: UInt = #line
)
```

## Parameters 

`condition`  

The condition to test. `condition` is not evaluated in `-Ounchecked` builds.

`message`  

A string to print if `condition` is evaluated to `false` in a playground or `-Onone` build. The default is an empty string.

`file`  

The file name to print with `message` if the precondition fails. The default is the file where `precondition(_:_:file:line:)` is called.

`line`  

The line number to print along with `message` if the assertion fails. The default is the line number where `precondition(_:_:file:line:)` is called.

## Discussion

Use this function to detect conditions that must prevent the program from proceeding, even in shipping code.

- In playgrounds and `-Onone` builds (the default for Xcode’s Debug configuration): If `condition` evaluates to `false`, stop program execution in a debuggable state after printing `message`.

- In `-O` builds (the default for Xcode’s Release configuration): If `condition` evaluates to `false`, stop program execution.

- In `-Ounchecked` builds, `condition` is not evaluated, but the optimizer may assume that it *always* evaluates to `true`. Failure to satisfy that assumption is a serious programming error.

## See Also

### Testing

func assert(@autoclosure () -> Bool, @autoclosure () -> String, file: StaticString, line: UInt)

Performs a traditional C-style assert with an optional message.

func assertionFailure(@autoclosure () -> String, file: StaticString, line: UInt)

Indicates that an internal consistency check failed.

func preconditionFailure(@autoclosure () -> String, file: StaticString, line: UInt) -> Never

Indicates that a precondition was violated.

