

- Xcode
- Debugging
- Diagnosing memory, thread, and crash issues early
-  Thread leaks 

Article

# Thread leaks

Detects when you don’t close threads after use.

## Overview

Use this check to detect threads you create using the `pthread_create(_:_:_:_:)` function without a corresponding call to the `pthread_join(_:_:)` function. Leaked threads can result in decreased performance and may lead to crashes. Available in Xcode 8 and later.

### Leaked thread in C

In the following example, the code creates a `thread` variable, but doesn’t close it after use:

```
void *run(){
    pthread_exit(0);
}
pthread_t thread;
pthread_create(&thread, NULL, run, NULL); // Error: thread leak
sleep(1);
```

#### Solution

Add a call to the `pthread_join(_:_:)` function.

```
void *run(){
    pthread_exit(0);
}
pthread_t thread;
pthread_create(&thread, NULL, run, NULL);
sleep(1);
pthread_join(thread, NULL); // Correct
```

Alternatively, you can create a detached thread by passing the `PTHREAD_CREATE_DETACHED` attribute to `pthread_create(_:_:_:_:)`, or calling `pthread_detach(_:)` on the thread after creation.

## See Also

### Thread Sanitizer

Data races

Detects unsynchronized access to mutable state across multiple threads.

Swift access races

Detects unsynchronized access to mutable state across multiple threads in Swift.

Races on collections and other APIs

Detects when one thread accesses a mutable object while another thread is writing to it.

Uninitialized mutexes

Detects when you use an uninitialized mutex.

