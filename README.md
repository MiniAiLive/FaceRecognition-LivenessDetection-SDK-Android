<div align="center">
   <h1>Face Recognition with Face Liveness Detection Android SDK</h1>
   <img src=https://miniai.live/wp-content/uploads/2024/02/logo_name-1-768x426-1.png alt="MiniAiLive Logo"
   width="300">
</div>

## Welcome to the [MiniAiLive](https://www.miniai.live/)!
"We provide system integrators with fast, flexible and extremely precise facial recognition with 3D passive face liveness detection (face anti-spoofing) that can be deployed across a number of scenarios, including security, access control, public safety, fintech, smart retail and home protection.
Feel free to use our MiniAI Face Recognition Android SDK."

> **Note**
>
> SDK is fully on-premise, processing all happens on hosting server and no data leaves server.
## Latest SDK Download [Here](https://drive.google.com/file/d/1xQKXovlnwAn63cIjusTppCfI4BbpbGoP/view?usp=drive_link)
## FaceRecognition APK
<a href="https://play.google.com/store/apps/details?id=com.miniai.facerecognition&hl=en-HK" target="_blank">
  <img alt="" src="https://user-images.githubusercontent.com/125717930/230804673-17c99e7d-6a21-4a64-8b9e-a465142da148.png" height=80/>
</a>

<br>

https://github.com/MiniAiLive/MiniAI-Face-Recognition-AndroidSDK/assets/153516004/85a939ed-a607-478b-b48a-80b8582c37b6

