# 網頁自創外掛

## 列表

- html
- css
  - #macosselection
  - #sort
- js
  - #macosselection
  - #sort
- php

## 外掛簡介

### js

#### #macosselection -> css&js bata 2.0.0
##### 簡介
因為原版的溢位條太醜就有了這個外掛

##### 使用方式
在要用的div上加上class macosselectiondiv
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
##### 下載地址及參考示例
[macossection download](http://hiiamchris.hopto.org/website/template/macossection/)


#### #sort -> css&js bata 1.2.0
##### 簡介
物件排序

##### 使用方式
在要用的div上加上class 任意
在要排序(被拖)的div上加上selector 任意
之後再js中傳入兩值  sort(在要用的div(不加selector),在要排序的div(要加selector))

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
    sort("div",".sort")
</script>
```
##### 下載地址及參考示例
[sortdiv download](http://hiiamchris.hopto.org/website/template/sort/)


## 註解及參見