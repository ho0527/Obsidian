# pymysql

## 介紹
讓python可以連接mysql資料庫


## 測試程式
### 請先安奘 pymysql (pip install pymysql)
```
import pymysql

# 資料庫連線設定(需使用自己的設定)
db=pymysql.connect(host="localhost",port=3306,user="root",passwd="",db="test",charset="utf8")

# 建立操作游標
query=db.cursor()

# 執行語法
query.execute("SELECT VERSION()")

# 選取第一筆結果
data=query.fetchone()

print("Database version:"+str(data))

# 關閉連線
db.close()
```

## 詳細介紹
INSERT:
```py
import pymysql
import datetime

now=datetime.datetime.now().strftime("%Y-%m-%d %H:%M:%S")

# 資料庫連線設定
db=pymysql.connect(host="localhost",port=3306,user="root",passwd="",db="test",charset="utf8")

# 建立操作游標
query=db.cursor()

#執行語法
try:
    # 要換成自己的資料庫語法
    query.execute("INSERT INTO `test`(`name`,`data`,`test1`,`test2`,`ps`)VALUES('123','234','345','666','"+str(now)+"')")
    # 提交修改
    db.commit()
    print("success")
except Exception as e:
    # 發生錯誤時停止執行SQL
    db.rollback()
    print("[ERROR]")

# 關閉連線
db.close()

# 輸出：success
```
update select delect 都一樣就不再重打
如果要使用fetch語法如下:
```py
query.fetchone() # 取得單條查詢結果
```

```py
query.fetchall() # 取得所有查詢筆數
```

```py
query.fetchmany(size=X) # 指定取回查詢筆數 (X為一數字)
```

## 註解及參見
