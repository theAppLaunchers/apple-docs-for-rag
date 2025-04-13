

- Xcode
- Distribution
-  Packaging Mac software for distribution 

Article

# Packaging Mac software for distribution

Build a zip archive, disk image, or installer package for distributing your Mac software.

## Overview

Xcode handles many common scenarios for Mac software distribution, such as uploading your app to the Mac App Store. Some products that you build with Xcode or with third-party developer tools require other steps for distribution. These products include the following:

- Products that aren’t apps

- Products that include multiple components, for example, an app with an associated daemon

- Products you distribute directly

- Products you build with third-party developer tools

If you can’t build and distribute your product using Xcode alone, choose a container format and package your product for distribution. If you distribute your product directly (in other words, through a channel other than the Mac App Store), you sign your code for distribution and create a distribution container file, then notarize the container file. You may consider automating this process to repeat it for each version of your app. For more information, see Creating distribution-signed code for macOS.

Note

If you use a third-party developer tool to build your app, consult its documentation for advice specific to that tool.

## Decide on a container format

To get started, decide on your container format. Mac products support two distribution channels:

- You can distribute apps in the Mac App Store.

- You can use Developer ID signing to distribute apps and other products directly, outside of the Mac App Store.

To distribute an app in the Mac App Store, you submit the app as an installer package. For direct distribution, you have a choice of various container formats, the most common being:

Zip archive (`.zip`)  
You can’t sign a zip archive, so any files or folders you include that aren’t covered by your code signature may be tampered with by an attacker. The person receiving your zip archive opens it with Finder to unarchive the contents, which they optionally move into their preferred location.

Disk image (`.dmg`)  
You can sign a disk image, which protects all files and folders you include from modification after you sign it. The person receiving your disk image opens it in Finder to access its contents, and they may choose to run your app from the disk image or move it to their preferred location. This experience is easiest if your product is a single file or bundle.

Installer package (`.pkg`)  
You need to sign an Installer package, which protects all files and folders you include from modification after you sign it. The person receiving your Installer package opens it in Finder to launch the Installer app, which guides them through the steps needed to install your product. An installer package is the best choice if your product contains multiple components, must be copied to specific locations, or if you need to run custom code during installation.

You can nest these containers. For example, you might want to ship an app inside an installer package on a disk image. To nest containers, work from the lowest-level container to the highest-level container, following the instructions for each container at each step.

Sign your code, and sign each nested container that supports signing. For example, if you ship an app inside an installer package on a disk image, sign the app, create the installer package, sign that package, create the disk image, and then sign the disk image. For more information about signing code for distribution, see Creating distribution-signed code for macOS.

## Build a zip archive

If you choose to distribute your product in a zip archive, use the `ditto` command-line tool to create that archive:

1.  Create a directory that holds everything you want to distribute.

2.  Run the `ditto` tool as shown below:

```
% ditto -c -k --keepParent  
```

In this example command, `` is the path to the directory you create in step 1, and `` is the location where `ditto` should create the zip archive. You can’t sign zip archives, but you can sign their contents.

## Build an Installer package

If you choose to distribute your product in an Installer package, start by determining your Installer signing identity. Choose the right identity for your distribution channel:

- If you’re distributing an app on the Mac App Store, use a Mac Installer Distribution signing identity. This is named `3rd Party Mac Developer Installer: `, where `` identifies your team.

- If you’re distributing a product independently, use a Developer ID Installer-signing identity. This is named `Developer ID Installer: `, where `` identifies your team.

For information on how to set up these Installer-signing identities, see Developer Account Help.

Run the following command to confirm that your Installer-signing identity is present and correct:

```
% security find-identity -v               
  1) 6210ECCC616B6A72F238DE6FDDFDA1A06DEFF9FB "3rd Party Mac Developer Installer: …"
  2) C32E0E68CE92936D5532E21BAAD8CFF4A6D9BAA1 "Developer ID Installer: …"
     2 valid identities found
```

The `-v` argument filters for valid identities only. If the Installer-signing identity you need isn’t listed, see Developer Account Help.

Important

Don’t use the `-p codesigning` option to filter for code-signing identities. Installer-signing identities are different from code-signing identities, so the `-p codesigning` option filters out installer-signing identities.

If your product consists of a single app, use the `productbuild` tool to create a simple Installer package for it. The following is the simplest use of `productbuild`, sufficient for submitting your app to the Mac App Store:

```
% productbuild --sign  --component  /Applications 
```

Make the following substitutions to this command:

``  
Your Installer-signing identity.

``  
The path to your app.

