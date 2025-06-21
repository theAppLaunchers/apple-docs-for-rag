*   [Xcode](/documentation/xcode)
*   [Build system](/documentation/xcode/build-system)
*   Enabling enhanced security for your app

Article

# Enabling enhanced security for your app

Detect out-of-bounds memory access, use of freed memory, and other potential vulnerabilities.

## [Overview](/documentation/Xcode/enabling-enhanced-security-for-your-app#Overview)

People’s devices can contain a large amount of sensitive data that an attacker might want to use for malicious purposes. If your app contains any security vulnerabilities, an attacker may exploit the vulnerabilities to access or modify the data in your app, extension, App Clip, or device driver.

Adopt the Enhanced Security capability in your Xcode project to enable a collection of build settings and entitlements designed to mitigate certain common vulnerabilities in your app. Review the behavior of your app with these settings enabled, and fix any problems that Xcode and the system report.

Important

The Enhanced Security capability enables security checks that can impact the performance and stability of an app that isn’t designed and built with security in mind. Review your app’s threat model, and only adopt the Enhanced Security capability if the protections it enables align with your app’s security goals. Test your app thoroughly to ensure that you address all situations in which Enhanced Security mitigations could lead to your app crashing.

Enhanced Security is available for apps and extensions built for iOS, iPadOS, macOS, and visionOS; App Clips in iOS; and DriverKit extensions in iPadOS and macOS.

### [Adopt the Enhanced Security capability](/documentation/Xcode/enabling-enhanced-security-for-your-app#Adopt-the-Enhanced-Security-capability)

Navigate to the Signing and Capabilities editor for your Xcode target, and click the Add Capability button. From the list of capabilities, select Enhanced Security. Xcode adds the following entitlements to your app’s provisioning profile:

*   [`Enhanced Security`](/documentation/BundleResources/Entitlements/com.apple.security.hardened-process.enhanced-security-version): Xcode sets the value to `1`.
    
*   [`Hardened Process`](/documentation/BundleResources/Entitlements/com.apple.security.hardened-process): Xcode sets the value to `true`.
    
*   [`Hardened Heap`](/documentation/BundleResources/Entitlements/com.apple.security.hardened-process.hardened-heap): Xcode sets the value to `true`.
    
*   [`Additional Runtime Platform Restrictions`](/documentation/BundleResources/Entitlements/com.apple.security.hardened-process.platform-restrictions): Xcode sets the value to `2`.
    
*   [`Enable Read-Only Platform Memory`](/documentation/BundleResources/Entitlements/com.apple.security.hardened-process.dyld-ro): Xcode sets the value to `true`.
    

When you add the Enhanced Security capability to your target, use the checkboxes in the Enhanced Security capability of the Signing and Capabilities editor to adopt specific hardening features. Additionally, click Enable Build Settings to add security-related build settings to all targets in your project, which turns on certain hardening features.

The sections below describe the individual entitlements and build settings that comprise Enhanced Security, and the steps you can take to adopt the hardening features in your code. Additionally, the sections describe how you can turn off any individual hardening setting, in case you need to do so while you prepare your code to support the additional protections.

### [Prepare your app for pointer authentication](/documentation/Xcode/enabling-enhanced-security-for-your-app#Prepare-your-app-for-pointer-authentication)

The Enhanced Security capability includes additional runtime platform restrictions, which Xcode enables by default for your app when you adopt the capability by setting the `ENABLE_POINTER_AUTHENTICATION` build setting to `Yes`. With these additional runtime platform restrictions enabled, Xcode builds your app for the `arm64e` architecture and enables _pointer authentication_.

When pointer authentication is enabled, the system generates signature metadata for pointers that your app creates by allocating memory or constructing C++ objects. Then the system validates that the signatures are unchanged when your app accesses the memory addressed by those pointers. If the signature for a pointer isn’t valid, the system encounters an exception and crashes your app. Doing so helps to protect against an attacker overwriting memory in your app to compromise the app’s control flow.

To adopt pointer authentication, use the `__ptrauth` type qualifier to instruct the compiler to generate pointer authentication protection for variables in your code that store data and function pointers.

