

- Xcode
- Debugging
- Diagnosing memory, thread, and crash issues early
-  Nonnull return value violation 

Article

# Nonnull return value violation

Detects when a function incorrectly returns null.

## Overview

Use this check to detect when a function with the `returns_nonnull` attribute, or a function with a return type that has the `_Nonnull` annotation, returns null. Available in Xcode 9 and later.

Note

The nonnull violation check for return types with the `_Nonnull` annotation is off by default. You can turn it on by enabling the `-fsanitize=nullability-return` compiler flag.

### Violation of the nonnull attribute for a function in C

In the following code, there is a violation of the `returns_nonnull` attribute of the `nonnull_returning_function` function:

```
__attribute__((returns_nonnull)) int *nonnull_returning_function(int *p) {
    return p; // Warning: NULL can be returned here
}
nonnull_returning_function(NULL); // Error: nonnull return value attribute violation
```

#### Solution

Correct logic errors, add any necessary null guards to the function, or remove the `returns_nonnull` attribute and rework the function caller logic accordingly.

### Violation of the nonnull annotation for a return type in C

The following code violates the `_Nonnull` annotation of the return type for the `nonnull_returning_function` function:

```
int *_Nonnull nonnull_returning_function(int *p) {
    return p; // Warning: NULL can be returned here
}
nonnull_returning_function(NULL); // Error: nonnull return value attribute violation
```

#### Solution

Correct logic errors, add any necessary null guards to the function, or remove the `_Nonnull` annotation and rework the function caller logic accordingly.

## See Also

### Undefined Behavior Sanitizer

Misaligned pointer

Detects when code accesses a misaligned pointer or creates a misaligned reference.

Invalid Boolean value

Detects when a program accesses a Boolean variable and its value isn’t true or false.

Out-of-bounds array access

Detects out-of-bounds access of arrays.

Invalid enumeration value

Detects when an enumeration variable has an invalid value.

Reaching of unreachable point

Detects when a program reaches an unreachable point.

Dynamic type violation

Detects when an object has the wrong dynamic type.

Invalid float cast

Detects out-of-range casts to, from, or between floating-point types.

Division by zero

Detects division where the divisor is zero.

Nonnull argument violation

Detects when an argument incorrectly receives a null value.

Nonnull variable assignment violation

Detects when you incorrectly assign null to a variable.

Null reference creation and null pointer dereference

Detects the creation of null references and null pointer dereferences.

Invalid object size

Detects invalid pointer casts due to differences in the sizes of types.

Invalid shift

Detects invalid and overflowing shifts.

Integer overflow

Detects overflow in arithmetic.

Invalid variable-length array

Detects negative array bounds.

