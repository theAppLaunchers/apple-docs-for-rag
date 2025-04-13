

- AVFoundation
- AVAssetReaderOutput
-  alwaysCopiesSampleData 

Instance Property

# alwaysCopiesSampleData

A Boolean value that indicates whether the output vends copied sample data.

iOS 5.0+iPadOS 5.0+Mac Catalyst 13.1+macOS 10.8+tvOS 9.0+visionOS 1.0+

``` source
var alwaysCopiesSampleData: Bool { get set }
```

## Discussion

The default value is true, which indicates that the output always provides copies of sample data to your app. This is the appropriate property value if you intend to modify the sample data it returns.

You can disable the default behavior by setting the value to false, which causes the output to vend buffers that may not be copies. Your app can reference these buffers, but it can’t modify them because the result of modifying a shared buffer isn’t defined. If you don’t need to modify the sample data, disabling copying may lead to performance improvements.

## See Also

### Configuring Reading

var supportsRandomAccess: Bool

A Boolean value that indicates whether the output supports reconfiguring the time ranges it reads.

func reset(forReadingTimeRanges: [NSValue])

Restarts reading with a new set of time ranges.

func markConfigurationAsFinal()

Tells the output that it’s finished reconfiguring time ranges, and allows the asset reader to advance to a completed state.

