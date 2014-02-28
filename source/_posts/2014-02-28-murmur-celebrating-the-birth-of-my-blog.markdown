---
layout: post
title: "[Murmur] Celebrating the birth of my blog"
date: 2014-02-28 01:31:28 +0800
comments: true
categories: [Murmur]

keywords: "Octopress, Blog, brew doctor, ruby, bundle install, foxslide"
description: "Octopress website"
---

由於之前已經玩過 Octopress，本來想說重新翻翻 document，就可以無痛使用，但沒想到毛病還是很多 orz。<!-- more -->

先是 bundle install 的時候，發現 ruby 一定要在 1.9.3 以上，由於之前是用 1.9.2，而且滿久沒碰了，所以就[安裝一下](http://goo.gl/SD915S)，接著又碰到一堆莫名其妙的問題 囧，像是 brew doctor 跟我說 “Error: /usr/bin occurs before /usr/local/bin”，照著它的建議也沒辦法解決，後來只好直接編輯 /etc/paths，把 /usr/local/bin 擺到 /usr/bin 前面，接著再 brew doctor，看看還有無問題，並照它的建議排除。最後，總算安全上壘惹，[設定好對應的 github page](http://goo.gl/BNDdd)，rake generate，rake deploy，並 commit、push。

由於完成後的版面實在太單調，我就換了 [foxslide](http://goo.gl/9gTiAH) 這個 theme，再把版面調整我想要的樣子 (背景圖、font 的顏色、大小等)，可是卻發現它的原始設定中 found on 的地方不能放上 facebook，後來只好編輯 source/_includes/custom/asides/found_on.html，並加上 facebook.user 判斷及需要的圖片，[詳細做法](http://goo.gl/SVdZh7)。

設定完 twitter user 後，發現那區塊也是爛的！居然一直給我出現 "loading tweets…"，原來是早在去年 twitter API v1 就[退休](http://goo.gl/VxbMYi)了，也正式推出 v1.1，而 Unauthenticated requests 這種方式在 v1.1 中是不能用的，官方建議我們改用 [Embedded Timelines](http://goo.gl/znBFr) 的方式。

P.S. 好家在問題都得以解決，終於可以蓋牌結束這回合。XDD