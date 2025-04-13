

- ARKit
- ARKit in iOS
- Content Anchors
-  Validating a Model for Motion Capture 

Article

# Validating a Model for Motion Capture

Verify that your character model matches ARKit’s Motion Capture requirements.

## Overview

ARKit‘s body-tracking functionality requires models to be in a specific format. Models that don’t match the expected format may work incorrectly, or not work at all. Use the detailed information in this article to verify that your character’s scene coordinate system and orientation match ARKit’s expectations, and ensure that your skeleton matches ARKit’s expected joint names and hierarchy for Motion Capture.

Additionally, you can verify models that you’ve rigged according to Rigging a Model for Motion Capture, and use the information to modify your existing rigged humanoid models to match the expected format.

### Confirm Scene and Model Coordinate Systems

Your exported model must use a scene coordinate system that uses +Y for up, +Z for forward, and +X for right. Your model also must face forward on the +Z axis.

If your 3D software package doesn’t use this coordinate system by default, you may be able to reconfigure your scene settings or transform the coordinate system as part of the export process.

### Validate Joint Names, Relationships, and Orientation

The joints that make up your model’s skeleton must exactly match ARKit’s required joint names. Additionally, the relationship between joints must also match ARKit’s layout.

Although your skeleton must contain all the expected joints in the correct hierarchy, you don’t have to bind vertices to every bone. If your character doesn’t need moving eyes, for example, its skeleton must still have the bones that control the eyes, but you can simply bind no part of your model to those bones so they have no affect on your model.

Make sure to match the orientation of every joint in your model in its bind post to match the values in the model biped skeleton.

Note

Joints in a skeletal model represent any potential point of articulation. While many of the joints correspond to anatomical joints, others simply represent a portion of the model that can be moved or deformed in some way.

### Confirm Bind Pose and Binding

Your characters should be rigged in a standard T-pose. Although some software packages allow you to bind your character mesh in multiple poses, your character model shouldn’t have any additional bind poses. No more than four joints should contribute to the movement of any single vertex in your model and you shouldn’t add any animation keyframes to your character.

### Match Torso Joints

The torso of a puppeteering skeleton should contain eight joints: the hip joint, which is the root of the joint hierarchy, and seven spine joints. The hip joint and first spine joint overlap when the character is in the T-pose position.

| Joint name      | Parent joint    |
|-----------------|-----------------|
| `hips_joint`    | `root`          |
| `spine_1_joint` | `hips_joint`    |
| `spine_2_joint` | `spine_1_joint` |
| `spine_3_joint` | `spine_2_joint` |
| `spine_4_joint` | `spine_3_joint` |
| `spine_5_joint` | `spine_4_joint` |
| `spine_6_joint` | `spine_5_joint` |
| `spine_7_joint` | `spine_6_joint` |

### Review Head and Neck Joints

The head contains four neck joints extending from the spine, as well as joints for controlling the specific parts of the head, including the eyes and eyelids, nose, chin, and jaw.

| Joint name                | Parent joint      |
|---------------------------|-------------------|
| `neck_1_joint`            | `spine_7_joint`   |
| `neck_2_joint`            | `neck_1_joint`    |
| `neck_3_joint`            | `neck_2_joint`    |
| `neck_4_joint`            | `neck_3_joint`    |
| `head_joint`              | `neck_4_joint`    |
| `jaw_joint`               | `head_joint`      |
| `chin_joint`              | `jaw_joint`       |
| `nose_joint`              | `head_joint`      |
| `right_eye_joint`         | `head_joint`      |
| `right_eyeUpperLid_joint` | `right_eye_joint` |
| `right_eyeLowerLid_joint` | `right_eye_joint` |
| `right_eyeball_joint`     | `right_eye_joint` |
| `left_eye_joint`          | `head_joint`      |
| `left_eyeUpperLid_joint`  | `left_eye_joint`  |
| `left_eyeLowerLid_joint`  | `left_eye_joint`  |
| `left_eyeball_joint`      | `left_eye_joint`  |

### Review Arm and Shoulder Joints

Both arms descend from the seventh spine joint and are comprised of three joints, representing the shoulder, elbow, and wrist.

| Joint name               | Parent joint             |
|--------------------------|--------------------------|
| `right_shoulder_1_joint` | `spine_7_joint`          |
| `right_arm_joint`        | `right_shoulder_1_joint` |
| `right_forearm_joint`    | `right_arm_joint`        |
| `left_shoulder_1_joint`  | `spine_7_joint`          |
| `left_arm_joint`         | `left_shoulder_1_joint`  |
| `left_forearm_joint`     | `left_arm_joint`         |

### Review Leg and Foot Joints

The leg and foot joints of the model descend from the hips, with joints for moving the upper legs, lower legs, feet, and toes.

