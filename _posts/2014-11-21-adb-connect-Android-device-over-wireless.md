---
title: "adb connect Android device over wireless"
description: "Android Debug Bridge (adb) is a versatile command line tool that lets you communicate with an emulator instance or connected Android-powered device. Even better, you can do it without cable."
layout: post
tags: android, adb, logcat
category: tech, dev
comments: yes
---

Android Debug Bridge(`adb`) is a versatile command line tool that lets you communicate with an emulator instance or connected Android-powered device. Even better, you can do it without cable, and it does NOT need root access.

###Setup TCP port

Connect to device via USB cable, enable "USB Debuging".
Enter the adb shell:

```bash
adb shell 
```

#####TCP Mode

Setup tcp port for adb:

```bash
setprop service.adb.tcp.port 5555
stop adbd
start adbd
```

#####USB Mode

```bash
setprop service.adb.tcp.port -1
stop adbd
start adbd
```

###Connect to device

Connect to device via tcp:

#####TCP Mode

```bash
adb tcpip 5555
adb connect 192.168.2.3:5555
```

#####USB mode

```bash
adb usb
```

###Apps to automate the process

There are also several apps on Google Play that automate this process. A quick search suggests [adbWireless](https://play.google.com/store/apps/details?id=siir.es.adbWireless&hl=en), [WiFi ADB](https://play.google.com/store/apps/details?id=com.ttxapps.wifiadb&hl=en) and [ADB WiFi](https://play.google.com/store/apps/details?id=com.ryosoftware.adbw&hl=en). All of these require root access, but adbWireless requires fewer permissions.


####References:
[Android Debug Bridge](http://developer.android.com/tools/help/adb.html)

[Using Hardware Devices](http://developer.android.com/tools/device.html)

[How can I connect to Android with ADB over TCP?](http://stackoverflow.com/questions/2604727/how-can-i-connect-to-android-with-adb-over-tcp)