

- Xcode
- Debugging
- Diagnosing memory, thread, and crash issues early
-  Use of deallocated memory 

Article

# Use of deallocated memory

Detects the use of deallocated memory.

## Overview

Use this check to detect when your code accesses deallocated memory, which can lead to unpredictable behavior. Available in Xcode 7 and later.

### Use of deallocated memory in Objective-C

In the following example, the `unsafePointer` variable has `__unsafe_unretained` ownership. Because there are no other objects that have a strong reference to it, the autorelease pool deallocates the variable, causing it to point to invalid memory.

```
__unsafe_unretained MyClass *unsafePointer;
@autoreleasepool {    
    MyClass *object = [MyClass new];
    unsafePointer = object;
}
NSLog(@"%d", unsafePointer->instanceVariable); 
// Error: unsafePointer is deallocated in autorelease pool
```

#### Solution

Use a `__strong` or `__weak` reference instead of `__unsafe_unretained`. Strong ownership ensures that you, or the system, can only deallocate an object when no strong references exist. Weak ownership has no effect on the life cycle of the object it refers to, but ensures that a variable is `nil` when you deallocate the object, or the system deallocates it.

### Use of deallocated pointer in Objective-C

This issue exists when using pointers to nonobject types, as well. In the following example, the pointer to the instance variable invalidates when deallocating the object:

```
int *unsafePointer;
@autoreleasepool {    
    MyClass *object = [MyClass new];
    unsafePointer = &object->instanceVariable;
}
NSLog(@"%d", *unsafePointer);
// Error: unsafePointer is invalidated when object is deallocated in autorelease pool
```

#### Solution

Use property accessors rather than direct access to instance variables and pointers whenever possible.

## See Also

### Address Sanitizer

Deallocation of deallocated memory

Detects attempts to free deallocated memory.

Deallocation of nonallocated memory

Detects attempts to free nonallocated memory.

Use of stack memory after function return

Detects when you access stack variable memory after its declaring function returns.

Use of out-of-scope stack memory

Detects access to variables outside of their declared scope.

Overflow and underflow of buffers

Detects when you access memory outside of a buffer’s boundaries.

Overflow of C++ containers

Detects when you access a C++ container outside its bounds.

