

- Accelerate
-  BNNSCreateNearestNeighbors(\_:\_:\_:\_:\_:) 

Function

# BNNSCreateNearestNeighbors(\_:\_:\_:\_:\_:)

Returns a new k-nearest neighbors object.

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+macOS 14.0+tvOS 17.0+visionOS 1.0+watchOS 10.0+

``` source
func BNNSCreateNearestNeighbors(
    _ max_n_samples: UInt32,
    _ n_features: UInt32,
    _ n_neighbors: UInt32,
    _ data_type: BNNSDataType,
    _ filter_params: UnsafePointer?
) -> BNNSNearestNeighbors?
```

## Parameters 

`max_n_samples`  

The maximum number of data points.

`n_features`  

The number of features or dimensions of each data point.

`n_neighbors`  

The number of nearest neighbors that a subsequent call to BNNSNearestNeighborsGetInfo(_:_:_:_:) calculates.

`data_type`  

The data type of the data points. This must be either `BNNSDataTypeFloat32` or `BNNSDataTypeFloat16`.

`filter_params`  

The filter runtime parameters.

## Return Value

A new k-nearest neighbors object, or `nil` if the operation failed.

## Discussion

The following code generates eight 2D data points and loads them into a k-nearest neighbors object with a single call to the BNNSNearestNeighborsLoad(_:_:_:) function. The code then computes the four nearest neighbors, based on Euclidean distance, to the sample data point at index 7 of the samples data.

```
let samples: [Float] = [
    1, 2,   // 0
    7, 2,   // 1
    3, 4,   // 2
    8, 4,   // 3
    3, 7,   // 4
    7, 7,   // 5
    2, 8,   // 6
    2, 5    // 7
]

let maximumSampleCount: UInt32 = 8
let dimensionCount: UInt32 = 2
let nearestNeighborCount: UInt32 = 4

let knn = BNNSCreateNearestNeighbors(
    maximumSampleCount,
    dimensionCount,
    nearestNeighborCount,
    BNNSDataType.float,
    nil)

defer {
    BNNSDestroyNearestNeighbors(knn)
}

BNNSNearestNeighborsLoad(
    knn,
    UInt32(samples.count) / dimensionCount,
    samples)

var indices = [Int32](repeating: 0,
                      count: Int(nearestNeighborCount))
var distances = [Float](repeating: 0,
                        count: Int(nearestNeighborCount))

let sampleDataPointIndex = 7
BNNSNearestNeighborsGetInfo(
    knn,
    Int32(sampleDataPointIndex),
    &indices,
    &distances)
```

On return, the `indices` array contains the values `[7, 2, 4, 6]` and the distances array contains the values `[0.0, 1.4142135, 2.236068, 3.0]`.

## See Also

### K-nearest neighbors calculation

struct NearestNeighbors

A structure that calculates k-nearest neighbors.

typealias BNNSNearestNeighbors

A k-nearest neighbors object.

func BNNSNearestNeighborsLoad(BNNSNearestNeighbors?, UInt32, UnsafeRawPointer) -> Int32

Adds new sample data to a k-nearest neighbors object.

func BNNSNearestNeighborsGetInfo(BNNSNearestNeighbors?, Int32, UnsafeMutablePointer&lt;Int32>?, UnsafeMutableRawPointer?) -> Int32

Calculates the sorted indices and Euclidean distances of the k-nearest neighbors to a specified sample data point.

func BNNSDestroyNearestNeighbors(BNNSNearestNeighbors?)

Destroys a k-nearest neighbors object.

