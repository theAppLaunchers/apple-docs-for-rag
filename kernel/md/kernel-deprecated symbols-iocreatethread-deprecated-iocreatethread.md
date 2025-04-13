

- Kernel
- Deprecated Symbols
-  IOCreateThread Deprecated

Function

# IOCreateThread

Deprecated function - use kernel_thread_start(). Create a kernel thread.

macOS 10.0–10.6Deprecated

``` source
IOThread IOCreateThread(IOThreadFunc function, void *argument);
```

## Parameters 

`function`  

A C-function pointer where the thread will begin execution.

`argument`  

Caller specified data to be passed to the new thread.

## Return Value

An IOThread identifier for the new thread, equivalent to an osfmk thread_t.

## Discussion

This function creates a kernel thread, and passes the caller supplied argument to the new thread. Warning: the value returned by this function is not 100% reliable. There is a race condition where it is possible that the new thread has already terminated before this call returns. Under that circumstance the IOThread returned will be invalid. In general there is little that can be done with this value except compare it against 0. The thread itself can call IOThreadSelf() 100% reliably and that is the prefered mechanism to manipulate the IOThreads state.