When a variable uses pointer authentication, the system throws an error if you overwrite its value with a raw pointer in your code, or copy its value to another variable that uses a different pointer authentication schema. If your app does either of these, the system encounters an exception and crashes your app. Instead, sign the pointer before storing it, re-signing it for a different use if necessary. For more information, see [Improving control flow integrity with pointer authentication](/documentation/Apple-Silicon/improving-control-flow-integrity-with-pointer-authentication).

If you need to turn off pointer authentication for your target, uncheck the Authenticate Pointers checkbox in the Signing and Capabilities editor, or set the `ENABLE_POINTER_AUTHENTICATION` build setting to `No`.

### [Adopt typed allocator support](/documentation/Xcode/enabling-enhanced-security-for-your-app#Adopt-typed-allocator-support)

When you adopt the Enhanced Security capability, Xcode configures build settings to enable the compiler’s typed allocator in C and C++ code. For more information on the typed allocator and the changes you need to make in your code if you use custom memory-allocator wrapper functions, see [Adopting type-aware memory allocation](/documentation/xcode/adopting-type-aware-memory-allocation).

To turn off typed allocator support for your target, uncheck the Enable Typed Allocators checkbox in the Signing and Capabilities editor, or set the `CLANG_ENABLE_C_TYPED_ALLOCATOR_SUPPORT` build setting to `No` for C code, and the `CLANG_ENABLE_CPLUSPLUS_TYPED_ALLOCATOR_SUPPORT` build setting to `No` for C++ code.

### [Initialize stack variables to zero](/documentation/Xcode/enabling-enhanced-security-for-your-app#Initialize-stack-variables-to-zero)

When you enable the Enhanced Security capability for your target, Xcode sets the `CLANG_TRIVIAL_AUTO_VAR_INIT` build setting to the string `zero`. This build setting configures the compiler to intialize automatic variables in your code with zeroes. Doing so helps to protect against particular types of use-after-free vulnerability, because your app zeroes out previous values in stack memory before it reuses them for other variables.

If you need to turn off zero-initialization of stack variables for your target, set the `CLANG_TRIVIAL_AUTO_VAR_INIT` build setting to `uninitialized`.

### [Address security-related compiler warnings](/documentation/Xcode/enabling-enhanced-security-for-your-app#Address-security-related-compiler-warnings)

When you enable the Enhanced Security capability for your target, Xcode configures some compiler warnings that help to identify potentially insecure code. These are:

`-Wshadow`

The compiler warns you when a variable declaration _shadows_ another variable or a type alias; that is, the variable has the same name as another entity, and uses of the variable’s name in the current scope use the newly declared variable when they might intend to use the original entity. Turn this warning off by setting the `GCC_WARN_SHADOW` build setting to `No`.

`-Wempty-body`

The compiler warns you when the body of a control flow statement, such as a `for` loop or `if` statement, doesn’t contain any code. Turn this warning off by setting the `CLANG_WARN_EMPTY_BODY` build setting to `No`.

Xcode additionally sets the `ENABLE_SECURITY_COMPILER_WARNINGS` target build setting to `Yes`. This turns on a collection of security-related compiler warnings that Xcode reports in the Issues navigator when you build the target. These additional warnings are:

`-Wbuiltin-memcpy-chk-size`

The compiler warns you when the destination buffer in a `memcpy` operation is smaller than the number of bytes you copy into it.

`-Wformat-nonliteral`

The compiler warns you when the format string for a `printf`\-like function isn’t a string literal.

`-Warray-bounds`

The compiler warns you when an array index is before the beginning of an array, or past the end of an array; or that an array argument you pass to a function is smaller than the minimum size the function expects.

`-Warray-bounds-pointer-arithmetic`

The compiler warns you when a calculated pointer value results in a pointer that’s before the beginning of an array, or past the end of an array.

`-Wsuspicious-memaccess`

The compiler warns you when a memory operation acts on a dynamic class and might operate on its `vtable` pointer; the arguments to `memset` are transposed; a memory operation moves or copies an object that isn’t trivially copyable; or the size requested for a memory operation is `0`, or the result of calling `sizeof` on the source pointer.

`-Wsizeof-array-div`

The compiler warns you when a `sizeof` calculation doesn’t correctly calculate the number of elements in an array, due to using incorrect types.

`-Wsizeof-pointer-div`

