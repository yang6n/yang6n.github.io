---
title: "Java: Convert GPS latitude/longitude to World Coordinates"
layout: post
tags: android, location, latlng
category: tech, dev
comments: yes
---

Google maps use wgs84 coordinate system, but sometimes you want to convert to world coordinate system. And you may also want to convert it back.


####Convert latitude to a Y value in World Coordinates.
```java
public static final double lat2y(double aLat) {
    return ((1 - Math.log(Math.tan(aLat * Math.PI / 180) + 1 / Math.cos(aLat * Math.PI / 180)) / Math.PI) / 2 * Math.pow(2, 0)) * 256;
}
```

####Convert longitude to a X value in World Coordinates.
```java
public static final double lon2x(double lon) {
    return (lon + 180f) / 360f * 256f;
}
```

####Convert Y value in World Coordinates to latitude
```java
public static final double y2lat(double y) {
    double z = Math.pow(Math.E, (2 * Math.PI * (1 - y / 128)));
    return Math.asin((z - 1) / (z + 1)) * 180 / Math.PI;
}
```

####Convert X value in World Coordinates to longitude
```java
public static final double x2lng(double x) {
    return x * 360 / 256 - 180;
}
```


#####References:
[Geographic coordinate conversion](http://en.wikipedia.org/wiki/Geographic_coordinate_conversion)

[Google IO 2013 App Mystery Values](http://stackoverflow.com/questions/21167584/google-io-2013-app-mystery-values/21174339#21174339)

[Google Map Hack](http://wiki.jackslab.org/Google_Map_Hack)

[Coordinate conversions made easy](http://www.ibm.com/developerworks/library/j-coordconvert/)

[UTM Coordinates](http://www.resurgentsoftware.com/GeoMag/utm_coordinates.htm)

