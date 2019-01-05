---
layout: post
title: "AVFoundation, Still and Video Media Capture"
date: 2018-12-30 11:30:00 +0800
tag: [Swift]
---

## AVFoundation

> The `AVFoundation` framework combines four major technology areas that together encompass a wide range of tasks for capturing, processing, synthesizing, controlling, importing and exporting audiovisual media on Apple platforms.

![](https://developer.apple.com/library/archive/documentation/AudioVideo/Conceptual/MediaPlaybackGuide/Contents/Resources/en.lproj/Art/media_playback_framework_2x.png)

- `Core Audio`
- `Core Video`
- `Core Media`
- `Core Animation`

---

## [Media Capture](https://developer.apple.com/library/archive/documentation/AudioVideo/Conceptual/AVFoundationPG/Articles/04_MediaCapture.html#//apple_ref/doc/uid/TP40010188-CH5-SW2)

---

- An instance of `AVCaptureDevice` to represent the input device, such as a camera or microphone
- An instance of a concrete subclass of `AVCaptureInput` to configure the ports from the input device
- An instance of a concrete subclass of `AVCaptureOutput` to manage the output to a movie file or still image
- An instance of `AVCaptureSession` to coordinate the data flow from the input to the output

![](https://developer.apple.com/library/archive/documentation/AudioVideo/Conceptual/AVFoundationPG/Art/captureOverview_2x.png)

---

##Putting It All Together: Capturing Video Frames as UIImage Objects
This brief code example to illustrates how you can capture video and convert the frames you get to UIImage objects. It shows you how to:

- Create an `AVCaptureSession` object to coordinate the flow of data from an AV input device to an output
- Find the `AVCaptureDevice` object for the input type you want
- Create an `AVCaptureDeviceInput` object for the device
- Create an `AVCaptureVideoDataOutput` object to produce video frames
- Implement a delegate for the `AVCaptureVideoDataOutput` object to process video frames
- Implement a function to convert the `CMSampleBuffer` received by the delegate into a `UIImage` object

---

# AVCaptureOutput

- subclasses

- AVCaptureFileOutput
- AVCaptureMetadataOutput
- AVCapturePhotoOutput
- AVCaptureDepthDataOutput
- AVCaptureMovieFileOutput
- AVCaptureVideoDataOutput
- AVCaptureStillImageOutput
- AVCaptureAudioDataOutput