

- Technotes
-  TN3155: Debugging universal links 

Article

# TN3155: Debugging universal links

Investigate why your universal links are opening in a web browser instead of your app.

## Overview

Universal links use applinks, an associated domains service, to link directly to content within your app without routing through a web browser or your website. If your app is installed, a universal link will open in your app. If it is not installed, the link will open in your default web browser, where your site handles the rest. If you are unfamiliar with universal links and how to support them in your code, see Supporting Associated Domains and Allowing apps and websites to link to your content.

This document outlines how to:

- Test your universal links

- Choose the correct applinks domains

- Use universal links on your site

- Verify your apple-app-site-association (AASA) file

- Debug using a sysdiagnose

- Understand Apple’s content delivery network (CDN)

## Test universal links behavior

To test your universal links behavior, paste a link into your Notes app and long-press it (iOS) or control-click it (macOS) to see your options for following the link. If universal links have been configured correctly, the option to open in your app and in the web browser will both show up. The option you choose will set the default behavior for your device when following universal links from this domain in the future. To change this default choice, repeat the same steps and choose a different option.

Note

Entering the URL directly into the web browser’s address bar will never open the app, as this is direct navigation within the web browser. As long as the user is on your domain after navigating there directly, your site will show a banner to open your app.

On iOS, you can additionally test your universal links with the associated domains diagnostic tests in Developer settings through these steps:

1.  Turn on Developer Mode in Settings. Read Enabling Developer Mode on a device for more help.

2.  In Settings \> Developer, scroll to the section labeled Universal Links and turn on Associated Domains Development.

3.  Open Diagnostics and type in your full URL. You will receive feedback on whether this link is valid for an installed app.

If your universal links are invalid, your `applinks` may be configured incorrectly.

## Understand applinks configuration and rules

Using the Signing and Capabilities tab in Xcode, verify the app has the Associated Domains capability which contains `applinks` in the form of:

```
applinks:
```

A common problem is caused by using a domain in your `applinks` that doesn’t have an AASA file hosted in the correct location.

Make sure your domains and AASA file paths match. To match a root domain and all subdomains with a wildcard, an AASA file should be hosted at:

```
https://example.com/.well-known/apple-app-site-association
```

This will only work with the root domain of `applinks:example.com` and subdomains that are matched with the wildcard `applinks:*.example.com`. This will not work with specific subdomains like `applinks:www.example.com` or `applinks:foo.example.com`.

To match a specific subdomain, an AASA file should be hosted at:

```
https://www.example.com/.well-known/apple-app-site-association
```

This will only work with `applinks:www.example.com`. Each specific subdomain in your `applinks` should have its own matching AASA file path.

Note

Domains in your `applinks` can’t contain a port number. For example, `applinks:example.com:8080` will not open your app.

## Use universal links on your site

To use a universal link to open your app while already browsing in the web browser, use a different subdomain. Reasons for this could be completing a questionnaire or choosing to sign in. If a universal link has the same domain as the previous navigation, the web browser will expect the user wants to continue navigating within the browser. Review Allowing apps and websites to link your content for more information.

For an example of when to use subdomains, consider an app with the root domain `applinks:example.com` and an AASA containing:

```
 "components" : [
 {
 "/" : "/login/*",
 "comment" : "Matches any URL with a path that starts with /login/."
 }]
```

If a user is browsing your site in a web browser and chooses a login button with the link `https://example.com/login`, the link will not be opened in the app. The web browser will continue navigation even though the path matches the component above since the domain did not change.

To avoid this:

- Add a subdomain such as `applinks:foo.example.com` to your associated domains in the Signing and Capabilities tab in Xcode.

- Host an AASA at:

```
https://foo.example.com/.well-known/apple-app-site-association
```

- Give the login button a link of:

```
https://foo.example.com/login
```

Using a different subdomain prevents the web browser from treating the link as navigation, so it will open the link in your app.

Important

It is up to third-party web browsers to enable universal links functionality. Universal links may not be enabled in every web browser. For information about other browsers, developers should check with the browser’s vendor. Safari implements all of the function described in this technote.

