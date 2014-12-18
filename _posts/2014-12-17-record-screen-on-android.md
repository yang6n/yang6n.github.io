---
title: "Record screen on Android via adb shell"
layout: post
tags: android, adb, shell
category: tech
comments: yes
---

Devices running Android 4.4 (API level 19) and higher, have ability to recording screen by adb shell.

####Commands:

* Launch into the command line with your Android 4.4 device connected to your computer and enter the command to record your screen:

```shell
adb shell screenrecord /sdcard/demo.mp4
```

* You can further customize the speed at which it captures video, the length of time it records (the default duration is 3-minutes) and the size of the video in terms of resolution.

Another example of a command to record a video would be:

```shell
adb shell screenrecord --bit-rate 8000000 --time-limit 30 /sdcard/kitkat.mp4
```

The above command would record at 8Mbps, instead of the default 4Mbps, for a duration of 30-seconds and save it to the SD Card on your device with the name of KitKat. 

####References:
[How to record your screen on Android 4.4 KitKat](http://www.cnet.com/how-to/how-to-record-your-screen-on-android-4-4-kitkat/)

[Recording a device screen](http://developer.android.com/tools/help/adb.html#screenrecord)