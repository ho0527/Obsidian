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
    - #運算子優先級
- #述句
- #迴圈
  - #forloop
  - #while
  - #do-while
  - #forEach
  - #while及do-while之差異
- #物件
  - #陣列
- #函式
- #例外處理
  - #例外介紹
  - #處理例外
- #表單
- #註解及參見
  - #關鍵保留字 一覽

## Chr1 #介紹
js 可以用來做很多事例如:
1. 存取網頁內容(access content)
2. 調整網頁內容(modify content)
3. 計畫運作規則(porgram rules)
4. 回應網頁事件(react to events)
主要就是為了增加網頁的互動性而出現的程式語言

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

## Chr6 #運算式及運算子
### #運算式
運算式是一個任何一段可以取得一個值的程式碼。

任何合乎語法的運算式都能取得一個值，概念上， 有兩種不同型態的運算式: 有副作用的 (例如: 將一個值指定給一個變數) 以及只為了取得值而解析的運算式。
運算式 x = 7 是上述的第一種類型。這個使用 = 運算子的運算式會將數值 7 賦與給 x。 運算式本身也會被解析為 7。
運算式 3 + 4 是上述的第二種類型。這個運算式使用 + 運算子把 3 和 4 加起來，而不指定給任何變數。
JavaScript 運算式有下列幾種種類:
算術: 解析出數字， 例如 3.14159。（通常使用算術運算子。）
字串: 解析出字串， 例如 "Fred" or "234"。（通常使用字串運算子。）
邏輯: 解析出 True 或 False（通常與邏輯運算子相關。）
主流運算式: JavaScript 基本的關鍵字及運算式。
左側運算式: 左側是指定值的對象。

主流運算式
JavaScript 基本的關鍵字及運算式。

this
this 關鍵字 能取得當前所在物件。 一般而言， this 能取得呼叫處所在的物件。 你可以使用 點 或是 中括號 來取用該物件中的特性:
this['特性名稱']
this.特性名稱
以下定義一個叫做 validate 的函式，比較物件中特性 value 與傳入的兩變數:
```js
function validate(obj, lowval, hival) {
  if (obj.value < lowval || obj.value > hival) console.log("不可用的值!");
}
```
你可以在表單的 onChange event handler 中呼叫 validate 函式， 並以 this 來傳入表單的元素， 範例如下:
```html
<p>請輸入一介於18 與 99 的數字:</p>
<input type="text" name="age" size="3" onChange="validate(this, 18, 99);" />
```
分組運算子
分組運算子 ( ) 控制了運算子的優先順序。 例如，你可以覆寫先乘除，後加減的優先順序，使其變成先加減，後乘除。
```js
var a = 1;
var b = 2;
var c = 3;

// 預設運算級
a + b * c; // 7
// 預設的結果
a +
  (b * c)(
    // 7

    // 現在複寫運算級
    // 變成先進行加法，後乘法了
    a + b,
  ) *
    c; // 9

// 結果
a * c + b * c; // 9
```
解析
解析是 JavaScript 中的一個實驗性功能， 在未來版本的 ECMAScript 計畫被導入。有兩種不同類型的解析:

實驗性質 [for (x of y) x] (en-US)
陣列解析。

實驗性質 (for (x of y) y) (en-US)
產生器解析。

解析在許多程式語言中都存在，允許你快速地基於現存陣列產生新的陣列，例如:

JS
Copy to Clipboard

[for (i of [ 1, 2, 3 ]) i*i ];
// [ 1, 4, 9 ]

var abc = [ 'A', 'B', 'C' ];
[for (letters of abc) letters.toLowerCase()];
// [ 'a', 'b', 'c' ]
左側運算式
左側是指定值的對象。

new
你可以使用 new 運算子 來建立一個使用者自定義物件或內建物件的實例。 用法如下:

JS
Copy to Clipboard

var 物件名稱 = new 物件型態([參數1, 參數2, ..., 參數N]);
super
super 關鍵字用於呼叫物件的父物件中的函式。在使用類別來呼叫父類別的建構子時很實用，例如:

