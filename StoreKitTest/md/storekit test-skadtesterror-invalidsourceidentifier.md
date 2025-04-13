

- StoreKit Test
- SKAdTestError
-  invalidSourceIdentifier 

Type Property

# invalidSourceIdentifier

The postback’s identifier isn’t two, three, or four digits.

iOS 16.4+iPadOS 16.4+Mac Catalyst 16.4+

``` source
static var invalidSourceIdentifier: SKAdTestError.Code { get }
```

## Discussion

A valid postback includes two to four digits of the impression’s sourceIdentifier. For more information about the varying length of source identifiers, see Receiving postbacks in multiple conversion windows.

## See Also

### Getting Other Errors

static var invalidVersion: SKAdTestError.Code

A postback contains an incorrect version number.

static var invalidImpressionId: SKAdTestError.Code

The impression ID isn’t a valid UUID string.

static var invalidSourceAppAdamId: SKAdTestError.Code

The app ID is less than zero.

static var invalidSourceDomain: SKAdTestError.Code

The source domain isn’t in the correct format.

static var unknownError: SKAdTestError.Code

An unknown error occurred in the testing environment.

