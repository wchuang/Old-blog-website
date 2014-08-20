---
layout: post
title: "Process versus Thread"
date: 2014-08-20 17:44:28 +0800
comments: true
categories: "process thread context-switch scheduling 排程"
keywords: "process, thread, context-switch, scheduling, 排程"
description: "Process versus Thread"
---
Process: 會在 CPU 的虛擬記憶體中分配 address，而每個 process 的 memory space 是彼此獨立且分開的 (系統資源不共享)。系統真正同時在運行的 process 數量最多不超過 CPU 數量，所以系統核心會在使用者無法察覺的時間內快速切換不同的 process，以達成同時處理多個 process 的假象。這裡又會牽扯到 [context switch](http://goo.gl/X6Aypg)、[scheduling](http://goo.gl/C5wbHx) 的問題。

Thread: 同個 process 可能由多個不同的 thread 所組成，這些 thread 共享 process 的資料以及資源，但有可能執行不同區塊的程式碼。在處理資源分配的時候，常會有 [synchronization](http://goo.gl/8yFi) 或 [deadlock](http://goo.gl/41N9k) 等問題。

總之，可以看成 process 是一個執行中的 programs，而 thread 就像是與程式同時運行的 functions。
