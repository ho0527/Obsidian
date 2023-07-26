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
  - #lightbox(Bata 1.0.6)
    - lightboxmask
    - lightboxmain
- js
  - #macosselection(Bata 1.0.0)
    - startmacossection()
  - #sort(Bata 1.0.0)
    - divsort()
  - #lightbox(Bata 1.0.6)
    - lightbox()
  - #pagechanger(Bata 1.0.10)
    - pagechanger()
  - #元件縮寫(Bata 1.0.0~Bata 1.0.5)
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


#### #lightbox -> css&js
##### 簡介
燈箱效果

##### 使用方式
### 語法: lightbox(*\[element\]*,*\[element\]*,*\[string\]*,*\[element(id)\]*?=null,*\[boolean\]*?=true)
被點的按鈕元素加上id
燈箱id
燈箱要顯示的內文
是否使用esc關閉燈箱(預設為真)

**使用macosselection可以獲得更好的效果**

如果要換樣式此為lightbox樣式表看要怎麼改刪都可以
```css
.lightboxmask{
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.8);
    transform: translateY(-100%);
    transition: transform 0.3s ease-in-out;
    display: none;
    z-index: 999;
}

.lightboxmain{
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    background: rgb(214, 214, 214);
    color: black;
    padding: 20px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.3);
}
```

ex:
```html
<input type="button" class="navigationbarbutton" id="newform" value="新增問卷">
<div class="lightboxmask" id="lightbox"></div>
<!-- 記得一定要加 class="lightboxmask"! -->
<script>
    let html=`
        <form>
            問卷名稱: <input type="text" class="input" name="title" placeholder="問卷名稱"><br><br>
            問卷題數: <input type="text" class="input" name="count" placeholder="問卷題數"><br><br>
            問卷分頁題數: <input type="text" class="inputshort" name="pagelen" placeholder="分頁題數">
            <input type="button" class="button" onclick="location.reload()" value="取消">
            <input type="submit" class="button" name="submit" value="確定">
        </form>
    `

    lightbox("#newform","lightbox",function(){
        return html
    })
</script>
```

如果想要用該funciton的event可以這樣做(按鈕的event)
```html
<input type="button" class="navigationbarbutton" id="newform" value="新增問卷">
<div class="lightboxmask" id="lightbox"></div>
<!-- 記得一定要加 class="lightboxmask"! -->
<script>
    let html=`
        <form>
            問卷名稱: <input type="text" class="input" name="title" placeholder="問卷名稱"><br><br>
            問卷題數: <input type="text" class="input" name="count" placeholder="問卷題數"><br><br>
            問卷分頁題數: <input type="text" class="inputshort" name="pagelen" placeholder="分頁題數">
            <input type="button" class="button" onclick="location.reload()" value="取消">
            <input type="submit" class="button" name="submit" value="確定">
        </form>
    `

    lightbox("#newform","lightbox",function(event){
        return `
            <h1>${event.value}</h1>
            <form>
                問卷名稱: <input type="text" class="input" name="title" placeholder="問卷名稱"><br><br>
                問卷題數: <input type="text" class="input" name="count" placeholder="問卷題數"><br><br>
                問卷分頁題數: <input type="text" class="inputshort" name="pagelen" placeholder="分頁題數">
                <input type="button" class="button" onclick="location.reload()" value="取消">
                <input type="submit" class="button" name="submit" value="確定">
            </form>
        `
    })
</script>
```

#### #pagechanger -> js (Bata 1.0.12~)
##### 簡介
換頁效果

##### 使用方式
### 語法: pagechanger(*\[array(data)\]*,*\[number(item per page)\]*,*\[string("first"|"prev"|"next"|"end")\]*,*\[function\]*)
回呼函式會帶data[i]個值
ex:
```js
let data=[["a1","a2","a3","a4"],["a5","a6","a7","a8"],["a9","a10","a11","a12"],["a9","a10","a11","a12"],["a9","a10","a11","a12"]]
pagechanger(data,4,"first",function(event){
    console.log(event[0])
    console.log(event[1])
    console.log(event[2])
    console.log(event[3])
    /* =>
    a1
    a2
    a3
    a4
    a5
    a6
    a7
    a8
    a9
    a10
    a11
    a12
    a9
    a10
    a11
    a12
    */
});
```

#### #元件縮寫 -> js
##### 列表
| 元件 | 功用 | 用法 | 可用版本 | 註解 |
| ----- | ----- | ----- | ----- | ----- |
| docget | document.getElement... | ("*id \| animation \| class \| name \| tag \| tagns \| qtor \| all*",*\[selector\]*) | Bata 1.0.0~ | |
| docgetid | document.getElementById | (*\[selector\]*) | Bata 1.0.0~ | |
| docgetall | document.querySelectorAll | (*\[selector\]*) | Bata 1.0.0~ | |
| ~~conlog~~ | consloe.log 值出來 | (*\[any\]*) | Bata 1.0.0~Bata 1.0.9 | 已被修改 |
| conlog | consloe.log 值出來 | (*\[string(要輸出的文本)\]*,*\[color(文字顏色)\]*,*\[font-size(文字大小)\]*,*\[font-weight(文字粗體)\]*) | Bata 1.0.9~ | |
| isset | 看值是否存在 | (*\[var\]*) | Bata 1.0.0~ | |
| blank | 看值是否不為空 | (*\[var\]*) | Bata 1.0.0~ | |
| weblsset | \[localStorage\](../webstorage.md).setItem | (*\[string\]*,*\[any\]*) | Bata 1.0.0~ | |
| weblsget | \[localStorage\](../webstorage.md).getItem | (*\[string\]*) | Bata 1.0.0~ | |
| doccreate | document.createElement | (*\[element\]*) | Bata 1.0.4~ | |
| newajax | 快捷創建ajax | (*\[method\]*,*\[url\]*,*\[string\]*?=null) | Bata 1.0.5~ | |
| docappendchild | document.getElement....appendChlid() | (*\[element\]*,*\[element\]*) | Bata 1.0.7~ | |
| regexpmatch | 正規表達式確定文本 | (*\[string(要檢測的文本)\]*,*\[regexp\]*,*\[string(特殊全域語法)\]*) | Bata 1.0.8~ | |
| regexpchange | 正規表達式換文本 | (*\[string(要檢測的文本)\]*,*\[any(交換成?)\]*,*\[regexp\]*,*\[string(特殊全域語法)\]*) | Bata 1.0.8~ | |
| ajaxdata | new FormData.append(key,data) | (*\[array(key,text)\]*) | Bata 1.0.10~ | |

## 註解及參見

[簡寫一覽](../../abbreviationslist.md)

##### 目前版本:Bata 1.0.14

小賀chris:) 2023/07/05 v1.0.3