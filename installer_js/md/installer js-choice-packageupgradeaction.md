

- Installer JS
- Choice
-  packageUpgradeAction 

# packageUpgradeAction

A string specifying the relationship between the choice’s packages (specified by the packages property) and the same packages (based on the package identifier) installed on the host.

## Overview

The possible values of this property are:

- `'clean'`: None of the packages are installed.

- `'installed'`: All the packages are already installed.

- `'upgrade'`: The versions of all the packages are higher than the versions of the installed packages.

- `'downgrade'`: The versions of all the packages are lower than the versions of the installed packages.

- `'mixed'`: At least two of the following conditions are true:

  - One or more of the packages are upgrades.

  - One or more of the packages are downgrades.

  - One or more of the packages are not installed.

For example, if a distribution contains a choice with a required package, you may deselect that choice if the installed package is more recent.

## See Also

### Working with Packages

packages

An array identifying each package attached to the choice.

