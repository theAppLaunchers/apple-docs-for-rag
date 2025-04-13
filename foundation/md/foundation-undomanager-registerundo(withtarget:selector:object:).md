

- Foundation
- UndoManager
-  registerUndo(withTarget:selector:object:) 

Instance Method

# registerUndo(withTarget:selector:object:)

Registers the selector of the specified target to implement a single undo operation that the target receives.

iOS 3.0+iPadOS 3.0+Mac Catalyst 13.1+macOS 10.0+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func registerUndo(
    withTarget target: Any,
    selector: Selector,
    object: Any?
)
```

## Parameters 

`target`  

The target of the undo operation.

The undo manager maintains an unowned reference to `target` to prevent retain cycles.

`selector`  

The selector for the undo operation.

`object`  

The argument sent with the selector.

The undo manager maintains a strong reference to ``` anO``bject ```.

## Discussion

Use registerUndo(withTarget:selector:object:) to register a selector for an undo operation. To register a selector on the undo stack, you also need to make the method available to the Objective-C runtime by applying the @`objc` attribute to the method. For more on how to create a selector, see Selectors.

Calling this method also clears the redo stack.

The following example demonstrates how to register and use a selector on the undo stack by modeling a `Garden` class with two methods: `plant(flower:)` and `pluck(flower:)`. The `plant(flower:)` method removes a flower from the garden while `pluck(flower:)` adds a flower such that effectively, the two methods are inverse operations of each other. This inverse quality makes it ideal to register `plant(flower:)` and `pluck(flower:)` to be each other’s undo operation.

```
class Garden {
    typealias FlowerName = String

    var flowers: [FlowerName: Int]
    var manager = UndoManager()

    init(flowers: [FlowerName: Int]) {
        self.flowers = flowers
    }
    @objc func plant(flower: FlowerName) {
        flowers[flower, default: 0] += 1
        manager.registerUndo(withTarget: self, selector: #selector(pluck), object: flower)
    }
    @objc func pluck(flower: FlowerName) {
        flowers[flower, default: 0] -= 1
        manager.registerUndo(withTarget: self, selector: #selector(plant), object: flower)
    }
}
var garden = Garden(flowers: ["orchid" : 2, "lavender": 1, "violet": 2])
garden.pluck(flower: "orchid")
//garden.flowers == ["orchid" : 1, "lavender": 1, "violet": 2]
garden.manager.undo()
//garden.flowers == ["orchid" : 2, "lavender": 1, "violet": 2]
```

Important

This method raises internalInconsistencyException if it’s called when no undo group has been established using beginUndoGrouping(). Undo groups are usually set by default, and you rarely need to create a top-level undo group explicitly.

## See Also

### Related Documentation

func undoNestedGroup()

Performs the undo operations in the last undo group (whether top-level or nested), recording the operations on the redo stack as a single group.

var groupingLevel: Int

The number of nested undo groups (or redo groups, if redo is the most recent operation) in the current event loop.

Introduction to Undo Architecture

### Registering undo operations

func registerUndo&lt;TargetType>(withTarget: TargetType, handler: (TargetType) -> Void)

Registers the specified closure to implement a single undo operation that the target receives.

func prepare(withInvocationTarget: Any) -> Any

Prepares the undo manager for invocation-based undo with the given target as the subject of the next undo operation.

