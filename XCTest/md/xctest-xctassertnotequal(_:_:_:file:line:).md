

- XCTest
-  XCTAssertNotEqual(\_:\_:\_:file:line:) 

Function

# XCTAssertNotEqual(\_:\_:\_:file:line:)

Asserts that two values are not equal.

``` source
func XCTAssertNotEqual(
    _ expression1: @autoclosure () throws -> T,
    _ expression2: @autoclosure () throws -> T,
    _ message: @autoclosure () -> String = "",
    file: StaticString = #filePath,
    line: UInt = #line
) where T : Equatable
```

## Parameters 

`expression1`  

An expression of type `T`, where `T` is `Equatable`.

`expression2`  

A second expression of type `T`, where `T` is `Equatable`.

`message`  

An optional description of a failure.

`file`  

The file where the failure occurs. The default is the filename of the test case where you call this function.

`line`  

The line number where the failure occurs. The default is the line number where you call this function.

## See Also

### Tests for Equality and Inequality

func XCTAssertEqual&lt;T>(@autoclosure () throws -> T, @autoclosure () throws -> T, @autoclosure () -> String, file: StaticString, line: UInt)

Asserts that two values are equal.

