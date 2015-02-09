---
title: "Get current running app id and activity"
description: "Get current running application's appId, and get the current visible activity name"
layout: post
tags: android, activity
category: tech
comments: yes
---

Sometimes you may want to check what's the app id for current running application, and also you want to know what's the current visible activity name. 

Here you go:

```bash
adb shell dumpsys window windows | grep -E 'mCurrentFocus|mFocusedApp'
```

####References:
[Android Debug Bridge](http://developer.android.com/tools/help/adb.html)