## Host and verify your AASA

If your universal links are still not opening in your app, take a closer look at your HTTP response headers and AASA content. You can do this by printing both the HTTP response headers and AASA JSON contents in Terminal using

```
% curl -v https://{domain}/.well-known/apple-app-site-association
```

If you see a 301 or 302 HTTP response status code, your site is doing an HTTP redirect, which is not supported when hosting the AASA file. The file must be directly reachable without any redirects.

Instead of hosting your AASA at your root domain and redirecting to serve a subdomain, host your AASA at each domain and subdomain included in your `applinks`. For example, if you have a subdomain like `applinks:www.example.com` and the wildcard `applinks:*.example.com`, host one AASA file here for the subdomain:

```
https://www.example.com/.well-known/apple-app-site-association
```

and one here for the wildcard:

```
https://example.com/.well-known/apple-app-site-association
```

Note

Redirection is allowed, although not preferred, when opening universal links from another app. If the link tapped on by the user is not a universal link but redirects to one, the user will be routed through the web browser to the app.

If you see a 403 or 404 HTTP error, your site denied access. Generally, this happens when the AASA file path is not publicly accessible from all IP addresses or your site is blocked for some other reason. Confirm your website’s configuration allows direct access to the AASA file in the `.well-known` directory, in all geographical locations, from any IP address. Specific IP addresses and ranges are not published as they cannot be guaranteed.

Verify the format of your AASA file. It should contain either an `Array` of `appIDs` and an `Array` of `components`, as shown in Supporting associated domains, or fields `appID` of type `String` and `paths` of type `Array` (matching an older format). Don’t mix and match these formats or universal links won’t work. Here’s the the recommended format:

```
 "appIDs": [ "ABCDE12345.com.example.app", "ABCDE12345.com.example.app2" ], 
 "components": [ { 
    "/": "/test/*", 
    "comment": "Matches any URL beginning with /test/" 
    },
    { 
    "/": "/path/1/*", 
    "exclude": true,
    "comment": "Matches any URL beginning with /path/1/ and instructs the system not to open it as a universal link" 
    }]
```

While this is the older format:

```
"appID": "ABCDE12345.com.example.app",
 "paths": [ "/test/*", NOT "/path/1/*"]
```

To verify that your AASA is in a valid format and pattern matches correctly, use the built-in `swcutil` tool on a Mac. Running `sudo swcutil` in Terminal shows the available commands, including `swcutil dl` and `swcutil verify`.

You can use these commands in Terminal by:

- Running `sudo swcutil dl -d ` to check that the AASA JSON can be downloaded successfully.

- Running `sudo swcutil verify -d  -j  [-u ]` to check the contents of a downloaded `.json` AASA file. Verify that your domains match with `-d` and your URL path pattern matches with the JSON with `-u`. If both are successful, you will get a confirmation message.

For an app containing `applinks:example.com` and the AASA shown above, here is an example of using `swcutil verify` where “s” is the service, “a” is the App ID, and “d” is the domain:

```
% sudo swcutil verify -d example.com -j ./example.json -u https://example.com/test
{ s = applinks, a = ABCD123.com.example.app, d = example.com }:
Pattern "https://example.com/test" matched.
```

Since the pattern `/test` is included in the AASA, the JSON has successfully pattern matched and is verified. For the path `/path/1`, since it is set to be excluded in the AASA, you would see a message confirming the exclusion:

```
Pattern "https://example.com/path/1" blocked match.
```

If you see this message for a URL path that is not excluded, your AASA has not been matched. Take a look at the Debug through sysdiagnose section for more information.

## Debug through sysdiagnose

If the output from `swcutil` in the section Host and verify your AASA is showing invalid universal links, take a sysdiagnose on a device with the app installed by following the linked instructions for each platform in Profiles and Logs. After you have opened the sysdiagnose, open the `swcutil_show.txt` file. Search for your `App ID` to see the information for your `applinks` as shown in the following example.

