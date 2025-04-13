

- Core Services
- File System Events
- FSEventStreamCreateFlags
-  kFSEventStreamCreateFlagUseCFTypes 

Global Variable

# kFSEventStreamCreateFlagUseCFTypes

Mac Catalyst 13.0+macOS 10.5+

``` source
var kFSEventStreamCreateFlagUseCFTypes: Int { get }
```

## Discussion

The framework will invoke your callback function with CF types rather than raw C types (i.e., a CFArrayRef of CFStringRefs, rather than a raw C array of raw C string pointers). See FSEventStreamCallback.

