

- Security
-  SecTaskCreateWithAuditToken(\_:\_:) 

Function

# SecTaskCreateWithAuditToken(\_:\_:)

Creates a task object for the task that sent the Mach message represented by the audit token.

Mac Catalyst 13.0+macOS 10.0+

``` source
func SecTaskCreateWithAuditToken(
    _ allocator: CFAllocator?,
    _ token: audit_token_t
) -> SecTask?
```

## Parameters 

`allocator`  

An allocator. Pass `NULL` to use the default.

`token`  

The audit token of a Mach message.

## Return Value

A new task, or `NULL` on error. In Objective-C, call the CFRelease function to free this task’s memory when you are done with it.

