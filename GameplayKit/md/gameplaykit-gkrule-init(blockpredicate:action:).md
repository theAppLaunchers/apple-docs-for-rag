

- GameplayKit
- GKRule
-  init(blockPredicate:action:) 

Initializer

# init(blockPredicate:action:)

Creates a rule whose predicate is evaluated and action is executed through the specified blocks.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.1+macOS 10.11+tvOS 9.0+visionOS 1.0+

``` source
convenience init(
    blockPredicate predicate: @escaping (GKRuleSystem) -> Bool,
    action: @escaping (GKRuleSystem) -> Void
)
```

## Parameters 

`action`  

A block to be invoked after the rule’s predicate is satisfied. The block takes a single parameter:

system  
The rule system in whose context the rule is executing its action.

## Return Value

A new rule object.

## Discussion

Rules created using this method can run arbitrary code in their predicate and action, but do not encode their predicate or action when archiving with the NSKeyedArchiver class. For archivable rules, use the GKRule methods listed in Creating Data-Driven Rules.

