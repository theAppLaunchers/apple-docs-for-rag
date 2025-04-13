

- Contacts UI
- CNContactPickerViewController
-  delegate 

Instance Property

# delegate

The delegate to be notified when the user selects a contact or a property.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.1+visionOS 1.0+

``` source
@MainActor
weak var delegate: (any CNContactPickerDelegate)? { get set }
```

## See Also

### Responding to User Interactions

protocol CNContactPickerDelegate

The methods that you implement to respond to contact-picker user events.

