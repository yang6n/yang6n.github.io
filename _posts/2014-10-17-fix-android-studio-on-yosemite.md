---
title: "Fix Android Studio on Yosemite"
description: "My Android Studio and Intellij crash after I upgraded to Yosemite, I thought I have to use Eclipse for the reset of my day. But thanks Jonas Osc, I got it fixed, now it's up and running. "
layout: post
tags: android, mac
category: tech
comments: yes
---

My Android Studio and Intellij crash after I upgraded to Yosemite, I thought I have to use Eclipse for the reset of my day. But thanks Jonas Osc, I got it fixed, now it's up and running. 

To fix it:
1. Right click on the app from the Dock
2. Choose "Options" -> "Show in Finder"
3. Right click on the app in Finder
4. Choose "Show Package Contents"
5. Open file: Contents/Info.plist
6. Search for "<key>JVMVersion</key>"
7. Change the value in the <string> to "1.7*"
8. Save it, and enjoy!

#####References:
https://intellij-support.jetbrains.com/entries/27854363-IDE-doesn-t-start-after-updating-to-Mac-OS-Yosemite-or-Mavericks
