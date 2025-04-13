

- Sign in with Apple
-  Displaying Sign in with Apple buttons on the web 

Article

# Displaying Sign in with Apple buttons on the web

Configure the appearance of Sign in with Apple buttons with CSS styles.

## Overview

You can specify the display of your Sign in with Apple button, and edit its appearance and size to fit your webpage. For a description of the button types and usage information, see Sign in with Apple Buttons in the Human Interface Guidelines.

### Create a wrapper tag and configure localization

Start by creating a wrapper tag for your button. Set the `id` to “`appleid-signin`”.

```
```

To configure the localization of the Sign in with Apple button, embed your desired localization code within the URI below:

```
```

Replace `en_US` in the code above with your localization code. For a list of available locales, see Incorporating Sign in with Apple into other platforms.

### Specify property values

The folowing example creates a black Sign in with Apple button.

```
```

Control the size of the button by adding a class that contains the desired CSS `width` and `height` styles. The above example creates a button that’s 210 pixels wide and 40 pixels high, and sets the properties of the Sign in with Apple button as described in the following sections.

#### Set the mode

To configure the appearance of the Sign in with Apple button, set the `data-mode` property to one of the following values:

`center-align`  
A center-aligned button. Both the logo and text are centered in the button. This is the default.

`left-align`  
A left-aligned button with an adjustable logo size, logo position, and label position.

`logo-only`  
A square button with a centered Apple logo and no text.

#### Set the type

You can request a specific button type by setting the `data-type` property of the Sign in with Apple button to one of the following values:

`sign-in`  
The Sign in with Apple button. This is the default.

`continue`  
The Continue with Apple button.

`sign-up`  
The Sign up with Apple button.

#### Set the color

To configure the background color of the Sign in with Apple button, set the `data-color` property to one of the following values:

`black`  
The button’s background color is black. This is the default.

`white`  
The button’s background color is white.

#### Set the border and radius

To configure the border of the Sign in with Apple button, set the `data-border` property to one of the following values:

`true`  
The button has a border. This is the default.

`false`  
The button doesn’t have a border.

To configure the border radius of the button, set the `data-border-radius` property to a number between `0—50`. The default is `15`.

#### Set the width and height

To configure the width of the Sign in with Apple button, set the `data-width` property to a value in points between `130—375`, or `100%` to fit the container size. The default is `100%`.

To configure the height of the button, set the `data-height` property to a value in points between `30—64`, or `100%` to fit the container size. The default is `100%`.

#### Set the logo size and position

You can control the size and position of the Apple logo on the Sign in with Apple button. These settings only work if you set `data-mode` to `left-align`.

To configure the logo size on the button, set the `data-logo-size` property to one of the following values:

`small`  
A small logo.

`medium`  
A medium logo.

`large`  
A large logo.

To configure the logo position on the button, set the `data-logo-position` property to a number in points. The minimum value is `0` and the maximum is the label position. The logo remains positioned to the left of the label. The system may override the value to maintain proper margins for the logo and font size.

#### Set the label position

You can configure the position of the text in the Sign in with Apple button if you set `data-mode` to `left-align`. Set the `data-label-position` property to a value in points between `0` and half the width of the button. The default is `0`.

## See Also

### Web support

Configuring your environment for Sign in with Apple

Authenticate users with your web service by associating an existing app with a Services ID and private key.

Processing changes for Sign in with Apple accounts

Manage user-initiated modifications to maintain privacy with server-to-server notifications.

