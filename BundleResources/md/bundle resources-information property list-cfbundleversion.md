

- Bundle Resources
- Information Property List
-  CFBundleVersion 

Property List Key

# CFBundleVersion

The version of the build that identifies an iteration of the bundle.

iOS 2.0+iPadOS 2.0+macOS 10.0+tvOS 9.0+visionOS 1.0+watchOS 2.0+

## Details 

Name  
Bundle version

Type  

string

## Discussion

This key is a machine-readable string composed of one to three period-separated integers, such as 10.14.1. The string can only contain numeric characters (0-9) and periods.

Each integer provides information about the build version in the format \[*Major*\].\[*Minor*\].\[*Patch*\]:

- Major: A major revision number.

- Minor: A minor revision number.

- Patch: A maintenance release number.

You can include more integers but the system ignores them.

You can also abbreviate the build version by using only one or two integers, where missing integers in the format are interpreted as zeros. For example, 0 specifies 0.0.0, 10 specifies 10.0.0, and 10.5 specifies 10.5.0.

This key is required by the App Store and is used throughout the system to identify the version of the build. For macOS apps, increment the build version before you distribute a build.

## See Also

### Bundle version

CFBundleShortVersionString

The release or version number of the bundle.

**Name:** Bundle versions string, short

CFBundleInfoDictionaryVersion

The current version of the Information Property List structure.

**Name:** InfoDictionary version

NSHumanReadableCopyright

A human-readable copyright notice for the bundle.

**Name:** Copyright (human-readable)

