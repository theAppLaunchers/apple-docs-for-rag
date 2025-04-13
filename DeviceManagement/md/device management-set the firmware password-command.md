

- Device Management
-  Set the Firmware Password 

Web Service Endpoint

# Set the Firmware Password

Change or clear the firmware password on a device.

macOS 10.13+Device Assignment ServicesVPP License Management

## URL

``` source
PUT https://yourmdmhost.example.com/mdm#SetFirmwarePasswordCommand
```

## HTTP Body

SetFirmwarePasswordCommand

The command to change or clear the firmware password on a device.

Content-Type: application/x-apple-aspen-mdm

## Response Codes

` 200 ``OK`

SetFirmwarePasswordResponse

`OK`

A response from the device after it processes the command to set the firmware password.

Content-Type: application/xml

## Discussion

This command has a throttle interval to prevent executing it more frequently than every 30 seconds. Requests that occur within the throttle interval return an error.

Important

There’s no way to set or clear a firmware password in MDM without knowing the current password, unless the server provides a way to prompt the administrator for the current password. Contact AppleCare service and support if the current password is unknown.

After processing the command, the device restarts so that the new firmware password takes effect. This command returns an error and fails if a firmware password is already pending.

Refer to the following sections to determine supported channels and requirements, and to see an example request and response.

This command isn’t supported on Mac computers with Apple silicon.

### Command Availability

|                            |                             |
|----------------------------|-----------------------------|
| Device Channel             | macOS                       |
| User Channel               | \-                          |
| Requires Supervision       | \-                          |
| Allowed in User Enrollment | \-                          |
| Required Access Right      | DeviceLockAndRemovePasscode |

### Example Request and Response

- Request
- Response

```

    Command

        AllowOroms

        CurrentPassword
        oldpassword
        NewPassword
        newpassword
        RequestType
        SetFirmwarePassword

    CommandUUID
    0001_SetFirmwarePassword

```

```

    CommandUUID
    0001_SetFirmwarePassword
    SetFirmwarePassword

        PasswordChanged

    Status
    Acknowledged
    UDID
    E84CD517-CB37-52F7-988C-DB5137B604B8

```

## Topics

### Command and Response

object SetFirmwarePasswordCommand

The command to change or clear the firmware password on a device.

object SetFirmwarePasswordResponse

A response from the device after it processes the command to set the firmware password.

## See Also

### Passwords

Clear the Passcode

Remove the passcode from a device.

Clear the Restrictions Password

Clear the restrictions password and the restrictions on a device.

Unlock a User Account

Unlock a user account that the system locked because of too many failed password attempts.

Set the Local Administrator Password

Update the local administrator account password.

Verify the Firmware Password

Verify the firmware password on a device.

