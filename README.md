# Android Shake-to-Capture Camera App

A native Android application that interacts directly with device hardware. The app utilizes the built-in accelerometer to detect physical movement and automatically launches the device's camera when a "shake" gesture is detected.

## Key Technologies
* Java (Android SDK)
* Android Hardware Sensors (`SensorManager`, Accelerometer)
* Camera API & Implicit Intents (`MediaStore.ACTION_IMAGE_CAPTURE`)
* Runtime Permissions Handling

## Features & Methodology
* **Motion Detection:** The app registers a `SensorEventListener` to monitor real-time accelerometer data. If the acceleration force exceeds a predefined threshold (`SHAKE_THRESHOLD`), it triggers the camera sequence.
* **Battery Optimization:** The sensor listener is strictly tied to the Activity's lifecycle. It registers during `onResume()` and unregisters during `onPause()` to prevent unnecessary battery drain while the app is in the background.
* **Dynamic Permissions:** Implements modern Android security protocols by requesting Camera permissions at runtime rather than relying solely on the Manifest declaration.
* **Image Retrieval:** Captures the resulting image via `onActivityResult` and renders the Bitmap directly onto the application's UI.
