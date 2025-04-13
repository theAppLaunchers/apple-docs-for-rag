

- Create ML
- MLWordEmbedding
-  prediction(from:maxCount:maxDistance:distanceType:) 

Instance Method

# prediction(from:maxCount:maxDistance:distanceType:)

Predicts neighbors.

macOS 10.15+

``` source
func prediction(
    from text: String,
    maxCount: Int = 10,
    maxDistance: Double = 2.0,
    distanceType: NLDistanceType = .cosine
) throws -> [(text: String, distance: Double)]
```

## Parameters 

`text`  

A string in the embedding vocabulary.

`maxCount`  

The largest number of neighboring strings.

`maxDistance`  

The maximum allowed neighbor distance.

`distanceType`  

The type of distance formula to use for evaluating a neighbor’s distance from the input string.

## Return Value

An array of neighboring strings and their distances to the input string.

## Discussion

The distance values are calculated with a formula determined by NLDistanceType, such as NLDistanceType.cosine.

## See Also

### Testing a word embedding

func distance(between: String, and: String, distanceType: NLDistanceType) -> Double

Calculates the distance between two strings in the vocabulary space.

enum NLDistanceType

The means of calculating a distance between two locations in a text embedding.

func contains(String) -> Bool

Returns a Boolean value indicating whether the vocabulary contains the given string.

func vector(for: String) -> [Double]?

Accesses the vector associated with the given string in the vocabulary.

