

- App Clips
-  Creating App Clip Codes with App Store Connect 

Article

# Creating App Clip Codes with App Store Connect

Select one or more advanced App Clip experiences in App Store Connect and create App Clip Codes for users to scan to launch your App Clip.

## Overview

By placing an App Clip Code at a physical location or using it in printed or digital marketing materials, you make your App Clip more discoverable. An App Clip Code always uses a design Apple provides, and users instantly recognize and scan it to launch your App Clip. You can generate an App Clip Code with the App Clip Code Generator command-line tool or App Store Connect. The latter is especially useful if you prefer a tool that offers a visual interface and lets you:

- Create App Clip Codes for one or more existing advanced App Clip experiences.

- Get color suggestions.

- Experiment with color patterns, verify custom colors, and instantly preview the generated App Clip Code.

- Save your generated App Clip Codes as Scalable Vector Graphics (SVG) files.

Important

To create an App Clip Code with App Store Connect, you first need to upload a build of your app that contains the App Clip and create an advanced App Clip experience. If you haven’t already done so — for example, during development — use the App Clip Code Generator command-line tool instead.

### Select one or more advanced App Clip experiences

App Store Connect offers functionality to create an App Clip Code for one or more advanced App Clip experiences. First, select your app’s latest version; then, under Advanced App Clip Experiences, click Edit Advanced Experiences. Next, click Get App Clip Codes. Select one or more advanced App Clip experiences. (Note that you can only select App Clip experiences with invocation URLs that fit in an App Clip Code.) Finally, click Get Started.

For more information, see Configuring the launch experience of your App Clip, Encoding a URL in an App Clip Code, and App Store Connect Help.

### Create one or more App Clip Codes

App Store Connect guides you through the process of creating an App Clip Code for each selected experience. If you select more than one advanced App Clip experience and click Get Started, App Store Connect generates an App Clip Code for each experience with the same type, color, and design.

If you select a single advanced App Clip experience and click Get Started, you can do either of the following:

- Create just one App Clip Code that encodes the experience’s registered invocation URL.

- Create multiple App Clip Codes for the experience where each encodes a different invocation URL.

The second option is especially useful if you only register one advanced App Clip experience and take advantage of URL prefix matching, and you use URL parameters to update your App Clip’s UI upon launch.

If you want to create a single App Clip Code or you selected several App Clip experiences, click Next. Otherwise, to create multiple App Clip Codes for the selected experience, click Yes for that option. On your Mac, choose the URLs you want App Store Connect to use, and store them in a file that uses the comma-separated values (CSV) file format. Each of the file’s rows represents one generated App Clip Code, and each value in a row represents one URL. Upload the CSV file to App Store Connect by clicking Upload URLs and choosing the file on your Mac.

The following code snippet shows the example content of a CSV file. App Store Connect creates one App Clip Code for each row in the file.

```
https://appclip.example.com/about
https://appclip.example.com/buy
https://appclip.example.com/buy?id=123
https://appclip.example.com/buy?id=456
https://appclip.example.com/buy?id=789
```

Note that each URL in the CSV file must match the selected App Clip experience.

Note

If adding parameters results in a URL that doesn’t fit into an App Clip Code, the website displays an error and doesn’t create a code. For more information about choosing the right URL to encode, see Encoding a URL in an App Clip Code.

### Configure your App Clip Code appearance

On the next screen, choose a default color pattern or experiment with custom colors and instantly preview and verify them. App Clip Codes use three different colors: a foreground color and a background color you choose, and a third color that App Store Connect generates for you based on the other two colors.

To ensure users can reliably scan an App Clip Code, the color combination must offer enough contrast. Apple offers default color pairs, but you can experiment and choose a custom pair. If your color selection doesn’t offer enough contrast, App Store Connect suggests different foreground colors based on your custom background color.

Next, select whether you want to create an NFC-integrated or scan-only App Clip Code. Then, choose the App Clip badge design with the App Clip logo or, if space is at a premium, use the design without the App Clip logo. Click Next and follow the workflow to finish creating your App Clip Code.

After creating your App Clip Code, download the created SVG file and print it yourself, or work with a professional printing service — for example, RR Donnelley. For printing guidance, see Preparing multiple App Clip Codes for production and Human Interface Guidelines > App Clips > Printing Guidelines.

