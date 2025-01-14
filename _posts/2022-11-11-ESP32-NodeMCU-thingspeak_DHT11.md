---
layout: post
title: IoT Thinkspeak
author: [chen]
category: [Lecture]
tags: [jekyll, ai]
---
---
## IoT Thinkspeak.com
### 應用功能說明
1. 透過sensor DHT11讀取溫度、溼度等數據
2. 利用API連接到thingspeak.com網站
3. 將數據以折線圖的方式呈現網頁中

### 設計考量與相關技術
**系統設計考量：**<br>
1. 操作方式:將ESP32與sensor DHT11聯接，並載入程式碼，便可讀取溫度、濕度
2. 元件:ESP32、sensor DHT11
3. 聯網方式:WI-FI
4. 通信方法:API連接

**所需相關技術：** 
1. Arduino程式設計

---

### 系統方塊圖
![](https://github.com/hjgyjg123/MCU-project/blob/main/images/ESP32_thingspeak_DHT11%E7%B3%BB%E7%B5%B1%E6%96%B9%E5%A1%8A%E5%9C%96.jpg?raw=true)

### ESP32_thingspeak_DHT11程式碼
![](https://github.com/hjgyjg123/MCU-project/blob/main/images/ESP32_thingspeak_DHT11%E7%A8%8B%E5%BC%8F%E7%A2%BC1.jpg?raw=true)
![](https://github.com/hjgyjg123/MCU-project/blob/main/images/ESP32_thingspeak_DHT11%E7%A8%8B%E5%BC%8F%E7%A2%BC2.jpg?raw=true)
![](https://github.com/hjgyjg123/MCU-project/blob/main/images/ESP32_thingspeak_DHT11%E7%A8%8B%E5%BC%8F%E7%A2%BC3.jpg?raw=true)

**ESP32_thingspeak_DHT11程式碼功能**

透過sensor DHT11讀取溫濕度，並將其數值透過程式碼呈現在thingspeak.com網頁
1. 定義所使用的DHT11溫濕度感測器的引腳和類型，include必要的函式庫
2. 設置Wi-Fi連接所需的SSID和密碼，並建立了與Thingspeak服務器的連接，透過API
3. 在setup() 函式中，確認是否連接到網路
4. 在loop() 函式中，通過WiFiClient創建TCP連接到Thingspeak網站
5. 構建要發送的URL，包括Thingspeak的API和溫度、濕度數據
6. 使用client.print()方法將HTTP GET請求發送到Thingspeak服務器
7. 每10秒一次，讀取數據

### 結果展示
![](https://github.com/hjgyjg123/MCU-project/blob/main/images/ESP32_thingspeak_DHT11%E7%B5%90%E6%9E%9C1.jpg?raw=true)
<iframe width="885" height="498" src="https://www.youtube.com/embed/UaEYn788kfQ" title="ESP32 thingspeak DHT11結果2" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>---

<br>
<br>

*This site was last updated {{ site.time | date: "%B %d, %Y" }}.*


