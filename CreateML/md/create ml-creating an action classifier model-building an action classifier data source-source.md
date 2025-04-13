

- Create ML
- Creating an Action Classifier Model
-  Building an Action Classifier Data Source 

Article

# Building an Action Classifier Data Source

Arrange your training videos in multiple folders with labels that describe actions, or in a single folder with an annotation file.

## Overview

The Create ML developer tool accepts several data-source types for an action classifier, each with its own file-system arrangement. Typically, you use one of these two types:

Labeled folders  
A collection of single-action video files you group into labeled folders

Annotated videos  
A collection of single- or multi-action video files with an accompanying annotation file you group into a single folder

If you’ve trimmed all your example video files and they demonstrate a single action one or more times, you can use either data-source type. Otherwise, if you haven’t trimmed all your videos or if one or more is a *montage* video — a video file that contains two or more distinct actions — you must use annotated videos.

For more information about the action-classifier data-source types the Create ML API supports, see MLActionClassifier.DataSource.

For general information about how to create an action classifier, see Creating an Action Classifier Model.

### Build a Data Source with Labeled Folders

Create a parent folder to contain the labeled folders. Then, create a folder for each action, using the name of the action for the label. Place each example video file into the folder with a label that matches the video’s action. For example, for a data source that has folders named “Jumping Jacks” and “Squats,” place videos of those actions into their corresponding folders.

Important

Each video in a labeled folder’s data source must demonstrate a single type of action.

Each video file may have more than one instance of an action, but the videos must minimize the time between each instance. If you notice inactivity between action instances, remove the inactivity by breaking the video file into separate files and trimming each video to the action.

### Build a Data Source with Annotated Videos

Create a folder and place all your example video files in it. Then, create an annotation file using either a CSV — with either `.csv` or `.txt` file extensions — or JSON format.

Each entry in the annotation file must have these categories:

`label`  
A name or label that describes the action

`video`  
The file name or path of the video that contains the example action

To mark the beginning and ending of an example video clip within a larger video file, your annotation file can also include time-index categories:

`start`  
The starting-time index in the video file

`end`  
The ending-time index in the video file

Use the `start` and `end` time indices for a *montage* video, which is a video that demonstrates two or more different types of action. If your annotation file omits the `start` category, Create ML defaults to the beginning of every video file for every entry. If your annotation file omits the `end` category, Create ML defaults to the end of every video.

Important

If you use a `start` or `end` category for any annotation entry, you must provide a value for that category in all annotation entries.

Create ML recognizes several different types of time indices including:

- An integer of seconds, for example: `0`, `3`, or `5`.

- A floating point number of seconds, for example: `0.0`, `3.14`, or `60.5`.

- A string of minutes and seconds, for example: `01:03`.

- A string of minutes, seconds, and fractional seconds, for example: `01:03.14`.

- A string of hours, minutes, and seconds, for example: `05:01:03`.

Use the these indices to specify when an example clip begins and ends within its video file. For example, if a single video file contains squats and lunges, you can use that file in multiple annotations with different time indices, as shown in this CSV file example:

```
video, label, start, end
lunge23.mov, Lunge, 0, 3.1
squats_13.mov, Squat, 0, 5
Jumping Jacks 1.mov, Jumping Jacks, 0, 4.7
Various_Exercises.mov, Lunge, 0.0, 2.2
Various_Exercises.mov, Lunge, 8:3.2, 8:4.5
Various_Exercises.mov, Squat, 1:59:5.8, 1:59:7
Various_Exercises.mov, Squat, 1:59:14, 1:59:15.1
```

To create an annotation file in JSON format, create an array of annotation objects at the root of the file. The following example shows the JSON equivalent of the preceding CSV file:

```
 [
  {
    "video" : "lunge23.mov",
    "label" : "Lunge",
    "start" : 0,
    "end"   : 3.1
  },
  {
    "video" : "squats_13.mov",
    "label" : "Squat",
    "start" : 0,
    "end"   : 5
  },
  {
    "video" : "Jumping Jacks 1.mov",
    "label" : " Jumping Jacks",
    "start" : 0,
    "end"   : 4.7
  },
  {
    "video" : "Various_Exercises.mov",
    "label" : "Lunge",
    "start" : 0.0,
    "end"   : 2.2
  },
  {
    "video" : "Various_Exercises.mov",
    "label" : "Lunge",
    "start" : "8:3.2",
    "end"   : "8:4.5"
  },
  {
    "video" : "Various_Exercises.mov",
    "label" : "Squat",
    "start" : "1:59:5.8",
    "end"   : "1:59:7"
  },
  {
    "video" : "Various_Exercises.mov",
    "label" : "Squat",
    "start" : "1:59:14",
    "end"   : "1:59:15.1"
  }
]
```

## See Also

### Action Classifier Data Sources

Gathering Training Videos for an Action Classifier

Collect quality example videos that effectively train action classifiers.

