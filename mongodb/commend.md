# 基本指令

## 目錄
- [基本指令](#基本指令)
	- [目錄](#目錄)
	- [指令](#指令)
	- [註解及參見](#註解及參見)
		- [註解](#註解)
			- [\[註1\]指令變數表](#註1指令變數表)
		- [參見](#參見)

## 指令
| 指令 | 作用 | ps |
| --- | --- | --- |
| cls | 清除命令行資料 | 終端機 |
| show dbs(/databases) | 顯示所有資料庫 | |
| use {database name} | 切換到指定的資料庫 | |
| db.{collection name}.insertOne({ {data} }) | 新增一筆資料至集合 | |
| db.{collection name}.insertMany({ {data}, {data}, ...inf }) | 新增一筆資料至集合 | |
| db.{collection name}.find(?({ {query} })) | 查詢集合中的所有資料或根據查詢條件查詢資料 | 條件可空 |
| db.{collection name}.find().limit({return max count<int>}) | 查詢集合中的資料並限制返回筆數 | |
| db.{collection name}.find().skip({skip count<int>}) | 查詢集合中的資料並跳過指定筆數 | |
| db.{collection name}.find().sort({ {sortkey}: {sortorder}, {sortkey}: {sortorder}, ...inf}) | 查詢集合中的資料並排序 | |

## 註解及參見

### 註解

1. request為請求之url method header等
   1. API request的排列方式為 APIurl method header
2. request body為請求正文(正常是json傳值)
3. response為回傳正文
   1. response 之排列方式為 回應碼 / 意義(成功將略過意義)
   2. "..."表示延伸
      1. inf表無限
4. date的表示法
   1. Y: 4位數的年份
   2. m: 2位數的月份
   3. d: 2位數的日期
   4. H: 2位數的小時(24小時制)
   5. i: 2位數的分鐘
   6. s: 2位數的秒鐘
5. ?表可選項

#### \[註1]指令變數表
| 變數 | 描述 | ps |
| --- | --- | --- |
| {database name} | 資料庫名稱 | |
| {collection name} | 集合名稱 | |
| {data} | 資料 | |
| {query} | 查詢條件 | |
| {return max count} | 限制返回筆數 | |
| {skip count} | 跳過指定筆數 | |
| {sortkey} | 排序依據的欄位 | |
| {sortorder} | 排序方式 | \[1(升冪排序),-1(降冪排序)] |

### 參見


*v001000000 / 2024-07-01*