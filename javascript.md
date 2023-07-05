# javascript語言介紹(.js)

## Chr1-介紹

## Chr2-語彙結構

## Chr3-註解方式
// 單行註解
/*
多行註解
*/

## Chr4-型別

## Chr4-變數
### 4.1-命名規定
須以 \$ 或 \_ 或 英文字母a-z(大小寫皆可)開始，之後可以使用數字在中間，但不得使用 #關鍵字(keyword) 和 #保留字(reserved word)


## Chr5-運算式及運算元

## Chr6-述句

## Chr7-迴圈
在本章收錄了js的 #forloop #while #do-while #forEach 迴圈
#### 7.1 #forloop

##### 語法架構
```
for(let i=0;i<count;i=i+1){
    // function...
}
```

#### 7.2 #while

##### 語法架構
```
let i=0
while(i<count){
    // function...
    i=i+1
}
```

#### 7.3 #do-while

##### 語法架構
```
let i=0
do{
    //function...
    i=i+1
}while(i<count)
```

#### 7.4 #forEach

##### 語法架構
```
array[].forEach(function(event){
    // function...
}
```

### 7.5 while 及 do-while 之差異


## 陣列

## 物件

## 函式

## 例外處理

網頁動畫及互動效果

## 註解及參見
- A
    - [ajax](ajax.md)
- B
- C
    - [canvas](canvas.md)
- D
- E
    - [EventListener](eventlistener.md)
- F
- G
- H
    - [html及css串接]()
- I
- J
    - [js API]()
- K
- L
- M
    - [metaprogramming]()
- N
    - [nodejs]()
- O
- P
- Q
- R
- S
    - [svg]()
- T
- U
- V
- W
    - [web非同步]()
    - [web storage](website/webstorage.md)
- X
- Y
- Z
- anthor
    - [內建函式一覽]()
    - [類別]()
    - [模組]()
    - [程式庫]()
    - [迭代器及產生器]()
    - [事件]()
    - [擴充功能]()

#關鍵字(keyword) 和 #保留字(reserved word) 一覽
- await
- break
- case
- catch
- class
- const
- continue
- debugger
- default
- delete
- do
- else
- enum
- export
- extends
- false
- finally
- for
- function
- if
- implements
- import
- in
- instanceof
- interface
- let
- new
- null
- package
- private
- protected
- public
- return
- super
- switch
- static
- this
- throw
- try
- true
- typeof
- var
- void
- while
- with
- yield

簡寫一覽:
*\[time\]*: 時間
*\[number\]*: all number
*\[number-nn\]*: all number no negative
*\[string\]*: string
*\[array\]* \| array\[\]: array
*\[object\]* \| object\{\}: object
*\[function\]*: function
*\[var\]*: 變數
*\[boolean\]*: boolean
*\[regexp\]*: using regular expression
*\[link\]*: link
*\[url\]*: url
*\[name\]*: name
*\[context\]*: context
*\[deg\]*: degree
*\[name\]*: name
*inf.*: infinite
*arb.*: arbitrarily(隨意值)
(\*)?**bold**: 預設值
*itiaic*: 可選值
?: 不必要(可選)

*\[width\]*: width(文字形)(要加單位)
*\[height\]*: height(文字形)(要加單位)
*\[event\]*: 事件
*\[element\]*: 元素
*\[canva\]*: canva doc
*\[ctx2d\]*: *\[canva\]*.getContext("2d")
*\[ctx3d\]*: *\[canva\]*.getContext("3d")
*\[ctx\]*: *\[canva\]*.getContext(*arb.*)
<!-- *\[number\]*: all number no negative
*\[number\]*: all number no negative
*\[number\]*: all number no negative
*\[number\]*: all number no negative
*\[number\]*: all number no negative -->
*inf.*: infinite
<!-- *inf.*: infinite -->

小賀chris:) 2023/06/22 v1.0.1