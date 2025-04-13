

- Swift
- Imported C and Objective-C APIs
-  Using Imported Protocol-Qualified Classes in Swift 

Article

# Using Imported Protocol-Qualified Classes in Swift

Learn how imported Objective-C protocol-qualified classes and metaclasses are represented.

## Overview

Objective-C classes qualified by one or more protocols, like the one in the example below, are imported by Swift as protocol composition types. The following Objective-C property refers to a view controller that also acts a data source and delegate:

```
@property UIViewController * myController;
```

When you import it, here’s the Swift interface:

```
var myController: UIViewController & UITableViewDataSource & UITableViewDelegate
```

An Objective-C protocol-qualified metaclass is imported by Swift as a protocol metatype, which is a type that represents the type of a protocol itself. For example, given the following Objective-C method that performs an operation on the specified class:

```
- (void)doSomethingForClass:(Class)codingClass;
```

When you import it, here’s the Swift interface:

```
func doSomething(for codingClass: NSCoding.Type)
```

## See Also

### Objective-C APIs

Using Imported Lightweight Generics in Swift

Understand the constraints of imported Obj-C lightweight generic type declarations.

