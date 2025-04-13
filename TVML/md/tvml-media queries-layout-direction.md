

- TVML
- Media Queries
-  layout-direction 

Article

# layout-direction

Sets the text direction based on the user’s language preference.

## Overview

All base style sheets now use `text-align:natural`. You must use the `layout-direction` query to change the language layout. Here’s an example for specifying styles for right-to-left languages.

```

    .socialBadgeInLockup {
        tv-position: bottom-trailing;
        tv-align: trailing;
        margin: 0 8 -8 0;
    }
    .socialBadgeInMonogramLockup {
        tv-position: bottom-trailing;
        tv-align: trailing;
        margin: 0 18 10 0;
    }

    @media (layout-direction: rtl) {
        .socialBadgeInLockup {
            margin: 0 0 -8 8;
        }
        .socialBadgeInMonogramLockup {
            margin: 0 0 10 18;
        }
    }

```

### Values for layout-direction

`ltr`  
Test for left-to-right language layout.

`rtl`  
Test for right-to-left language layout.

## See Also

### Media Queries

tv-theme

Sets an element’s appearance according to the specified theme.

