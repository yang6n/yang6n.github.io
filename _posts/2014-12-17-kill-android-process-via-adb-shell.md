---
title: "Kill Android process via adb shell"
layout: post
tags: android, adb, shell
category: tech
comments: yes
---

Android ADB shell stop application like “force-stop” for non rooted device.

#####1. Find package id, use `Google Keep` as example
```shell
adb shell pm list package -f | grep keep
package:/data/app/com.google.android.keep-1/base.apk=com.google.android.keep
```

#####2. Enter ADB shell
```shell
adb shell
```

#####3. Enter application debuging mode
```shell
run-as "com.google.android.keep"
```

#####4. Find the process ID
```shell
ps | grep "com.google.android.keep"
73254 ttys009    0:00.00 grep com.google.android.keep
```

#####5. Kill process
```shell
kill -9 73254
```

#####6. Done :D


####References:

[Android Debug Bridge](http://developer.android.com/tools/help/adb.html)

[Stopping an Android app from console](http://stackoverflow.com/questions/3117095/stopping-an-android-app-from-console)

[Android mulitple way to stop application](http://stackoverflow.com/questions/17829606/android-adb-stop-application-command-like-force-stop-for-non-rooted-device)