---
title: "Hello World - C++的基本架構"
date: 2022-04-27T22:07:46+08:00
draft: false
tags:
- C++
---
## 程式基本架構

```c++=1
#include <iostream>
using namespace std;

int main(){
	//code here
	return 0;
}
```
1. C++中的語句結尾須加上 `;`。
1. C++中大小寫不可混用(case sensitive)
1. 以 `#` 開頭為程式的預處理，也就是程式編譯前先執行的指令。
1. 第一行為引入標頭檔，可以想像成給電腦一本字典，以便認識你所使用的庫存函式。
1. `iostream` 是IO(輸入輸出)與stream(流)，也就是與輸入輸出有關的函式庫。
1. 未來用到更多庫存函式時就會需要引入其他標頭檔，多起來也是不好記，此時可選擇使用 `include <bits/stdc++.h>` 萬用標頭檔。
1. 第二行為使用標準命名空間，不同命名空間可能出現同名不同意義的單辭，像不同班級可能出現同名的同學一樣。若不加此行，在用到此命名空間的成員時須加上 `std::`，如 `std::cout`。
1.  `main()` 為主函式，主函式程式放在 `{}` 中，依上到下循序執行。
1. 以 `//` 開頭為單行註解，是寫給人的，電腦會跳過不執行。
1. 另有多行註解，以`/*`與`*/`包裹。
1.  `return 0` 使程式結束。

---
## 輸出 - 第一支程式 Hello World !

```c++=1
#include <iostream>
using namespace std;

int main(){
	cout<<"Hello World !"<<endl;
	return 0;
}
```
1. `endl` 代表輸出換行。
1. 以 `"` 包起來的是字串。(有關資料型態下章會介紹)
1. 除了字串，`cout` 還可輸出數字、運算式等。

### Output

```c++=1
Hello World !
```

## 換你試試看

* 試試看 `cout<< "1 + 1 = " << 1 + 1 <<endl;` 的結果

---