```
Service:              applinks
App ID:               1234abcd.com.example
Domain:               example.com
User Approval:        unspecified
Site/Fmwk Approval:   approved
Last Checked:         2023-08-24 10:09:00 +0000
Next Check:           2023-08-18 21:00:19 +0000
```

`User Approval`: Shows the user’s decision to open links in your app or in the web browser. Review Test universal links behavior for more information.

`Site/Fmwk Approval`: Specifies if the Apple-managed content delivery network (CDN) has approved your universal links and pattern matched successfully. If it is `approved`, your universal links are working correctly.

If it is `unspecified` or `denied`, please ensure you are allowing full access to all IP addresses and the domain is included in your associated domains. For more information, review Understand Apple’s CDN.

`Last Check/Next Check`: Specifies the last time Apple’s CDN requested your site for your AASA and when it will check again.

## Understand Apple’s CDN

When your app is installed on a device, Apple’s CDN requests your AASA file. For the CDN to successfully cache the file, it must be hosted on a domain that is available to all IP addreses and ranges, does not redirect, and is not blocked by access policies.

When testing, if you’re running your app from Xcode, using a server that is unreachable from the public internet, or testing changes faster than Apple’s CDN can cache them, use an alternate `developer` mode as described in Associated Domains Entitlement. This allows you to bypass Apple’s CDN and pulls your AASA directly from your domain.

Important

On iOS 14 and later, Apple’s CDN retrieves and caches the AASA file. When your app is installed, devices download the file from the CDN immediately. Devices check for updates approximately once per week after app installation. To download a newer version of the AASA file, reinstall the app. There is no direct CDN invalidation option.

## Revision History

- **2025-03-12** Clarified how web browsers interact with universal links. Made other minor editorial changes.

- **2024-08-13** Made minor changes, added note for port numbers.

- **2023-09-05** First published.

## See Also

### Latest

TN3182: Adding privacy tracking keys to your privacy manifest

Declare the tracking domains you use in your app or third-party SDK in a privacy manifest.

TN3183: Adding required reason API entries to your privacy manifest

Declare the APIs that can potentially fingerprint devices in your app or third-party SDK in a privacy manifest.

TN3184: Adding data collection details to your privacy manifest

Declare the data your app or third-party SDK collects in a privacy manifest.

TN3181: Debugging an invalid privacy manifest

Identify common configurations that cause unsuccessful privacy manifest validation with the App Store.

TN3180: Reverting to App Store Server Notifications V1

Migrate from version 2 to version 1 of App Store Server Notifications using the Modify an App endpoint.

TN3179: Understanding local network privacy

Learn how local network privacy affects your software.

TN3178: Checking for and resolving build UUID problems

Ensure that every Mach-O image has a UUID, and that every distinct Mach-O image has its own unique UUID.

TN3177: Understanding alternate audio track groups in movie files

Learn how alternate groups collect audio tracks, and how to choose which audio track to use in your app.

TN3111: iOS Wi-Fi API overview

Explore the various Wi-Fi APIs available on iOS and their expected use cases.

TN3176: Troubleshooting Apple Pay payment processing issues

Diagnose errors that occur when processing Apple Pay payments, identify common causes, and explore potential solutions.

TN3175: Diagnosing issues with displaying the Apple Pay button on your website

Diagnose common errors received while displaying the Apple Pay button on your website by identifying the underlying causes, and explore potential solutions.

TN3174: Diagnosing issues with the Apple Pay payment sheet on your website

Diagnose errors received while presenting the Apple Pay payment sheet on your website by identifying the underlying causes of common errors and explore their potential solutions.

TN3173: Troubleshooting issues with your Apple Pay merchant identifier configuration

Diagnose errors due to invalid Apple Pay merchant identifier configurations by identifying the underlying causes of common errors and explore their potential solutions.

TN3168: Making your App Clip available in the App Store

Learn how to configure your App Clip to prevent it from being unavailable in the App Store.

TN3124: Debugging coordinate space issues

Learn techniques to help debug any coordinate space issue.

