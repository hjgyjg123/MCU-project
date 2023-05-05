---
layout: post
title: ESP32 WiFi
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
There are a bunch of alternatives for OTA programming with the ESP32 boards. For example, in the Arduino IDE, under the Examples folder, there is the BasicOTA example (that never worked well for us); the OTA Web Updater (works well, but it isn’t easy to integrate with web servers using the ESPAsyncWebServer library);

### [ESP32 OTA (Over-the-Air) Updates](https://randomnerdtutorials.com/esp32-ota-over-the-air-arduino/#:~:text=ESP32%20OTA%20(Over%2Dthe%2DAir)%20Programming,access%20to%20the%20ESP32%20board.)
![](https://i0.wp.com/randomnerdtutorials.com/wp-content/uploads/2021/01/Async-Elegant-OTA-Web-Server-ESP32-How-it-Works.png?w=751&quality=100&strip=all&ssl=1)
OTA (Over-the-Air) update is the process of loading new firmware to the ESP32 board using a Wi-Fi connection rather than a serial communication.

---
### [AsyncElegantOTA library](https://github.com/ayushsharma82/AsyncElegantOTA)
1. Install **AyncElegantOTA**, **AsyncTCP**, and **ESPAsyncWebServer** libraries;
2. Include AsyncElegantOTA library at the top of the Arduino sketch: **#include <AsyncElegantOTA.h>;**
3. Add this line **AsyncElegantOTA.begin(&server);** before server.begin();
4. Open your browser and go to http://<IPAddress>/update, where <IPAddress> is your ESP32 IP address.

---
### Install [AsyncElegantOTA Library](https://github.com/ayushsharma82/AsyncElegantOTA)
![](https://i0.wp.com/randomnerdtutorials.com/wp-content/uploads/2021/01/Install-Async-ElegantOTA-Library-Arduino-IDE.png?w=786&quality=100&strip=all&ssl=1)

### Install AsyncTCP and ESPAsyncWebServer Libraries
You also need to install the AsyncTCP and the ESPAsyncWebServer libraries. Click the links below to download the libraries.
* [ESPAsyncWebServer](https://github.com/me-no-dev/ESPAsyncWebServer)
* [AsyncTCP](https://github.com/me-no-dev/AsyncTCP)

---
### AsyncElegantOTA ESP32 Basic Example
Upload this exmaple to ESP32 to start with
```
#include <Arduino.h>
#include <WiFi.h>
#include <AsyncTCP.h>
#include <ESPAsyncWebServer.h>
#include <AsyncElegantOTA.h>

const char* ssid = "YOUR_SSID";
const char* password = "YOUR_PASSWORD";

AsyncWebServer server(80);

void setup(void) {
  Serial.begin(115200);
  WiFi.mode(WIFI_STA);
  WiFi.begin(ssid, password);
  Serial.println("");

  // Wait for connection
  while (WiFi.status() != WL_CONNECTED) {
    delay(500);
    Serial.print(".");
  }
  Serial.println("");
  Serial.print("Connected to ");
  Serial.println(ssid);
  Serial.print("IP address: ");
  Serial.println(WiFi.localIP());

  server.on("/", HTTP_GET, [](AsyncWebServerRequest *request) {
    request->send(200, "text/plain", "Hi! I am ESP32.");
  });

  AsyncElegantOTA.begin(&server);    // Start ElegantOTA
  server.begin();
  Serial.println("HTTP server started");
}

void loop(void) {
}  
```
![](https://i0.wp.com/randomnerdtutorials.com/wp-content/uploads/2021/01/Elegant-OTA-Demo-Example-Root-URL.png?w=603&quality=100&strip=all&ssl=1)
![](https://i0.wp.com/randomnerdtutorials.com/wp-content/uploads/2021/01/Async-ElegantOTA-Update-Page.png?w=789&quality=100&strip=all&ssl=1)

---
### Sketch > Export Compiled Binary 
1. Copy the [code](https://raw.githubusercontent.com/RuiSantosdotme/Random-Nerd-Tutorials/master/Projects/ESP32/AsyncElegantOTA/ESP32_Web_Server_LED_OTA/ESP32_Web_Server_LED_OTA.ino) and modify:
  - `#include <AsyncElegantOTA.h>`<br>
  -  `AsyncElegantOTA.begin(&server);`<br>
  - revised: [ESP32_Async_OTA_Web_Server_LED.ino](https://github.com/rkuo2000/arduino/blob/master/examples/ESP32/ESP32_Async_OTA_Web_Server_LED/ESP32_Async_OTA_Web_Server_LED.ino)
2. Save your sketch: File > Save and give it a name. For example: [eb_Server_LED_OTA_ESP32.ino(https://raw.githubusercontent.com/RuiSantosdotme/Random-Nerd-Tutorials/master/Projects/ESP32/AsyncElegantOTA/ESP32_Web_Server_LED_OTA/ESP32_Web_Server_LED_OTA.ino)
3. Generate a .bin file from your sketch. Go to Sketch > Export Compiled Binary. A new .bin file should be created under the project folder.
![](https://i0.wp.com/randomnerdtutorials.com/wp-content/uploads/2021/01/bin-file-generated-for-OTA-updates.png?resize=237%2C167&quality=100&strip=all&ssl=1)
4. Now,youneed to upload that file using the ElegantOTA page. Go to your ESP IP address followed by /update. Make sure you have the firmware option selected. Click on Choose File and select the .bin file you’ve just generated.
![](https://i0.wp.com/randomnerdtutorials.com/wp-content/uploads/2021/01/Uploading-new-firmware-elegantOTA.png?w=988&quality=100&strip=all&ssl=1)  
5. When it’s finished, click on the Back button.
![](https://i0.wp.com/randomnerdtutorials.com/wp-content/uploads/2021/01/upload-new-firmware-elegantOTA-success.png?w=789&quality=100&strip=all&ssl=1)  
6. Then, you can go to the root (/) URL to access the new web server.
![](https://i0.wp.com/randomnerdtutorials.com/wp-content/uploads/2021/01/WebSocket-Server-ESP32-Control-Outputs.png?w=789&quality=100&strip=all&ssl=1)

---
### ESP32-PCA9685 Async OTA WebServer
[RobotCat](https://github.com/rkuo2000/arduino/tree/master/examples/Robots/RobotCat)<br>
![](https://github.com/rkuo2000/Robotics/raw/gh-pages/images/RobotCat.jpg?raw=true)
  
[ESP32_PCA9685_Async_OTA_WebServer.ino](https://github.com/rkuo2000/arduino/blob/master/examples/Robots/RobotCat/ESP32_PCA9685_Async_OTA_WebServer/ESP32_PCA9685_Async_OTA_WebServer.ino)<br>
![](https://github.com/rkuo2000/Robotics/raw/gh-pages/images/ESP32_PCA9685_Async_OTA_WebServer.png?raw=true)
  
<br>
<br>

*This site was last updated {{ site.time | date: "%B %d, %Y" }}.*


