

- Foundation
- Bundle
-  principalClass 

Instance Property

# principalClass

The bundle’s principal class.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.0+macOS 10.0+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
var principalClass: AnyClass? { get }
```

## Discussion

This property is set after ensuring that the code containing the definition of the class is dynamically loaded. If the bundle encounters errors in loading or if it can’t find the executable code file in the bundle directory, this property is `nil`.

The principal class typically controls all the other classes in the bundle; it should mediate between those classes and classes external to the bundle. Classes (and categories) are loaded from just one file within the bundle directory. The bundle obtains the name of the code file to load from the dictionary returned from infoDictionary, using “`NSExecutable`” as the key. The bundle determines its principal class in one of two ways:

- It first looks in its own information dictionary, which extracts the information encoded in the bundle’s property list (`Info.plist`). The bundle obtains the principal class from the dictionary using the key `NSPrincipalClass`. For non-loadable bundles (applications and frameworks), if the principal class is not specified in the property list, this property is `nil`.

- If the principal class is not specified in the information dictionary, the bundle identifies the first class loaded as the principal class. When several classes are linked into a dynamically loadable file, the default principal class is the first one listed on the `ld` command line. In the following example, Reporter would be the principal class:

```
ld -o myBundle -r Reporter.o NotePad.o QueryList.o
```

The order of classes in Xcode’s project browser is the order in which they will be linked. To designate the principal class, control-drag the file containing its implementation to the top of the list.

As a side effect of code loading, the receiver posts didLoadNotification after all classes and categories have been loaded; see `Notifications` for details.

The following method obtains a bundle by specifying its path (bundleWithPath:), then loads the bundle with principalClass and uses the principal class object to allocate and initialize an instance of that class:

```
- (void)loadBundle:(id)sender
{
    Class exampleClass;
    id newInstance;
    NSString *path = @"/tmp/Projects/BundleExample/BundleExample.bundle";
    NSBundle *bundleToLoad = [NSBundle bundleWithPath:path];
    if (exampleClass = bundleToLoad.principalClass) {
        newInstance = [[exampleClass alloc] init];
        [newInstance doSomething];
    }
}
```

## See Also

### Related Documentation

func load() -> Bool

Dynamically loads the bundle’s executable code into a running program, if the code has not already been loaded.

var infoDictionary: [String : Any]?

A dictionary, constructed from the bundle’s `Info.plist` file, that contains information about the receiver.

### Getting Classes from a Bundle

func classNamed(String) -> AnyClass?

Returns the `Class` object for the specified name.

class let didLoadNotification: NSNotification.Name

A notification that lets observers know when classes are dynamically loaded.

let NSLoadedClasses: String

A constant used as a key for the `userInfo` dictionary of a didLoadNotification notification that corresponds to an array of names of each class that was loaded.

