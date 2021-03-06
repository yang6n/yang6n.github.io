---
title: "Android - get screen size programmatically"
description: "Simple android example, first tech post in github."
layout: post
tags: android, ui
category: tech
comments: yes
---

If you want the display dimensions in pixels you can use getSize:

```java
Display display = getWindowManager().getDefaultDisplay();
Point size = new Point();
display.getSize(size);
int width = size.x;
int height = size.y;
```

If you're not in an Activity you can get the default Display via WINDOW_SERVICE:

```java
WindowManager wm = (WindowManager) context.getSystemService(Context.WINDOW_SERVICE);
Display display = wm.getDefaultDisplay();
```

Before getSize was introduced (in API level 13), you could use the getWidth and getHeight methods that are now deprecated:

```java
Display display = getWindowManager().getDefaultDisplay(); 
int width = display.getWidth();  // deprecated
int height = display.getHeight();  // deprecated
```

For the use case you're describing however, a margin/padding in the layout seems more appropriate.
