---
created: 2024-02-05T14:13
updated: 2024-02-05T21:14
title: SymmetricDSInstall
description: 
author: mandy
aliases: 
category: 
tags:
  - symmetricds
AutoNoteMover: disable
disabled rules:
  - all
template-output: 030-Inbox
template-input: title,body
template-replacement: "[[learning-template]]"
template-should-replace: sometimes
template-should-create: open-pane
published: false
---
# 🚀 SymmetricDS Install

- [ ] [symmetricds](https://www.symmetricds.org/)
- [ ] [Running as a Service](https://www.symmetricds.org/doc/3.14/html/user-guide.html#_running_as_a_service)
- [ ] [SymmetricDS 3.14 Tutorials](https://www.symmetricds.org/doc/3.14/html/tutorials.html)
- [ ] [異質資料庫同步方案-SymmetricDS](http://kenny-on-rails.blogspot.com/2015/05/symmetricds_28.html)

# 安裝方法
- 安裝共有三種方法，本文件以**獨立安裝**進行實作

## 獨立安裝 ( Standalone Installation )
- SymmetricDS 使用內置 Jetty Web 服務器作為獨立進程安裝和運行。這是安裝實例的最簡單和推薦的方法。
## Web 存檔 ( Web Archive (WAR) )
- 一個 SymmetricDS web 存檔 (WAR) 檔案被部署到一個現有的 web 應用程序容器中，該容器是單獨安裝、維護和運行的。
## 嵌入式 ( Embedded )
- SymmetricDS 嵌入到現有應用程序中。在這個選項中，編寫了一個自定義包裝程序，它調用 SymmetricDS API 來同步數據。
  
# 獨立安裝
## 安裝步驟
- 到 [官網](https://www.symmetricds.org/download) 下載安裝壓縮檔 `symmetric-server-3.14.7.zip`
- SymmetricDS 透過**解壓縮**到安裝位置來進行安裝
- 本機路徑：`D:\mandy\Project\symmetricds\example`
- 將壓縮檔(.zip)放置到本機路徑 ➔ 解壓縮至此 ➔ 將資料夾`symmetric-server-3.14.7` 中所有檔案移到 `example` 資料夾中 ➔ 刪除資料夾 `symmetric-server-3.14.7` 及解壓縮(.zip)

## 範例配置
- 實際案例說明請參閱文件 [SymmetricDS 3.14 Tutorials](https://www.symmetricds.org/doc/3.14/html/tutorials.html)

- `samples` 資料夾為實作以下案例的配置，為一個範例
- 將安裝三個節點，代表三個嵌入式數據庫。一個節點將代表一個中央企業數據庫，另外兩個節點將代表兩個單獨的零售店數據庫。
	- Corp 000：根節點
  - Store 001：第一子節點
  - Store 002：第二子節點 

![gh](https://raw.githubusercontent.com/singyichen/images/main/images/symmetricds-use-case-demo.png)

## 資料夾結構

```
│  change-log-txt                    
│
├─bin                               # 安裝執行檔資料夾
│     sym_service                   ## 執行管理服務
│     symadmin                      ## 執行管理任務
│     sym                           ## 啟動引擎作為獨立的客戶端或服務器
│     setenv                        ## 設置環境變量和啟動引擎
│     jmx                           ## 提供一個命令列介面，以執行特定引擎的 JMX 方法
│     dbcompare                     ## 比對資料庫
│     dbexport                      ## 匯出資料庫
│     dbfill                        ## 使用隨機生成的資料填充資料庫表格
│     dbimport                      ## 匯入資料庫
│     dbsql                         ## 連接資料庫，提供一個 sql shell，以便從命令與資料庫進行溝通
│
├─conf                              # 服務設定檔資料夾
│     sym_service.conf              ## 服務身份資訊檔案    
│     symmetric-server.properties   ## 服務 port 檔案
│  
├─samples                           # 範例服務的資料夾
│     corp-000.properties           ## 根節點資料庫連接資訊的屬性檔案
│     store-001.properties          ## 第一子節點資料庫連接資訊的屬性檔案
│     store-002.properties          ## 第二子節點資料庫連接資訊的屬性檔案
│     create_sample.xml             ## 要在根資料庫建立的資料表檔案
│     insert_sample.sql             ## 要在根資料庫建立的資料檔案及組態設定檔
│     mask-account-number.bsh
│     node-id-generator.bsh
│
├─engines                           # 自己服務的資料夾，預設為空資料夾
│
│
├─lib                               # 連接資料庫驅動程式 driver 資料夾
│     jtds-1.3.1.jar                ## 可連接 mssql
│     postgresql-42.5.1.jar         ## 可連接 postgresql
│
├─logs                              # 服務日誌資料夾，預設為空資料夾 
│     symmetric.log                 ## 服務執行詳細紀錄日誌檔案
│     wrapper.log                   ## 
│
├─patches
├─security
├─tmp
└─web                              
```

# 管理工具
- 參閱文件 [[SymmetricDSTool]]
# 啟用服務步驟
## 部屬啟用服務所需設定檔
- 將 `corp-000.properties`、`store-001.properties`、`store-002.properties` 複製到資料夾 `engines` 中
- 將 `create_sample.xml`、`insert_sample.sql` 複製到資料夾 `bin` 中

## 使用管理員身分開啟 PowerShell  執行
- 開始列表 ➔ `PowerShell 7(x64)` ➔ 右鍵選取 `Run as Administrator`

![gh](https://raw.githubusercontent.com/singyichen/images/main/images/PowerShell-Run-as-Administrator.png)


![PowerShell Run as Administrator.png](http://192.168.25.60:8000/files/file_storage/5808dc4c.png)

- 到安裝執行檔資料夾

```shell
cd D:\mandy\Project\symmetricds\example\bin
```
## 安裝服務
```shell
.\sym_service install
```
- 安裝成功
```
Installing SymmetricDS ...
Done
```

## 啟用服務
```shell
.\sym_service start
```
- 啟用成功
```
Waiting for server to start
......
Started
```
- 會在 SymmetricDS 系統表中寫入節點的基本資料

## 查看服務狀態
```shell
.\sym_service status
```
- 狀態
```
Installed: true
Running: true
Wrapper PID: 4452
Wrapper Running: true
Server PID: 38676
Server Running: true
```

## 資料庫初始化
- 在根資料庫中建立商品(`item`)、價格(`item_selling_price`)和銷售額(`sale_return_line_item`)的示例表

```shell
.\dbimport -e corp-000 --format XML --alter-case create_sample.xml
```
- 在根資料庫建立 SymmetricDS 系統表

```shell
.\symadmin -e corp-000 create-sym-tables
```
- 將 SymmetricDS 組態和示例數據加載到根資料庫中

```shell
.\dbimport -e corp-000 insert_sample.sql
```

- 建立成功之後會在根目錄多一個資料夾 `db`

## 啟動 SymmetricDS 實例
- 所有三個節點都在同一個實例中運行
```shell
.\sym
```

## 初始加載 Initial Load 
- 初始載入是從源節點中使用資料填充目標節點的表格的過程。
- 不同於捕獲資料，資料是使用 SQL 語句從源表格中選擇，然後流式傳輸到客戶端。
- 存儲節點預先組態為在註冊後進行初始加載。
```shell
.\symadmin -e corp-000 reload-node 001
```
```shell
.\symadmin -e corp-000 reload-node 002
```

# 同步服務的資料驗證
## 資料驗證方式
- 使用 `dbsql` 連接資料庫執行 sql 進行驗證
- 開啟三個 PowerShell 執行

![symmetricds use case dbsql.png](http://192.168.25.60:8000/files/file_storage/8d5f05d9.png)

- 連接資料庫 corp-000
```shell
.\dbsql -e corp-000
```
- 連接資料庫 store-001
```shell
.\dbsql -e store-001
```
- 連接資料庫 store-002
```shell
.\dbsql -e store-002
```

## 資料驗證項目
- 尋找從根同步到客戶端（即從公司到商店）的項目表：`item` 和 `item_selling_price`。

- 尋找從商店同步到公司的銷售表：`sale_transaction` 和 `sale_return_line_item`。

- 驗證 corp 項目表是否具有示例資料。

## 拉取資料 Pulling Data
- 更改中心辦公室 corp 節點資料庫中的項目資料（我們將新增一個新項目），並觀察資料被拉下到商店。
- 在 corp 中建立資料以供所有商店提取。

### 建立資料 Create Data
- 新增一個新的待售商品，在商店 001 和商店 002 的價格不同。
- 觀察兩個節點的日誌輸出以查看資料傳輸。store 組態為每分鐘將資料推送到 corp 節點。

```sql
// corp-000
insert into item (item_id, name) values (110000055, 'Soft Drink');
insert into item_selling_price (item_id, store_id, price)
        values (110000055, '001', 0.65);
insert into item_selling_price (item_id, store_id, price)
        values (110000055, '002', 1.00);
```

### 驗證傳出批次 Verify Outgoing Batches
- 查看已發送的批次（狀態OK）。
```sql
// corp-000
select * from sym_outgoing_batch order by batch_id desc;
```

### 驗證傳入批次 Verify Incoming Batches
- 查看批次是否已收到（狀態為OK）。
```sql
// store-001
select * from sym_outgoing_batch order by batch_id desc;
```
```sql
// store-002
select * from sym_outgoing_batch order by batch_id desc;
```

#### 驗證 SQL Verify SQL
- 直接在商店資料庫中驗證更改。
```sql
// store-001
select * from item_selling_price;
```
```sql
// store-002
select * from item_selling_price;
```

## 推送資料 Pushing Data
### 建立資料 Create Data
- 在商店中建立要推送到公司的資料。
- 將新的銷售新增到商店節點資料庫。
- 觀察兩個節點的日誌輸出以查看資料傳輸。store 組態為每分鐘將資料推送到 corp 節點。

```sql
// store-001
insert into sale_transaction (tran_id, store_id, workstation, day, seq)
        values (1000, '001', '3', '2014-03-21', 100);

insert into sale_return_line_item (tran_id, item_id, price, quantity)
        values (1000, 110000055, 0.65, 1);
```

### 驗證傳出批次 Verify Outgoing Batches
- 查看已發送的批次（狀態OK）。
```sql
// store-001
select * from sym_outgoing_batch order by batch_id desc;
```

### 驗證傳入批次 Verify Incoming Batches
- 查看批次是否已收到（狀態為OK）。
```sql
// corp-000
select * from sym_incoming_batch order by batch_id desc;
```

### 驗證 SQL Verify SQL
- 直接在 corp 資料庫中驗證更改。
```sql
// corp-000
select * from sale_transaction;
```
```sql
// corp-000
select * from sale_return_line_item;
```

# 節點屬性檔案 Node Properties File 
- 參閱文件 [SymmetricDS Node Properties File](/軟體開發/學習心得/11542/DataIntegration/SymmetricDS/SymmetricDSNodePropertiesFile)

# 組態 Configuration
- 參閱文件 [SymmetricDS Configuration](/軟體開發/學習心得/11542/DataIntegration/SymmetricDS/SymmetricDSConfiguration)


