

- MusicKit
-  Using Automatic Developer Token Generation for Apple Music API 

Article

# Using Automatic Developer Token Generation for Apple Music API

Enable your app’s integration with the MusicKit App Service in the developer portal.

## Overview

MusicKit accelerates the way you integrate your app with Apple Music API by automatically generating the developer token on behalf of your app. It then includes the developer token in requests that it issues to Apple Music API for your app.

To benefit from this automatic behavior, just enable the MusicKit App Service in the developer portal for your app. The MusicKit App Service is a runtime service that automatically associates with your app’s bundle identifier.

### Enable the MusicKit App Service

1.  In Safari, visit the Certificates, Identifiers, and Profiles section of the developer web site.

2.  In the Identifiers subsection, open the App ID for your app and begin editing its configuration, or create a new one.

3.  On the Register an App ID page, select the Explicit option for the bundle ID of your app.

4.  Click or tap the App Services tab, and select the Enabled checkbox for MusicKit. 

5.  Complete the App ID creation process, or save the changes.

Be sure to set the bundle identifier of your app target to the same value you use for your App ID in these steps.

## See Also

### Essentials

Using MusicKit to Integrate with Apple Music

Find an album in Apple Music that corresponds to a CD in a user’s collection, and present the information for the album.

NSAppleMusicUsageDescription

A message that tells the user why the app is requesting access to the user’s media library.

