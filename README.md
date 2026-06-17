# EdgeVision

COMP4310 Mobile Software Development
Birzeit University, Group 2, Assignment 2

## What this is

A small Flutter app that does object detection through the phone camera. Runs locally so it still works in airplane mode.

## How it works

The camera frames go through Google ML Kit. ML Kit runs a TensorFlow Lite model called object_labeler.tflite (around 3.7 MB) that we bundled inside the assets folder. For each frame the model classifies what is in the picture and the app draws a box around the object with a label like Clothing or Plant on top.

## Stuff we used

Flutter and Dart, Google ML Kit (the google_mlkit_object_detection package), the camera package for the live feed, provider for state, permission_handler for the camera popup, and path_provider to copy the model out of the assets folder so ML Kit can load it from a real file path.

## Project layout

```
lib/
  main.dart                              app entry
  data/
    ml_repository.dart                   loads the tflite model and runs detection
    models/detection_result.dart         small data class
  viewmodel/
    detection_viewmodel.dart             camera lifecycle and frame loop
  view/
    camera_screen.dart                   main screen
    widgets/bounding_box_painter.dart    draws the boxes
assets/
  ml/object_labeler.tflite               the model
```

## Running it

Needs Flutter and an Android phone or emulator.

```
flutter pub get
flutter run
```

It asks for camera permission once then you can point it at things.

## Heads up

The model is tiny so accuracy is not great. A lighter sometimes shows up as a water bottle, a water bottle as tableware, etc. The labels are very general too (Clothing, Food, Plant, Home good, things like that). A bigger model would do better but would also make the apk way heavier so we kept this one.

## Team

Ahmad Hamza 1210381
Tala Khateeb 1222091
Laith Amro 1230018
Mohammad Aljamal 1220378
