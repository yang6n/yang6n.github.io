---
title: "Missing 'from' field from GCM notification extra"
description: "Handle the notification only from your push sender."
layout: post
tags: android, gcm, notification
category: tech
comments: yes
---

GoogleCloudMessaging allow the application receiving messages from up to 100 senders. 

You can register them in two ways:

```java
Intent intent = new Intent(GCMConstants.INTENT_TO_GCM_REGISTRATION);
intent.setPackage(GSF_PACKAGE);
intent.putExtra(GCMConstants.EXTRA_APPLICATION_PENDING_INTENT,
        PendingIntent.getBroadcast(context, 0, new Intent(), 0));
String senderIds = "968350041068,652183961211";
intent.putExtra(GCMConstants.EXTRA_SENDER, senderIds);
ontext.startService(intent);
```

Or use the utility class GoogleCloudMessaging.register(String...). I prefer this simple one :D


```java
String registrationId = GoogleCloudMessaging.register("968350041068", "652183961211");
```

Then your application can receive messages from multiple senders now. 

But if you're writing a SDK, you only want to handle the notification send from your sender. There is a "from" field in the extra bundle send from GCM. The paylay will like this:

```
data.collapseKey=<!-- collapseKey -->, 
from=<!-- SENDER ID -->, 
data.alert=<!-- messsage -->, 
data.pushType=1, 
android.support.content.wakelockid=1, 
data.pid=1, 
collapse_key=<!-- collapseKey -->
```

In your code, you can use it to determine which sender sends this notification. 

It's works pretty good in my projects. 

But the wired issue happend today, the "from" become empty string for only one of my SDK. I tried two other different push SDK, both of them still have the sender id in "from" field.

After hours research, it turns out we haven't login to [Developer Console](http://console.developers.google.com) for a loooooong time. There is a "Term Update" is waiting for me. 

I just agreed whatever its changed, then the sender id is back. 

So, if you saw the same issue("from" become empty string), please login to [Developer Console](http://console.developers.google.com), see is there anything waiting for you :-)

####References:
[Receiving Messages from Multiple Senders](http://developer.android.com/google/gcm/adv.html#multi-senders)