---
layout: post
title: ESP32 IoT webserver & client
author: [chen]
category: [Lecture]
tags: [jekyll, ai]
---
---
### ESP32_Webserver_IoT、ESP32_Webclient_IoT


### 應用功能說明
1. WIFI遠端控制 
2. 透過DHT11 sensor感測周圍溫度、濕度
3. server 和 client 聯機控制

### 設計考量與相關技術
**系統設計考量：**<br>
1. 操作方式:WIFI遙控手機App or 筆電
2. 元件:ESP32、DHT11 sensor 
3. 聯網方式:WI-FI

**所需相關技術：**
1. Arduino程式設計


### 系統方塊圖
![](https://github.com/hjgyjg123/MCU-project/blob/main/images/Webserver%E7%B3%BB%E7%B5%B1%E6%96%B9%E5%A1%8A%E5%9C%96.jpg?raw=true)


### webserver程式碼
![](https://github.com/hjgyjg123/MCU-project/blob/main/images/webserver%2001.jpg?raw=true)
![](https://github.com/hjgyjg123/MCU-project/blob/main/images/webserver_IOT%202.jpg?raw=true)
![](https://github.com/hjgyjg123/MCU-project/blob/main/images/webserver_IOT%203.jpg?raw=true)
![](https://github.com/hjgyjg123/MCU-project/blob/main/images/webserver_IOT%204.jpg?raw=true)
![](https://github.com/hjgyjg123/MCU-project/blob/main/images/webserver_IOT%205.jpg?raw=true)
![](https://github.com/hjgyjg123/MCU-project/blob/main/images/webserver_IOT%206.jpg?raw=true)

**webserver程式碼功能**
1. 在程式的開頭，include必要的函式庫並設置了WiFi連接的SSID和密碼，創建了一個WebServer物件，並將其綁定到80端口
2. 定義一些HTML代碼的字符串，用於生成網頁。定義了一些變數來存儲感測器的數據，如溫度、濕度和PM2.5顆粒物數據等
3. 在handleRoot()函數中，用於處理根路徑的請求，它會返回一個HTML頁面，其中包含感測器數據的表格
4. dht22()、htu21()和pm25()函數分別用於處理/dht22、/htu21和/pm25路徑的請求。這些函數解析URL中的參數，並將數據存儲到對應的變數中。然後，它們返回更新後的HTML頁面，顯示最新的感測器數據
5. 在setup()函數中，我們初始化串口並連接到WiFi網絡。然後，設置伺服器的路由處理函數。最後，我們啟動伺服器
6. 在loop()函數中，我們通過調用server.handleClient()來處理網頁用戶端的請求。這使得伺服器能夠不斷接收並處理請求

### webclient程式碼
![](https://github.com/hjgyjg123/MCU-project/blob/main/images/webclient%2001.jpg?raw=true)
![](https://github.com/hjgyjg123/MCU-project/blob/main/images/webclient%2002.jpg?raw=true)

**webclient程式碼功能**
1. include必要的函式庫：WiFi、WiFiClient、HTTPClient、Wire和Adafruit_HTU21DF
2. 設定連接的WiFi網絡名稱（SSID）和密碼，並連接到WiFi
3. 初始化HTU21DF傳感器：檢查是否成功初始化HTU21DF溫濕度傳感器，如果無法找到傳感器，則進入無窮迴圈
3. loop函式：程式延遲5秒，然後讀取HTU21DF傳感器的溫度和濕度數據，並構建URL，使用Webserver的IP地址，構建發送數據的URL，將溫度和濕度數據附加到URL的查詢參數中
4. 檢查WiFi連接狀態：檢查是否成功連接到WiFi，如果WiFi連接成功，則使用HTTPClient類的物件來發送POST請求，請求的目標URL是之前構建的URL，請求的內容為"Message from ESP32"
5. 獲取請求的回應：獲取HTTP回應的狀態碼和回應內容，並將其輸出到序列埠，再來關閉HTTP連接，在每次迴圈結束後，程式會延遲1分鐘，然後再次進入下一輪迴圈，不斷接收數據

### 結果
![](https://github.com/hjgyjg123/MCU-project/blob/main/images/webserver%202.jpg?raw=true)
![](https://github.com/hjgyjg123/MCU-project/blob/main/images/webserver%203.jpg?raw=true)
![](https://github.com/hjgyjg123/MCU-project/blob/main/images/webserver%204.jpg?raw=true)
![](https://github.com/hjgyjg123/MCU-project/blob/main/images/webserver%201.jpg?raw=true)

---
<br>
<br>

*This site was last updated {{ site.time | date: "%B %d, %Y" }}.*


