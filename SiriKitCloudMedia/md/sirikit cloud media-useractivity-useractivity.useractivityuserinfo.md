

- SiriKit Cloud Media
- UserActivity
-  UserActivity.UserActivityUserInfo 

Object

# UserActivity.UserActivityUserInfo

A dictionary that contains service-specific state information necessary to continue an activity in a separate request.

SiriKit Cloud Media 1.0.2+

``` source
object UserActivity.UserActivityUserInfo
```

## Discussion

Customize the contents of this dictionary with information your service needs to continue a playback activity. Limit the size of this object to 8 kilobytes. The client doesn’t preserve the order of sets or dictionary keys, and may minimize or remove optional whitespace. The client may apply Unicode canonicalization rules to keys or values.

