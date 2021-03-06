---
title: "IO 優化 (Fast IO)"
date: 2022-04-27T22:06:49+08:00
draft: false
tags:
- CP
---

在程式競賽中，偶爾會看到輸入輸出量較大的題目建議參賽者使用 `scanf()` 和 `printf()` 以避免TLE，或者使用 `cin` 和 `cout` 時加入：
```c++=1
ios_base::sync_with_stdio(false);
cin.tie(0);
```
在操作上 `cin` 和 `cout` 比 `scanf()` 和 `printf()` 更方便直觀，且保證型別安全。效率上`cin` 和 `cout` 卻似乎輸了不少，這是為什麼呢？

---
## 兩個輸入輸出系統 (stdio & iostream)

C\++中有兩種IO系統，`stdio` 源自於C語言，而 `iostream` 來自C\++，為了避免在混用時發生問題，C++會自動同步兩者，然而這樣的操作便會降低效率。
所以如果確定不會有混用的需求，可以透過指令解除同步：
(用了之後要記得 `stdio` 和 `iostream` 不能混用)
```C++=1
ios_base::sync_with_stdio(false);
```

---
## 緩衝區 (buffer)

在資訊被輸出前，會先到「緩衝區」等待輸出，而分次輸出很耗資源，因此釋放緩衝區的次數是影響效率的一大變因。
在 `iostream` 中，可以用 `cout<<flush;` 來釋放緩衝區， `cin` 則因為使用上的考量(讓使用者在輸入時能看見先前操作的輸出結果)，具有自動釋放緩衝區的功能。
 `cin` 的效率之所以比 `scanf()` 差便是因為 `scanf()` 並不會自動釋放緩衝區，我們可以透過指令來解除 `cin` 的自動釋放：
```C++=2
cin.tie(0);
```
另外，使用 `endl` 換行也會釋放緩衝區，即 `endl` 等於 `flush` + `'\n'`。所以如果不是互動題，建議換行使用 `'\n'` 就可以了。

---