super([參數]); // 呼叫父物件的建構子.
super.父物件的函式([參數]);
展開運算子
展開運算子 (en-US)能將運算式展開於需要多個參數的地方（如函式呼叫）或是需要多個元素（如陣列字串常數）的地方。

範例：現在你想要用已存在的一個陣列做為新的一個陣列的一部份，當字串常數不再可用而你必須使用指令式編程，也就是使用，一連串的 push、splice、concat，等等。展開運算子能讓過程變得更加簡潔:

JS
Copy to Clipboard

var parts = ["肩膀", "膝蓋"];
var lyrics = ["頭", ...parts, "和", "腳趾"];
相同的，展開運算子也適用於函式呼叫:

JS
Copy to Clipboard

function f(x, y, z) {}
var args = [0, 1, 2];
f(...參數);

### #運算子
運算子是一個
js有以下幾種運算子分別為:**賦值運算子**,**比較運算子**,**算術運算子**,**位元運算子**,**邏輯運算子**,**字串運算子**,**條件（三元）運算子**,**逗點運算子**,**一元運算子**,**關係運算子**

#### #運算子規則
一個二元運算子需要具備兩個運算元， 一個在運算元之前，一個在運算元之後:
運算元1 運算子 運算元2
例如,3+4 或 x*y.

#### #賦值運算子
一個 #賦值運算子 將 基於其右方的運算元 的值賦予其 左方的運算元。 最簡單的 賦值運算子 是 等於 (=)， 它將賦予 左方運算元 與 右方運算元相同之值。 也就是， x = y 會把 y 的值賦予給 x。

也有一些復合的 #賦值運算子 是為了縮短下面表中的運算:

