# javascript語言基本(.js)

## 架構
- #介紹
- #語彙結構
- #註解方式
- #型別
- #變數
  - #命名規定
- #運算式及運算子
  - #運算式
    - #主流運算式
      - #this
  - #運算子
    - #運算子規則
    - #賦值運算子
    - #比較運算子
    - #算術運算子
    - #位元運算子
      - #位元邏輯運算子
      - #位元移動運算子
    - #邏輯運算子
      - #短路解析
    - #字串運算子
    - #條件運算子
    - #逗點運算子
    - #一元運算子
      - #delete
      - #typeof
      - #void
    - #關係運算子
      - #in
    - #分組運算子
    - #new
    - #展開運算子
    - #運算子優先級
- #判斷式
  - #ifelse
  - #switchcase
  - #ifelseTOswitchcase
- #迴圈
  - #forloop
  - #while
  - #do-while
  - #forEach
  - #while及do-while之差異
- #物件
  - #陣列
- #函式
  - #函式介紹
  - #定義函式
  - #呼叫函式
  - #功能範圍
  - #函式vs方法
  - #匿名函式
  - #函式參數
  - #函式作用域及衝突
  - #函式裡的函式
  - #arguments物件
  - #可預定義的函式
    - #eval
    - #isFinite
    - #isNaN
    - #parseInt
    - #parseFloat
    - #Number
    - #String
    - #encodeURI
    - #decodeURI
    - #encodeURIComponent
    - #decodeURIComponent
- #例外處理
  - #例外介紹
  - #處理例外
    - #throw
    - #try-catch
- #DOM操作
- #註解及參見
  - #關鍵保留字

## Chr1 #介紹
js 可以用來做很多事例如:
1. 存取網頁內容(access content)
2. 調整網頁內容(modify content)
3. 計畫運作規則(porgram rules)
4. 回應網頁事件(react to events)
主要就是為了增加網頁的互動性而出現的程式語言

