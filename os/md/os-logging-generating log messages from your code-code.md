

- os
- Logging
-  Generating Log Messages from Your Code 

Article

# Generating Log Messages from Your Code

Record useful debugging and analysis information, and include dynamic content in your messages.

## Overview

Insert log messages at appropriate points in your code and use them to diagnose issues later. Typically, you use log messages to:

- Write a message at the start and end of functions and important tasks.

- Write a message for any interesting events.

- Write a message when a significant error occurs.

- Write messages for important or unusual actions with a function. For example, log rarely taken code paths.

- Write a message before each step of a multi-step task.

Messages may contain more than just static strings. The unified logging system allows you to include custom data from your app, and format that data to make it more readable. Like `fprintf`, you can incorporate strings, numbers, Objective-C objects, and other custom data types from your app directly into your log messages. When data types contain sensitive user information, the system has privacy options that hide the actual values without losing any filtering capabilities.

### Create a Log Object to Organize Messages

A log object collects messages associated with a particular part of your app. When you generate log messages, you do so either directly from, or in conjunction with, a log object that you create. The type of log object you create depends on whether you write your code using Swift or Objective-C.

- In Swift, create a Logger structure and use its methods to generate log messages.

- In Objective-C, create an OSLog object and pass it to logging functions.

To prevent the system from displaying an overwhelmingly large number of log messages each time you diagnose issues, each log object contains two custom strings to help you filter out unrelated messages. You specify both strings when creating the log object, using values that are relevant to your app:

- The subsystem string identifies a large functional area within your app or apps. For example, if your app spawns additional processes, you might use a different string for each process. Use reverse-DNS notation, such as `com.example.myapp`, for each subsystem string.

- The category string identifies a particular component or module in a given subsystem. For example, you might define separate strings for your app’s user interface, data model, and networking code. Use any convention you want for these strings.

If you don’t need to filter messages, Logger and OSLog provide a default log for storing messages. You might use the default log to record messages that don’t require a specific subsystem and category.

### Choose the Appropriate Log Level for Each Message

Log levels define the severity and importance of a particular message, and you specify a log level value each time you record a message. The log level you choose determines how the system handles the message. The system stores all messages in memory initially, and it writes messages with more severe log levels to disk. The following table lists the log levels in increasing order of severity.

| Log level | Persisted to disk | Notes |
|----|----|----|
| Debug | No | Captures verbose information during development that is useful only for debugging your code. |
| Info | Only when collected with the log tool | Captures information that is helpful, but not essential, to troubleshoot problems. |
| Notice (Default) | Yes, up to a storage limit | Captures information that is essential for troubleshooting problems. For example, capture information that might result in a failure. |
| Error | Yes, up to a storage limit | Captures errors seen during the execution of your code. If an activity object exists, the system captures information for the related process chain. |
| Fault | Yes, up to a storage limit | Captures information about faults and bugs in your code. If an activity object exists, the system captures information for the related process chain. |

Normally, the system stores debug and info messages only in memory, but you can write info messages to disk using the `log` command-line tool. For the other message types, the system compresses the messages and writes them to the on-disk data store. When that data store exceeds a predefined size, the system purges old messages to make room for new ones.

Note

You can override the default storage behavior of each log level using tools or custom configuration profiles. For more information on how to do so, see Customizing Logging Behavior While Debugging.

The severity of the log level impacts the speed at which the system logs the information. Debug logs have very low overhead because the system stores them only in memory. Faults and other severe messages incur more overhead because the system often captures additional information and writes all of that information to disk.

### Generate a Log Message

To generate a log message:

- In Swift, call the appropriate method of the Logger structure in macOS 11 and later. In earlier versions of macOS, call `os_log(_:log:type:)` or one of the related log functions that take an OSLog object as a parameter.

- In Objective-C code, call os_log or an equivalent function that takes an os_log_t type as a parameter.

The simplest type of log message contains only static text. You might use such messages to report specific events, or anytime you don’t need to include program variables in the message. The following example shows different ways to log messages that contain only static text. The first two examples add messages to the default log, but the third example adds an error message to a custom log object.

```
```

### Include Custom Data Values in Log Messages

Message strings may include the content of program variables. How you include these variables depends on which programming language you use:

- In Swift, add interpolated variables of the form `\(variableName)` to your message strings.

