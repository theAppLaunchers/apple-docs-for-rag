

- ClassKit
- Enabling ClassKit in your app
-  About ClassKit and user roles 

Article

# About ClassKit and user roles

Understand how ClassKit interacts with different kinds of users.

## Overview

When you adopt ClassKit, you enable your app to participate in an educational ecosystem where teachers create assignments and students report progress. Users of your app can choose to participate in this ecosystem by signing in to a device running your app with a Managed Apple ID. This is a special Apple ID provided to the user by a school enrolled in Apple School Manager. It identifies its owner as either a student or a teacher. Other users of your app, using a standard Apple ID, don’t participate in this ecosystem at all. This creates three distinct classes of users that your app deals with: students, teachers, and unmanaged users. ClassKit modulates its behavior according to the current user’s role.

### ClassKit doesn’t share the user’s role with your app

Some of the data you provide to ClassKit is specific to the user’s role. For example, only teachers need to store a complete enumeration of all possible assignments (so they can assign them from the Schoolwork app), whereas only students need to record progress as they move through assignments. Users without a Managed Apple ID don’t need to record any data at all.

However, to ensure privacy, ClassKit doesn’t share the role of the current user, or even whether the current user has a Managed Apple ID, with your app. To prevent leaking information to your app, all ClassKit interactions, including delegate callbacks and error messages, look the same no matter what the user’s role. This means you can build a single implementation that works for any user. ClassKit efficiently ignores data that it doesn’t need.

For example, your implementation should always report progress through every unit of assignable content. ClassKit takes care to drop any progress data reported for a teacher, an unmanaged user, and even a student that hasn’t yet received an assignment corresponding to that content.

Note

For more information about handling privacy in your app, see Privacy Requirements for Apps Using ClassKit.

### ClassKit alerts students that their progress is measured

When a student runs your app, ClassKit alerts the student on your behalf that progress is shared with teachers by briefly showing a message over your content. For a student in a class called *Dev Class* using an app called *GreatPlays*, the overlay looks like this:

You don’t need to take any special action in your app for this message to appear.

As the message indicates, ClassKit only retains progress on tasks that have explicitly been assigned by a teacher. Even for a student, ClassKit discards any usage data not explicitly requested in the form of an assignment.

Other users—teachers and those without managed accounts—don’t receive this warning, because ClassKit discards all progress data that you attempt to record for them.