``  
The path where `productbuild` creates the Installer package.

If you have a more complex product, you’ll need a more complex Installer package. For more details on how to work with Installer packages, see the manual pages for `productbuild`, `productsign`, `pkgbuild`, and `pkgutil`. For instructions on how to read a manual page, see Reading UNIX Manual Pages.

## Build a disk image file

If you choose to distribute your product in a disk image file (`.dmg`), follow these steps:

1.  Create a directory to act as the source for the root directory of your disk image’s volume.

2.  Populate that directory with the items you want to distribute. If you’re creating a script to automate this process, use `ditto` rather than `cp` because `ditto` preserves symlinks.

3.  Use the `hdiutil` command below to create the disk image file:

```
% hdiutil create -srcFolder  -o 
```

In this command, `` is the directory you created in step 1, and `` is the path where `hdiutil` creates the disk image file.

4.  Decide on a code-signing identifier for this disk image. If you’re signing bundled code, construct a code-signing identifier using your code’s bundle ID as the prefix followed by a unique string. Otherwise, construct the prefix by following the steps in Sign each code item in Creating distribution-signed code for macOS. Use a unique code-signing identifier that differs from the identifiers on your other products, including code-bundle identifiers.

5.  Use the `codesign` command below to sign the disk image:

```
% codesign -s  --timestamp -i  
```

In this command, `` is your Developer ID application code-signing identity (for example, `Developer ID Application: `), `` is the code-signing identifier you chose in step 4, and `` is the path to the disk image you created in step 3. Use a code-signing identity, not an installer-signing identity.

For more information on code-signing identities, see “Confirm your code-signing identity” in Creating distribution-signed code for macOS.

You can use a third-party tool to configure a disk image for distribution. For example, the tool might arrange the icons, set a background image, and add a symlink to the Applications folder. If you use a third-party tool, make sure that the resulting disk image:

- Is signed with your Developer ID Application code-signing identity

- Is a UDIF-format read-only zip-compressed disk image (type `UDZO`)

## Submit your app to the Mac App Store

If you’re creating an app for the Mac App Store, submit your signed installer package using either the `altool` command-line tool or the Transporter app. For detailed instructions, see App Store Connect Help > Reference > Upload tools.

## Notarize your product

If you distribute your product directly, notarize the file you intend to distribute to your users. For more information, see Customizing the notarization workflow. Skip the “Export a package for notarization” section because you already have the file that you want to submit.

If you distribute your product using nested containers, only notarize the outermost container. For example, if you have an app inside an installer package on a disk image, sign the app, sign the installer package, and sign the disk image, but only notarize the disk image.

If you use a third-party installer tool, refer to Customizing the notarization workflow.

## Staple your product

Once you’ve notarized your product, staple the resulting ticket to the file you intend to distribute. For information about how to do this for an app within a zip archive, see “Staple the Ticket to Your Distribution” in Customizing the notarization workflow. The other common container formats, installer packages and disk images, support stapling directly. For example, to staple a ticket to a disk image:

```
% xcrun stapler staple FlyingAnimals.dmg
```

If you don’t staple the ticket to your distribution file, Gatekeeper might block a user from installing or using your product while their Mac is offline.

## Test your distributed product

For products that you distribute directly, test that the product works correctly when you use it from the installer package, disk image, or zip file you created. If possible, do this testing on a different Mac than the one where you develop the software, so that development data doesn’t affect the test outcomes. Consider these scenarios:

- A fresh distribution, on a Mac where your product hasn’t been used before

- An upgrade distribution, on a Mac where the person has already used an older version of your product (consider both the situations where the new version replaces the old version, and the new version is in a different location than the old version)

- A duplicate distribution, on a Mac that already contains the same version of your product in a different location

- A distribution where the person using your app is signed in to a different account on the Mac than the person who installed the app

For products that you distribute as zip files or disk image files, consider these additional scenarios:

- The person opens your app without moving it to a different location. In this situation, when the person first opens your app, Gatekeeper randomizes its path as returned from bundleURL and other API. This measure stops your app from accessing resources outside its bundle (and therefore not sealed by its code signature) using a relative path, as an attacker could control those resources to change your app’s behavior. Gatekeeper only performs this *translocation* on first launch, so test the behavior on a subsequent launch too.

- The person moves your app to a different location, then launches it. Gatekeeper doesn’t translocate your app’s path in this case.

## See Also

### Distribution and release

Distributing your app for beta testing and releases

Release your app to beta testers and users.

Distributing your app to registered devices

Register devices in your developer account and deploy your app to them for testing.

