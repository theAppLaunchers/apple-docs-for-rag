

- App Store Connect API
- ScmPullRequest
-  ScmPullRequest.Attributes 

Object

# ScmPullRequest.Attributes

The attributes that describe a Pull Requests resource.

App Store Connect API 1.5+

``` source
object ScmPullRequest.Attributes
```

## Properties

`destinationBranchName`

`string`

The name of the pull request’s destination branch.

`destinationRepositoryName`

`string`

The name of the pull request’s destination repository. If the pull request is not for a fork, this is the same value as the source repository name.

`destinationRepositoryOwner`

`string`

The owner of the pull request’s destination repository.

`isClosed`

`boolean`

A Boolean value that indicates whether the pull request is open or closed.

`isCrossRepository`

`boolean`

A Boolean value that indicates whether the pull request is for a Git fork.

`number`

`integer`

The pull request number.

`sourceBranchName`

`string`

The name of the pull request’s source branch.

`sourceRepositoryName`

`string`

The name of the pull request’s source repository.

`sourceRepositoryOwner`

`string`

The owner of the pull request’s destination repository.

`title`

`string`

The pull request’s title.

`webUrl`

`uri`

The URL of the pull request.

## See Also

### Objects

object ScmPullRequest.Relationships

The relationships of the Pull Requests resource you included in the request and those on which you can operate.

