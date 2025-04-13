

- Foundation
- NSScriptSuiteRegistry
-  aeteResource(\_:) 

Instance Method

# aeteResource(\_:)

Returns an `NSData` object that contains data in `'aete'` resource format describing the scriptability information currently known to the application.

Mac Catalyst 13.0+macOS 10.0+

``` source
func aeteResource(_ languageName: String) -> Data?
```

## Discussion

This method is typically invoked to implement the `get aete` Apple event for an application that provides scriptability information in the script suite format. The `languageName` argument is the name of a language for which a localized resource directory (such as `English.lproj`) exists. This language indication specifies the set of `.scriptTerminology` files to be used to generate the data. `NSScriptSuiteRegistry` does not create an `'aete'` resource unless this method is called.

## See Also

### Getting Other Suite Information

func appleEventCode(forSuite: String) -> FourCharCode

Returns the Apple event code associated with the suite named `suiteName`, such as `‘core’` for the Core suite.

func bundle(forSuite: String) -> Bundle?

Returns the bundle containing the suite-definition property list (extension `.scriptSuite`) identified by `suiteName`.