The compiler warns you when a `sizeof` calculation results in the size of a pointer, instead of the size of the array it refers to.

`-Wreturn-stack-address`

The compiler warns you when your code returns an address on the stack (for example, the address of a local variable) to the calling function.

If you need to turn off the additional compiler warnings that Enhanced Security configures for your target, set the `ENABLE_SECURITY_COMPILER_WARNINGS` build setting to `No`.

### [Adopt C++ standard library hardening and compiler bounds checking](/documentation/Xcode/enabling-enhanced-security-for-your-app#Adopt-C++-standard-library-hardening-and-compiler-bounds-checking)

When you enable the Enhanced Security capability for your target, Xcode sets the `ENABLE_CPLUSPLUS_BOUNDS_SAFE_BUFFERS` target build setting to `YES`. This enables a collection of safety checks in the C++ standard library. Specifically, it enables the _fast_ hardening mode.

In fast mode, the C++ standard library performs the following assertion checks in your code that uses standard library container types:

Valid element access

The standard library checks that when your code accesses collection elements, including elements contained in the single-element collection types `std::function` and `std::optional`, the elements exist in the collection.

Valid input range

The standard library checks that ranges you pass to standard algorithm functions are valid, and that if you define a range using a `begin` iterator and a sentinel, the library can reach the sentinel from the iterator.

The standard library calculates these checks in constant time. If a hardening assertion fails (that is, if the check evaluates to `false`), the system encounters an exception and crashes your app.

To change the C++ standard library hardening mode for a single file in your project, define the `_LIBCPP_HARDENING_MODE` macro with one of the following values:

`_LIBCPP_HARDENING_MODE_NONE`

No hardening

`_LIBCPP_HARDENING_MODE_FAST`

Fast mode

`_LIBCPP_HARDENING_MODE_EXTENSIVE`

Extensive hardening

`_LIBCPP_HARDENING_MODE_DEBUG`

All hardening checks

If you define the macro in code, you need to place the definition at the beginning of the file, before you include any standard library headers.

Additionally, setting `ENABLE_CPLUSPLUS_BOUNDS_SAFE_BUFFERS` to `Yes` adds compiler warnings on unsafe buffer usage in C++, configuring the compiler to treat these warnings as errors. The C++ compiler encounters an error if it detects that your code:

*   Indexes an array, performs pointer arithmetic, or uses an unsafe C standard library function on a raw pointers
    
*   Calls `operator` on a smart pointer that refers to a list of objects
    
*   Constructs a `std::span` object using the two-argument (pointer and size) constructor
    

To turn off C++ standard library hardening and compiler bounds checking for your target, set the `ENABLE_CPLUSPLUS_BOUNDS_SAFE_BUFFERS` build setting to `No`.

