

- Service Management
- SMAppService
-  register() 

Instance Method

# register()

Registers the service so it can begin launching subject to user approval.

Mac Catalyst 16.0+macOS 13.0+

``` source
func register() throws
```

## Discussion

The registration process applies to the following rules, depending upon the type of service:

- If the service corresponds to a LoginItem bundle, the helper starts immediately and on subsequent logins. If the helper crashes or exits with a non-zero status, the system relaunches it.

- If the service corresponds to the main application, the application launches on subsequent logins.

- If the service corresponds to a LaunchAgent, the LaunchAgent is immediately bootstrapped and may begin running. In addition LaunchAgents registered with this method bootstrap on each subsequent login.

- If an app needs to register a LaunchAgent for multiple users, you must call the API once per user while that user is running the app.

- If the service corresponds to a LaunchDaemon, the system won’t bootstrap the LaunchDaemon until an admin approves the LaunchDaemon in System Preferences. The system bootstraps LaunchDaemons registered with this method and approved by an admin on each subsequent boot.

If the service is already registered, this method returns kSMErrorAlreadyRegistered.

If the service isn’t approved by the user, this method returns kSMErrorLaunchDeniedByUser.

## See Also

### Registering services

func unregister() throws

Unregisters the service so the system no longer launches it.

func unregister(completionHandler: ((any Error)?) -> Void)

Unregisters the service so the system no longer launches it and calls a completion handler you provide with the resulting error value.

