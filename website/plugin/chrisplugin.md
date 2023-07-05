# 網頁自創外掛

## 函式列表

- html
- css
  - #macossectiondiv(Bata 1.0.0)
    - .macossectiondiv
    - .macossectiondivx
    - .macossectiondivy
  - #sort(Bata 1.0.0)
    - divsortdragging
- js
  - #macosselection(Bata 1.0.0)
    - startmacossection()
  - #sort(Bata 1.0.0)
    - divsort()
  - #元件縮寫(Bata 1.0.0~Bata 1.0.3)
- php

## 外掛簡介

### js

#### #macosselection -> css&js

##### 簡介
因為原版的溢位條太醜就有了這個外掛

##### 使用方式
### 語法: startmacossection() // calling function
在要用的div上加上class macosselectiondiv(如果只要x要改成 macosselectiondivx 只要y要改成 macosselectiondivy(註: 另外一軸會被hidden))
寬高須自行用css設定

ex:
```html
<style>
    .div{
        width: 200px;
        height: 200px;
    }
</style>
<div class="div macosselectiondiv">
</div>
```

#### #divsort -> css&js
##### 簡介
物件排序

##### 使用方式
### 語法: divsort("*class no selector*","*selector*")
在要用的div上加上class 任意
在要排序(被拖)的div上加上selector 任意
之後再js中傳入兩值  divsort(在要用的div(不加selector),在要排序的div(要加selector))

ex:
```html
<style>
    .div{
        width: 600px;
        height: 700px;
    }
</style>
<div class="div">
    <div class="sort">
        test1
    </div>
    <div class="sort">
        test2
    </div>
    <div class="sort">
        test3
    </div>
    <div class="sort">
        test4
    </div>
</div>
<script>
    divsort("div",".sort")
</script>
```

#### #元件縮寫 -> js
##### 列表
| 元件 | 功用 | 用法 | 可用版本 | 註解 |
| ----- | ----- | ----- | ----- | ----- |
| docget | document.getElement... | ("*id|animation|class|name|tag|tagns|qtor|all*",*\[selector\]*) | Bata 1.0.0~ | |
| docgetid | document.getElementById | (*\[selector\]*) | Bata 1.0.0~ | |
| docgetall | document.querySelectorAll | (*\[selector\]*) | Bata 1.0.0~ | |
| conlog | consloe.log 值出來 | (*\[any\]*) | Bata 1.0.0~ | |
| isset | 看值是否存在 | (*\[var\]*) | Bata 1.0.0~ | |
| blank | 看值是否不為空 | (*\[var\]*) | Bata 1.0.0~ | |
| weblsset | \[localStorage\](../webstorage.md).setItem | (*\[string\]*,*\[any\]*) | Bata 1.0.0~ | |
| weblsget | \[localStorage\](../webstorage.md).getItem | (*\[string\]*) | Bata 1.0.0~ | |
| doccreate | document.createElement | (*\[element\]*) | Bata 1.0.4~ | |

## 註解及參見

簡寫一覽:
*\[time\]*: 時間
*\[number\]*: all number
*\[number-nn\]*: all number no negative
*\[string\]*: string
*\[array\]* \| array\[\]: array
*\[object\]* \| object\{\}: object
*\[any\]*: 任意值
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
*inf.*: infinite

##### 目前版本:Bata 1.0.3

小賀chris:) 2023/07/05 v1.0.1