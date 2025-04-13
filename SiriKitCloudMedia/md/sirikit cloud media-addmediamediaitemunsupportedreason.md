

- SiriKit Cloud Media
-  AddMediaMediaItemUnsupportedReason 

Type

# AddMediaMediaItemUnsupportedReason

Reasons the media service can’t add the media item to the user’s library or to a playlist.

SiriKit Cloud Media 1.0.2+

``` source
string AddMediaMediaItemUnsupportedReason
```

## Possible Values 

`loginRequired`  

The user must log in to the service.

`subscriptionRequired`  

The user must have an active subscription to access the media item.

`unsupportedMediaType`  

Your service doesn’t support the media item’s type.

`explicitContentSettings`  

The content settings don’t allow the user to access the media item.

`restrictedContent`  

The media item is restricted content.

`regionRestriction`  

The media item isn’t available in the user’s geographic region.

`serviceUnavailable`  

The media service is currently unavailable.

## See Also

### Reporting a Problem

object AddMediaMediaItemResolutionResult.Unsupported

The reason your service can’t add the media item to the user’s library or to a playlist.

