

- CloudKit
- CKSubscription
- CKSubscription.NotificationInfo
-  subtitleLocalizationArgs 

Instance Property

# subtitleLocalizationArgs

The fields for building a notification’s subtitle.

iOS 11.0+iPadOS 11.0+Mac Catalyst 13.1+macOS 10.13+visionOSwatchOS 6.0+Swift 4.2+

``` source
var subtitleLocalizationArgs: [CKRecord.FieldKey]? { get set }
```

## Discussion

This property is an array of field names that CloudKit uses to extract the corresponding values from the record that triggers the push notification. The values must be strings, numbers, or dates. Don’t specify keys that use other value types. CloudKit may truncate strings with a length greater than 100 characters when it adds them to a notification’s payload.

If you use `%@` for your substitution variables, CloudKit replaces those variables by traversing the array in order. If you use variables of the form `%n$@`, where `n` is an integer, `n` represents the index (starting at 1) of the item in the array to use. So, the first item in the array replaces the variable `%1$@`, the second item replaces the variable `%2$@`, and so on. You can use indexed substitution variables to change the order of items in the resulting string, which might be necessary when you localize your app’s content.

## See Also

### Accessing the Notification Subtitle

var subtitle: String?

The notification’s subtitle.

var subtitleLocalizationKey: String?

The key that identifies the localized string for the notification’s subtitle.

