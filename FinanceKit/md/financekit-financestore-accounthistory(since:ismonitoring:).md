

- FinanceKit
- FinanceStore
-  accountHistory(since:isMonitoring:) 

Instance Method

# accountHistory(since:isMonitoring:)

Returns a list of accounts a person added since a time specified by the provided financial history token.

iOS 17.4+iPadOS 17.4+

``` source
func accountHistory(
    since token: FinanceStore.HistoryToken? = nil,
    isMonitoring: Bool = true
) -> FinanceStore.History
```

## Parameters 

`isMonitoring`  

A Boolean value that indicates if the framework should return a `History` that indicates the changes to the accounts over time. Defaults to `true.`

## Return Value

A `History` that describes the accounts.

## Discussion

Use this method to list and monitor accounts present in a person’s Wallet. If provided, the framework uses the `since` history token as a starting point to evaluate which accounts to return.

## See Also

### Accounts

func accounts(query: AccountQuery) async throws -> [Account]

Returns a list of accounts a person added to their Wallet that meet the criteria in the provided account query.

struct AssetAccount

A structure that describes the characteristics of an asset account.

struct LiabilityAccount

A structure that describes the characteristics of a liability account.

enum Account

A structure that describes a financial account.