| 名稱 | 簡化的運算子 | 意義 |
| ----- | ----- | ----- |
| 賦值 | x = y | x = y |
| 加法賦值 | x += y | x = x + y |
| 減法賦值 | x -= y | x = x - y |
| 乘法賦值 | x *= y | x = x * y |
| 除法賦值 | x /= y | x = x / y |
| 餘數賦值 | x %= y | x = x % y |
| 指數賦值 | x **= y | x = x ** y |
| 左移賦值 | x <<= y | x = x << y |
| 右移賦值 | x >>= y | x = x >> y |
| 無號右移賦值 | x >>>= y | x = x >>> y |
| 位元 AND 賦值 | x &= y | x = x & y |
| 位元 XOR 賦值 | x ^= y | x = x ^ y |
| 位元 OR 賦值 | x |= y | x = x | y |

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
var var1=3
var var2=4
```
|運算子 | 描述 | 會回傳 True 的例子 |
| ----- | ----- | ----- |
|等於(==) | 假如運算元等價就回傳 True | 3==var1,"3"==var1,3=='3' |
|不等於(!=) | 假如運算元等價就回傳 True | var1!=4,var2!="3" |
|嚴格等於(===) | 假如運算元具有相同型態且等價則回傳 True參考 Object.is(en-US) 及 JS 中的等價性 | 3===var1 |
|嚴格不等於(!==) | 假如運算元具有相同型態但不等價，或是具有不同型態，回傳 True | var1!=="3",3!=='3' |
|大於(>) | 假如左方運算元大於右方運算元，回傳 True | var2>var1,"12">2 |
|大於或等於(>=) | 假如左方運算元大於或等於右方運算元，回傳 True | var2>=var1,var1>=3 |
|小於(<) | 假如左方運算元小於右方運算元，回傳 True | var1\<var2,"2"<12 |
|小於或等於(<=) | 假如左方運算元小於或等於右方運算元，回傳 True | var1\<=var2,var2<=5 |

#### #算術運算子
#算術運算子 以數值(文字或變數也可以)作為其運算元，並回傳單一數值。最常見的算術運算元是加法(+)，減法(-)，乘法(*)，及除法(/)在js中比較特別的是，在除數為0時Infinity。
範例:
```js
1 / 2; // =>0.5
1 / 2 == 1.0 / 2.0; // =>會是 true
```

js算術運算子列表:
| 運算子 | 描述 | 範例 |
| ----- | ----- | ----- |
| 取餘數 (+) | 二元運算子。加法。 | 12+5 回傳 17. |
| 取餘數 (-) | 二元運算子。減法。 | 12-5 回傳 7. |
| 取餘數 (\*) | 二元運算子。乘法。 | 12\*5 回傳 60. |
| 取餘數 (/) | 二元運算子。除法。 | 12/5 回傳 2.4. |
| 取餘數 (%) | 二元運算子。回傳兩個運算元相除後的餘數。 | 12 % 5 回傳 2. |
| 增加 (++) | 一元運算子。 將運算元增加 1。假如使用在運算元之前 (++x)，會運算元回傳增加 1 後的值;假如使用在運算元之後。 (x++)， 會回傳運算元加 1 前的值。 | 假如 x是 3，那 ++x 將把 x 設定為 4 並回傳 4，而 x++ 會回傳 3 ， 接著才把 x 設定為 4。 |
| 減少 (--) | 一元運算子。 將運算元減少 1。回傳值的情況與 增加運算元 相同。 | 假如 x是 3，那 --x 將把 x 設定為 2 並回傳 2，而 x-- 會回傳 3 ， 接著才把 x 設定為 2。 |
| (一元運算子)減號 (-) | 一元運算子。回傳運算元的負數。 | 假如 x 是 3，-x 回傳 -3。 |
| (一元運算子)加號 (+) | 一元運算子。嘗試將運算元轉換成數字，假如它還不是數字的話。 | +"3" 回傳 3。 +true 回傳 1. |
| 指數運算子(**) | 計算以 a 為底的 b 次方， 也就是,a^b | 2 ** 3 回傳 8. 10 ** -1 回傳 0.1. |

#### #位元運算子
#位元運算子 把運算元當作**32**位元的集合來看待(0和1)，而不是十進位，十六進位，或八進位。例如，十進位數字9以二進位表示就是1001。位元運算子將運算元以上述二進位的形式處理，但是回傳js中的數字類型值。

js位元運算子列表:
| 運算子 | 用法 | 描述 | 範例 |
| ----- | ----- | ----- | -----|
| 位元 AND | a & b | 回傳兩個運算元對於每個 bit 做 AND 的結果。 | |
| 位元 OR | a | b | 回傳兩個運算元對於每個 bit 做 OR 的結果。 | |
| 位元 XOR | a ^ b | 回傳兩個運算元對於每個 bit 做 XOR 的結果。 | |
| 位元 NOT | ~ a | 將運算元中的每個 bit 反轉(1->0,0->1)。 | |
| 左移 | a << b | 將 a 的每個 bit 向左移動 b 個 bits，空餘的位數以 0 填滿。 | |
| 有號右移 | a >> b | 將 a 的每個 bit 向右移動 b 個 bits，空餘位數以最高位補滿。 | |
| 以 0 填充的右移 | a >>> b | 將 a 的每個 bit 向右移動 b 個 bits，空餘的位數以 0 填滿。 | |

##### #位元邏輯運算子
概念上， #位元邏輯運算子 運作過程如下:

運算元被轉換為 32 bits 的整數以二進位形式表示 (0 和 1)。大於 32 bits 的數字將被捨棄多出來的位元。例如， 下列整數大於 32 個 bit 但是會被轉換為 32 個 bit 的整數:
轉換之前:  11100110111110100000000000000110000000000001
轉換之後:              10100000000000000110000000000001
第一個運算元中的每個 bit 分別對應到第二個運算元的每個 bit: 第一個 bit 對 第一個 bit,第二個 bit 對 第二個 bit， 以此類推。
運算子會對於 bit 進行運算， 結果也是基於 bit 來決定的。
例如， 9 的二元表示法是 1001， 15 的二元表示法是 1111。因此，在使用位元運算子的時候，結果如下:

| 運算式 | 結果 | 二元描述式 |
| ----- | ----- | ----- |
| 15 & 9 | 9 | 1111 & 1001 = 1001 |
| 15 | 9 | 15 | 1111 | 1001 = 1111 |
| 15 ^ 9 | 6 | 1111 ^ 1001 = 0110 |
| ~15 | -16 | ~ 0000 0000 … 0000 1111 = 1111 1111 … 1111 0000 |
| ~9 | -10 | ~ 0000 0000 … 0000 1001 = 1111 1111 … 1111 0110 |
注意，在使用 位元 NOT 運算子時， 所有的 32 個 bit 都被進行 NOT 了，包含最左邊用來描述正負數的位元(two's-complement representation)。

##### #位元移動運算子
#位元移動運算子 需要兩個運算元: 第一個是運算的目標，第二個是要移動的位元數。移動的方向取決於使用的運算子。
移動運算子會將運算元轉換成 32 bits 的整數，並且會回傳與左方運算元相同的型態。

移動運算子在下表被列出.
| 運算子 | 描述 | 範例 |
| ----- | ----- | ----- |
| 左移 (<<) | 這個運算子會將第 一個運算元的每個 bit 向左移動 第二個運算元所指定的 bit 數量。左邊超出的位數會被捨棄，右邊空出的位數以 0 補齊。 | 9<<2 得到 36，因為 1001 向左移動 2 bits 會得到 100100， 也就是二進位的 36。 |
| 有號右移 (>>) | 這個運算子會將第 一個運算元的每個 bit 向右移動 第二個運算元所指定的 bit 數量。右邊超出的位數會被捨棄，左邊空出的位數以最高位補齊。 | 9>>2 得到 2，因為 1001 向右移動 2 bits 會得到 10，也就是二進位的 2。 相同的， -9>>2 會得到 -3，因為最高位用來表示正負號的 bit 被保留了。 |
| 以 0 填充的右移 (>>>) | 這個運算子會將第 一個運算元的每個 bit 向右移動 第二個運算元所指定的 bit 數量。右邊超出的位數會被捨棄，左邊空出的位數以 0 補齊。 | 19>>>2 得到 4， 因為 10011 向右移動 2 bits 會得到 100，是二進位的 4。對於非負的數字而言， 以 0 填充的右移 會得到和 有號右移相同的結果。 |

#### #邏輯運算子
#邏輯運算子 通常被用於布林(邏輯)值; 使用於 布林(邏輯)值時， 它們會回傳布林型態的值。 然而，&& 和 || 運算子實際上是回傳兩指定運算元之一，因此用於非布林型態值時，它可能會回傳一個非布林型態的值。 邏輯運算子將在下表中被詳細解釋。

| Operator | Usage | Description |
| 邏輯 AND (&&) | 運算式1 && 運算式2 | 假如 運算式1 可以被轉換成 false 的話，回傳 運算式1; 否則，回傳 運算式2。 因此，&&只有在 兩個運算元都是 True 時才會回傳 True，否則回傳 false。 |
| 邏輯 OR (||) | 運算式1 || 運算式2 | 假如 運算式1 可以被轉換成 true 的話，回傳 運算式1; 否則，回傳 運算式2。 因此，||在 兩個運算元有任一個是 True 時就會回傳 True，否則回傳 false。 |
| 邏輯 NOT (!) | !運算式 | 假如單一個運算元能被轉換成 True 時，回傳false ， 不然回傳 true。 |

可以被轉換為 false 的運算式是 null、0、NaN、空字串（""），或 undefined。

```js
// &&（邏輯 AND）運算子的範例。
let a1 = true && true; // =>true
let a2 = true && false; // =>false
let a3 = false && true; // =>false
let a4 = false && 3 == 4; // =>false
let a5 = "Cat" && "Dog"; // =>Dog
let a6 = false && "Cat"; // =>false
let a7 = "Cat" && false; // =>false
```

```js
//  ||（邏輯 OR）運算子的範例。