- In Objective-C, add format string specifiers such as `%@` and `%d`.

The following example shows several log messages that include different types of variables. In macOS 11 and later, specify variables in Swift directly in the message string as interpolated values. Otherwise, use format-string specifiers and a variable list of arguments to specify values. To log raw bytes from a pointer in Objective-C, use the `%.*P` format modifier.

```
```

### Format Custom Values in Message Strings

The unified logging system formats Swift interpolated variables based on the default settings, but you can apply custom formatting to your variables to make them more readable. In particular, you can:

- Specify the width of a variable and align the variable’s text inside that space.

- Format integers as decimal, hex, or octal numbers.

- Format floating-point numbers using fixed-point, hex, exponential, or hybrid notation.

- Format Boolean values as true/false or yes/no strings.

- Specify the precision of floating-point numbers.

- Specify the minimum number of digits.

- Specify whether a number includes an explicit plus or minus sign.

- Log binary data contained in a pointer.

To specify a formatting option for an interpolated value, include the appropriate format parameter and value. In the following example, the first log message includes alignment parameters to set the column width and alignment within that column. The second log message formats a floating-point number to include extra digits of precision and a plus sign in front of positive numbers. The third log message formats a Boolean value as a yes/no answer to a question.

```
```

In addition to the preceding formatting options, the unified logging system supports custom formatting modifiers. In Swift, specify them using the `format` parameter. In Objective-C, use a modifier of the form `%{value_type}d`. Each modifier formats the corresponding data according to the specific type. To format binary data types, use the `%.*P` specifier and add the total number of bytes and the pointer as arguments to the function. The following table lists the built-in format specifiers.

| Value type | Custom specifier | Example output |
|----|----|----|
| `time_t` | `%{time_t}d` | `2016-01-12 19:41:37` |
| `timeval` | `%{timeval}.*P` | `2016-01-12 19:41:37.774236` |
| `timespec` | `%{timespec}.*P` | `2016-01-12 19:41:37.2382382823` |
| `errno` | `%{errno}d` | `Broken pipe` |
| `iec-bytes` | `%{iec-bytes}d` | `2.64 MiB` |
| `bitrate` | `%{bitrate}d` | `123 kbps` |
| `iec-bitrate` | `%{iec-bitrate}d` | `118 Kibps` |
| `uuid_t` | `%{uuid_t}.*16P`  `%{uuid_t}.*P` | `10742E39-0657-41F8-AB99-878C5EC2DCAA` |

The following example shows how to format custom bit rates and a UUID structure.

```
```

For information about the options to use when formatting values, see OSLogStringAlignment, OSLogIntegerFormatting, OSLogFloatFormatting, OSLogBoolFormat, OSLogInt32ExtendedFormat, and OSLogPointerFormat.

### Redact Sensitive User Data from a Log Message

Log messages that contain sensitive user data present a potential problem for users, because anyone with access to the logs or the user’s computer can see the information. To protect the privacy of your users, try to limit your log messages to static strings and numbers that you define. If you must include dynamically generated data in your messages, redact any values that contain sensitive user information.

The unified logging system uses privacy options to hide or show interpolated variables in a message. By default, the system doesn’t redact integer, floating-point and Boolean values, but it does redact the contents of dynamic strings and complex dynamic objects. To make a private value public again, configure the privacy of the variable using appropriate modifiers in your message string or interpolated variable. For example, the following code shows how to make a dynamic string visible again using the public modifier:

```
```

When you know a variable contains potentially sensitive user information, mark it as private explicitly, as shown in the following example:

```
```

To diagnose certain problems, you might need to identify when several log messages all refer to the same piece of user data. For example, when diagnosing issues with a particular user account, you might want to see all log messages associated with that account number. To allow this behavior and still protect user privacy, configure your privacy setting with a OSLogPrivacy.Mask.hash value, as shown in the following example:

```
```

The inclusion of the OSLogPrivacy.Mask.hash option replaces the generic redaction text with a hash value that is unique for the current process. The OSLogPrivacy.Mask.hash value corresponds to the redacted value, but doesn’t provide any identifying information about that value.

## See Also

### Essentials

Viewing Log Messages

Use various tools to retrieve log information.

Customizing Logging Behavior While Debugging

Control which log events are recorded.

