---
layout: post
title: Innovative Project Proposal
author: [chen]
category: [Lecture]
tags: [jekyll, ai]
---

This homework is to propose an innovative project and describe the key features, list all Design Considerations and the required technologies, then draw the System Block Diagram.

---
## Homework Report Format
**Contents:**<br>
* **應用與功能說明**
  - Specify the future home application, and Describe the key features
  - Describe the key features which may be applied to the home space (kitchen, living room, play room, study room, bed room)
* **設計考量與所需相關技術**
  - List all design considerations and the required technologies
* **系統方塊圖**
  - Draw a System Block Diagram

---
## 藍芽智能家居機器人
![](https://github.com/hjgyjg123/MCU-project/blob/main/images/2023-1.png?raw=true)

### 應用功能說明
1. 處理家庭事務:打掃房間、收拾碗盤、倒垃圾、煮飯等等
2. 操作工具:鍋具、掃具
3. 人機互動:依照使用者的命令，執行相應的指令
4. 遠端操控:透過手機或電腦進行遠距離操控
5. 購物功能:透過網路連接到購物網站進行購物
6. 人工智能:可自行判斷要事順序，並自主執行，且能自主學習，明白使用者的習慣
7. 娛樂功能:可播放音樂、影片

### 設計考量與相關技術
**系統設計考量：**<br>
1. 操作方式:垂直升降式手臂 
2. 移動方式:兩輪 
3. 供電方式:鋰電池、無線or有線充電
4. 聯網方式:WiFi或BT to 手機
5. 交互方式:語言輸入+介面操控

**所需相關技術：**
1. 滑軌式機器手臂 ＆ 軟式夾具
2. 物體辨識分類：Jetson-Nano + IMX219
3. AI技術
4. 語音識別技術
5. 自主運動與導航技術

### 系統方塊圖
![](https://github.com/hjgyjg123/MCU-project/blob/main/images/ESP32%E5%89%B5%E6%96%B0%E4%BD%9C%E6%A5%AD%E8%A8%AD%E8%A8%88.png?raw=true)

---
### 參考範例
<iframe width="1239" height="697" src="https://www.youtube.com/embed/VGj3daiFNdM" title="CEATEC JAPAN 2018: 全自動お片付けロボットシステム（Autonomous Tidying-up Robot System）" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

---
## Market Analysis (市場分析)
![](https://blog.hubspot.com/hs-fs/hubfs/tam-sam-som.png?width=1200&name=tam-sam-som.png)

### TAM of Future Home Products
The Target Market size (TAM) of Future Home Products is the number of household.<br>

### Taiwan Households = 8.93M (台灣 9百萬戶）
* [Total number of households in Taiwan from 2010 to 2020(in 1,000s)](https://www.statista.com/statistics/330804/taiwan-national-total-number-of-households/#:~:text=By%20the%20end%20of%202020,households%20in%20the%20previous%20year.)

### Japan Households = 57.2M (日本 5千7百萬戶)
* [Number of Households in Japan](https://www.helgilibrary.com/indicators/number-of-households/japan/) 

### American Households = 129.93M (美國 1.3億戶)
* [Number of households in the U.S. from 1960 to 2021(in millions)](https://www.statista.com/statistics/183635/number-of-households-in-the-us/)<br>
* [The average American household consisted of 2.51 people in 2021.](https://www.statista.com/statistics/183648/average-size-of-households-in-the-us/)<br>

<br>
<br>

*This site was last updated {{ site.time | date: "%B %d, %Y" }}.*


