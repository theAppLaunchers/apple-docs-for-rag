

- Apple Pay on the Web
-  Displaying Apple Pay Buttons Using JavaScript 

Article

# Displaying Apple Pay Buttons Using JavaScript

Load and configure the JavaScript Apple Pay button.

## Overview

The JavaScript Apple Pay button provides a variety of Apple Pay button types that you can use on your website to initiate a transaction. You can specify the Apple Pay button style, type, and localization using attributes. Use CSS to set other properties, such as the size and corner radius.

Use the following code to load the button script into your webpage from the content delivery network:

```

```

### Display the Button

Add an `apple-pay-button` element to your webpage to display the button. Set the style, type, and locale when you add the button. The following code adds a black Buy with Apple Pay button localized to Greek, using the default size and corner radius:

```

```

Use CSS to customize the size and other attributes. The following example adds the same Greek button with a height of `40` pixels, a width of `140` pixels, and a corner radius of `5` pixels. The height includes the top and bottom padding.

```

apple-pay-button {
  --apple-pay-button-width: 140px;
  --apple-pay-button-height: 30px;
  --apple-pay-button-border-radius: 5px;
  --apple-pay-button-padding: 5px 0px;
}

```

The CSS properties for the button are:

`--apple-pay-button-width`  
The width of the button.

The minimum value for the width of a plain Apple Pay button is `100` pixels.

The minimum value for the width of all other Apple Pay buttons is `140` pixels.

The button renders at the minimum width when the specified value is less than the minimum.

`--apple-pay-button-height`  
The height of the button.

The default and minimum value for the height is `30` pixels.

The button renders at the minimum height when the specified value is less than the minimum.

`--apple-pay-button-border-radius`  
The corner radius of the button.

The default value is `4` pixels.

`--apple-pay-button-padding`  
The amount of padding on each side of the button.

The default value is `0` pixels.

`--apple-pay-button-box-sizing`  
The box size for the Apple Pay button. The possible values are the same as the `box-sizing` CSS property.

For design guidance, see Human Interface Guidelines > Apple Pay > Buttons and Marks.

## See Also

### Apple Pay buttons

ApplePayButton

An object that displays a button either to trigger payments through Apple Pay or to prompt the user to set up a card.

Displaying Apple Pay Buttons Using CSS

Use CSS templates to display Apple Pay buttons in Safari.