## Request license
Feel free to [Contact US](https://www.miniai.live/contact/) to get a trial License. We are 24/7 online on [WhatsApp](https://wa.me/+19162702374).


## Face & IDSDK Online Demo, Resources
<div style="display: flex; justify-content: center; align-items: center;"> 
   <table style="text-align: center;">
      <tr>
         <td style="text-align: center; vertical-align: middle;"><a href="https://github.com/MiniAiLive"><img src="https://miniai.live/wp-content/uploads/2024/10/new_git-1-300x67.png" style="height: 60px; margin-right: 5px;" title="GITHUB"/></a></td> 
         <td style="text-align: center; vertical-align: middle;"><a href="https://huggingface.co/MiniAiLive"><img src="https://miniai.live/wp-content/uploads/2024/10/new_hugging-1-300x67.png" style="height: 60px; margin-right: 5px;" title="HuggingFace"/></a></td> 
         <td style="text-align: center; vertical-align: middle;"><a href="https://demo.miniai.live"><img src="https://miniai.live/wp-content/uploads/2024/10/new_gradio-300x67.png" style="height: 60px; margin-right: 5px;" title="Gradio"/></a></td> 
      </tr> 
      <tr>
         <td style="text-align: center; vertical-align: middle;"><a href="https://docs.miniai.live/"><img src="https://miniai.live/wp-content/uploads/2024/10/a-300x70.png" style="height: 60px; margin-right: 5px;" title="Documentation"/></a></td> 
         <td style="text-align: center; vertical-align: middle;"><a href="https://www.youtube.com/@miniailive"><img src="https://miniai.live/wp-content/uploads/2024/10/Untitled-1-300x70.png" style="height: 60px; margin-right: 5px;" title="Youtube"/></a></td> 
         <td style="text-align: center; vertical-align: middle;"><a href="https://play.google.com/store/apps/dev?id=5831076207730531667"><img src="https://miniai.live/wp-content/uploads/2024/10/googleplay-300x62.png" style="height: 60px; margin-right: 5px;" title="Google Play"/></a></td>
      </tr>
   </table>
</div>

## SDK License

Please replace the our license key with your license key on the MainActivity.kt.
```
        var ret = FaceSDK.setActivation(
            "dYSREvlnlNxuMwFlDCngsmkG5rFIck95ymNvkPDeTUXt3Cj7y0sFIoYIuv3rXaeCb6Imf7lbr7r09S" + 
                "sAPPPhL6oD1uCsdRqddQcMjzHThgjLBXjphSMnclb8SM8mzs/brmMZ+Ofu2p7nqKIy7zJASB3iRo2L5gy7e" + 
                "hNvKUy4bSyt7n7xCz8PrGWmBnphupYbQJLGU24RdVN1suybukqjZX5ctUUu2sDSd2CawEDH7ftLyoLuFrG1v" + 
                "YqExNq/FOhgBjzHgSmZ1tiZa+35rrU6kyzUG6O9Nl8A+Wr/lsV2QDjqn7iGgPmzimGL2pr7OLXJRUkOOWldW" + 
                "detUeqohaI9eA=="
        )
```
## About SDK

### 1. Set up
1. Copy the SDK (`libfacesdk` folder) to the `root` folder in your project.

2. Add SDK to the project in `settings.gradle`.
```bash
include ':libfacesdk'
```

3. Add dependency to your `build.gradle`.
```bash
implementation project(path: ':libfacesdk')
```

### 2. Initializing an SDK

- Step One

To begin, you need to activate the SDK using the license that you have received.
```kotlin
FaceSDK.setActivation("...")
```

If activation is successful, the return value will be `SDK_SUCCESS`. Otherwise, an error value will be returned.

- Step Two

After activation, call the `SDK`'s initialization function.
```kotlin
FaceSDK.init(getAssets());
```
If initialization is successful, the return value will be `SDK_SUCCESS`. Otherwise, an error value will be returned.

### 3. SDK Classes
  - FaceDetectionParam
  
    This class serves as the input parameter for face detection, allowing the inclusion of face liveness detection and specifying the desired liveness detection level.

    | Feature| Type | Name |
    |------------------|------------------|------------------|
    | Check liveness        | boolean    | check_liveness |
    | Check liveness level        | int    | check_liveness_level |

    When check_liveness_level is set to `0`, the liveness detection achieves high accuracy.
    When check_liveness_level is set to `1`, the liveness detection operates with light weight.

### 4. APIs
#### - Face Detection and Liveness Detection

The `FaceSDK` offers a single function for detecting faces, allowing the inclusion of face liveness detection and specifying the desired liveness detection level.
```kotlin
FaceSDK.faceDetection(bitmap, param)
```

This function requires two parameters: a `Bitmap` object and a `FaceDetectionParam` object that enables various processing functionalities.

The return value of the function is a list of `FaceBox` objects. Each `FaceBox` object contains the detected face rectangle, liveness score, and facial angles such as `yaw`, `roll`, and `pitch`.


#### - Create Templates

The `FaceSDK` provides a function that can generate a `template` from a `Bitmap` image. This `template` can then be used to verify the identity of the individual image captured.

```kotlin
byte[] templates = FaceSDK.templateExtraction(bitmap, faceBox);
```

The `SDK`'s `template` extraction function takes two parameters: a `Bitmap` object and an object of `FaceBox`. 

The function returns a byte array, which contains the `template` that can be used for person verification.

#### - Calculation similarity

The `similarityCalculation` function takes a byte array of two `template`s as a parameter. 

```kotlin
float similarity = FaceSDK.similarityCalculation(templates1, templates1);
```

It returns the similarity value between the two `template`s, which can be used to determine the level of likeness between the two individuals.

#### - Yuv to Bitmap
The `SDK` provides a function called `yuv2Bitmap`, which converts a `yuv` frame to a `Bitmap`. Since camera frames are typically in `yuv` format, this function is necessary to convert them to `Bitmap`. The usage of this function is as follows:
```kotlin
Bitmap bitmap = FaceSDK.yuv2Bitmap(nv21, image.getWidth(), image.getHeight(), 7);
```
The first parameter is an `nv21` byte array containing the `yuv` data. 

The second parameter is the width of the `yuv` frame, and the third parameter is its height. 

The fourth parameter is the `conversion mode`, which is determined by the camera orientation.

To determine the appropriate `conversion mode`, the following method can be used:
```kotlin
 1        2       3      4         5            6           7          8

 888888  888888      88  88      8888888888  88                  88  8888888888
 88          88      88  88      88  88      88  88          88  88      88  88
 8888      8888    8888  8888    88          8888888888  8888888888          88
 88          88      88  88
 88          88  888888  888888
```

## Our Products

### Face Recognition SDK
| No | Project | Features |
|----|---------|-----------|
| 1 | [FaceRecognition-SDK-Docker](https://github.com/MiniAiLive/FaceRecognition-SDK-Docker) | 1:1 & 1:N Face Matching SDK |
| 2 | [FaceRecognition-SDK-Windows](https://github.com/MiniAiLive/FaceRecognition-SDK-Windows) | 1:1 & 1:N Face Matching SDK |
| 3 | [FaceRecognition-SDK-Linux](https://github.com/MiniAiLive/FaceRecognition-SDK-Linux) | 1:1 & 1:N Face Matching SDK |
| 4 | [FaceRecognition-LivenessDetection-SDK-Android](https://github.com/MiniAiLive/FaceRecognition-LivenessDetection-SDK-Android) | 1:1 & 1:N Face Matching, 2D & 3D Face Passive Liveness Detection SDK |
| 5 | [FaceRecognition-LivenessDetection-SDK-iOS](https://github.com/MiniAiLive/FaceRecognition-LivenessDetection-SDK-iOS) | 1:1 & 1:N Face Matching, 2D & 3D Face Passive Liveness Detection SDK |
| 6 | [FaceRecognition-LivenessDetection-SDK-CPP](https://github.com/MiniAiLive/FaceRecognition-LivenessDetection-SDK-CPP) | 1:1 & 1:N Face Matching, 2D & 3D Face Passive Liveness Detection SDK |
| 7 | [FaceMatching-SDK-Android](https://github.com/MiniAiLive/FaceMatching-SDK-Android) | 1:1 Face Matching SDK |
| 8 | [FaceAttributes-SDK-Android](https://github.com/MiniAiLive/FaceAttributes-SDK-Android) | Face Attributes, Age & Gender Estimation SDK |

### Face Liveness Detection SDK
| No | Project | Features |
|----|---------|-----------|
| 1 | [FaceLivenessDetection-SDK-Docker](https://github.com/MiniAiLive/FaceLivenessDetection-SDK-Docker) | 2D & 3D Face Passive Liveness Detection SDK |
| 2 | [FaceLivenessDetection-SDK-Windows](https://github.com/MiniAiLive/FaceLivenessDetection-SDK-Windows) | 2D & 3D Face Passive Liveness Detection SDK |
| 3 | [FaceLivenessDetection-SDK-Linux](https://github.com/MiniAiLive/FaceLivenessDetection-SDK-Linux) | 2D & 3D Face Passive Liveness Detection SDK |
| 4 | [FaceLivenessDetection-SDK-Android](https://github.com/MiniAiLive/FaceLivenessDetection-SDK-Android) | 2D & 3D Face Passive Liveness Detection SDK |
| 5 | [FaceLivenessDetection-SDK-iOS](https://github.com/MiniAiLive/FaceLivenessDetection-SDK-iOS) | 2D & 3D Face Passive Liveness Detection SDK |

### ID Document Recognition SDK
| No | Project | Features |
|----|---------|-----------|
| 1 | [ID-DocumentRecognition-SDK-Docker](https://github.com/MiniAiLive/ID-DocumentRecognition-SDK-Docker) | ID Document, Passport, Driver License, Credit Card, MRZ Recognition SDK |
| 2 | [ID-DocumentRecognition-SDK-Windows](https://github.com/MiniAiLive/ID-DocumentRecognition-SDK-Windows) | ID Document, Passport, Driver License, Credit Card, MRZ Recognition SDK |
| 3 | [ID-DocumentRecognition-SDK-Linux](https://github.com/MiniAiLive/ID-DocumentRecognition-SDK-Linux) | ID Document, Passport, Driver License, Credit Card, MRZ Recognition SDK |
| 4 | [ID-DocumentRecognition-SDK-Android](https://github.com/MiniAiLive/ID-DocumentRecognition-SDK-Android) | ID Document, Passport, Driver License, Credit Card, MRZ Recognition SDK |

### ID Document Liveness Detection SDK
| No | Project | Features |
|----|---------|-----------|
| 1 | [ID-DocumentLivenessDetection-SDK-Docker](https://github.com/MiniAiLive/ID-DocumentLivenessDetection-SDK-Docker) | ID Document Liveness Detection SDK |
| 2 | [ID-DocumentLivenessDetection-SDK-Windows](https://github.com/MiniAiLive/ID-DocumentLivenessDetection-SDK-Windows) | ID Document Liveness Detection SDK |
| 3 | [ID-DocumentLivenessDetection-SDK-Linux](https://github.com/MiniAiLive/ID-DocumentLivenessDetection-SDK-Linux) | ID Document Liveness Detection SDK |

### Web & Desktop Demo
| No | Project | Features |
|----|---------|-----------|
| 1 | [FaceRecognition-IDRecognition-Playground-Next.JS](https://github.com/MiniAiLive/FaceRecognition-IDRecognition-Playground-Next.JS) | FaceSDK & IDSDK Playground |
| 2 | [FaceCapture-LivenessDetection-Next.JS](https://github.com/MiniAiLive/FaceCapture-LivenessDetection-Next.JS) | Face Capture, Face LivenessDetection, Face Attributes |
| 3 | [FaceMatching-Windows-App](https://github.com/MiniAiLive/FaceMatching-Windows-App) | 1:1 Face Matching Windows Demo Application |

## About MiniAiLive
[MiniAiLive](https://www.miniai.live/) is a leading AI solutions company specializing in computer vision and machine learning technologies. We provide cutting-edge solutions for various industries, leveraging the power of AI to drive innovation and efficiency.

## Contact US
For any inquiries or questions, please contact us on [WhatsApp](https://wa.me/+19162702374).
