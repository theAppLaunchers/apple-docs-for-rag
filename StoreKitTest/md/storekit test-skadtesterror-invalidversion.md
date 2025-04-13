

- StoreKit Test
- SKAdTestError
-  invalidVersion 

Type Property

# invalidVersion

A postback contains an incorrect version number.

iOS 16.4+iPadOS 16.4+Mac Catalyst 16.4+

``` source
static var invalidVersion: SKAdTestError.Code { get }
```

## See Also

### Getting Other Errors

static var invalidImpressionId: SKAdTestError.Code

The impression ID isn’t a valid UUID string.

static var invalidSourceAppAdamId: SKAdTestError.Code

The app ID is less than zero.

static var invalidSourceDomain: SKAdTestError.Code

The source domain isn’t in the correct format.

static var invalidSourceIdentifier: SKAdTestError.Code

The postback’s identifier isn’t two, three, or four digits.

static var unknownError: SKAdTestError.Code

An unknown error occurred in the testing environment.

