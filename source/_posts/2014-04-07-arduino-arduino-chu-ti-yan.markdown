---
layout: post
title: "[Arduino] Arduino 初體驗"
date: 2014-04-07 11:44:47 +0800
comments: true
categories: "Arduino Processing Arduino-Uno Arduino-Mega-2560 Potentiometer"
keywords: "Arduino, Processing, Arduino Uno, Arduino Mega 2560, Potentiometer"
description: "Beginning to Arduino"
---

這是一篇剛接觸 Arduino 的心得(ㄘㄞˇㄌㄟˊ)記錄，有錯的地方歡迎指正 :P <!-- more -->

安裝介紹相關的文章谷歌已經很多了～就不再寫了

* 買原廠正版的吧: 原本想要買 Arduino mega 2560 板，但因為原廠的要一千八百多，筆者想說是實驗用途以及自己剛接觸，先用非原廠的吧，所以在X瓏訂了一塊 (NTD 650)，但要 upload 時，才發現程式無法上傳，不知道是要自己灌 bootloader 還是壞了？理論上應該要灌好啊啊啊。之後也去X華電子試了 Uno (非原廠)，但結果也是一樣 Q_Q (賽狼)。噴出的錯誤訊息是: `avrdude: stk500v2_ReceiveMessage(): timeout`、、、、、`avrdude: stk500v2_getsync(): timeout communicating with programmer`，嘗試了一些做法
	* (X) 有人說程式碼裡面不要包含"!!!"，否則 bootloader 會認為是 escape，不過不是這個問題
	* (X) 也有人說在按下 upload 的同時也按下板子上的 reset button，等到 TX/RX LED 燈亮起時瞬間放掉 reset，然後要抓放掉的 timing，這..
	* (X) 更改 boards.txt 設定檔，把 `mega2560.upload.protocol = wiring` 改為 `mega2560.upload.protocol = stk500v2` via. [Modify boards.txt](http://goo.gl/1Vhpgz)
	* (X) 利用別塊板子當作 AVR ISP Programmer 來重燒 bootloader，不過我一直沒試成功就是.. Reference: [Using an Arduino as an ISP-1](http://goo.gl/JQbOo) or [Using an Arduino as an ISP-2](http://goo.gl/CeLPmg) or [多種板子接法](http://goo.gl/HGtZu)
	* (O) 買一塊新的，最後還是選擇這個..
* 沒有 Multi-Thread: 由於板子不是那麼高階(咦?)，所以官方表示不支援多執行緒，也就是說多個 methods 沒辦法同時做到，一定得在 loop 裡面一個接著一個跑，這是件還滿囧的事情，不過也有一些 libraries 模擬多執行緒的實作方式，來達到類似效果，但不太適用我的情況，且效果不太好 via. [Protothreads](http://goo.gl/X2uFL5)
* `tone()` method 同一時間只能播一個: `tone()` 這個方法可以產生特定頻率及特定長短時間的音波，筆者在多個 pin 上外接許多蜂鳴器當作 output，而每個 buzzer 都是單獨觸發的個體，但卡到前一點的原因以及此點因素而作罷
* 與 Processing 完美搭配: 通常你會想拿那些從 serial 傳過來的 Arduino 資料在電腦上做些事情，比如說寫檔案、播音樂等，在還沒發現 Processing 之前，筆者本來想用 serial programming 硬幹，不過還好有這強大的 programming language / software，幫我做到了這些事情。它的優點有很多，open source、跨平台、讓不會寫程式的人可以較容易的使用、也可以繪圖 (2D/3D)，以及有多種 libraries 可以使用，總之，功能相當強大，有興趣的話可以看下這篇 [入門程式設計的好工具 Processing](http://goo.gl/6D3ls)、[Let's begin!](http://goo.gl/zvWuk)
* (待續...)

----------------------------

* 底下整理近期購買移動式可變電阻時，詢問的店家資訊(還活著的)，要買其它電子材料的人也可以參考:
	* 供應商，皆需大量訂購，最小訂購量大部分為375隻
		* [Mouser 貿澤電子](http://goo.gl/cKco9s)，電話: 02-2799-2096，地址: [台北市內湖區瑞光路582號7樓](http://goo.gl/zVonNU)
		* [廣為科技](http://goo.gl/AxI7Gs)，電話: 02-2698-8676，地址: [新北市汐止區新台五路一段
77號6樓之8 遠東世界中心B棟](http://goo.gl/xeekG9) => 私心推下這間，裡面有個工程師還滿 nice，跟我說滿多的
		* [全科科技](http://goo.gl/wjH7Ra)，電話: 02-2627-5859，地址: [台北市內湖區瑞光路360號9樓](http://goo.gl/8JUMBh)
		* [盛泰科技](http://goo.gl/42UNfr)，電話: 02-8797-1297，地址: [台北巿內湖區洲子街112號6樓](http://goo.gl/1dTGZH)
		* [穩得實業](http://goo.gl/NkUsNA)，電話: 02-2917-5770，地址: [新北市新店區寶橋路188號6樓](http://goo.gl/zFhzCD)
	* 材料行
		* [良興電子-光華門市](http://goo.gl/xJMCug)，電話: 02-2393-0899，地址: [台北市中正區新生南路一段6號B1(國際電子廣場)](http://goo.gl/s5mU8C)
		* [今華電子-新生門市](http://goo.gl/Z8TVz2)，電話: 02-2392-1111，地址: [台北市中正區新生南路一段12巷2號](http://goo.gl/bHZqYq)
		* [德昌富鴻](http://goo.gl/FZzm1H)，電話: 02-2370-8989，地址: [台北市萬華區中華路一段14號16號](http://goo.gl/8nKqRU)
		* [金電子-台北門市](http://goo.gl/6aaPHT)，電話: 02-2558-1912，地址: [台北市市民大道一段100號台北地下街90號](http://goo.gl/Ahj1Bu)
		* 恆茂電子，電話: 02-2361-0766，地址: [台北市萬華區西寧南路7號1樓](http://goo.gl/d6AP2c)
		* 利聲，電話: 02-2314-5439，地址: [台北市萬華區西寧南路4號1樓](http://goo.gl/HSnMia)
		* 電洋電子，電話: 02-2381-5199，地址: [台北市萬華區忠孝西路二段24號1樓](http://goo.gl/tQBbNG)
		* 川禾電氣五金行，電話: 02-2388-3850，地址: [台北市萬華區中華路1段8-10號](http://goo.gl/bEXPzc)