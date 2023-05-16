---
layout: post
title: ESP32 OTA (Over the Air)
author: [chen]
category: [Lecture]
tags: [jekyll, ai]
---
---
## ESP32 OTA (Over the Air)
### 應用功能說明
1. WiFi遠端控制 
2. WIFI聯網到OTA，透過手機or筆電將檔案載到ESP32

### 設計考量與相關技術
**系統設計考量：**<br>
1. 操作方式:WiFI遙控手機or筆電
2. 元件:ESP32
3. 聯網方式:WI-FI

**所需相關技術：** 
1. Arduino程式設計


### 系統方塊圖
![](https://github.com/hjgyjg123/MCU-project/blob/main/images/OTA%E7%B3%BB%E7%B5%B1%E6%96%B9%E5%A1%8A%E5%9C%96.jpg?raw=true)


###  AsyncElegantOTA程式碼
![](https://github.com/hjgyjg123/MCU-project/blob/main/images/ESP32%20OTA%20(Over%20the%20Air)%201.jpg?raw=true)
![](https://github.com/hjgyjg123/MCU-project/blob/main/images/ESP32%20OTA%20(Over%20the%20Air)%202.jpg?raw=true)
**AsyncElegantOTA程式碼功能**
1. include必要的函式庫與Wi-Fi名稱和密碼的設定
2. 初始化連接：程式碼中的 setup 函式負責初始化，並連接到 Wi-Fi 網路
3. 啟動 Web 伺服器：程式碼創建了一個 AsyncWebServer 物件，並將其綁定到 80 號端口。然後，它設置了一個基本的路由處理器，當收到根路徑的 HTTP GET 請求時，回覆一個簡單的文本回應
4. 啟動 OTA 功能：程式碼使用 AsyncElegantOTA 函式庫啟動了 OTA 功能。這個函式庫允許通過簡單的 Web 界面進行程式碼的上傳與燒錄
5. 進入主循環loop()：不執行任何操作。這是因為所有的伺服器和 OTA 功能都是在非同步的背景任務中執行，並不需要主循環的處理

### eb_Server_LED_OTA_ESP32程式碼
![](https://github.com/hjgyjg123/MCU-project/blob/main/images/eb_Server_LED_OTA_ESP32%201.jpg?raw=true)
![](https://github.com/hjgyjg123/MCU-project/blob/main/images/eb_Server_LED_OTA_ESP32%202.jpg?raw=true)
![](https://github.com/hjgyjg123/MCU-project/blob/main/images/eb_Server_LED_OTA_ESP32%203.jpg?raw=true)
**eb_Server_LED_OTA_ESP32程式碼功能**
1. include所需的函式庫，包括 Arduino.h、WiFi.h、AsyncTCP.h、ESPAsyncWebServer.h 和 AsyncElegantOTA.h。這些函式庫提供了連接無線網路、建立網頁伺服器和執行 OTA (Over-The-Air) 更新的功能
2. 變數宣告 : 定義了要連接到的 Wi-Fi 網路的 SSID 和密碼
3. 定義變數和腳位：程式碼中定義了一個 ledState 變數用於記錄 LED 的狀態，以及一個 ledPin 變數用於指定控制 LED 的腳位
4. 建立伺服器物件：在程式碼中建立了一個 AsyncWebServer 物件 server，並指定它監聽的連接埠為 80
5. 建立 WebSocket 物件：程式碼中建立了一個 AsyncWebSocket 物件 ws，並指定它的路徑為 "/ws"
6. 建立網頁內容：在程式碼中使用 const char 陣列 index_html 定義了 HTML 網頁的內容，這個網頁包含了一個按鈕和一個顯示 LED 狀態的文字
7. WebSocket 事件處理：程式碼中定義了處理 WebSocket 事件的函式，包括連接、斷開連接、接收訊息等事件
8. 初始化 WebSocket：在程式碼中呼叫 initWebSocket() 函式，設定 WebSocket 的事件處理
9. 頁面處理函式：程式碼中定義了一個處理網頁的函式 processor()，用於將網頁中的變數替換為對應的值
10. 設定伺服器路由：在程式碼中使用 server.on() 函式設定了根路徑 "/" 的處理函式，並指定網頁的內容為 index_html
11. 開始 OTA 和伺服器：程式碼中使用 AsyncElegantOTA.begin(&server) 開始 OTA 更新功能，並使用 server.begin() 啟動伺服器
12. 主迴圈：程式碼中的 loop() 函式主要處理 WebSocket 客戶端的清理和 LED 狀態的控制

### 結果展示
![](https://github.com/hjgyjg123/MCU-project/blob/main/images/eb_Server_LED_OTA_ESP32%20a1.png?raw=true)
![](https://github.com/hjgyjg123/MCU-project/blob/main/images/eb_Server_LED_OTA_ESP32%20a2.png?raw=true)
![](https://github.com/hjgyjg123/MCU-project/blob/main/images/eb_Server_LED_OTA_ESP32%20a3.png?raw=true)
![](https://github.com/hjgyjg123/MCU-project/blob/main/images/eb_Server_LED_OTA_ESP32%20a4.png?raw=true)
![](https://github.com/hjgyjg123/MCU-project/blob/main/images/eb_Server_LED_OTA_ESP32%20a5.jpg?raw=true)

### 實作影片
<iframe width="329" height="586" src="https://www.youtube.com/embed/1YZVsSbFLMQ" title="" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
---
<br>
<br>

*This site was last updated {{ site.time | date: "%B %d, %Y" }}.*


