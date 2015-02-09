---
title: "Export SQLite database from your android devices"
description: "Export SQLite database from your android devices"
layout: post
tags: android, sqlite, database
category: tech
comments: yes
---

On Android, if you want to access the SQLite database on device, you can use adb to cat it. 

```bash
adb shell
run-as com.example.sample
cat databases/SampleDB
```

It works pretty well, if you just want to check some text or row numbers. But it doesn't give you the full view of the database.


To download the full database, you have to do something extra:

* Add permissions for read/write external storage

```xml
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
<uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE" />
```

* Add the code to export the SQLite database from private data to SD card

```java
    protected void exportDb() {
        File externalStorageDirectory = Environment.getExternalStorageDirectory();
        File dataDirectory = Environment.getDataDirectory();

        FileChannel source = null;
        FileChannel destination = null;

        String currentDBPath = "/data/" + getApplicationContext().getApplicationInfo().packageName + "/databases/SampleDB";
        String backupDBPath = "SampleDB.sqlite";
        File currentDB = new File(dataDirectory, currentDBPath);
        File backupDB = new File(externalStorageDirectory, backupDBPath);

        try {
            source = new FileInputStream(currentDB).getChannel();
            destination = new FileOutputStream(backupDB).getChannel();
            destination.transferFrom(source, 0, source.size());

            Toast.makeText(this, "DB Exported!", Toast.LENGTH_LONG).show();
        } catch (IOException e) {
            e.printStackTrace();
        } finally {
            try {
                if (source != null) source.close();
            } catch (IOException e) {
                e.printStackTrace();
            }
            try {
                if (destination != null) destination.close();
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
    }
```

* Call it somewhere
* Download the file from SD card. Personally I prefer [WiFi File Transfer](https://play.google.com/store/apps/details?id=com.smarterdroid.wififiletransfer), after it start, just open the http://YOUR_ID_ADDRESS:1234 to download the files. :D


####References:
[Export SQLite data from your Android device](http://www.techrepublic.com/blog/software-engineer/export-sqlite-data-from-your-android-device/)