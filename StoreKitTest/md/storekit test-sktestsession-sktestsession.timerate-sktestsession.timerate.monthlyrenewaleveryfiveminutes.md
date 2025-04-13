

- StoreKit Test
- SKTestSession
- SKTestSession.TimeRate
-  SKTestSession.TimeRate.monthlyRenewalEveryFiveMinutes 

Case

# SKTestSession.TimeRate.monthlyRenewalEveryFiveMinutes

A rate of time in the test environment in which monthly subscriptions renew every 5 minutes.

iOS 15.2+iPadOS 15.2+Mac Catalyst 15.2+macOS 12.1+tvOS 15.2+visionOS 1.0+watchOS 8.3+

``` source
case monthlyRenewalEveryFiveMinutes
```

## Discussion

The following table shows how this time rate affects subscriptions with various renewal periods in the testing environment:

| Subscription renewal period | Renewal time |
|-----------------------------|--------------|
| Weekly                      | 3 minutes    |
| Monthly                     | 5 minutes    |
| Bimonthly                   | 10 minutes   |
| Quarterly                   | 15 minutes   |
| Semiannually                | 30 minutes   |
| Annually                    | 1 hour       |

The sandbox environment also supports this subscription renewal rate. For more information about renewal rates in the sandbox environment, see Test in-app purchases.

The time rate also affects the billing grace period and the billing retry period in the testing environment, as the table below shows:

| Type | Time period |
|----|----|
| Grace period for subscriptions with a weekly renewal period | 2 minutes 34 seconds |
| Grace period for subscriptions with all other renewal periods | 2 minutes 30 seconds |
| Billing retry period | 10 minutes |

## See Also

### Scaled time rates for subscription renewals

case realTime

A rate of time in which the test environment runs in real time.

case monthlyRenewalEveryHour

A rate of time in the test environment in which monthly subscriptions renew every hour.

case monthlyRenewalEveryThirtyMinutes

A rate of time in the test environment in which monthly subscriptions renew every 30 minutes.

case monthlyRenewalEveryFifteenMinutes

A rate of time in the test environment in which monthly subscriptions renew every 15 minutes.

case monthlyRenewalEveryThirtySeconds

A rate of time in the test environment in which monthly subscriptions renew every 30 seconds.

