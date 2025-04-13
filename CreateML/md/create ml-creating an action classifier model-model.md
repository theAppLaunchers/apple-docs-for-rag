

- Create ML
-  Creating an Action Classifier Model 

# Creating an Action Classifier Model

Train a machine learning model to recognize a person’s body movements.

## Overview

An *action classifier* is a machine learning model that identifies a person’s body movements in a video. For example, an action classifier you train to classify exercise movements can predict “jumping jacks” when you provide it with a video of a person doing jumping jacks.

Create an action classifier with Create ML by gathering example videos of individuals performing each action you want the classifier to recognize and identify. For example, to train an exercise action classifier, gather videos of individuals performing various exercises, such as jumping jacks, squats, and lunges.

Create ML uses Vision during training to find significant points on a person’s body, called *landmarks*, in each frame of a video. Action classifiers learn to recognize the movement patterns of these points over time. For more information about how to use Vision to locate body landmarks, see Detecting Human Body Poses in Images.

The Create ML developer tool helps you train, assess, and preview an action classifier model. You can train multiple models in a single project by configuring a *model source* — a combination of training data and parameters — for each. Once you’re satisfied with an action classifier, export it as a Core ML model file to add it to your Xcode project.

At runtime, your app uses the action classifier to identify a person’s action by analyzing a series of video frames from a camera or file.

Training an action classifier with the Create ML developer tool follows the same general workflow as other model types, such as an image classifier (see Creating an Image Classifier Model). However, the workflow for an action classifier has some important differences, including:

- Configuring the action classifier’s frame rate based on its destination app

- Acquiring videos that meet or exceed that frame rate

- Acquiring videos of humans clearly performing actions in a suitable environment

- Acquiring videos of related but irrelevant actions

Note

Session 10043: Build an Action Classifier with Create ML

### Choose a Frame Rate

Before you create an action classifier, decide what *frame rate —* the number of video frames, per second — the destination app uses from a camera or file.

Important

Your app’s frame rate is a significant factor that affects your action classifier and the training data you’ll need to collect.

Plan to match your action classifier’s frame rate to the destination app’s frame rate. For example, if your app acquires video from a camera at 30 frames per second (fps), plan to configure your action classifier to 30 fps.

### Collect Example Action Videos

Once you’ve determined your action classifier’s frame rate, collect training videos. Unlike the classifier and destination app frame rates that need to match, the frame rates of these videos can be greater than or equal to the classifier’s frame rate. For example, you can use videos at 30, 50, or 60 frames per second to train an action classifier you configure to 30 fps.

Collect at least 50 example videos for each action you want the action classifier to identify. Make sure each example video clearly shows a single person performing the action. For videos of multiple people, ensure the individual performing the action is the largest and most dominant person in the frame.

Additionally, collect example videos for a *negative class*, which is a group of related actions the action classifier might see but aren’t relevant to your app. Negative classes help action classifiers avoid mistaking irrelevant actions for relevant ones.

See Gathering Training Videos for an Action Classifier for more details on collecting high-quality training videos and creating negative classes.

### Organize the Example Videos

The Create ML developer tool supports several types of data sources, each with its own arrangement of files within a parent folder. For example, two common data-source types are:

- Single-action video files sorted into labeled folders

- Single- or multiple-action video files and one annotation file

See Building an Action Classifier Data Source for detailed instructions on organizing your video files into one of these arrangements.

### Configure an Action Classification Project

Open the developer tool by choosing Xcode \> Open Developer Tool \> Create ML, and create a new Action Classification project.

In the Data section of the model source’s Settings tab, drag the parent folder of your training data source onto the Training Data box.

If applicable, drag your validation and testing data sources’ folders onto the Validation Data and Testing Data boxes, respectively. If you don’t provide a data source for validation, Create ML automatically configures Validation Data to use a portion of Training Data’s data source.

Configure the action classifier’s model source by setting the values in the Parameters section. Set the Frame Rate parameter to the same value as your destination app’s frame rate. For example, if the action classifier’s destination app captures and analyzes video at 30 frames per second, set Frame Rate to 30 fps.

