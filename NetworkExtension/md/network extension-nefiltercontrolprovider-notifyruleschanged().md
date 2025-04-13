

- Network Extension
- NEFilterControlProvider
-  notifyRulesChanged() 

Instance Method

# notifyRulesChanged()

Notify the Filter Data Provider that the filtering rules have changed on disk.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.1+visionOS 1.0+

``` source
func notifyRulesChanged()
```

## Discussion

The Filter Control Provider can call this method to notify the Filter Data Provider that the rules changed. It is only necessary to call this method when the update to the rules was not a direct result of a call to handleNewFlow(_:completionHandler:).

## See Also

### Handling requests for new rules

func handleNewFlow(NEFilterFlow, completionHandler: (NEFilterControlVerdict) -> Void)

Handle a request for new filtering rules.

