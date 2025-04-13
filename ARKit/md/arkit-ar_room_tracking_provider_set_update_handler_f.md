

- ARKit
-  ar_room_tracking_provider_set_update_handler_f 

Function

# ar_room_tracking_provider_set_update_handler_f

visionOS 2.0+

``` source
extern void ar_room_tracking_provider_set_update_handler_f(ar_room_tracking_provider_t room_tracking_provider, dispatch_queue_t room_tracking_updates_queue, void * context, ar_room_tracking_update_handler_function_t room_tracking_update_handler_function);
```

## See Also

### Room tracking functions

ar_room_tracking_configuration_create

ar_room_tracking_provider_copy_all_room_anchors

ar_room_tracking_provider_copy_current_room_anchor

ar_room_tracking_provider_create

ar_room_tracking_provider_get_required_authorization_type

ar_room_tracking_provider_is_supported

ar_room_tracking_provider_set_update_handler

room_tracking_h

