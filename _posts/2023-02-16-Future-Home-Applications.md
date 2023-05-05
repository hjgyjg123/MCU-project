---
layout: post
title: ESP32 IoT webserver & client
author: [chen]
category: [Lecture]
tags: [jekyll, ai]
---

### Sketch>ESP32_Webserver_IoT
* [ESP32_Webserver_IoT.ino](https://github.com/rkuo2000/arduino/blob/master/examples/ESP32/ESP32_Webserver_IoT/ESP32_Webserver_IoT.ino)
![](https://github.com/rkuo2000/MCU-course/blob/main/images/Sketch_ESP32_Webserver_IoT.png?raw=true)
![](https://github.com/rkuo2000/MCU-course/blob/main/images/Sketch_ESP32_Webserver_IoT_monitor.png?raw=true)
![](https://github.com/rkuo2000/MCU-course/blob/main/images/Sketch_ESP32_Webserver_IoT_browser.png?raw=true)

### Sketch>ESP32_Webclient_IoT_HTU21DF
* [ESP32_Webclient_IoT_HTU21DF.ino](https://github.com/rkuo2000/arduino/blob/master/examples/ESP32/ESP32_Webclient_IoT_HTU21DF/ESP32_Webclient_IoT_HTU21DF.ino)
![](https://github.com/rkuo2000/MCU-course/blob/main/images/Sketch_ESP32_Webclient_IoT_HTU21DF.png?raw=true)

---
## OTA (Over the Air)

### AsyncElegantOTA ESP32 Basic Example

![](https://i0.wp.com/randomnerdtutorials.com/wp-content/uploads/2021/01/Elegant-OTA-Demo-Example-Root-URL.png?w=603&quality=100&strip=all&ssl=1)
![](https://i0.wp.com/randomnerdtutorials.com/wp-content/uploads/2021/01/Async-ElegantOTA-Update-Page.png?w=789&quality=100&strip=all&ssl=1)

---
### Sketch > Export Compiled Binary 

4. Now,youneed to upload that file using the ElegantOTA page. Go to your ESP IP address followed by /update. Make sure you have the firmware option selected. Click on Choose File and select the .bin file you’ve just generated.
![](https://i0.wp.com/randomnerdtutorials.com/wp-content/uploads/2021/01/Uploading-new-firmware-elegantOTA.png?w=988&quality=100&strip=all&ssl=1)  
5. When it’s finished, click on the Back button.
![](https://i0.wp.com/randomnerdtutorials.com/wp-content/uploads/2021/01/upload-new-firmware-elegantOTA-success.png?w=789&quality=100&strip=all&ssl=1)  
6. Then, you can go to the root (/) URL to access the new web server.
![](https://i0.wp.com/randomnerdtutorials.com/wp-content/uploads/2021/01/WebSocket-Server-ESP32-Control-Outputs.png?w=789&quality=100&strip=all&ssl=1)

---
<br>
<br>

*This site was last updated {{ site.time | date: "%B %d, %Y" }}.*


