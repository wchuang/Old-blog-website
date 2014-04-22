---
layout: post
title: "[Coding] Online Judge"
date: 2014-04-16 01:16:10 +0800
comments: true
categories: [Coding]
keywords: "code, coding, online judge"
description: "Intro of online judge"
---

* 使用較舊版的 ANSI C compilers (C90?)，不能用單行註解 (//)，需用 (/* ... */)，[Ref.1](http://goo.gl/JQ5E2i)、[Ref.2](http://goo.gl/tlIkva)

* Compile 時會加入這些參數: `-lm -lcrypt -O2 -pipe -ansi -DONLINE_JUDGE`，前兩個會幫你 link 到要用到的 libraries (math.h and crypt.h)，最後一個幫你定義一個 macro (ONLINE_JUDGE)，所以如果有不想被執行到的地方，可以用 `#ifndef ONLINE_JUDGE {...} #endif` 包住

* 如果題目沒有說明會有幾筆輸入可以用迴圈包住並偵測輸入資料直到資料的最後一筆

	while (EOF != scanf("%ld %ld", &input_1, &input_2)) {
		// Your code.
	}
	
* would update in few days..

----------------

BTW. 兩個查詢 C/C++ 函式庫的地方:

* [cppreference.com](http://goo.gl/h9lGN)
* [cplusplus.com](http://goo.gl/OoQx)