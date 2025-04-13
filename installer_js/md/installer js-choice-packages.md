

- Installer JS
- Choice
-  packages 

# packages

An array identifying each package attached to the choice.

## Overview

Each item of the array references a `pkg-ref` element in the installation definition and contains the following two properties:

- `identifier`: The package identifier. Corresponds to the `id` attribute of the `pkg-ref` element.

- `version`: The package version. Corresponds to the `version` attribute of the `pkg-ref` element.

## See Also

### Working with Packages

packageUpgradeAction

A string specifying the relationship between the choice’s packages (specified by the packages property) and the same packages (based on the package identifier) installed on the host.

