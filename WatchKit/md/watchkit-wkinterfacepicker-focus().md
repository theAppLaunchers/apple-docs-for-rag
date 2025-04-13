

- WatchKit
- WKInterfacePicker
-  focus() 

Instance Method

# focus()

Configures the picker to receive input from the Digital Crown.

watchOS 2.0+

``` source
func focus()
```

## Discussion

The picker adds custom highlighting when it is configured as the target of crown input. For an interface that contains multiple pickers, you might use this method to switch the focus at an appropriate time. Because scrolling in an interface controller causes the picker to lose focus, you can also use this method to select the picker again later.

## See Also

### Managing Input from the Digital Crown

func resignFocus()

Removes focus from the picker, causing it to stop receiving input from the Digital Crown.

