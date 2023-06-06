## 介紹

就畫畫


## 主功用

就畫畫


## 用法

###### 先拿到他的tag

```
let canva=document.getElementById("canva")
```


###### 也可以設定他的長寬
#### 注意: 不用打單位

```
canva.width=[width]
canva.height=[height]
```

###### 之後要用[getContext](getcontext.md)
大部分的操作都會用到getContext所以可以先存進一個變數中(接下來的說明會以ctx取代)

```
let ctx=canva.getContext("2d")
```

###### 基本畫直線

```
let canva=document.getElementById("canva")
let ctx=canva.getContext("2d")
let color="black" // 畫筆顏色
let isdrawing=false // 是否正在畫畫
let x1=0 // x軸 start
let y1=0 // y軸 start
let x2=0 // x軸 end
let y2=0 // y軸 end

function paintdown(event){
    ctx.strokeStyle=color // 畫筆顏色
    ctx.lineWidth=thick // 畫筆寬度
    x1=event.offsetX // 定義開始座標
    y1=event.offsetY // 定義開始座標
    ctx.lineCap="round" // 讓交接處為弧形
    ctx.lineJoin="round" // 讓交接處為弧形
    isdrawing=true
}

function paintmove(event){
    if(isdrawing){
        x2=event.offsetX // 定義結束座標
        y2=event.offsetY // 定義結束座標
        ctx.beginPath() // 開始畫畫
        ctx.moveTo(x1, y1) // 移動定位
        ctx.lineTo(x2, y2) // 畫畫
        ctx.stroke() // 停
        x1=x2 // 復原
        y1=y2 // 復原
    }
}

function paintup(e){
    if(isdrawing){
        isdrawing=false
    }
}

canva.addEventListener("pointerdown",paintdown)
canva.addEventListener("pointermove",paintmove)
canva.addEventListener("pointerup",paintup)

```

###### 基本油漆桶







```
let width=localStorage.getItem("width")
let height=localStorage.getItem("height")
let mod="select"
let canva=document.getElementById("canva")
let undohistory=[]
let redohistory=[]
let isdrawing=false
let x=0
let y=0
let ctx=canva.getContext("2d")
let color="black"
let paintstin=1

canva.width=width
canva.height=height
document.getElementById("undo").disabled=true
document.getElementById("redo").disabled=true



function undo(){
    if(undohistory.length==0){ return }

    redohistory.push(ctx.getImageData(0,0,canva.width,canva.height))
    ctx.putImageData(undohistory.pop(),0,0)
    if(undohistory.length==0){ document.getElementById("undo").disabled=true }
    else{ document.getElementById("undo").disabled=false }
}



function redo(){
    if(redohistory.length==0){ return }

    undohistory.push(ctx.getImageData(0,0,canva.width,canva.height))
    ctx.putImageData(redohistory.pop(),0,0)
    if(redohistory.length==0){ document.getElementById("redo").disabled=true }
    else{ document.getElementById("redo").disabled=false }

}



function save(){
    // TODO: Implement save functionality
}



function savesample(){
    // TODO: Implement savesample functionality
}



function upload(){
    // TODO: Implement upload functionality
}



function drawline(context,strokeStyle,lineWidth,x0,y0,x1,y1){
    context.beginPath()
    context.strokeStyle=strokeStyle
    context.lineWidth=lineWidth
    context.moveTo(x0,y0)
    context.lineTo(x1,y1)
    context.stroke()
}



function paintdown(event){
    undohistory.push(ctx.getImageData(0,0,canva.width,canva.height))
    redohistory.length=0
    document.getElementById("redo").disabled=true
    document.getElementById("undo").disabled=false
    x=event.offsetX
    y=event.offsetY
    isdrawing=true
}



function paintmove(event){
    if(isdrawing){
        drawline(ctx,color,1,x,y,event.offsetX,event.offsetY)
        x=event.offsetX
        y=event.offsetY
    }
}



function paintup(event){
    if(isdrawing){
        drawline(ctx,color,1,x,y,event.offsetX,event.offsetY)
        x=0
        y=0
        isdrawing=false
    }
}



function removealllistener(){
    canva.removeEventListener("pointerdown",paintdown)
    canva.removeEventListener("pointermove",paintmove)
    canva.removeEventListener("pointerup",paintup)
}



document.getElementById("new").onclick=function(){ if(confirm("是否裡開編輯頁面?")){ location.href="index.html" } }

document.getElementById("undo").onclick=function(){ undo() }
document.getElementById("redo").onclick=function(){ redo() }
document.getElementById("save").onclick=function(){ save() }
document.getElementById("savesample").onclick=function(){ savesample() }
document.getElementById("upload").onclick=function(){ upload() }
document.getElementById("black").style.borderColor="yellow"

document.getElementById("canva").addEventListener("keydown",function(event){
    if(event.ctrlKey&&event.key=="Z"){ undo() }
    if(event.ctrlKey&&event.shiftKey&&event.key=="Z"){ redo() }

})



document.querySelectorAll(".button").forEach(function(event){
    event.onclick=function(){
        mod=event.id
        document.querySelectorAll(".button").forEach(function(event){
            if(event.id==mod){ event.classList.add("selectbutton") }
            else{ event.classList.remove("selectbutton") }
        })

        if(mod=="paint"){
            removealllistener()
            canva.addEventListener("pointerdown",paintdown)
            canva.addEventListener("pointermove",paintmove)
            canva.addEventListener("pointerup",paintup)
        }else{
            removealllistener()
        }

    }
   
    if(event.id==mod){ event.classList.add("selectbutton") }
    else{ event.classList.remove("selectbutton") }
})



document.querySelectorAll(".color").forEach(function(event){
    event.style.width=getComputedStyle(event).getPropertyValue("height")
    event.style.backgroundColor=event.id
    event.onclick=function(){
        document.querySelectorAll(".color").forEach(function(event2){
            event2.style.borderColor="black"
        })
        this.style.borderColor="yellow"
        color=this.id
    }
})



document.getElementById("rainbow").onclick=function(){



}
```