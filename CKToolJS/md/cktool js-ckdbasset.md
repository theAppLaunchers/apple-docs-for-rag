

- CKTool JS
-  CKDBAsset 

Structure

# CKDBAsset

An object that represents an asset uploaded to CloudKit.

CKTool JS 1.2.15+

``` source
dictionary CKDBAsset {
 Int64? size;
 string? receipt;
 string? fileChecksum;
 string? wrappingKey;
 string? referenceChecksum;
 string? downloadUrl;
};
```

## Overview

In JavaScript, this is a plain object with properties as described.

In TypeScript, this type is imported in the following way:

```
import type { CKDBAsset } from "@apple/cktool.database";
```

## Topics

### Instance Properties

downloadUrl

The URL for accessing the asset.

fileChecksum

The signature of a file returned from the file upload step.

receipt

The receipt for uploading the asset.

referenceChecksum

The checksum of the wrapping key returned from the upload step.

size

The size of the asset in bytes.

wrappingKey

The secret key used to encrypt the asset.

## See Also

### Structures

CKDBAssetUploadUrlResponse

An object that represents the results of creating an asset upload URL.

CKDBChangeMetadata

An object that represents metadata about a record change via creation or modification.

CKDBCreateAssetUploadUrlRequestBody

An object that represents the request for creating an asset upload URL.

CKDBCreateRecordRequestBody

An object that represents the request to create a new record.

CKDBCreateZoneRequestBody

An object that represents the request to create a new zone.

CKDBDeleteRecordsByQueryRequestBody

An object that represents the request to delete multiple records that match a query.

CKDBDeletedRecordResult

An object that represents a deleted record result.

CKDBErrorRecordResult

An object that represents a record lookup failure.

CKDBExistingRecordResult

An object that represents a successful record result.

CKDBForRecord

An object that represents a record that is being shared.

CKDBLocation

An object that represents a location field value.

CKDBLookupRecordsRequestBody

An object that represents the request for looking up multiple records by record name.

CKDBLookupRecordsResponse

An object that represents the results of a batch record lookup operation.

CKDBModifyRecordRequestBody

An object that represents the request for updating an existing record.

CKDBNullableReference

An object that represents a reference to another record.