let o1 = true || true; // =>true
let o2 = false || true; // =>true
let o3 = true || false; // =>true
let o4 = false || 3 == 4; // =>false
let o5 = "Cat" || "Dog"; // =>Cat
let o6 = false || "Cat"; // =>Cat
let o7 = "Cat" || false; // =>Cat
```

```js
// !（邏輯 NOT）運算子的範例。

let n1 = !true; // =>false
let n2 = !false; // =>true
let n3 = !"Cat"; // =>false
```

##### #短路解析
邏輯運算式是由左向右解析的， 他們會以下列規則嘗試進行 短路解析:
false && 任何東西 是 false 的短路解析。
true || 任何東西 是 true 的短路解析。
這些規則保證 解析總是正確的。 值得注意的地方是，剩餘部分的運算式並沒有被解析，所以不會占用任何效能。

#### #字串運算子
除了作為比較運算子之外， 運算子 (+) 也能用於字串，將兩字串接在一起，並回傳接在一起後的結果。

例如:

```js
console.log("我的 " + "字串"); // 會印出 字串 "我的字串"。
```

簡化的設定運算子 += 也能用於串接字串。

例如
```js
let mystring = "字";
mystring += "母"; // 得到 "字母" 並賦與給變數 mystring.
```

#### #條件運算子
#條件運算子 (又稱三元運算子、三元運算式等等)是js中唯一需要三個運算元的運算子。 這個運算子接受兩個運算元作為值且一個運算元作為條件。 語法是:
**條件 ? 值1 : 值2**
如果 條件 為 true，運算子回傳 值 1， 否則回傳 值 2。 你可以在任何使用標準運算子的地方改用 條件運算子。

例如
```js
var status = age >= 18 ? "成人" : "小孩";
```
這個陳述句會將 "成人" 賦與給變數 status 假如 age 大於等於 18。 否則，會將 "小孩" 賦與給變數 status。

#### #逗點運算子
#逗點運算子 (,) 作用是解析兩個運算元並回傳後面那個運算元的值。 這個運算子通常用於 for 迴圈內部，讓多個變數能在每次迴圈中被更新。

例如，假如 a 是一個有十個物件在裡面的二維陣列， 下面的程式中就使用了逗點運算子來同時更新兩個變數。 這段程式碼會印出陣列中所有對角線上的物件:
```js
for (var i = 0,j = 9; i <= j; i++,j--)
    console.log("a[" + i + "][" + j + "]= " + a[i][j]);
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
delete 物件名稱;
delete 物件名稱.性質;
delete 物件名稱[索引];
delete 性質; // 只有在 with 陳述句中可以使用
```
物件名稱 是物件的名稱， 性質 是物件中的一個特性， 索引 是用來表示物件在陣列中位置的一個整數。

第四種形式只有在 with 陳述句中可用， 用來刪除物件中的一個特性。

你可以用 delete 運算子來刪除隱式宣告的變數， 但不適用於使用 var 宣告的變數。

假如 delete 運算子使用成功， 它會將物件 或是 物件的特性設定為 未定義。 delete 運算子會在運算成功時回傳 true ，失敗時回傳 false 。
```js
x = 42;
var y = 43;
myobj = new Number();
myobj.h = 4; // 建立特性 h
delete x; // 回傳 true (只有在隱式宣告時能被刪除)
delete y; // 回傳 false (在使用 var 宣告時無法刪除)
delete Math.PI; // 回傳 false (不能刪除內建定義的特性)
delete myobj.h; // 回傳 true (可以刪除使用者自定義的特性)
delete myobj; // 回傳 true (在隱式宣告時可被刪除)
```
刪除陣列元素
在你刪除了陣列中的一個元素後， 陣列的長度並不會改變。 例如， 假如你刪除 a[3]， a[4] 依然是 a[4] 而 a[3] 為 未定義。

當使用 delete 運算子刪除陣列中的一個元素後， 那個元素便不再存在於陣列中了。 在下面的程式中， trees[3] 被用 delete 移除了。然而， trees[3] 的記憶體位址仍可用並且會回傳 未定義。
```js
var trees = ["redwood","bay","cedar","oak","maple"];
delete trees[3];
if (3 in trees) {
  // 不會執行到這裡
}
```
假如你希望給予陣列元素 未定義 的值， 你可以直接使用 undefined 關鍵字而不是使用 delete 運算子。 下列範例中， trees[3] 被指定了 undefined， 然而陣列元素依然存在:

```js
var trees = ["redwood","bay","cedar","oak","maple"];
trees[3] = undefined;
if (3 in trees) {
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
var myFun = new Function("5 + 2");
var shape = "round";
var size = 1;
var today = new Date();

// typeof 運算子會回傳下列結果:
typeof myFun; // 回傳 "function"
typeof shape; // 回傳 "string"
typeof size; // 回傳 "number"
typeof today; // 回傳 "object"
typeof doesntExist; // 回傳 "undefined"
// 對於 true 和 null關鍵字， typeof 運算子會回傳下列結果:
typeof true; // 回傳 "boolean"
typeof null; // 回傳 "object"

// 對於字串或數字， typeof 運算子會回傳下列結果:
typeof 62; // 回傳 "number"
typeof "Hello world"; // 回傳 "string"

// 對於特性，typeof 運算子會回傳 特性的值的類型:
typeof document.lastModified; // 回傳 "string"
typeof window.length; // 回傳 "number"
typeof Math.LN2; // 回傳 "number"

// 對於 方法 及 函式， typeof 運算子會回傳下列結果:
typeof blur; // 回傳 "function"
typeof eval; // 回傳 "function"
typeof parseInt; // 回傳 "function"
typeof shape.split; // 回傳 "function"

// 對於內建定義的物件， typeof 運算子會回傳下列結果:
typeof Date; // 回傳 "function"
typeof Function; // 回傳 "function"
typeof Math; // 回傳 "object"
typeof Option; // 回傳 "function"
typeof String; // 回傳 "function"
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
var trees = ["redwood","bay","cedar","oak","maple"];
0 in trees; // 回傳 true
3 in trees; // 回傳 true
6 in trees; // 回傳 false
"bay" in trees; // 回傳 false (你必須指定 索引，
// 而不是 索引所對應的元素)
"length" in trees; // 回傳 true (length 是陣列的性質之一)

// 內建物件
"PI" in Math; // 回傳 true
var myString = new String("coral");
"length" in myString; // 回傳 true

// 自訂義物件
var mycar = { make: "Honda",model: "Accord",year: 1998 };
"make" in mycar; // 回傳 true
"model" in mycar; // 回傳 true
instanceof
instanceof 運算子 在 指定物件 具有 指定的物件型態 時回傳 true。 語法是:
```
物件名稱 instanceof 物件類型
物件名稱 是用來與 物件類型 比較的物件的名字， 物件類型 是物件的類型， 例如 Date 或 Array。

當你需要在程式執行中確認物件的形態時，你可以使用 instanceof 運算子。 例如，當捕捉到例外時， 你可以依照例外的類型來決定用來處理意外的程式碼。

例如，下列程式碼使用 instanceof 來判斷變數 theDay 是不是 Date 類型的物件。 因為 theDay 是 Date 類型的物件， 所以 if 陳述中的陳述句會被執行。
```js
var theDay = new Date(1995,12,17);
if (theDay instanceof Date) {
  // 會被執行的陳述
}
```

#### #運算子優先級
運算子優先級決定運算子被使用於運算元的先後順序。 你也可以使用括號來強制指定優先級。

下列表格列出了運算子的優先級， 從高到低。

| 優先性 | 運算子名稱 | 相依 | 運算子 |
| ----- | ----- | ----- | ----- |
| 19 | Grouping | 無 | ( ) |
| 18 | Member Access | 從左至右 | . |
| 18 | Computed Member Access | 從左至右 | [] |
| 19 | new (with argument list) | 無 | new name() |
| 18 | 呼叫函式 | 從左至右 | function() |
| 18 | 可選串連（Optional chaining） | 從左至右 | ?. |
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
| 12 | 加減法 | 從左至右 | + - |
| 11 | 位元移動 | 從左至右 | << >> >>> |
| 10 | 關係運算子 | 從左至右 | < <= > >= in instanceof |
| 09 | 相等性 | 從左至右 | == != === !== |
| 08 | 位元AND | 從左至右 | & |
| 07 | 位元XOR | 從左至右 | ^ |
| 06 | 位元OR | 從左至右 | | |
| 05 | 邏輯AND | 從左至右 | && |
| 04 | 邏輯OR | 從左至右 | || |
| 04 | Nullish Coalescing | 從左至右 | ?? |
| 03 | 條件運算子 | 從右至左 | ?: |
| 02 | 指定運算子 | 從右至左 | = … += … -= … **= … *= … /= … %= … <<= … >>= … >>>= … &= … ^= … |= … &&= … ||= … ??= |
| 01 | 逗點運算子 | 從左至右 | , |

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
物件(object)



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

## Chr12 #表單

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

小賀chris:) 2023/06/22 v1.1.2