[詳細介紹參見](https://developer.mozilla.org/zh-TW/docs/Learn/JavaScript/First_steps/What_is_JavaScript)

## Chr2 #語彙結構
1. 大小寫敏感
    - 但true false null undefined 不敏感
2. 結尾分號模糊

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
4. 須以 \$ 或 \_ 或 英文字母a-z(大小寫皆可)開始，之後可以使用數字在中間，但不得使用 #關鍵保留字

例如以下都是合法的變數
```js
let abc=123
let $345678
let _adv
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

## Chr6 #運算式及運算子
### #運算式
運算式是一個任何一段可以取得一個值的程式碼。

任何合乎語法的運算式都能取得一個值，概念上， 有兩種不同型態的運算式: 有副作用的(例如: 將一個值指定給一個變數) 以及只為了取得值而解析的運算式。
運算式 x=7 是上述的第一種類型。這個使用=運算子的運算式會將數值7賦與給x。運算式本身也會被解析為 7。
運算式 3+4 是上述的第二種類型。這個運算式使用+運算子把3和4加起來，而不指定給任何變數。

js中運算式有下列幾種種類:
算術運算式: 解析出數字， 例如 3.14159。（通常使用算術運算子。）
字串運算式: 解析出字串， 例如 "Fred" or "234"。（通常使用字串運算子。）
邏輯運算式: 解析出 True 或 False（通常與邏輯運算子相關。）
主流運算式: js中基本的關鍵字及運算式。
左側運算式: 左側是指定值的對象。

#### #主流運算式
js中基本的關鍵字及運算式。

##### #this
#this 關鍵字能取得當前所在物件。一般而言，this能取得呼叫處所在的物件。
可以使用**.**或**\[\]**來取用該物件中的特性:
this['特性名稱']
this.特性名稱

以下定義一個叫做a的函式，比較物件中特性value與傳入的兩變數:
```js
function a(obj,lowval,hival){
    if (obj.value < lowval||obj.value > hival) console.log("不可用的值!")
}
```
你可以在表單的onChange event handler中呼叫函式，並以this傳入表單的元素，範例如下:
```html
<p>請輸入一介於18 與 99 的數字:</p>
<input type="text" name="age" size="3" onChange="validate(this,18,99);">
```

#### #解析(實驗)
解析是js中的一個實驗性功能，在未來版本的 ECMAScript 計畫被導入。有兩種不同類型的解析:

實驗性質 [for (x of y) x]
陣列解析。

實驗性質 (for (x of y) y)
產生器解析。

解析在許多程式語言中都存在，允許你快速地基於現存陣列產生新的陣列，例如:
```js
[for (i of [ 1,2,3 ]) i*i ];
// =>[ 1,4,9 ]

let abc=[ 'A','B','C' ];
[for (letters of abc) letters.toLowerCase()];
// =>[ 'a','b','c' ]
```

#### #左側運算式
左側是指定值的對象。

### #運算子
運算子是一個
js有以下幾種運算子分別為:**賦值運算子**,**比較運算子**,**算術運算子**,**位元運算子**,**邏輯運算子**,**字串運算子**,**條件（三元）運算子**,**逗點運算子**,**一元運算子**,**關係運算子**

#### #運算子規則
一個二元運算子需要具備兩個運算元， 一個在運算元之前，一個在運算元之後:
運算元1 運算子 運算元2
例如,3+4 或 x*y.

#### #賦值運算子
一個 #賦值運算子 將 基於其右方的運算元 的值賦予其 左方的運算元。 最簡單的 賦值運算子 是 等於 (=)， 它將賦予 左方運算元 與 右方運算元相同之值。 也就是， x=y 會把 y 的值賦予給 x。

也有一些復合的 #賦值運算子 是為了縮短下面表中的運算:

| 名稱 | 簡化的運算子 | 意義 |
| ----- | ---- | ----- |
| 賦值 | x=y | x=y |
| 加法賦值 | x+=y | x=x+y |
| 減法賦值 | x-=y | x=x-y |
| 乘法賦值 | x*=y | x=x*y |
| 除法賦值 | x/=y | x=x/y |
| 餘數賦值 | x%=y | x=x%y |
| 指數賦值 | x**=y | x=x**y |
| 左移賦值 | x<<=y | x=x<<y |
| 右移賦值 | x>>=y | x=x>>y |
| 無號右移賦值 | x>>>=y | x=x>>>y |
| 位元 AND 賦值 | x&=y | x=x&y |
| 位元 XOR 賦值 | x^=y | x=x^y |
| 位元 OR 賦值  | x\|=y | x=x\|y |

解構
為了進行更複雜的賦值，解構賦值是js用來從陣列或物件中提取資料的語法。
```js
let foo=["one","two","three"];

// 不使用解構
let one=foo[0]
let two=foo[1]
let three=foo[2]

// 使用解構
let [one,two,three]=foo
```

#### #比較運算子
#比較運算子 會比較 運算元 並基於比較的結果回傳邏輯值。運算元可以是數字，字串，邏輯，或物件的值。 字串的比較是基於字典序的， 使用 Unicode 的值。 在多數情況下，假如兩個運算元不具有相同型態，js會嘗試將它們轉換成相同型態。這個行為通常是將運算元以數學形式對待。 在某些的轉換型態的例外中會使用到 === 及 !== 運算子， 它們會嚴格地進行相等或不相等的比較。 這些運算子不會在確認相等與否前嘗試轉換運算元的型態。 下面的表解釋了比較運算子:
```js
let var1=3
let var2=4
```
| 運算子 | 描述 | 會回傳True的例子 |
| ----- | ----- | ----- |
| 等於(==) | 假如運算元等價就回傳True | 3==var1,"3"==var1,3=='3' |
| 不等於(!=)| 假如運算元不等價就回傳True | var1!=4,var2!="3" |
| 嚴格等於(===)| 假如運算元具有相同型態且等價則回傳 True參考 Object.is(en-US) 及 JS 中的等價性 | 3===var1 |
| 嚴格不等於(!==) | 假如運算元具有相同型態但不等價，或是具有不同型態，回傳True | var1!=="3",3!=='3' |
| 大於(>) | 假如左方運算元大於右方運算元，回傳True | var2>var1,"12">2 |
| 大於或等於(>=)  | 假如左方運算元大於或等於右方運算元，回傳 True | var2>=var1,var1>=3 |
| 小於(<) | 假如左方運算元小於右方運算元，回傳True | var1<var2,"2"<12 |
| 小於或等於(<=) | 假如左方運算元小於或等於右方運算元，回傳 True| var1\<=var2,var2<=5|

#### #算術運算子
#算術運算子 以數值(文字或變數也可以)作為其運算元，並回傳單一數值。最常見的算術運算元是加法(+)，減法(-)，乘法(*)，及除法(/)在js中比較特別的是，在除數為0時Infinity。
範例:
```js
1 / 2; // =>0.5
1 / 2==1.0 / 2.0; // =>會是 true
```

js算術運算子列表:
| 運算子 | 描述 | 範例 |
| ----- | ----- | ----- |
| 取餘數(+) | 二元運算子。加法。  | 12+5 回傳 17.   |
| 取餘數(-) | 二元運算子。減法。  | 12-5 回傳 7.    |
| 取餘數(\*) | 二元運算子。乘法。  | 12\*5 回傳 60. |
| 取餘數(/) | 二元運算子。除法。  | 12/5 回傳 2.4.  |
| 取餘數(%) | 二元運算子。回傳兩個運算元相除後的餘數。 | 12%5回傳2. |
| 增加 (++) | 一元運算子。將運算元增加 1。假如使用在運算元之前(++x)，會運算元回傳增加1後的值;假如使用在運算元之後。(x++)，會回傳運算元加1前的值。 | 假如x是3，那**++x將把x設定為4並回傳4**，而**x++會回傳3，接著才把x設定為4**。 |
| 減少 (--)  | 一元運算子。 將運算元減少 1。回傳值的情況與增加運算元相同。 | 假如x是3，那--x將把x設定為2並回傳2，而x--會回傳3，接著才把x設定為2。 |
| (一元運算子)減號(-) | 一元運算子。回傳運算元的負數。 | 假如x是3，-x回傳-3。|
| (一元運算子)加號(+) | 一元運算子。嘗試將運算元轉換成數字，假如它還不是數字的話。 | +"3"回傳3。+true回傳1. |
| 指數運算子(**) | 計算以a為底的b次方，也就是a^b | 2**3回傳8 10**-1回傳0.1.   |

#### #位元運算子
#位元運算子 把運算元當作**32**位元的集合來看待(0和1)，而不是十進位，十六進位，或八進位。例如，十進位數字9以二進位表示就是1001。位元運算子將運算元以上述二進位的形式處理，但是回傳js中的數字類型值。

js位元運算子列表:
| 運算子 | 用法 | 描述 | 範例 |
| ----- | ----- | ----- | ----- |
| 位元 AND | a&b | 回傳兩個運算元對於每個 bit 做 AND 的結果。 |   |
| 位元 OR | a\|b | 回傳兩個運算元對於每個 bit 做 OR 的結果。 |  |
| 位元 XOR | a^b | 回傳兩個運算元對於每個 bit 做 XOR 的結果。 |   |
| 位元 NOT | ~a | 將運算元中的每個 bit 反轉(1->0,0->1)。 |   |
| 左移 | a<<b | 將a的每個bit向左移動b個bits，空餘的位數以0填滿。 | |
| 有號右移 | a>>b | 將a的每個bit向右移動b個bits，空餘位數以最高位補滿。 | |
| 以0填充的右移 | a>>>b | 將a的每個bit向右移動b個bits，空餘的位數以0填滿。 |   |

##### #位元邏輯運算子
概念上， #位元邏輯運算子 運作過程如下:

運算元被轉換為32bits的整數以二進位形式表示(0和1)。大於32bits的數字將被捨棄多出來的位元。例如，下列整數大於32個bit但是會被轉換為32個bit的整數:
轉換之前: 11100110111110100000000000000110000000000001
轉換之後:             10100000000000000110000000000001
第一個運算元中的每個bit分別對應到第二個運算元的每個bit:第一個bit對第一個bit,第二個bit對第二個bit，以此類推。
運算子會對於bit進行運算，結果也是基於bit來決定的。
例如，9的二元表示法是1001，15的二元表示法是1111。因此，在使用位元運算子的時候，結果如下:

| 運算式 | 結果 | 二元描述式           |
| ----- | ----- | ----- |
| 15&9 | 9 | 1111 & 1001=1001 |
| 15\|9 | 15 | 1111 | 1001=1111 |
| 15^9 | 6 | 1111^1001=0110 |
| ~15 | -16 | ~ 0000 0000 … 0000 1111=1111 1111 … 1111 0000 |
| ~9 | -10 | ~ 0000 0000 … 0000 1001=1111 1111 … 1111 0110 |
注意，在使用位元NOT運算子時， 所有的 32 個 bit 都被進行 NOT 了，包含最左邊用來描述正負數的位元(two's-complement representation)。

##### #位元移動運算子
#位元移動運算子 需要兩個運算元: 第一個是運算的目標，第二個是要移動的位元數。移動的方向取決於使用的運算子。
移動運算子會將運算元轉換成 32 bits 的整數，並且會回傳與左方運算元相同的型態。

移動運算子在下表被列出.
| 運算子 | 描述 | 範例 |
| ----- | ----- | ----- |
| 左移(<<) | 這個運算子會將第一個運算元的每個bit向左移動第二個運算元所指定的bit數量。左邊超出的位數會被捨棄，右邊空出的位數以0補齊。|9<<2得到36，因為1001向左移動2bits會得到100100，也就是二進位的36。 | |
| 有號右移(>>) | 這個運算子會將第一個運算元的每個bit向右移動第二個運算元所指定的bit數量。右邊超出的位數會被捨棄，左邊空出的位數以最高位補齊。|9>>2得到2，因為1001向右移動2bits會得到10，也就是二進位的2。相同的，-9>>2會得到-3，因為最高位用來表示正負號的bit被保留了。 | |
| 以0填充的右移(>>>) | 這個運算子會將第一個運算元的每個bit向右移動第二個運算元所指定的bit數量。右邊超出的位數會被捨棄，左邊空出的位數以0補齊。|19>>>2得到4，因為10011向右移動2bits會得到100，是二進位的4。對於非負的數字而言，以0填充的右移會得到和有號右移相同的結果。 | |

#### #邏輯運算子
#邏輯運算子 通常被用於布林(邏輯)值; 使用於 布林(邏輯)值時， 它們會回傳布林型態的值。 然而，&& 和 || 運算子實際上是回傳兩指定運算元之一，因此用於非布林型態值時，它可能會回傳一個非布林型態的值。 邏輯運算子將在下表中被詳細解釋。

| Operator | Usage | Description |
| ----- | ----- | ----- |
| 邏輯 AND (&&) | 運算式1&&運算式2 | 假如運算式1可以被轉換成false的話，回傳運算式1，否則，回傳運算式2。因此，&&只有在兩個運算元都是True時才會回傳True，否則回傳false。 |
| 邏輯 OR (\|\|) | 運算式1\|\|運算式2 | 假如運算式1可以被轉換成true的話，回傳運算式1，否則，回傳運算式2。因此，\|\|在兩個運算元有任一個是True時就會回傳True，否則回傳false。 |
| 邏輯 NOT (!) | !運算式 | 假如單一個運算元能被轉換成 True 時，回傳false，不然回傳 true。 |

可以被轉換為 false 的運算式是 null、0、NaN、空字串（""），或 undefined。

```js
// &&（邏輯 AND）運算子的範例。
let a1=true&&true // =>true
let a2=true&&false // =>false
let a3=false&&true // =>false
let a4=false&&3==4 // =>false
let a5="Cat"&&"Dog" // =>Dog
let a6=false&&"Cat" // =>false
let a7="Cat"&&false // =>false
```

```js
//  ||（邏輯 OR）運算子的範例。

let o1=true||true // =>true
let o2=false||true // =>true
let o3=true||false // =>true
let o4=false||3==4 // =>false
let o5="Cat"||"Dog" // =>Cat
let o6=false||"Cat" // =>Cat
let o7="Cat"||false // =>Cat
```

```js
// !（邏輯 NOT）運算子的範例。

let n1=!true // =>false
let n2=!false // =>true
let n3=!"Cat" // =>false
```

##### #短路解析
邏輯運算式是由左向右解析的， 他們會以下列規則嘗試進行 短路解析:
false&&任何東西 是 false 的短路解析。
true||任何東西 是 true 的短路解析。
這些規則保證 解析總是正確的。 值得注意的地方是，剩餘部分的運算式並沒有被解析，所以不會占用任何效能。

#### #字串運算子
除了作為比較運算子之外，運算子(+)也能用於字串，將兩字串接在一起，並回傳接在一起後的結果。

例如:

```js
console.log("我的"+"字串") // 會印出 字串 "我的字串"。
```

簡化的設定運算子 += 也能用於串接字串。

例如
```js
let mystring="字"
mystring += "母" // 得到 "字母" 並賦與給變數 mystring.
```

#### #條件運算子
#條件運算子 (又稱三元運算子、三元運算式等等)是js中唯一需要三個運算元的運算子。 這個運算子接受兩個運算元作為值且一個運算元作為條件。 語法是:
**條件 ? 值1 : 值2**
如果 條件 為 true，運算子回傳 值 1， 否則回傳 值 2。 你可以在任何使用標準運算子的地方改用 條件運算子。

例如
```js
let status=age >= 18 ? "成人" : "小孩";
```
這個陳述句會將 "成人" 賦與給變數 status 假如 age 大於等於 18。 否則，會將 "小孩" 賦與給變數 status。

#### #逗點運算子
#逗點運算子 (,) 作用是解析兩個運算元並回傳後面那個運算元的值。 這個運算子通常用於 for 迴圈內部，讓多個變數能在每次迴圈中被更新。

例如，假如 a 是一個有十個物件在裡面的二維陣列， 下面的程式中就使用了逗點運算子來同時更新兩個變數。 這段程式碼會印出陣列中所有對角線上的物件:
```js
for (let i=0,j=9; i <= j; i++,j--)
    console.log("a[" + i + "][" + j + "]= " + a[i][j])
```

#### #一元運算子
一元運算 是只需要一個運算元的運算。

一個 一元運算子 需要一個運算元， 位於運算子之前或之後:
運算子 運算元
或
運算元 運算子
例如， x++ 或 ++x.

##### #delete
delete 運算子會刪除物件，物件的性質，或是陣列中指定 index 的物件。 語法是:
```js
delete 物件名稱
delete 物件名稱.性質
delete 物件名稱[索引]
delete 性質 // 只有在 with 陳述句中可以使用
```
物件名稱 是物件的名稱， 性質 是物件中的一個特性， 索引 是用來表示物件在陣列中位置的一個整數。

第四種形式只有在 with 陳述句中可用， 用來刪除物件中的一個特性。

你可以用 delete 運算子來刪除隱式宣告的變數， 但不適用於使用 let 宣告的變數。

假如 delete 運算子使用成功， 它會將物件 或是 物件的特性設定為 未定義。 delete 運算子會在運算成功時回傳 true ，失敗時回傳 false 。
```js
x=42
let y=43
myobj=new Number()
myobj.h=4 // 建立特性 h
delete x // 回傳 true (只有在隱式宣告時能被刪除)
delete y // 回傳 false (在使用 let 宣告時無法刪除)
delete Math.PI // 回傳 false (不能刪除內建定義的特性)
delete myobj.h // 回傳 true (可以刪除使用者自定義的特性)
delete myobj // 回傳 true (在隱式宣告時可被刪除)
```
刪除陣列元素
在你刪除了陣列中的一個元素後， 陣列的長度並不會改變。 例如， 假如你刪除 a[3]， a[4] 依然是 a[4] 而 a[3] 為 未定義。

當使用 delete 運算子刪除陣列中的一個元素後， 那個元素便不再存在於陣列中了。 在下面的程式中， trees[3] 被用 delete 移除了。然而， trees[3] 的記憶體位址仍可用並且會回傳 未定義。
```js
let trees=["redwood","bay","cedar","oak","maple"]
delete trees[3]
if (3 in trees){
  // 不會執行到這裡
}
```
假如你希望給予陣列元素 未定義 的值， 你可以直接使用 undefined 關鍵字而不是使用 delete 運算子。 下列範例中， trees[3] 被指定了 undefined， 然而陣列元素依然存在:

```js
let trees=["redwood","bay","cedar","oak","maple"]
trees[3]=undefined
if (3 in trees){
  // 會執行這裡
}
```

##### #typeof
typeof 運算子 能以下列任一方式使用:
```js
typeof 運算元
typeof (運算元)
typeof 運算子會回傳代表運算元類型的 字串。 運算元能是字串，變數，關鍵字，或是會回傳型態的物件。 括號是可有可無的。
```
假設你定義了以下這些變數:
```js
let myFun=new Function("5 + 2")
let shape="round"
let size=1
let today=new Date()

// typeof 運算子會回傳下列結果:
typeof myFun // 回傳 "function"
typeof shape // 回傳 "string"
typeof size // 回傳 "number"
typeof today // 回傳 "object"
typeof doesntExist // 回傳 "undefined"
// 對於 true 和 null關鍵字， typeof 運算子會回傳下列結果:
typeof true // 回傳 "boolean"
typeof null // 回傳 "object"

// 對於字串或數字， typeof 運算子會回傳下列結果:
typeof 62 // 回傳 "number"
typeof "Hello world" // 回傳 "string"

// 對於特性，typeof 運算子會回傳 特性的值的類型:
typeof document.lastModified // 回傳 "string"
typeof window.length // 回傳 "number"
typeof Math.LN2 // 回傳 "number"

// 對於 方法 及 函式， typeof 運算子會回傳下列結果:
typeof blur // 回傳 "function"
typeof eval // 回傳 "function"
typeof parseInt // 回傳 "function"
typeof shape.split // 回傳 "function"

// 對於內建定義的物件， typeof 運算子會回傳下列結果:
typeof Date // 回傳 "function"
typeof Function // 回傳 "function"
typeof Math // 回傳 "object"
typeof Option // 回傳 "function"
typeof String // 回傳 "function"
```

#### #void
void 運算子 能以下列任一方式使用:
```js
void (運算式)
void 運算式
void 運算子會解析運算式而不回傳任何值。 運算式 是js中要解析的對象。 括號是可有可無的，但是建議使用。
```
你可以使用 void 運算子來解析超連結中的運算式。 運算式會被解析而不會在當前頁面被印出。

下列範例是一個在點擊時甚麼都不做的超連結。 當使用者點擊連結時， void(0) 被解析為 未定義， 而甚麼都不會發生。
```html
<a href="javascript:void(0)">點擊這裡，甚麼都不會發生</a>
```

下列範例是一個在使用者點擊時傳送表單的超連結。
```html
<a href="javascript:void(document.form.submit())"> 點擊以送出</a>
```

#### #關係運算子
#關係運算子 比較兩運算元並基於比較結果回傳布林值。

##### #in
in 運算子在指定性質存在於物件中時回傳 true。語法是:
性質名稱 in 物件名稱
性質名稱 可以是 字串或數字，或是陣列的索引， 且物件名稱是物件的名稱。
下列範例示範了 in 運算子的一些用法。
```js
// 陣列
let trees=["redwood","bay","cedar","oak","maple"]
0 in trees // 回傳 true
3 in trees // 回傳 true
6 in trees // 回傳 false
"bay" in trees // 回傳 false (你必須指定 索引，
// 而不是 索引所對應的元素)
"length" in trees // 回傳 true (length 是陣列的性質之一)

// 內建物件
"PI" in Math // 回傳 true
let myString=new String("coral")
"length" in myString // 回傳 true

// 自訂義物件
let mycar={ make: "Honda",model: "Accord",year: 1998 }
"make" in mycar // 回傳 true
"model" in mycar // 回傳 true
instanceof
instanceof 運算子 在 指定物件 具有 指定的物件型態 時回傳 true。 語法是:
```
物件名稱 instanceof 物件類型
物件名稱 是用來與 物件類型 比較的物件的名字， 物件類型 是物件的類型， 例如 Date 或 Array。

當你需要在程式執行中確認物件的形態時，你可以使用 instanceof 運算子。 例如，當捕捉到例外時， 你可以依照例外的類型來決定用來處理意外的程式碼。

例如，下列程式碼使用 instanceof 來判斷變數 theDay 是不是 Date 類型的物件。 因為 theDay 是 Date 類型的物件， 所以 if 陳述中的陳述句會被執行。
```js
let theDay=new Date(1995,12,17)
if (theDay instanceof Date){
  // 會被執行的陳述
}
```

#### #分組運算子
分組運算子()控制了運算子的優先順序。 例如，你可以覆寫先乘除，後加減的優先順序，使其變成先加減，後乘除。
```js
let a=1
let b=2
let c=3

// 預設運算級
a + b * c // =>7
// 預設的結果
a+(b*c) // =>7

// 現在複寫運算級
// 變成先進行加法，後乘法了
(a+b)*c // =>9

// 結果
a*c+b*c // 9
```

#### #new
你可以使用 new 運算子 來建立一個使用者自定義物件或內建物件的實例。 用法如下:
```js
let 物件名稱=new 物件型態([參數1,參數2,...,參數N])
super
super 關鍵字用於呼叫物件的父物件中的函式。在使用類別來呼叫父類別的建構子時很實用，例如:

super([參數]) // 呼叫父物件的建構子.
super.父物件的函式([參數])
```

#### #展開運算子
展開運算子 (en-US)能將運算式展開於需要多個參數的地方（如函式呼叫）或是需要多個元素（如陣列字串常數）的地方。

範例：現在你想要用已存在的一個陣列做為新的一個陣列的一部份，當字串常數不再可用而你必須使用指令式編程，也就是使用，一連串的 push、splice、concat，等等。展開運算子能讓過程變得更加簡潔:
```js
let parts=["肩膀","膝蓋"]
let lyrics=["頭",...parts,"和","腳趾"]
```
相同的，展開運算子也適用於函式呼叫:
```js
function f(x,y,z){}
let args=[0,1,2]
f(...參數)
```

#### #運算子優先級
運算子優先級決定運算子被使用於運算元的先後順序。 你也可以使用括號來強制指定優先級。

下列表格列出了運算子的優先級， 從高到低。

| 優先性 | 運算子名稱 | 相依 | 運算子 |
| ----- | ----- | ----- | ----- |
| 19 | 分組運算子 | 無 | () |
| 18 | Member Access | 從左至右 | . |
| 18 | Computed Member Access | 從左至右 | [] |
| 19 | new (with argument list) | 無 | new name() |
| 18 | 呼叫函式 | 從左至右 | function() |
| 18 | 可選串連（Optional chaining）| 從左至右 | ?. |
| 17 | new (without argument list) | 從右至左 | new |
| 16 | **字尾**遞增遞減 | 無 | ++ -- |
| 15 | Logical NOT | 從右至左 | ! |
| 15 | Bitwise NOT | 從右至左 | ~ |
| 15 | Unary Plus | 從右至左 | + |
| 15 | Unary Negation | 從右至左 | - |
| 15 | 字首遞增遞減 | 從右至左 | ++ -- |
| 15 | typeof | 從右至左 | typeof |
| 15 | void | 從右至左 | void |
| 15 | delete | 從右至左 | delete |
| 15 | await | 從右至左 | await |
| 14 | 次方 | 從右至左 | ** |
| 13 | 乘除法模除 | 從左至右 | * / % |
| 12 | 加減法 | 從左至右 | + -  |
| 11 | 位元移動 | 從左至右 | << >> >>> |
| 10 | 關係運算子 | 從左至右 | < <= > >= in instanceof |
| 09 | 相等性 | 從左至右 |==!= === !== |
| 08 | 位元AND | 從左至右 | & |
| 07 | 位元XOR | 從左至右 | ^ |
| 06 | 位元OR | 從左至右 | \| |
| 05 | 邏輯AND | 從左至右 | && |
| 04 | 邏輯OR | 從左至右 | \|\| |
| 04 | Nullish Coalescing | 從左至右 | ?? |
| 03 | 條件運算子 | 從右至左 | ?:   |
| 02 | 指定運算子 | 從右至左 | = += -= \*\*= \*= /= %= <<= >>= >>>= &= ^= \|= &&= \|\|= ??= |
| 01 | 逗點運算子 | 從左至右 | , |

## Chr7 #判斷式
### #ifelse
當條件成立的時候會執行if陳述式裡的程式，而不成立時則執行另外一個陳述式。
```js
if(condition){
    context
}

// With an else clause
if(condition){
    context
}else{
    context
}
```
condition
一個成立或不成立的運算式。

context
如果if中的條件(conditions)為真時執行陳述式(statements)。陳述式可以為任何內容，包含巢狀式(nested)的 if 陳述。當要執行多行的陳述式(statements)時，使用區塊(block)將所要執行的陳述式包覆。
如果不需要執行任何動作時，則不撰寫任何陳述式(empty statement)。
當條件不成立時所執行的部份，當else被撰寫時才會被執行。可以是任何的陳述式，包含使用區塊(block)及巢狀(nested)的陳述。

描述
多重的ifelse陳述式可以使用else if子句來建立一個巢狀結構的句子。要記住，在 JavaScript 中**沒有 elseif **的語法可以用。

```js
if(condition){
    context
}else if(condition){
    context
}else if(condition){
    context
}
// inf.
else{
    context
}
```

將巢狀結構適當的排版後，我們能更了解其背後運作的邏輯：

```js
if(condition){
    context
}else{
    if(condition){
        context
    }else{
        if(condition){
            context
        }
    }
}
```

如果在一個條件式中只要一行可以這樣簡化。

```js
if(condition)
    context
else
    context
```

但通常來說，無論如何都使用區塊陳述式(第一種方式)是個很好的習慣，尤其是當你使用巢狀結構的 if 陳述式時，這會讓人更容易理解你的程式碼。

不要被Boolean物件中，布林值的 true 和 false 給混淆了。任何值只要不是 false、 undefined、 null、 0、 NaN，或者空字串 ("")，並且任何物件，包括其值是 false的布林物件 ，仍然會被條件陳述式視為條件成立。舉例而言：
```
let b = new Boolean(false);
if (b) // this condition is truthy
```

### #switchcase

switch 語句會比對一個表達式裡頭的值是否符合 case 條件，然後執行跟這個條件相關的陳述式，以及此一符合條件以外，剩下其他條件裡的陳述式。

嘗試一下

語法
```js
switch(expression){
    case value1:
        context
        break
    case value2:
        context
        break
    // inf..
    case valueN:
        context
        break
    default:
        break;
}
```
expression: 一個表達式其結果用來跟每個 case 條件比對。

case value: 一個 case 條件是用來跟 expression 匹配的。 如果 expression 符合特定的 valueN，那在 case 條件裡的語句就會執行，直到這個 switch 陳述式結束或遇到一個 break 。

default: 那在 expression 的值並不符合任何一個 case 條件的情況下，就會執行這個條件裡的語句。

一個 switch 陳述式會先評估自己的 expression。然後他會按照 case 條件順序開始尋找，直到比對到第一個表達式值跟輸入 expression 的值相等的 case 條件（使用嚴格的邏輯運算子, ===）並把控制流交給該子句、並執行裡面的陳述式（如果給定值符合多個 case，就執行第一個符合的 case，就算該 case 與其他 case 不同）

如果未找到匹配的 case 子句，程序將查找可選的 default 子句，如果找到，則將控制權轉移到該子句，執行關聯的語句。 如果沒有找到 default 子句，程序將繼續執行 switch 末尾後面的語句。
按照慣例， default 語句會是最後一個條件，但**不一定要存在**。（如果給定值符合多個 case，就執行第一個符合的 case，就算該 case 與其他 case 不同）

與每個 case 標籤關聯的可選的break語句確保一旦執行匹配的語句，程序就跳出switch，並在switch後面的語句處繼續執行。 如果省略break，程序將繼續執行switch 語句中的下一條語句。

使用 switch
在以下示例中，如果 expr 的計算結果為“Bananas”，則程序將該值與大小寫“Bananas”匹配並執行關聯的語句。 當遇到break時，程序跳出switch並執行switch後面的語句。 如果省略了break，則case“Cherries”的語句也將被執行。

```js
switch(expr){
    case "Oranges":
        console.log("Oranges are $0.59 a pound.")
        break
    case "Apples":
        console.log("Apples are $0.32 a pound.")
        break
    case "Bananas":
        console.log("Bananas are $0.48 a pound.")
        break
    case "Cherries":
        console.log("Cherries are $3.00 a pound.")
        break
    case "Mangoes":
    case "Papayas":
        console.log("Mangoes and papayas are $2.79 a pound.")
        break
    default:
        console.log("Sorry, we are out of " + expr + ".")
}

console.log("Is there anything else you'd like?")
```

如果忘記 break ，則腳本將從滿足條件的情況開始運行，並且無論是否滿足條件都將運行之後的情況。 請參閱此處的示例：
```js
let foo=0
switch(foo){
    case -1:
        console.log("negative 1")
        break
    case 0: // foo is 0 so criteria met here so this block will run
        console.log(0)
        // NOTE: the forgotten break would have been here
    case 1: // no break statement in 'case 0:' so this case will run as well
        console.log(1)
        break // it encounters this break so will not continue into 'case 2:'
    case 2:
        console.log(2)
        break
    default:
        console.log("default")
}
```

cases 中間可以放 default! 如果 JavaScript 找不到匹配項，它會將您返回到默認值(就算置於所有其他情況之前時，它也適用)：
```js
let foo=5
switch(foo){
    case 2:
        console.log(2)
        break // it encounters this break so will not continue into 'default:'
    default:
        console.log("default")
    // fall-through
    case 1:
        console.log("1")
}
```

同時使用多個條件 case 的方法
此方法利用了以下事實：如果 case 語句下面沒有中斷，則無論 case 是否滿足條件，它將繼續執行下一個 case 語句。 請參閱標題為“如果我忘記休息會怎樣？”的部分。

這是單個操作順序 switch 語句的示例，其中四個不同的值執行完全相同的操作。
```js
let Animal="Giraffe"
switch (Animal){
    case "Cow":
    case "Giraffe":
    case "Dog":
    case "Pig":
        console.log("This animal will go on Noah's Ark.")
        break
    case "Dinosaur":
    default:
        console.log("This animal will not.")
}
```
Multi-case - 鍊式操作
這是多操作順序 switch 語句的示例，其中根據提供的整數，您可以收到不同的輸出。 這表明它將按照放置 case 語句的順序進行遍歷，並且不必按數字順序排列。 在 JavaScript 中，您甚至可以將字符串定義混合到這些 case 語句中。
```js
let foo=1
let output="Output: "
switch (foo){
    case 0:
        output=output+"So "
    case 1:
        output=output+"What "
        output=output+"Is "
    case 2:
        output=output+"Your "
    case 3:
        output=output+"Name"
    case 4:
        output=output+"?"
        console.log(output)
        break
    case 5:
        output=output+"!"
        console.log(output)
        break
    default:
        console.log("Please pick a number from 0 to 5!")
}
```

switch 語句中的塊作用域變量
由於大多數現代瀏覽器都提供了 ECMAScript 2015 (ES6) 支持，因此在某些情況下您可能希望使用 let 和 const 語句來聲明塊作用域變量。

看一下這個例子：
```js
const action="say_hello"
switch(action){
    case "say_hello":
        let message="hello"
        console.log(message)
        break
    case "say_hi":
        let message="hi"
        console.log(message)
        break
    default:
        console.log("Empty action received.")
        break
}
```
此示例將輸出您可能沒有預料到的錯誤 Uncaught SyntaxError: Identifier 'message' has not been displayed。

這是因為第一個let message='hello'; 與第二個 let 語句衝突 let message='hi'; 即使它們在自己單獨的 case 語句中 case 'say_hello': 和 case 'say_hi';
最終，這是由於兩個 let 語句都被解釋為同一塊作用域內相同變量名的重複聲明。

我們可以通過用括號括起我們的 case 語句來輕鬆解決這個問題：

```js
const action="say_hello"
switch(action){
    case "say_hello":{
        // added brackets
        let message="hello"
        console.log(message)
        break
    } // added brackets
    case "say_hi":{
        // added brackets
        let message="hi"
        console.log(message)
        break
    } // added brackets
    default:{
        // added brackets
        console.log("Empty action received.")
        break
    } // added brackets
}
```

現在，此代碼將在控制台中正常輸出 hello，完全不會出現任何錯誤。

### #ifelseTOswitchcase
例如這個switchcase
```js
let test=0
switch(test){
    case -1:
        console.log("negative 1")
        break
    case 0:
        console.log(0)
        break
    case 1:
        console.log(1)
        break
    case 2:
        console.log(2)
        break
    default:
        console.log("default")
}
```
改成if要這樣寫
```js
let test=0
if(test==-1){
    console.log("negative 1")
}else if(test==0){
    console.log(0)
}else if(test==1){
    console.log(1)
}else if(test==2){
    console.log(2)
}else{
    console.log("default")
}
```

如果沒break，if判斷式會等效成
```js
let test=0
let check=0

if(test==-1){
    console.log("negative 1")
    check=1
}

if(test==0){
    console.log(0)
    check=1
}

if(test==1){
    console.log(1)
    check=1
}

if(test==2){
    console.log(2)
    check=1
}

if(!check){
    console.log("default")
}
```

if轉switchcase則相反這裡就不加闡述

## Chr8 #迴圈
在本章收錄了js的 #forloop #while #do-while #forEach 迴圈
#### 8-1 #forloop

##### 語法架構
```js
for(let i=0;i<count;i=i+1){
    // function...
}
```

#### 8-2 #while

##### 語法架構
```js
let i=0
while(i<count){
    // function...
    i=i+1
}
```

#### 8-3 #do-while

##### 語法架構
```js
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
在網頁設計中，「while」迴圈是一種常用的迴圈結構，它可以重複執行一段程式碼，只要特定的條件保持為真。這種迴圈結構通常用於處理需要重複執行、直到特定條件不再滿足的情況。在網頁設計及程式開發時，「while」迴圈可以應用在處理資料的判斷、動態載入資料、處理事件等方面。
你可以根據具體的需求和情境，在網頁設計中使用「while」迴圈處理、動態操作 DOM 元素、處理事件循環等。請確保在使用迴圈時考慮好迴圈終止的條件，以避免無窮迴圈的發生。
網頁設計中，「do-while」是一種迴圈結構，它允許在滿足特定條件的情況下重複執行一段程式碼。這種迴圈結構通常用於處理需要至少執行一次的操作，然後根據特定條件是否滿足來決定是否繼續重複執行。
在網頁設計及程式開發時，「do-while」迴圈可以應用在處理使用者輸入驗證、表單驗證、動態載入資料等場景中。你也可以根據具體的需求和情境，適應並應用這種迴圈結構在不同的網頁設計場景中。
以一般程式或網頁設計師來說，用 while 的次數會遠比用 do-while 來得高。

## Chr9 #物件
再說物件之前我們先來說說 #陣列
### #陣列
陣列是一個特殊的物件主要的功能就是**儲存大量資料**
陣列元素從一開始

js的陣列語法如下:
```js
// 1
let array1=["1","2","3"] // 以,分隔每隔值
console.log(array1) // => ["1","2","3"]

// 2
let array2=new Array("1","2","3") // 以,分隔每隔值
console.log(array2) // => ["1","2","3"]

// 如果要拿到陣列的第一個值要這樣寫
consloe.log(array1[0]) // => "1"
consloe.log(array2.item(0)) // => "1"

// 如果要改變陣列的直可以這麼做
array1[2]="4"
console.log(array1) // => ["1","2","4"]
```
建議使用第一種方式，本篇教學也都以第一種方式寫

二維及多維陣列:
範例:
```js
let array3=[
    ["1","2","3"],
    ["a","b","c"]
] // 像這樣子一個陣列又有一個就是二維(有兩個就是三維以此類推)

console.log(array3) /*
0:(3) ['1','2','3']
1:(3) ['a','b','c']
*/
```

### #物件
物件(object)是一個包含資料與處理資料指令的資料結構。
語法
// Object initialiser or literal
{
    *\[value\]*: *\[any\]*
    // *inf.*
}
// Called as a constructor
new Object(*\[any\]*)

描述
構造Object函數為給定值創建對象包裝器。如果值為null或undefined，它將創建並返回一個空對象，否則，它將返回與給定值對應的 Type 的對象。如果該值已經是一個對象，它將返回該值。

當在非構造函數上下文中調用時，Object其行為與 相同new Object()。

Object 物件實體與 Object 原型物件
JavaScript 中的所有對像都源自Object 所有對像都繼承自 的方法和屬性Object.prototype，儘管它們可能會被覆蓋。
例如，其他構造函數的原型重寫該constructor屬性並提供它們自己的toString()方法。對原型對象的更改Object將傳播到所有對象，除非受這些更改影響的屬性和方法沿著原型鏈進一步被覆蓋。

範例
下面例子儲存一個空物件至變數o
```js
let o=new Object()
let o=new Object(undefined)
let o=new Object(null)
```

下面例子儲存 Boolean 物件在 o:
```js
let o=new Object(true) // equivalent to o=new Boolean(true)
let o=new Object(Boolean()) // equivalent to o=new Boolean(false)
```

## Chr10 #函式

### 函式介紹
程式設計的另一個基本概念是函數，它允許您儲存一段程式碼，該程式碼在定義的區塊內執行單個任務，然後在需要時使用一個簡短命令調用該程式碼區塊，而不必多次輸入相同的程式碼。

函式是構成js的基本要素之一。一個函式本身就是一段js程序—包含用於執行某一個任務或計算的語法。要呼叫某一個函式之前，你必需先在這個函式欲執行的 scope 中定義它。

### #定義函式
一個函式的定義由一系列的函式關鍵詞組成,依次為：
- 函式的**名稱(不得為 #關鍵保留字 )**。
- 包圍在**括號**中，並由**半形逗號**區隔的一個函式參數列表(可以為無參數)。
- 包圍在**大括號**中，用於定義函式功能的一些js語句。

例如，以下的程式碼定義了一個名為 square 的簡單函式:
```js
function square(number){
  return number * number
}
```
函式 square 有一個參數，叫作 number。這個函式只有一行程式碼，它會回傳 number 自乘的結果。函式的 return 語法描述函式的返回值。
原始參數（例如一個數字）被作為值傳遞給函式，如果呼叫的函式改變了這個參數的值，不會影響到函式外部的原始變數。
如果傳遞一個物件（例如Array或自定義的其它物件）作為參數，而函式改變了這個物件的屬性，這樣的改變對函式外部是有作用的(因為是傳遞物件的位址)，如下面的例子所示：

```js
let mycar={ make: "Honda",model: "Accord",year: 1998 }
let x
let y

function myFunc(theObject){
    theObject.make="Toyota"
}

x=mycar.make // => "Honda"

myFunc(mycar)
y=mycar.make // => "Toyota"
// (屬性 make 被 function 改變)
```

請注意，重新給參數指定一個對象，並不會對函式的外部有任何影響，因為這樣只是改變了參數的值，而不是改變了對象的一個屬性值：
```js
let mycar={ make: "Honda",model: "Accord",year: 1998 }
let x
let y

function myFunc(theObject){
    theObject={ make: "Ford",model: "Focus",year: 2006 }
}

x=mycar.make // => "Honda"

myFunc(mycar)
y=mycar.make // => "Honda"
```

儘管上述函式定義都是用的是陳述式，函式也同樣可以由函式表達式來定義。這樣的函式可以是匿名的；它不必有名稱。例如，上面提到的函式 square 也可這樣來定義：
```js
let square=function(number){
    return number*number
}
let x=square(4); // => 16
```

必要時，函式名稱可與函式表達式同時存在，並且可以用於在函式內部代指其本身(遞迴)：
```js
let factorial=function fac(n){
    if(n<2){
        return 1
    }else{
        return n*fac(n-1)
    }
}

console.log(factorial(3))
```
函式表達式在將函式作為一個參數傳遞給其它函式時十分方便。下面的例子展示了一個叫 map 的函式如何被定義，而後呼叫一個匿名函式作為其第一個參數：

```js
function map(f,a){
    let result=[] // Create a new Array
    for(let i=0;i!=a.length;i=i+1){
        result[i]=f(a[i])
    }
    return result
}
```

下面的程式碼呼叫 map 函式並將一個匿名函式傳入作為第一個參數:
```js
map(
    function(x){
        return x*x*x
    },
    [0,1,2,5,10],
)
// 結果會回傳 [0,1,8,125,1000]
```
除了上述的定義方式以外，我們也可以透過 Function constructor來定義，類似 eval()。

### #呼叫函式
定義一個函式並不會自動的執行它。定義了函式僅僅是賦予函式以名稱並明確函式被呼叫時該做些什麼。呼叫函式才會以給定的參數真正執行這些動作。例如，一旦你定義了函式 square，你可以如下這樣呼叫它：
```js
square(5)
```
上述程式碼把 5 傳遞給 square 函式。函式執行完會回傳 25。
函式必須在呼叫區塊的可視範圍內，但函數也可以宣告在使用處的下面，如下列範例:
```js
console.log(square(5))
/* ... */
function square(n){
    return n*n
}
```

函數的作用域是聲明它的函數，如果是在頂層聲明的，則為整個程序。請注意，這僅在使用上述語法定義函數時有效（即 function funcName(){}）。 下面的代碼將不起作用。
```js
console.log(square(5))
square=function(n){
    return n*n
};
```

函數的參數不限於字符串和數字。 您也可以將整個對像傳遞給函數。 show_props 函數（在使用對像中定義）是將對像作為參數的函數示例。
函數可以是遞歸的； 也就是說，它可以調用自己。 例如，這是一個遞歸計算階乘的函數：
```js
function factorial(n){
    if(n==0||n==1){
        return 1
    }else{
        return n*factorial(n-1)
    }
}
```

然後，您可以計算一到五的階乘，如下所示：
```js
let a,b,c,d,e
a=factorial(1) // a gets the value 1
b=factorial(2) // b gets the value 2
c=factorial(3) // c gets the value 6
d=factorial(4) // d gets the value 24
e=factorial(5) // e gets the value 120
```
還有其他方法可以調用函數。 通常情況下，需要動態調用函數，或者函數的參數數量不同，或者需要將函數調用的上下文設置為運行時確定的特定對象。 事實證明，函數本身就是對象，而這些對象又具有方法（請參閱函數對象）。
其中之一，apply()方法，可以用來實現這個目標。

### #功能範圍
函數內部定義的變量無法從函數外部的任何地方訪問，因為變量僅在函數範圍內定義。
但是，函數可以訪問其定義範圍內定義的所有變量和函數。
換句話說，在全局作用域中定義的函數可以訪問在全局作用域中定義的所有變量。
在另一個函數內定義的函數還可以訪問其父函數中定義的所有變量以及父函數有權訪問的任何其他變量。
```js
// The following variables are defined in the global scope
let num1=20
let num2=3
let name="Chamahk"

// This function is defined in the global scope
function multiply(){
    return num1*num2
}
multiply(); // => 60

// A nested function example
function getScore(){
    let num1=2
    let num2=3
    function add(){
        return name+" scored "+(num1+num2)
    }
    return add()
}

getScore(); // => "Chamahk scored 5"
```
### #函式vs方法
在我們繼續前，有件事需要先釐清——技術上來說，瀏覽器內建函數並不是函數（function）——它們是方法（method）。這聽起來有點令人疑惑，不過別擔心——在你目前的學習階段，「函數」與「方法」這兩個詞彙大多時候是可以互換的，至少對我們的目標而言。

這兩個詞的區別在方法（method）是定義在物件裡的函數（function）。瀏覽器內建函數（方法）和變數（此處被稱作屬性（property））被儲存在建構好的物件裡，令程式碼控制起來更有效率也更簡單。

你還不需要了解js物件的內部運作——在之後的模組我們會學到物件內部的所有運作方式，以及如何創建你自己的物件。此時，我們只需要釐清方法與函數之間任何可能搞混的地方——在你上網查相關教學資源時很可能兩個詞彙都會碰到。

### #匿名函式
你可能會看到以稍微不同的方式定義和調用函數。到目前為止，我們創建的函數通常像這樣：
```js
function myFunction(){
    alert("hello")
}
```
But you can also create a function that doesn't have a name:
```js
function(){
  alert("hello")
}
```

這被稱為匿名函數—它沒有名稱！它自己並不會執行任何動作。通常，你會將匿名函數與事件處理程式一起使用，例如以下範例將在按鈕被點擊時運行函數內的程式碼：
```js
let myButton=document.querySelector("button")
myButton.onclick=function(){
    alert("hello")
}
```
以上的範例要求頁面上有一個`<button>`元素，以便選取並點擊。在課程中你已經多次見過這種結構，你將在下一篇文章中學到更多並且使用它。

你還可以將匿名函數指派為變數的值，例如：
```js
let myGreeting=function(){
    alert("hello")
}
```
這個函數現在可以這樣調用：
```js
myGreeting()
```

這實際上就是給這個函數取了個名字；你也可以將這個函數指派為多個變數的值，例如：
```js
let anotherGreeting=function(){
    alert("hello")
};
```
這個函數現在可以這樣調用：
```js
myGreeting()
anotherGreeting()
```
但這只會造成混亂，所以不要這麼做！在創建函數時，最好堅持以下形式：
```js
function myGreeting(){
  alert("hello")
}
```
你主要使用匿名函數只是為了在事件觸發時執行一系列程式碼 — 像按下按鈕之後運行一些程式碼 — 使用事件處理程式。再次強調，它看起來像這樣：
```js
myButton.onclick=function(){
    // 程式碼在這
}
```

### #函式參數
有些函數在調用時需要指定參數 — 這些參數是需要放在函數括號內的值，這些值是函數正確運作所需的。
備註： 有時參數被稱為引數、屬性或特性。
舉個例子，瀏覽器內建的 Math.random() 函數不需要任何參數。當調用它時，它總是返回 0 到 1 之間的一個隨機數：

```js
let myNumber=Math.random();
```

而瀏覽器內建的字串 replace() 函數則需要兩個參數 — 在主字串中要查找的子字串，以及要用來替換該字串的子字串：
```js
let myText="I am a string";
let newString=myText.replace("string","sausage");
```

備註： 當你需要指定多個參數時，它們之間用**半形逗號**分隔。
還要注意，有時參數是可選的 — 你不一定要指定它們。如果不指定，該函數通常會使用一些預設行為。舉個例子，陣列 join() 函數的參數是可選的：
```js
let myArray=["I","love","chocolate","frogs"];
let madeAString=myArray.join(" ");
// 回傳 'I love chocolate frogs'
let madeAString=myArray.join();
// 回傳 'I,love,chocolate,frogs'
```
如果不包含參數來指定連接/分隔字符，則默認使用逗號。

### #函式作用域及衝突
讓我們來談談作用域 — 這是處理函數時非常重要的概念。當你創建一個函數時，該函數內定義的變量和其他內容會位於自己單獨的作用域中，這意味著它們被封鎖在自己單獨的區域內，無法從其他函數內部或外部程式碼訪問。
在所有函數之外的頂層稱為全局作用域。在全局作用域中定義的值可以在程式碼的任何地方訪問。
JavaScript 之所以這樣設計，是基於多種原因 — 主要是出於安全和組織考慮。有時你不希望變數在程式碼的任何地方都是可訪問的 — 從其他地方引入的外部腳本可能會開始干擾你的程式碼，並造成問題，因為它們可能恰好使用與程式碼其他部分相同的變數名稱，造成衝突。這可能是惡意的，也可能是無意的。
例如，假設你有一個 HTML 文件在調用兩個外部的js文件，並且這兩個文件都有一個使用相同名稱變數和函數的定義：

```html
<!-- Excerpt from my HTML -->
<script src="first.js"></script>
<script src="second.js"></script>
<script>
  greeting();
</script>
```

```js
// first.js
let name="Chris";
function greeting(){
    alert("Hello "+name+": welcome to our company.")
}
```

```js
// second.js
let name="Zaptec"
function greeting(){
    alert("Our company is called "+name+".")
}
```
你希望呼叫的兩個函數都被稱為 greeting()，但你只能夠訪問 second.js 文件中的 greeting() 函數 — 它是在 HTML 中的後面引入，因此它的變數和函數覆蓋了 first.js 文件中的相同名稱。
將程式碼的部分功能封閉在函數中，可以避免這樣的問題，也被視為最佳實踐。
簡單的說後創的蓋掉了先創的函式


### #函式裡的函式
請記住，您可以從任何地方調用函數，甚至可以在另一個函數內部調用。
這通常被用來保持代碼整潔——如果你有一個大而復雜的函數，如果你把它分解成幾個子函數，會更容易理解：

```js
function myBigFunction(){
    let myValue

    subFunction1() // X: ReferenceError: myValue is not Define
    subFunction2()
    subFunction3()
}

function subFunction1(){
    console.log(myValue)
}

function subFunction2(){
    console.log(myValue)
}

function subFunction3(){
    console.log(myValue)
}
```

只需確保函數內使用的值在範圍內正確即可。 上面的示例會拋出錯誤 ReferenceError: myValue is not Define，因為儘管 myValue 變量是在與函數調用相同的作用域中定義的，但它並未在函數定義內部定義 - 調用函數時運行的實際代碼。
要實現此功能，您必須將值作為參數傳遞給函數，如下所示：

```js
function myBigFunction(){
    let myValue=1

    subFunction1(myValue)
    subFunction2(myValue)
    subFunction3(myValue)
}

function subFunction1(value){
    console.log(value)
}

function subFunction2(value){
    console.log(value)
}

function subFunction3(value){
    console.log(value)
}
```





閉包
閉包是js最強大的特性之一。JavaScript 允許巢狀函式（nesting of functions）並給予內部函式完全訪問（full access）所有變數，與外部函式定義的函式（還有所有外部函式內的變數與函式）。
不過，外部函式並不能訪問內部函式的變數與函式。這保障了內部函式的變數安全。另外，由於內部函式能訪問外部函式定義的變數與函式，將存活得比外部函式還久。

閉包在以下情況下被創建：當內部函式以某種方式被指定為可以在外部範圍中使用時。
```js
let pet=function(name){
    // The outer function defines a variable called "name"
    let getName=function(){
        return name // The inner function has access to the "name" variable of the outer function
    }
    return getName // Return the inner function,thereby exposing it to outer scopes
}
let myPet=pet("Vivie")

myPet() // => "Vivie"
```

閉包也可以更複雜，當內部函式回傳一個包含用於操作外部函式內部變數的方法的物件時，例如：
```js
let createPet=function(name){
    let sex
    return{
        setName:function(newName){
           name=newName
        },

        getName:function(){
           return name
        },

        getSex:function(){
           return sex
        },

        setSex:function(newSex){
            if(typeof newSex=="string"&&(newSex.toLowerCase()=="male"||newSex.toLowerCase()=="female")){
               sex=newSex
            }
        },
    }
}

let pet=createPet("Vivie")
pet.getName() // Vivie

pet.setName("Oliver")
pet.setSex("male")
pet.getSex() // male
pet.getName() // Oliver
```
在上述程式碼中，name 變數是內部函式 createPet 定義的，但是可以透過回傳的物件中的方法來操作它。這樣的特性稱為閉包，允許內部函式訪問外部函式的變數。

值得注意的是，使用閉包時要小心處理 this 變數。它的值取決於函式的呼叫方式，而不是它的定義方式。一篇詳細且精緻的關於閉包的文章可以在這裡找到（英文）。

### #arguments物件
函式的參數保存在一個類似陣列的物件中。在函式內部，你可以使用以下方式來引用傳遞給它的參數：
```js
arguments[i];
```
其中 i 是參數的序數，從 0 開始。所以，傳遞給函式的第一個參數將是 arguments[0]。實際傳遞給函式的參數數量可以通過 arguments.length 屬性來獲取。
使用 arguments 物件，你可以以比函式正式聲明的參數更多的參數來呼叫函式。這在你事先不知道會傳遞多少個參數給函式時非常有用。你可以使用 arguments.length 來確定實際傳遞給函式的參數數量，然後使用 arguments 物件來訪問每個參數。
舉個例子，考慮一個函式，它將幾個字串連接在一起。該函式的唯一正式參數是指定連接這些項目的字符。函式定義如下：

```js
function myConcat(separator){
    let result="" // initialize list

    // iterate through arguments
    for(let i=1;i<arguments.length;i=i+1){
        result=result+(arguments[i]+separator)
    }
    return result
}
```

你可以傳遞任意數量的參數給該函式，並將每個參數連接成一個字串 "list"：
```js
// returns "red,orange,blue,"
myConcat(",","red","orange","blue")

// returns "elephant; giraffe; lion; cheetah; "
myConcat("; ","elephant","giraffe","lion","cheetah")

// returns "sage. basil. oregano. pepper. parsley. "
myConcat(". ","sage","basil","oregano","pepper","parsley")
```

請注意，arguments 變數是 "類陣列" 的，但不是真正的陣列。它被稱為 "類陣列" 是因為它具有編號索引和長度屬性，但並不具備陣列的所有操作方法。

### #可預定義的函式
js 有幾個頂級的可預定義函式：
1. eval
2. isFinite
3. isNaN
4. parseInt
5. parseFloat
6. Number
7. String
8. encodeURI
9. decodeURI
10. encodeURIComponent
11. decodeURIComponent

#### #eval
eval 函式在不參考特定物件的情況下評估js代碼的字符串。eval 的語法是：
```js
eval(expr);
```

其中 expr 是要評估的字符串。

如果該字符串表示表達式，則 eval 評估該表達式。如果該參數表示一個或多個 JavaScript 陳述式，eval 則執行這些陳述式。eval 代碼的範圍與呼叫代碼的範圍相同。不要呼叫 eval 來評估算術表達式；JavaScript 會自動評估算術表達式。

#### #isFinite
isFinite 函式評估參數以確定它是否是一個有限數。isFinite 的語法是：
```js
isFinite(number);
```
其中 number 是要評估的數值。
如果參數是 NaN、正無窮或負無窮，該方法返回false；否則返回 true。
以下代碼檢查用戶輸入是否為有限數：
```js
if(isFinite(ClientInput)){
    // code
}
```
#### #isNaN
isNaN 函式評估參數以確定它是否為 "NaN"（不是一個數字）。isNaN 的語法是：
```js
isNaN(testValue)
```
其中 testValue 是你想要評估的值。

#### #parseFloat 和 #parseInt 函式
兩個 "parse" 函式，parseFloat 和 parseInt，當傳遞一個字串作為參數時，它們會回傳一個數值。

parseFloat 的語法是：
```js
parseFloat(str);
```
其中 parseFloat 分析其參數，即字符串 str，並嘗試回傳一個浮點數。
如果遇到一個不是加號 (+) 或減號 (-)、數字 (0-9)、小數點或指數的字符，則它會返回該字符之前的值，並忽略該字符和所有後續字符。如果第一個字符無法轉換為數字，則它返回 "NaN"（不是一個數字）。
parseInt 的語法是：
```js
parseInt(str [, radix]);
```
parseInt 分析其第一個參數，即字符串 str，並嘗試回傳指定基數（進制，基）的整數。
例如，十進制數使用基數 10，八進制數使用基數 8，十六進制數使用基數 16，等等。對於大於 10 的進制，字母表的字母表示大於 9 的數字。例如，對於十六進制數（基數 16），A 到 F 用於表示大於

其中 str 是要解析的字符串，而 radix 是可選參數，表示解析時使用的基數（進制）。radix 參數可以是介於 2 到 36 之間的整數值。如果省略 radix 或基數為 0，parseInt 會根據以下規則分析字符串 str：

- 如果字符串以 "0x" 或 "0X" 開頭，則基數被設定為 16（十六進制）。
- 如果字符串以 "0" 開頭且後跟非十六進制數字字符，則基數被設定為 8（八進制）。這是因為前置的 0 表示八進制數。
- 如果字符串以任何其他字符開頭，或者 radix 為 10，則基數被設定為 10（十進制）。
- 如果第一個字符無法轉換為數字，或者字符串是空的，parseInt 則返回 NaN。

以下是一些例子：
```js
parseInt("123") // => 123
parseInt("12.3") // => 12
parseInt("0x10") // => 16
parseInt("0xAF",16) // => 175（0xAF 在十進制中是 175）
parseInt("010") // => 8
```

#### #Number 和 #String 函式
#Number 和 #String 是 JavaScript 內置的函式，分別用於將其他資料類型轉換為數字和字串。

Number函式可以將其他資料類型轉換為數字，String函式可以將其他資料類型轉換為字串。
它們的語法是：
```js
Number(value)
String(value)
```
其中 value 是你想要轉換的值。

這些函式的使用方式如下：
```js
Number("123") // => 123
Number("12.3") // => 12.3
Number(true) // => 1
Number(false) // => 0

String(123) // => "123"
String(12.3) // => "12.3"
String(true) // => "true"
String(false) // => "false"
```

#### #encodeURI #decodeURI #encodeURIComponent #decodeURIComponent

這些函式用於對網址或 URI 中的特殊字符進行編碼或解碼。
encodeURI 函式用於對整個 URI 进行編碼，但是它不會編碼以下字符：ASCII字母、數字、~!@#$&*()=:/,;?+'。
decodeURI 函式用於解碼 encodeURI 編碼的 URI。
encodeURIComponent 函式用於對 URI 中的個別組件進行編碼。它會對所有特殊字符進行編碼，包括對於 encodeURI 函式不進行編碼的字符。
decodeURIComponent 函式用於解碼 encodeURIComponent 編碼的 URI 組件。
這些函式的語法如下：

```js
encodeURI(uri)
decodeURI(uri)
encodeURIComponent(uriComponent)
decodeURIComponent(uriComponent)
```
其中 uri 或 uriComponent 是你想要編碼或解碼的 URI 或 URI 組件。

以下是一些例子：
```js
let url="https://www.example.com/my page.html"
let encodedUrl=encodeURI(url)
console.log(encodedUrl) // => "https://www.example.com/my%20page.html"

let decodedUrl=decodeURI(encodedUrl)
console.log(decodedUrl) // => "https://www.example.com/my page.html"

let query="name=John&age=30"
let encodedQuery=encodeURIComponent(query)
console.log(encodedQuery) // => "name%3DJohn%26age%3D30"

let decodedQuery=decodeURIComponent(encodedQuery)
console.log(decodedQuery) // => "name=John&age=30"
```
請注意，encodeURI 和 encodeURIComponent 函式是將URI組件編碼為安全的URI字符串的好方法，以防止URI中出現非法字符。
這在URL中傳遞參數時特別重要，以確保參數的值不會影響URL的解析。

## Chr11 #例外處理
在js種共有7+1種不同的例外情形分別為**Error**,**RangeError**,**ReferenceError**,**SyntaxError**,**TypeError**,**URIError**,~~**EvalError**~~+NaN

### #例外介紹
1. Error(一般錯誤)
Error 這個類型用來代表一般的錯誤情況，最常用在**客製化例外**情況。透過下面的指令可以產生一個錯誤物件的實例：
```js
let error=new Error("error message");
console.log(error)          // X: Error: error message
```
這個 Error 物件包含兩個屬性－name 和 message：
name: 用來說明錯誤的類型(這裡就是 Error)
message: 提供更多關於此例外情況的描述。

2. RangeError(範圍錯誤)
這是一個當**數值落在特定的區間外**時會拋出的錯誤
例如，透過 toFixed() 方法時，它可以接受介於 0 ~ 20 的參數來說明要顯示到小數後第幾位，當這個參數超過這個區間時，就會拋出 RangeError：
```js
let pi=3.14159;
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
if (false){    // X: SyntaxError: Unexpected token (3:0)
  // 缺少結束的大括號
```

5. TypeError(找不到函式)
這是一個如果某一**變項的型別和所期待的操作不同**時會拋出的錯誤，這經常發生在去呼叫執行一個不存在的函式時。
```js
// 由於 foo 當中並不包含 bar 這個函式，因此會拋出 TypeError 錯誤
let foo={};
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
你可以用以 #throw 陳述式丟出例外，並以 #try-catch 陳述式處理之。

#### #throw 陳述式
使用 #throw 陳述式拋出例外。當拋出例外時，你要指定包含在要拋出物件中的值:
您可以拋出任何運算式，而不僅僅是特定類型的運算式。以下的程式碼會拋出一些不同類型的例外：

```js
throw "Error2" // 字串形態
throw 42 // 數字形態
throw true // True/False
throw{
    toString: function (){
        return "我是物件!"
    },
}
```
備註： 您可以在拋出例外時指定物件。然後，可以在 catch 區塊中引用對象的屬性。
```js
// 創建類型爲 UserException 的物件
function UserException(message){
    this.message=message
    this.name="UserException"
}

// 讓例外轉換成整齊的字串當它被當作字串使用時
// （舉例來說:於 error console）
UserException.prototype.toString=function (){
    return this.name+': "' + this.message + '"'
}

// 創建一個物件的實例並丟出它
throw new UserException("Value too high")
```
#### #try-catch 陳述式
try-catch陳述式標記了一組要嘗試的陳述式，並在拋出例外時指定一個或多個響應。 如果例外被拋出，try-catch陳述式捕獲它。
try-catch陳述式包括一個try區塊它包含一個或多個陳述式，零個或多個 catch 區塊，包含在 try 區塊中拋出例外時該做什麼的陳述式。 也就是說，你希望try區塊成功，如果它不成功，你希望控制權傳遞給catch區塊。
如果try區塊內的任何陳述式拋出例外，則控制**立即切換到catch區塊**。如果在try區塊中沒有拋出例外，則**跳過catch區塊**。finally區塊在try和catch區塊執行完後執行，但在try-catch陳述式之後的陳述式之前執行。
以下的範例使用try-catch陳述式。該範例調用基於傳遞給函數的值並從陣列中檢索月份名稱的函數。如果值不對應於月份數（1-12），則會拋出一個例外，其值為 "InvalidMonthNo"，並且 catch 區塊中的陳述式將 monthName 變數設置為 unknown。
```js
function getMonthName(mo){
    mo=mo - 1 // Adjust month number for array index (1=Jan,12=Dec)
    let months=["Jan","Feb","Mar","Apr","May","Jun","Jul","Aug","Sep","Oct","Nov","Dec"]
    if (months[mo]){
        return months[mo]
    } else{
        throw "InvalidMonthNo" //throw 關鍵字在這裏被使用
    }
}

try{
    // statements to try
    monthName=getMonthName(myMonth) // 函式可以丟出例外
} catch (e){
    monthName="unknown"
    logMyErrors(e) // 將例外傳至例外處理機制
}
```
catch 區塊
你可以使用 catch 區塊來處理 try 區塊可能丟出的例外。
catch 區塊指定用來保存 throw 陳述式所丟出的值的標識符（前面語法中的 catchID） 您可以使用此標識符獲取有關被拋出的例外的信息。js在進入catch 區塊時創建此標識符 標識符僅持續 catch 區塊的持續時間；在 catch 區塊完成執行後，標識符不再可用。
例如，下列的程式碼中丟出了一個例外，當例外發生後，控制權被轉交給 catch 區塊。
```js
try{
    throw "myException" // 產生例外
} catch (e){
    // 用於處理例外的陳述式
    logMyErrors(e) // 將例外物件傳給 error handler
}
```
finally 區塊
finally 區塊中包含在 try 和 catch 區塊執行之後但在 try...catch 陳述式之後的陳述式之前 執行的陳述式。 無論是否拋出例外，finally 區塊都會執行。 如果拋出例外，則即使沒有 catch 區塊處理例外，finally 區塊中的陳述式也會執行。
您可以使用 finally 區塊來使腳本在發生例外時正常地結束。例如，您可能需要釋放腳本中綁定的資源。 在以下示例中，打開一個文件，然後執行使用該文件的陳述式（伺服器端js允許您訪問文件）。 如果在打開文件時拋出例外，finally 區塊會在腳本結束之前關閉文件。
```js
openMyFile()
try{
    writeMyFile(theData) // 可能產生例外
} catch (e){
    handleError(e) // 處理可能發生的例外
} finally{
   closeMyFile() // 總是在 try 結束後關閉檔案
}
```
如果 finally 區塊有返回值，那麼該值將成為整個 try-catch-finally 過程的返回值，而捨棄 try 和 catch 區塊中的任何返回陳述式：
```js
function f(){
    try{
        console.log(0)
        throw "bogus"
    } catch (e){
        console.log(1)
        return true // 這個回傳會被擱置
        // 直到 finally 區塊結束
        console.log(2) // 不會到達這裏
    } finally{
        console.log(3)
        return false // 覆寫先前的 "return"
        console.log(4) // 不會到達這裏
    }
    // "return false" 在這裏被執行
    console.log(5) // 不會到達這裏
}
f() // console 0,1,3 會回傳false
```
finally 區塊覆寫返回值也適用於在 catch 區塊中拋出或重新拋出的例外（即便在catch 中再次丟出例外，catch 所屬的 finally 區塊還是會被執行）：
```js
function f(){
    try{
        throw "bogus"
    } catch (e){
        console.log("caught inner 'bogus'")
        throw e // 此處的 throw 陳述式將被擱置到
        // finally 區塊結束
    } finally{
        return false // 覆寫先前的"throw"
    }
    // "return false" 在此被執行
}

try{
    f()
} catch (e){
    // 這裏永遠不可能到達因為在 f 函式中 catch 的 throw
    // 被 finally 中的 return 覆寫了
    console.log("caught outer 'bogus'")
}

// 輸出 -> caught inner "bogus"
```
巢狀 #try-catch 陳述式
你可以使用一個或多個的 #try-catch 陳述式。 假如一個內層的#try-catch 陳述式不具有 catch 區塊， 它將必須要有 finally 區塊與及封閉的 #try-catch 陳述式來檢測是否有符合的例外。

使用 Error 物件
根據錯誤的類型，您可以使用 "name" 和 "message" 屬性來獲取更精確的資訊。"name" 提供了錯誤所屬的類別（class）（例如，"DOMException" 或 "Error"），而 "message" 通常提供藉由將錯誤物件轉換為字串所獲得的更簡潔的資訊。參見巢狀 try 區塊位於 #try-catch 參考資料頁面。

假如您要丟出自定義的例外，為了方便使用這些屬性（例如，如果你的 catch 區塊並不要區分你自己的例外和系統的），你可以使用 Error 構造子。舉例來說：
```js
function doSomethingErrorProne (){
    if (ourCodeMakesAMistake()){
        throw (new Error("The message"))
    } else{
        doSomethingToGetAJavascriptError()
    }
}

try{
    doSomethingErrorProne()
}
catch (e){
    console.log(e.name) // 紀錄 'Error'
    console.log(e.message) // 紀錄 'The message' 或者其他js例外的資訊)
}
```

## Chr12 #DOM操作

## #註解及參見

### 參見
[while及do-while之差異](https://www.eztrust.com.tw/webdesign/C/94)
[運算式與運算子](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Guide/Expressions_and_operators#%E9%97%9C%E4%BF%82%E9%81%8B%E7%AE%97%E5%AD%90)
[ifelse](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Statements/if...else)
[switchcase](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Statements/switch)

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
    - [promiss](js/promiss.ms)
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

#關鍵保留字(keyword and reserved word) 一覽
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

小賀chris:) 2023/08/04 v1.3.0