For more information on C++ standard library hardening, see [Hardening Modes](https://libcxx.llvm.org/Hardening.html) in the LLVM documentation.

### [Adopt additional run-time restrictions](/documentation/Xcode/enabling-enhanced-security-for-your-app#Adopt-additional-run-time-restrictions)

When you enable the Enhanced Security capability for your target, Xcode adds the [`Additional Runtime Platform Restrictions`](/documentation/BundleResources/Entitlements/com.apple.security.hardened-process.platform-restrictions) entitlement to your app. This entitlement informs the system to perform additional checks on dynamic libraries your app or extension loads, and on Mach messages your app or extension receives from other processes.

If you use [XPC](/documentation/XPC) for inter-process communication (IPC) and don’t use Mach IPC traps, or don’t have any explicit IPC mechanism in your app or extension, enabling additional run-time restrictions turns on protections that are unlikely to require you to make any code changes.

In apps and extensions that use Mach IPC traps, additional run-time restrictions turn potentially insecure situations into crashes to avoid giving an attacker privileged access to your process via Mach ports. For information on interpreting these crashes and changes to your code that avoid potentially insecure use of Mach messaging APIs, see [Conforming to Mach IPC security restrictions](/documentation/xcode/conforming-to-mach-ipc-security-restrictions).

To turn off additional run-time restrictions for your target, uncheck the Enable Additional Runtime Platform Restrictions checkbox in the Signing and Capabilities editor.

### [Adopt read-only memory for internal platform state](/documentation/Xcode/enabling-enhanced-security-for-your-app#Adopt-read-only-memory-for-internal-platform-state)

When you enable the Enhanced Security capability for your target, Xcode adds the [`Enable Read-Only Platform Memory`](/documentation/BundleResources/Entitlements/com.apple.security.hardened-process.dyld-ro) entitlement to your app. This entitlement informs the system to mark regions of memory in your process that the platform uses for its internal state as read-only.

In most situations, this additional protection doesn’t require you to make any changes. If your app modifies data in the protected regions — for example, it modifies the value of `const` data sections — the system crashes your app when you adopt this entitlement. To fix the crash, remove the code that modifies the read-only memory regions.

If you need to turn off read-only memory for the dynamic loader, uncheck the Enable Read-Only Platform Memory checkbox in the Signing and Capabilities editor.

### [Adopt bounds checking in C](/documentation/Xcode/enabling-enhanced-security-for-your-app#Adopt-bounds-checking-in-C)

When you enable build settings for Enhanced Security, Xcode sets the `ENABLE_C_BOUNDS_SAFETY` build setting with the value `Yes` for all targets in your app.

The `ENABLE_C_BOUNDS_SAFETY` build setting adds the `-fbounds-safety` flag to the compiler invocation when Xcode compiles C source files. This is an extension to the C programming language that prevents out-of-bounds memory access by enforcing bounds safety.

The compiler assumes that every pointer in your code that it compiles with the `-fbounds-safety` flag points to a single object, and emits an error if you attempt to perform pointer arithmetic using the pointer, or use a subscript to access an array element based on the pointer. To indicate that a pointer identifies a collection of objects of a given size, use one of these annotations:

`__counted_by(N)`

The pointer locates the first element in an array of length `N`. The parameter `N` can be a constant, an arithmetic expression, or the name of a variable.

`__sized_by(N)`

The pointer is the start of a memory buffer of size `N` bytes. The parameter `N` can be a constant, an arithmetic expression, or the name of a variable.

`__ended_by(P)`

The pointer is in a memory region with upper bound `P`. The parameter `P` is the first pointer that’s beyond the last element in the memory region.

If the pointer can potentially be `NULL`, add the suffix `_or_null` to the annotation name; for example, `__counted_by_or_null(N)`.

To indicate that a pointer identifies a collection of objects that has a particular sentinel value signifying the end — for example, a null-terminated string — use one of these annotations:

`__null_terminated`

The sentinal value is `0`.

`__terminated_by(T)`

The sentinal value is `T`.

To indicate that a pointer refers to a value that you haven’t audited for bounds safety, add the `__unsafe_indexable` annotation.

For more information, see [`-fbounds-safety`: Enforcing bounds safety for C](https://clang.llvm.org/docs/BoundsSafety.html) on the LLVM website.

To turn off bounds checking in C, set the value of the `ENABLE_C_BOUNDS_SAFETY` build setting to `No`.

### [Adopt enhanced security for extensions](/documentation/Xcode/enabling-enhanced-security-for-your-app#Adopt-enhanced-security-for-extensions)

Enabling the Enhanced Security capability for your projects adds build settings and entitlements to your app and extension targets. To enable all protections and ensure your extension works correctly with Enhanced Security, you need to make some additional code changes. For more information, see [Creating extensions with enhanced security](/documentation/xcode/creating-extensions-with-enhanced-security).

## [See Also](/documentation/Xcode/enabling-enhanced-security-for-your-app#see-also)

### [Security and privacy](/documentation/Xcode/enabling-enhanced-security-for-your-app#Security-and-privacy)

[

Verifying the origin of your XCFrameworks](/documentation/xcode/verifying-the-origin-of-your-xcframeworks)

Discover who signed a framework, and take action when that changes.

[

Creating extensions with enhanced security](/documentation/xcode/creating-extensions-with-enhanced-security)

Reduce opportunities for an attacker to target your app through its extensions.

[

Adopting type-aware memory allocation](/documentation/xcode/adopting-type-aware-memory-allocation)

Reduce the opportunities to treat pointers as data in your code.

[

Conforming to Mach IPC security restrictions](/documentation/xcode/conforming-to-mach-ipc-security-restrictions)

Avoid crashes and potentially insecure situations associated with Mach messages.