Choose an Action Duration based on the time it takes to complete most of the data source’s actions. For example, if the majority of actions in the training video files take about two seconds, set Action Duration to 2 seconds.

Create ML calculates the model’s prediction window size — the number of frames it needs to make a prediction — by multiplying the Frame Rate and Action Duration settings. In this example, the prediction window is 60 frames long, or 30 fps multiplied by 2 seconds.

If all the actions are equally valid from the camera’s left or right, you can effectively double your training data by enabling the Horizontal Flip augmentation. When you enable Horizontal Flip, Create ML makes a horizontally mirrored copy of the landmark position outputs for each video frame Vision analyzes.

### Train the Action Classifier

To begin the training session, click Train. Create ML starts with the feature-extraction phase, using a VNDetectHumanBodyPoseRequest to find the person’s body landmarks in each frame.

The feature-extraction phase can take some time, depending on the size of the training data and your Mac’s performance. Upon completion, Create ML starts the training phase, where it teaches the action classifier to recognize the actions from sequences of landmark outputs. As it learns, Create ML displays a plot of the model’s accuracy against training iteration.

If you need to temporarily suspend the training session for any reason, such as to save battery power, click Pause. When you’re ready to continue training, click Resume.

If you want to try a preliminary version of the model before it’s finished training, click Snapshot. You can create a Core ML model file from a snapshot by selecting the snapshot and then exporting it in the Output tab. See “Export the Action Classifier” below for more details about the Output tab.

### Assess the Action Classifier

Evaluate the model’s prediction accuracy by inspecting its Recall and Precision metrics for the training, validation, or testing phases in the Evaluation tab.

If the action classifier doesn’t meet your needs, click Train More to further train the model. If the additional training iterations don’t improve the action classifier’s performance, you can select File \> New Model Source to train a model with either or both of the following:

- A new or modified training-data source

- Different parameters

If you need an action classifier with better accuracy, try adjusting the Action Duration parameter or enabling the Horizontal Flip augmentation. If the action classifier struggles to identify specific actions, create or modify a data source with additional, high-quality example videos of those actions.

If an action classifier misidentifies a nonaction as an action, create or augment a negative class with examples of that irrelevant action. See Gathering Training Videos for an Action Classifier for more information about creating a negative class.

Once you’ve configured the new model source, click Train to create a new action classifier with that configuration. Repeat the process of evaluating, adjusting, and training action classifiers until you’re satisfied with the performance of one of them.

### Preview the Action Classifier

Use the Preview tab to quickly test your action classifier before you add it to an Xcode project. Get a visual sense of how the model works by dragging in a video and clicking the Play button to see the model’s predictions.

When you drag in a video file, Create ML uses the action classifier to analyze the entire file at once. When you play the video, Create ML shows the action classifier’s predictions for each frame in real time.

Tip

Quickly test an action classifier’s ability to recognize all of its action classes by previewing an action montage video.

### Export the Action Classifier

To save an action classifier as a Core ML file, select the Output tab and click the Get, Xcode, or Share button. You can export a model from any model source that’s finished training or from any snapshot you created while training the model.

For an example app that integrates and applies an action classifier, see the related sample code projects:

- Detecting Human Actions in a Live Video Feed

- Building a feature-rich app for sports analysis

## Topics

### Action Classifier Data Sources

Gathering Training Videos for an Action Classifier

Collect quality example videos that effectively train action classifiers.

Building an Action Classifier Data Source

Arrange your training videos in multiple folders with labels that describe actions, or in a single folder with an annotation file.

## See Also

### Video Models

Detecting Human Actions in a Live Video Feed

Identify body movements by sending a person’s pose data from a series of video frames to an action-classification model.

struct MLActionClassifier

A model you train with videos to classify a person’s body movements.

struct MLHandActionClassifier

A task that creates a hand action classification model by training with videos of people’s hand movements that you provide.

struct MLStyleTransfer

A model you train to apply an image’s style to other images or videos.