| Joint name            | Parent joint        |
|-----------------------|---------------------|
| `left_upLeg_joint`    | `hips_joint`        |
| `left_leg_joint`      | `left_upLeg_joint`  |
| `left_foot_joint`     | `left_leg_joint`    |
| `left_toes_joint`     | `left_foot_joint`   |
| `left_toesEnd_joint`  | `left_toes_joint`   |
| `right_upLeg_joint`   | `hips_joint`        |
| `right_leg_joint`     | `right_upLeg_joint` |
| `right_foot_joint`    | `right_leg_joint`   |
| `right_toes_joint`    | `right_foot_joint`  |
| `right_toesEnd_joint` | `right_toes_joint`  |

### Review Right-Hand Joints

The hands contain many joints, with each of the four fingers comprised of five joints descending from the hand. The thumb has only four joints, but also descends from the hand joint.

| Joint name                   | Parent joint                 |
|------------------------------|------------------------------|
| `right_hand_joint`           | `right_forearm_joint`        |
| `right_handPinkyStart_joint` | `right_hand_joint`           |
| `right_handPinky_1_joint`    | `right_handPinkyStart_joint` |
| `right_handPinky_2_joint`    | `right_handPinky_1_joint`    |
| `right_handPinky_3_joint`    | `right_handPinky_2_joint`    |
| `right_handPinkyEnd_joint`   | `right_handPinky_3_joint`    |
| `right_handRingStart_joint`  | `right_hand_joint`           |
| `right_handRing_1_joint`     | `right_handRingStart_joint`  |
| `right_handRing_2_joint`     | `right_handRing_1_joint`     |
| `right_handRing_3_joint`     | `right_handRing_2_joint`     |
| `right_handRingEnd_joint`    | `right_handRing_3_joint`     |
| `right_handMidStart_joint`   | `right_hand_joint`           |
| `right_handMid_1_joint`      | `right_handMidStart_joint`   |
| `right_handMid_2_joint`      | `right_handMid_1_joint`      |
| `right_handMid_3_joint`      | `right_handMid_2_joint`      |
| `right_handMidEnd_joint`     | `right_handMid_3_joint`      |
| `right_handIndexStart_joint` | `right_hand_joint`           |
| `right_handIndex_1_joint`    | `right_handIndexStart_joint` |
| `right_handIndex_2_joint`    | `right_handIndex_1_joint`    |
| `right_handIndex_3_joint`    | `right_handIndex_2_joint`    |
| `right_handIndexEnd_joint`   | `right_handIndex_3_joint`    |
| `right_handThumbStart_joint` | `right_hand_joint`           |
| `right_handThumb_1_joint`    | `right_handThumbStart_joint` |
| `right_handThumb_2_joint`    | `right_handThumb_1_joint`    |
| `right_handThumbEnd_joint`   | `right_handThumb_2_joint`    |

### Review Left-Hand Joints

The structure and naming convention of the joints of the left hand are similar to those of the right.

| Joint name                  | Parent joint                |
|-----------------------------|-----------------------------|
| `left_hand_joint`           | `left_forearm_joint`        |
| `left_handPinkyStart_joint` | `left_hand_joint`           |
| `left_handPinky_1_joint`    | `left_handPinkyStart_joint` |
| `left_handPinky_2_joint`    | `left_handPinky_1_joint`    |
| `left_handPinky_3_joint`    | `left_handPinky_2_joint`    |
| `left_handPinkyEnd_joint`   | `left_handPinky_3_joint`    |
| `left_handRingStart_joint`  | `left_hand_joint`           |
| `left_handRing_1_joint`     | `left_handRingStart_joint`  |
| `left_handRing_2_joint`     | `left_handRing_1_joint`     |
| `left_handRing_3_joint`     | `left_handRing_2_joint`     |
| `left_handRingEnd_joint`    | `left_handRing_3_joint`     |
| `left_handMidStart_joint`   | `left_hand_joint`           |
| `left_handMid_1_joint`      | `left_handMidStart_joint`   |
| `left_handMid_2_joint`      | `left_handMid_1_joint`      |
| `left_handMid_3_joint`      | `left_handMid_2_joint`      |
| `left_handMidEnd_joint`     | `left_handMid_3_joint`      |
| `left_handIndexStart_joint` | `left_hand_joint`           |
| `left_handIndex_1_joint`    | `left_handIndexStart_joint` |
| `left_handIndex_2_joint`    | `left_handIndex_1_joint`    |
| `left_handIndex_3_joint`    | `left_handIndex_2_joint`    |
| `left_handIndexEnd_joint`   | `left_handIndex_3_joint`    |
| `left_handThumbStart_joint` | `left_hand_joint`           |
| `left_handThumb_1_joint`    | `left_handThumbStart_joint` |
| `left_handThumb_2_joint`    | `left_handThumb_1_joint`    |
| `left_handThumbEnd_joint`   | `left_handThumb_2_joint`    |

## See Also

### Body Position Tracking

Capturing Body Motion in 3D

Track a person in the physical environment and visualize their motion by applying the same body movements to a virtual character.

Rigging a Model for Motion Capture

Configure custom 3D models so ARKit’s human body-tracking feature can control them.

class ARBodyAnchor

An anchor that tracks the position and movement of a human body in the rear-facing camera.

