

- XCTest
- XCTSkip
-  init(\_:file:line:) 

Initializer

# init(\_:file:line:)

Intitializes an error to skip a test.

``` source
init(
    _ message: String? = nil,
    file: StaticString = #filePath,
    line: UInt = #line
)
```

## Parameters 

`message`  

A description of the skip.

`file`  

The file in which the skip occurred. This value defaults to the file name of the test case in which this error was initialized.

`line`  

The line number on which the skip occurred. This value defaults to the line number on which this error was initialized.

