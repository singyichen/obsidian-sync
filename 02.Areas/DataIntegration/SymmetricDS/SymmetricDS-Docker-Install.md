---
created: 2024-02-05T14:13
updated: 2024-02-06T08:26
title: SymmetricDSDockerInstall
description: 
author: mandy
aliases: 
category: 
tags:
  - docker
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
# 🚀 SymmetricDS Docker Install

- [ ] [jumpmind/symmetricds](https://hub.docker.com/r/jumpmind/symmetricds)

# 安裝方法
- 本文件使用 **Docker** 進行安裝
  
# Docker 安裝步驟
## 執行 container 
- 使用 git bash
- 預設 port 有兩個 31415 與 31417
- 各檔案會放在資料夾 `/opt/symmetric-ds` 底下，故可做 volumn 映射

```shell
docker run -d -p 31415:31415 -p 31417:31417 --name sym -v sym-engines:/opt/symmetric-ds/engines -v sym-conf:/opt/symmetric-ds/conf -v sym-security:/opt/symmetric-ds/security -v sym-bin:/opt/symmetric-ds/bin jumpmind/symmetricds
```

## 進入到 container 
```shell
winpty docker exec -it sym sh
```

## 回到根目錄
```shell
cd ..
```

## 到管理工具
```shell
cd opt/symmetric-ds/bin
```

# 啟用服務步驟
## 部屬啟用服務所需設定檔
- 將 `corp-000.properties`、`store-001.properties`、`store-002.properties` 複製到資料夾 `engines` 中

```shell
cp corp-000.properties store-001.properties store-002.properties /opt/symmetric-ds/engines
```

- 將 `create_sample.xml`、`insert_sample.sql` 複製到資料夾 `bin` 中
```shell
cp create_sample.xml insert_sample.sql /opt/symmetric-ds/bin
```

## 安裝服務
```shell
./sym_service install
```

## 啟用服務
```shell
./sym_service start
```
- 會在 SymmetricDS 系統表中寫入節點的基本資料

## 查看服務狀態
```shell
./sym_service status
```

## 資料庫初始化
- 在根資料庫中建立商品(`item`)、價格(`item_selling_price`)和銷售額(`sale_return_line_item`)的示例表

```shell
./dbimport -e corp-000 --format XML --alter-case create_sample.xml
```
- 在根資料庫建立 SymmetricDS 系統表

```shell
./symadmin -e corp-000 create-sym-tables
```
- 將 SymmetricDS 組態和示例數據加載到根資料庫中

```shell
./dbimport -e corp-000 insert_sample.sql
```

- 建立成功之後會在根目錄多一個資料夾 `db`

## 啟動 SymmetricDS 實例
- 所有三個節點都在同一個實例中運行
```shell
./sym
```

## 初始加載 Initial Load 
- 初始載入是從源節點中使用資料填充目標節點的表格的過程。
- 不同於捕獲資料，資料是使用 SQL 語句從源表格中選擇，然後流式傳輸到客戶端。
- 存儲節點預先組態為在註冊後進行初始加載。
```shell
./symadmin -e corp-000 reload-node 001
```
```shell
./symadmin -e corp-000 reload-node 002
```

# 同步服務的資料驗證
## 資料驗證方式
- 使用 `dbsql` 連接資料庫執行 sql 進行驗證
- 開啟三個 git bash 執行
- 連接資料庫 corp-000
```shell
./dbsql -e corp-000
```
- 連接資料庫 store-001
```shell
./dbsql -e store-001
```
- 連接資料庫 store-002
```shell
./dbsql -e store-002
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

