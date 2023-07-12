# javascript語言基本(.js)

## 架構
- #介紹
- #語彙結構
- #註解方式
- #型別
- #變數
  - #命名規定
- #運算式及運算元
  - #運算式
  - #運算元
- #述句
- #迴圈
  - #forloop
  - #while
  - #do-while
  - #forEach
  - #while及do-while之差異
- #物件
- #函式
- #例外處理
  - #例外介紹
  - #處理例外
- #註解及參見
  - #關鍵字 #保留字 一覽

## Chr1 #介紹
js 可以用來做很多事例如:
1. 存取網頁內容(access content)
2. 調整網頁內容(modify content)
3. 計畫運作規則(porgram rules)
4. 回應網頁事件(react to events)
主要就是為了增加網頁的互動性而出現的

## Chr2 #語彙結構

## Chr3 #註解方式
```js
// 這是一個單行註解

/*
這是一個多行註解
*/

/*
*甚至有人喜歡
*這
*樣
*打
*!
*/

```

## Chr4 #型別
js中的型別共計有7種分別為**boolean**,**null**,**undefined**,**number**,**bigint**,**string**,**symbol**,**object**
### boolean
布林值: 只有兩個型態**true**或**false**

### null
空值: 通常是指一個**不存在**的或無效的物件或地址(反正就是沒有東西)

### undefined
未定義: 是自動分配給剛剛聲明的變量或**沒有實際參數**的形式參數的原始值。

### number
數字: 就數字XD 分別有integer,float,double,bignum
例如:
123456
4564151.12312
4546513123.4566
13132.123123132132
皆為數字

### bigint
大整數: 是一種數字數據類型，可以表示任意精度格式的**整數**

### string
字串: 就文本(大小引號模糊)
例如:
"132156456"
"abcdefg"
"小賀大帥哥"
"123.123"
皆為字串

### symbol
象徵(ECMAScript 6 new): 是一個內置對象，其構造函數返回一個symbol 原語(也稱為符號值或只是符號)，保證是唯一的。符號通常用於向對象添加唯一的屬性鍵，這些屬性鍵不會與任何其他代碼可能添加到該對象的鍵發生衝突，並且對於其他代碼通常用於訪問該對象的任何機制都是隱藏的。這實現了一種弱封裝形式，或者一種弱形式的信息隱藏。

### object
物件: 是一個包含資料與處理資料指令的資料結構(array也是物件)

## Chr5 #變數
程式碼如果需要**暫時**儲存資料就會放在**變數**中
### 5-1 #命名規定
1. js的最一開始的變數會需要用let或const或var開始
2. 不能被重複宣告
3. 常數(const)不能被更改
4. 須以 \$ 或 \_ 或 英文字母a-z(大小寫皆可)開始，之後可以使用數字在中間，但不得使用 #關鍵字(keyword) 和 #保留字(reserved word)

例如以下都是合法的變數
```js
let abc=123
let $345678
var _adv
// 上面是一般的變數
const aaa // 這是一個常數(不能被更改)
```

建議要先使用let const var
```js
abc=456 // 正常輸出
```

變數不能被**重複宣告**
```js
let abc=123
let abc=456 // X: Uncaught SyntaxError: Identifier 'abc' has already been declared
```

如果要交換就直接換即可
```js
let abc=123
abc=456
```

常數不能被更改
```js
const abc=123
abc=456 // X: Uncaught TypeError: Assignment to constant variable. at <anonymous>:1:4
```

變數須以 \$ 或 \_ 或 英文字母a-z(大小寫皆可)開始
```js
let 1aa // X: Uncaught SyntaxError: Invalid or unexpected token
```

## Chr6 #運算式及運算元
### #運算式
運算式是一個

### #運算元
運算式是一個

## Chr7 #述句

## Chr8 #迴圈
在本章收錄了js的 #forloop #while #do-while #forEach 迴圈
#### 8-1 #forloop

##### 語法架構
```
for(let i=0;i<count;i=i+1){
    // function...
}
```

#### 8-2 #while

##### 語法架構
```
let i=0
while(i<count){
    // function...
    i=i+1
}
```

#### 8-3 #do-while

##### 語法架構
```
let i=0
do{
    //function...
    i=i+1
}while(i<count)
```

#### 8-4 #forEach

##### 語法架構
```js
array[].forEach(function(event){
    // function...
})
```

### 8-5 #while及do-while之差異


## Chr9 #物件

## Chr10 #函式

## Chr11 #例外處理
在js種共有7+1種不同的例外情形分別為**Error**,**RangeError**,**ReferenceError**,**SyntaxError**,**TypeError**,**URIError**,~~**EvalError**~~ + NaN

### #例外介紹
1. Error(一般錯誤)
Error 這個類型用來代表一般的錯誤情況，最常用在**客製化例外**情況。透過下面的指令可以產生一個錯誤物件的實例：
```js
var error = new Error("error message");
console.log(error)          // X: Error: error message
```
這個 Error 物件包含兩個屬性－name 和 message：
name: 用來說明錯誤的類型(這裡就是 Error)
message: 提供更多關於此例外情況的描述。

2. RangeError(範圍錯誤)
這是一個當**數值落在特定的區間外**時會拋出的錯誤
例如，透過 toFixed() 方法時，它可以接受介於 0 ~ 20 的參數來說明要顯示到小數後第幾位，當這個參數超過這個區間時，就會拋出 RangeError：
```js
var pi = 3.14159;
pi.toFixed(100000);  // X: RangeError: toFixed() digits argument must be between 0 and 100
```

3. ReferenceError(找不到變數：拼錯字)
這是一個當試圖**存取一個不存在的變數**時會拋出的錯誤，這個錯誤經常發生在拼錯字的情況。
```js
console.log(bar);    // X: ReferenceError: bar is not defined
```

4. SyntaxError(語法錯誤)
這是一個當有程式碼**違反js的語法規則**時會拋出的錯誤。熟悉C或java的通常是在編譯的過程中(compulation process)遇到語法錯誤但js是直譯式語言(interpreted language)，因此當程式碼被執行到時，才會辨認到語法錯誤。
這種錯誤類型是所有例外狀況中唯一不能被修復的。
```js
if (false) {    // X: SyntaxError: Unexpected token (3:0)
  // 缺少結束的大括號
```

5. TypeError(找不到函式)
這是一個如果某一**變項的型別和所期待的操作不同**時會拋出的錯誤，這經常發生在去呼叫執行一個不存在的函式時。
```js
// 由於 foo 當中並不包含 bar 這個函式，因此會拋出 TypeError 錯誤
var foo = {};
foo.bar();     // X: TypeError: foo.bar is not a function
```

6. URIError(uri 錯誤)
這是一個當使用encodeURI()或decodeURI()的方法，但卻有**給了不合法的URI**時會拋出的錯誤
```js
// "%" 表示的是 URI 中的跳脫片段，但在下面的例子中 "%" 後沒有接任和字串，因此是不合法的跳脫片段
decodeURIComponent("%");   // X: URIError: URI malformed
```

7. ~~EvalError(eval 錯誤)~~
這是一個**當eval()使用不恰當**時會拋出的錯誤。這個錯誤不再被當前的 ECMAScript 規範所採用。

8. 數學例外:NaN
此例外並非正式例外是數學在運算時出現錯誤會拋出的值

### #處理例外

## #註解及參見
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

[簡寫一覽](abbreviationslist.md)

小賀chris:) 2023/06/22 v1.1.1