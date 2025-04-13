

- Security
-  SecTransformConnectTransforms(\_:\_:\_:\_:\_:\_:) Deprecated

Function

# SecTransformConnectTransforms(\_:\_:\_:\_:\_:\_:)

Chains transforms together.

macOS 10.7–12.0Deprecated

``` source
func SecTransformConnectTransforms(
    _ sourceTransformRef: SecTransform,
    _ sourceAttributeName: CFString,
    _ destinationTransformRef: SecTransform,
    _ destinationAttributeName: CFString,
    _ group: SecGroupTransform,
    _ error: UnsafeMutablePointer?>?
) -> SecGroupTransform?
```

Deprecated

SecTransform is no longer supported

## Parameters 

`sourceTransformRef`  

The transform that sends the data to the destinationTransformRef.

`sourceAttributeName`  

The name of the attribute in the sourceTransformRef that supplies the data to the destinationTransformRef. Any attribute of the transform may be used as a source.

`destinationTransformRef`  

The transform that has one of its attributes be set with the data from the sourceTransformRef parameter.

`destinationAttributeName`  

The name of the attribute within the destinationTransformRef whose data is set with the data from the sourceTransformRef sourceAttributeName attribute. Any attribute of the transform may be set.

`group`  

In order to ensure referential integrity, transforms are chained together into a directed graph and placed into a group. Each transform that makes up the graph must be placed into the same group. After a SecTransformRef has been placed into a group by calling the SecTransformConnectTransforms it may be released as the group will retain the transform. CFRelease the group after you execute it, or when you determine you will never execute it.

In the example below, the output of trans1 is set to be the input of trans2. The output of trans2 is set to be the input of trans3. Since the same group was used for the connections, the three transforms are in the same group.

```

                       SecGroupTransformRef group =SecTransformCreateGroupTransform();
                       CFErrorRef error = NULL;

                       SecTransformRef trans1; // previously created using a
                                               // Transform construction API
                                               // like SecEncryptTransformCreate

                       SecTransformRef trans2; // previously created using a
                                               // Transform construction API
                                               // like SecEncryptTransformCreate

                       SecTransformRef trans3; // previously created using a
                                               // Transform construction API
                                               // like SecEncryptTransformCreate

                       SecTransformConnectTransforms(trans1, kSecTransformOutputAttributeName,
                                                     trans2, kSecTransformInputAttributeName,
                                                     group, &error);

                       SecTransformConnectTransforms(trans2, kSecTransformOutputAttributeName,
                                                     trans3, kSecTransformInputAttributeName.
                                                     group, &error);
                       CFRelease(trans1);
                       CFRelease(trans2);
                       CFRelease(trans3);

                       CFDataRef = (CFDataRef)SecTransformExecute(group, &error, NULL, NULL);
                       CFRelease(group);
```

`error`  

An optional pointer to a CFErrorRef. This value is set if an error occurred. If not NULL, the caller is responsible for releasing the CFErrorRef.

## Return Value

A SecGroupTransform object that you can use for chaining calls to SecTransformConnectTransforms(_:_:_:_:_:_:).

## Discussion

This function places transforms into a group by attaching the value of an attribute of one transform to the attribute of another transform. Typically the attribute supplying the data is the kSecTransformAttrOutput attribute but that is not a requirement. It can be used to set an attribute like Salt with the output attribute of a random number transform. This function returns an error and the named attribute will not be changed if SecTransformExecute(_:_:) had previously been called on the transform.

