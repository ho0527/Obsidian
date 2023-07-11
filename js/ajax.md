
## 介紹

**AJAX**即「**Asynchronous JavaScript and XML**」(非同步的JavaScript and XML 技術),指的是一套綜合了多項技術的瀏覽器端網頁開發技術.


## 主程式架構(原生)

```

let ajax=new XMLHttpRequest()

ajax.onreadystatechange=function(){
    if(ajax.readyState==4){
        if(ajax.status==200){
	        // maincontext...
        }else{
            console.log("[ERROR] ajax error")
        }
    }
}

ajax.open("GET","apiindex.php",true) // method,url
ajax.send() // 送出請求

```


## 主功用

可以到另一檔案爬取資料後回傳到主程式去使用

## 註解及參見

[簡寫一覽](../abbreviationslist.md)