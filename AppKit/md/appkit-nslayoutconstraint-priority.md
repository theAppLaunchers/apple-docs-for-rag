

- AppKit
- NSLayoutConstraint
-  priority 

Instance Property

# priority

The priority of the constraint.

macOS 10.7+

``` source
var priority: NSLayoutConstraint.Priority { get set }
```

## Discussion

By default, all constraints are required; this property is set to required in macOS or `UILayoutPriorityRequired` in iOS.

If a constraint’s priority level is less than required in macOS or `UILayoutPriorityRequired` in iOS, then it is optional. Higher priority constraints are satisfied before lower priority constraints; however, optional constraint satisfaction is not all or nothing. If a constraint `a == b` is optional, the constraint-based layout system will attempt to minimize `abs(a-b)`.

Priorities may not change from nonrequired to required, or from required to nonrequired. An exception will be thrown if a priority of required in macOS or `UILayoutPriorityRequired` in iOS is changed to a lower priority, or if a lower priority is changed to a required priority after the constraints is added to a view. Changing from one optional priority to another optional priority is allowed even after the constraint is installed on a view.

Priorities must be greater than 0 and less than or equal to required in macOS or `UILayoutPriorityRequired` in iOS.

## See Also

### Getting the layout priority

struct Priority

Layout priority used to indicate the relative importance of constraints, allowing Auto Layout to make appropriate tradeoffs when satisfying the constraints of the system as a whole.

