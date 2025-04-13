

- Application Services
- ColorSync Manager
-  Flag Mask Definitions for Version 2.x Profiles 

# Flag Mask Definitions for Version 2.x Profiles

Define masks your application can use to set or test various bits in the `flags` field of the `CM2Header` structure.

## Overview

The `flags` field of the structure CM2Header is an unsigned long value whose bits specify information about a profile. The ICC reserves the use of bits 0 to 15 and has assigned values to bits 0 and 1. Bits 16 to 31 are reserved for use by color management system (CMS) vendors. ColorSync has assigned values to bits 16 through 19.

## Topics

### Constants

var cmICCReservedFlagsMask: Int

var cmEmbeddedMask: Int

This mask provides access to bit 0 of the `flags` field, which specifies whether the profile is embedded. It has the value 1 if the profile is embedded, 0 if it is not.

var cmEmbeddedUseMask: Int

var cmCMSReservedFlagsMask: Int

var cmQualityMask: Int

var cmInterpolationMask: Int

var cmGamutCheckingMask: Int

var cmBlackPointCompensationMask: Int

