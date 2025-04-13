

- QuickTime File Format
- Basic QuickTime data types
-  Calendar date and time values 

Article

# Calendar date and time values

QuickTime movies store date and time information in Macintosh date format.

## Overview

The Macintosh date format is a 32-bit value indicating the number of seconds that have passed since midnight January 1, 1904.

This value does not specify a time zone. Common practice is to use local time for the time zone where the value is generated.

It is strongly recommended that all calendar date and time values be stored using UTC time, so that all files have a time and date relative to the same time zone.

