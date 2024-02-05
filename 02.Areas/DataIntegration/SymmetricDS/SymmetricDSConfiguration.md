---
title: SymmetricDS Configuration
description: 
published: true
date: 2023-06-19T05:55:44.710Z
tags: symmetricds
editor: markdown
dateCreated: 2023-06-17T01:24:54.414Z
---

# SymmetricDS Configuration

# 組態
- 初始化系統表資料：進行組態( Configuration )設定
- 組態 ( Configuring )  SymmetricDS 是設定同步方法的過程
- 參閱官網 [組態設定文件](https://www.symmetricds.org/doc/3.14/html/user-guide.html#_configuration)
- 範例組態設定紀錄在 `insert_sample.sql` 中，以下進行拆解說明

## Init
- 匯入範例資料

```sql
------------------------------------------------------------------------------
-- Sample Data 
-- 匯入範例資料
------------------------------------------------------------------------------

-- Items to sell and their prices
insert into item (item_id, name) values (11000001, 'Yummy Gum');
insert into item_selling_price (item_id, store_id, price, cost) values (11000001, '001',0.20, 0.10);
insert into item_selling_price (item_id, store_id, price, cost) values (11000001, '002',0.30, 0.20);

-- Sales transactions and line items
insert into sale_transaction (tran_id, store_id, workstation, day, seq) 
values (900, '001', '3', '2012-12-01', 90);
insert into sale_return_line_item (tran_id, item_id, price, quantity, returned_quantity)
values (900, 11000001, 0.20, 1, 0);
```

- 刪除系統表中的資料並匯入設定資料

```sql
------------------------------------------------------------------------------
-- Clear and load SymmetricDS Configuration
-- 刪除系統表中的資料並匯入設定資料
------------------------------------------------------------------------------

delete from sym_trigger_router;
delete from sym_trigger;
delete from sym_router;
delete from sym_channel where channel_id in ('sale_transaction', 'item');
delete from sym_node_group_link;
delete from sym_node_group;
delete from sym_node_host;
delete from sym_node_identity;
delete from sym_node_security;
delete from sym_node;
```

## Node Groups
> `sym_node_group` **節點群組表**：設定節點群組
- `node_group_id` **節點群組編號**：唯一的節點群組識別值，PK，對應節點屬性檔案中(`.properties`)的 `group.id`
- `description` **描述**：節點群組的描述
- 此表在跑節點屬性檔案時會自動匯入資料，故不需要額外再 insert 資料，但可以 update 資料
```sql
------------------------------------------------------------------------------
-- Node Groups
-- sym_node_group 節點群組表：設定節點群組
------------------------------------------------------------------------------
-- node_group_id 節點群組編號：唯一的節點群組識別值，PK，對應節點屬性檔案中(.properties)的 `group.id`
-- description 描述：節點群組的描述
-- 此表在跑節點屬性檔案時會自動匯入資料，故不需要額外再 insert 資料，但可以 update 資料
------------------------------------------------------------------------------

--insert into sym_node_group (node_group_id, description) values ('corp', 'A corporate node');
--insert into sym_node_group (node_group_id, description) values ('store', 'A retail store node');
```

## Node
> `sym_node` **節點表**：設定節點
- `node_id` **節點編號**：唯一的節點識別值，PK
- `node_group_id` **節點群組編號**：`sym_node_group` 中的節點群組編號，對應節點屬性檔案中(`.properties`)的 `group.id`
- `external_id` **節點的外部編號**：對應節點屬性檔案中(`.properties`)的 `external.id`
- `sync_enabled` **節點的外部編號**：`1` 表示可同步
- 此表在跑節點屬性檔案時會自動匯入資料，故不需要額外再 insert 資料
```sql
------------------------------------------------------------------------------
-- Node
-- sym_node 節點表：設定節點
------------------------------------------------------------------------------
-- node_id 節點編號：唯一的節點識別值，PK
-- node_group_id 節點群組編號：sym_node_group 中的節點群組編號，對應節點屬性檔案中(.properties)的 group.id
-- external_id 節點的外部編號：對應節點屬性檔案中(.properties)的 external.id
-- sync_enabled 節點的外部編號：1 表示可同步
-- 此表在跑節點屬性檔案時會自動匯入資料，故不需要額外再 insert 資料
------------------------------------------------------------------------------

-- insert into sym_node (node_id, node_group_id, external_id, sync_enabled) values ('000', 'corp', '000', '1');
```

## Node Group Links
> `sym_node_group_link` **節點群組連接表**：設定各節點群組間的**資料同步模式**
- `source_node_group_id` **來源節點群組編號**：來源節點群組編號，PK + FK
- `target_node_group_id` **目標節點群組編號**：目標節點群組編號，PK + FK
- `data_event_action` **資料連接方式**：`P` 推送（push）/ `W` 等待拉取（wait for pull）
- `sync_config_enabled` **同步配置是否同步**：`1` 表示啟用，`0` 表示停用
```sql
------------------------------------------------------------------------------
-- Node Group Links
-- sym_node_group_link 節點群組連接表：設定各節點群組間的資料同步模式
------------------------------------------------------------------------------
-- source_node_group_id 來源節點群組編號：來源節點群組編號
-- target_node_group_id 目標節點群組編號：目標節點群組編號
-- data_event_action 資料連接方式：P 推送（push）/ W 等待拉取（wait for pull）
-- sync_config_enabled 同步配置是否啟用：1 表示啟用，0 表示停用
-- 此表在跑節點屬性檔案時會自動匯入資料，故不需要額外再 insert 資料
------------------------------------------------------------------------------

-- Corp sends changes to Store when Store pulls from Corp
-- 允許 store 從 corp 拉取資料
insert into sym_node_group_link (source_node_group_id, target_node_group_id, data_event_action) values ('corp', 'store', 'W');

-- Store sends changes to Corp when Store pushes to Corp
-- 允許 store 推送資料到 corp
insert into sym_node_group_link (source_node_group_id, target_node_group_id, data_event_action) values ('store', 'corp', 'P');
```

## Routers
> `sym_router` **資料路由表**：設定資料同步時資料的走向，即從哪個節點向哪個節點同步
- `router_id` **路由編號**：唯一的路由編號識別值，PK
- `source_node_group_id` **來源節點群組編號**：來源節點群組編號
- `target_node_group_id` **目標節點群組編號**：目標節點群組編號 
- `router_type` **路由類型**：
	- `default` **預設**：將所有捕獲的資料發送到屬於路由器中定義的目標節點組的所有節點的路由器
  - `column` **欄位**：將捕獲的資料行中的舊列值或新列值與常數值或目標節點的外部 ID 或節點 ID 的值進行比對的路由器，需設定條件在 `router_expression` 中
- `router_expression` 設定條件：設定條件
- `sync_on_update` 設定是否同步更新資料：`1` 表示啟用，`0` 表示停用
- `sync_on_insert` 設定是否同步新增資料：`1` 表示啟用，`0` 表示停用
- `sync_on_delete` 設定是否同步刪除資料：`1` 表示啟用，`0` 表示停用
- `create_time` **建立時間**：設定為當下時間 `current_timestamp`
- `last_update_time` **最後更新時間**：設定為當下時間 `current_timestamp`

```sql
------------------------------------------------------------------------------
-- Routers
-- sym_router 資料路由表：設定資料同步時資料的走向，即從哪個節點向哪個節點同步
------------------------------------------------------------------------------
-- router_id 路由編號：唯一的路由編號識別值
-- source_node_group_id 來源節點群組編號：來源節點群組編號
-- target_node_group_id 目標節點群組編號：目標節點群組編號
-- router_type 路由類型：
    -- default 預設：將所有捕獲的資料發送到屬於路由器中定義的目標節點組的所有節點的路由器
  -- column 欄位：將捕獲的資料行中的舊列值或新列值與常數值或目標節點的外部 ID 或節點 ID 的值進行比對的路由器，需設定條件在 router_expression 中
-- router_expression 設定條件：設定條件
-- sync_on_update 設定是否同步更新資料：1 表示啟用，0 表示停用
-- sync_on_insert 設定是否同步新增資料：1 表示啟用，0 表示停用
-- sync_on_delete 設定是否同步刪除資料：1 表示啟用，0 表示停用
-- create_time 建立時間：設定為當下時間 current_timestamp 
-- last_update_time 最後更新時間：設定為當下時間 current_timestamp
-- 此表在跑節點屬性檔案時會自動匯入資料，其實不需要額外再 insert 資料，但由於我們需要做額外設定，故自行 insert 資料
------------------------------------------------------------------------------

-- Default router sends all data from corp to store
-- 從 corp 同步所有資料到 store
insert into sym_router 
(router_id,source_node_group_id,target_node_group_id,router_type,create_time,last_update_time)
values('corp_2_store', 'corp', 'store', 'default',current_timestamp, current_timestamp);

-- Default router sends all data from store to corp
-- 從 store 同步所有資料到 corp
insert into sym_router 
(router_id,source_node_group_id,target_node_group_id,router_type,create_time,last_update_time)
values('store_2_corp', 'store', 'corp', 'default',current_timestamp, current_timestamp);

-- Column match router will subset data from corp to specific store
-- 從 corp 同步滿足條件的資料到 特定 store
insert into sym_router 
(router_id,source_node_group_id,target_node_group_id,router_type,router_expression,create_time,last_update_time)
values('corp_2_one_store', 'corp', 'store', 'column','STORE_ID=:EXTERNAL_ID or OLD_STORE_ID=:EXTERNAL_ID',current_timestamp, current_timestamp);
```

## Channels
> `sym_channel` **通道表**：設定哪些資料（表、檔案系統等）應該通過這些連接和路由器同步，有外部索引鍵關聯的表，一定要定義在同一通道中，才能進行關聯同步。
- `channel_id` **通道編號**：唯一的通道編號識別值，PK
- `processing_order` **通道處理順序數值**：`1` 表示升序處理
- `max_batch_size` **通道批次處理的最大資料事件數**：`100000`
- `enabled` **通道是否啟用**：`1` 表示啟用，`0` 表示停用
- `description` **通道描述**：通道描述

```sql
------------------------------------------------------------------------------
-- Channels
-- sym_channel 通道表：設定哪些資料（表、檔案系統等）應該通過這些連接和路由器同步，有外部索引鍵關聯的表，一定要定義在同一通道中，才能進行關聯同步。
------------------------------------------------------------------------------
-- channel_id 通道編號：唯一的通道編號識別值，PK
-- processing_order 通道處理順序數值：1 表示升序處理
-- max_batch_size 通道批次處理的最大資料事件數：100000
-- enabled 通道是否啟用：1 表示啟用，0 表示停用
-- description 通道描述：通道描述
------------------------------------------------------------------------------

-- Channel "sale_transaction" for tables related to sales and refunds
insert into sym_channel 
(channel_id, processing_order, max_batch_size, enabled, description)
values('sale_transaction', 1, 100000, 1, 'sale_transactional data from register and back office');

-- Channel "item" for tables related to items for purchase
insert into sym_channel 
(channel_id, processing_order, max_batch_size, enabled, description)
values('item', 1, 100000, 1, 'Item and pricing data');
```

## Triggers
> `sym_trigger` **觸發器表**：定義需要同步資料庫中的哪些表，注意有外部索引鍵關聯的表，通道值要相同
- `trigger_id` **觸發器編號**：唯一的觸發器編號識別值，PK
- `source_table_name` **來源資料表名稱**：來源資料表名稱
- `channel_id` **通道編號**：通道編號
- `sync_on_insert` **設定是否同步新增資料**：`1` 表示啟用，`0` 表示停用
- `sync_on_update` **設定是否同步更新資料**：`1` 表示啟用，`0` 表示停用 
- `sync_on_delete` **設定是否同步刪除資料**：`1` 表示啟用，`0` 表示停用 
- `last_update_time` **最後更新時間**：設定為當下時間 `current_timestamp`
- `create_time` **建立時間**：設定為當下時間 `current_timestamp`

```sql
------------------------------------------------------------------------------
-- Triggers
-- sym_trigger 觸發器表：定義需要同步資料庫中的哪些表，注意有外部索引鍵關聯的表，通道值要相同
------------------------------------------------------------------------------ 
-- trigger_id 觸發器編號：唯一的觸發器編號識別值
-- source_table_name 來源資料表名稱：來源資料表名稱
-- channel_id 通道編號：通道編號
-- sync_on_insert 設定是否同步新增資料：1 表示啟用，0 表示停用 
-- sync_on_update 設定是否同步更新資料：1 表示啟用，0 表示停用  
-- sync_on_delete 設定是否同步刪除資料：1 表示啟用，0 表示停用  
-- last_update_time 最後更新時間：設定為當下時間 current_timestamp
-- create_time 建立時間：設定為當下時間 current_timestamp
------------------------------------------------------------------------------

-- Triggers for tables on "item" channel
insert into sym_trigger 
(trigger_id,source_table_name,channel_id,last_update_time,create_time)
values('item_selling_price','item_selling_price','item',current_timestamp,current_timestamp);

insert into sym_trigger 
(trigger_id,source_table_name,channel_id,last_update_time,create_time)
values('item','item','item',current_timestamp,current_timestamp);

-- Triggers for tables on "sale_transaction" channel
insert into sym_trigger 
(trigger_id,source_table_name,channel_id,last_update_time,create_time)
values('sale_transaction','sale_transaction','sale_transaction',current_timestamp,current_timestamp);

insert into sym_trigger 
(trigger_id,source_table_name,channel_id,last_update_time,create_time)
values('sale_return_line_item','sale_return_line_item','sale_transaction',current_timestamp,current_timestamp);

-- Triggers with capture disabled, so they are used for initial load only
insert into sym_trigger 
(trigger_id,source_table_name,channel_id, sync_on_insert, sync_on_update, sync_on_delete,last_update_time,create_time)
values('sale_transaction_corp','sale_transaction','sale_transaction',0,0,0,current_timestamp,current_timestamp);

insert into sym_trigger 
(trigger_id,source_table_name,channel_id, sync_on_insert, sync_on_update, sync_on_delete,last_update_time,create_time)
values('sale_return_line_item_corp','sale_return_line_item','sale_transaction',0,0,0,current_timestamp,current_timestamp);
```

## Trigger Routers
> `sym_trigger_router` **觸發器路由表**：設定觸發時的資料流向，將觸發器對應到路由器
- `trigger_id` **觸發器編號**：唯一的觸發器編號識別值，PK + FK
- `router_id` **路由編號**：唯一的路由編號識別值，PK + FK
- `initial_load_order` **初始負載順序**：將初始負載發送到節點時此表的順序，如果多個表的這個值相同，則 SymmetricDS 將嘗試根據 FK 約束對錶進行排序
- `initial_load_select` **初始負載條件**：可選表達式，可用於減少在初始加載過程中從表中選擇的資料
- `last_update_time` **最後更新時間**：設定為當下時間 `current_timestamp`
- `create_time` **建立時間**：設定為當下時間 `current_timestamp`

```sql
------------------------------------------------------------------------------
-- Trigger Routers
-- sym_trigger_router 觸發器路由表：設定觸發時的資料流向，將觸發器對應到路由器
------------------------------------------------------------------------------ 
-- trigger_id 觸發器編號：唯一的觸發器編號識別值
-- router_id 路由編號：唯一的路由編號識別值
-- initial_load_order 初始負載順序：將初始負載發送到節點時此表的順序，如果多個表的這個值相同，則 SymmetricDS 將嘗試根據 FK 約束對錶進行排序
-- initial_load_select 初始負載條件：可選表達式，可用於減少在初始加載過程中從表中選擇的資料
-- last_update_time 最後更新時間：設定為當下時間 current_timestamp
-- create_time 建立時間：設定為當下時間 current_timestamp
------------------------------------------------------------------------------

-- Send all items to all stores
insert into sym_trigger_router
(trigger_id,router_id,initial_load_order,last_update_time,create_time)
values('item','corp_2_store', 100, current_timestamp, current_timestamp);

-- Send item prices to associated stores
insert into sym_trigger_router
(trigger_id,router_id,initial_load_order,initial_load_select,last_update_time,create_time)
values('item_selling_price','corp_2_one_store',100,'store_id=''$(externalId)''',current_timestamp,current_timestamp);

-- Send all sales transactions to corp
insert into sym_trigger_router
(trigger_id,router_id,initial_load_order,last_update_time,create_time)
values('sale_transaction','store_2_corp', 200, current_timestamp, current_timestamp);

insert into sym_trigger_router
(trigger_id,router_id,initial_load_order,last_update_time,create_time)
values('sale_return_line_item','store_2_corp', 200, current_timestamp, current_timestamp);

-- Send all sales transactions to store during initial load
insert into sym_trigger_router
(trigger_id,router_id,initial_load_order,last_update_time,create_time)
values('sale_transaction_corp','corp_2_store', 200, current_timestamp, current_timestamp);

insert into sym_trigger_router
(trigger_id,router_id,initial_load_order,last_update_time,create_time)
values('sale_return_line_item_corp','corp_2_store', 200, current_timestamp, current_timestamp);
```

# 統整組態檔案
```sql
-- config.sql
------------------------------------------------------------------------------
-- Clear and load SymmetricDS Configuration
-- 刪除系統表中的資料並匯入設定資料
------------------------------------------------------------------------------

delete from sym_trigger_router;
delete from sym_trigger;
delete from sym_router;
delete from sym_channel where channel_id in ('sale_transaction', 'item');
delete from sym_node_group_link;
delete from sym_node_group;
delete from sym_node_host;
delete from sym_node_identity;
delete from sym_node_security;
delete from sym_node;

------------------------------------------------------------------------------
-- Node Groups
-- sym_node_group 節點群組表：設定節點群組
------------------------------------------------------------------------------
-- node_group_id 節點群組編號：唯一的節點群組識別值，PK，對應節點屬性檔案中(.properties)的 `group.id`
-- description 描述：節點群組的描述
------------------------------------------------------------------------------

insert into sym_node_group (node_group_id, description) values ('corp', 'A corporate node');
insert into sym_node_group (node_group_id, description) values ('store', 'A retail store node');


------------------------------------------------------------------------------
-- Node
-- sym_node 節點表：設定節點
------------------------------------------------------------------------------
-- node_id 節點編號：唯一的節點識別值，PK
-- node_group_id 節點群組編號：sym_node_group 中的節點群組編號，對應節點屬性檔案中(.properties)的 group.id
-- external_id 節點的外部編號：對應節點屬性檔案中(.properties)的 external.id
-- sync_enabled 節點的外部編號：1 表示可同步
-- 此表在跑節點屬性檔案時會自動匯入資料，故不需要額外再 insert 資料
------------------------------------------------------------------------------
-- insert into sym_node (node_id, node_group_id, external_id, sync_enabled) values ('000', 'corp', '000', '1');


------------------------------------------------------------------------------
-- Node Group Links
-- sym_node_group_link 節點群組連接表：設定各節點群組間的資料同步模式
-- source_node_group_id 來源節點群組編號：來源節點群組編號
-- target_node_group_id 目標節點群組編號：目標節點群組編號
-- data_event_action 資料連接方式：P 推送（push）/ W 等待拉取（wait for pull）
------------------------------------------------------------------------------

-- Corp sends changes to Store when Store pulls from Corp
-- 允許 store 從 corp 拉取資料
insert into sym_node_group_link (source_node_group_id, target_node_group_id, data_event_action) values ('corp', 'store', 'W');

-- Store sends changes to Corp when Store pushes to Corp
-- 允許 store 推送資料到 corp
insert into sym_node_group_link (source_node_group_id, target_node_group_id, data_event_action) values ('store', 'corp', 'P');


------------------------------------------------------------------------------
-- Routers
-- sym_router 資料路由表：設定資料同步時資料的走向，即從哪個節點向哪個節點同步
------------------------------------------------------------------------------
-- router_id 路由編號：唯一的路由編號識別值
-- source_node_group_id 來源節點群組編號：來源節點群組編號
-- target_node_group_id 目標節點群組編號：目標節點群組編號
-- router_type 路由類型：
    -- default 預設：將所有捕獲的資料發送到屬於路由器中定義的目標節點組的所有節點的路由器
  -- column 欄位：將捕獲的資料行中的舊列值或新列值與常數值或目標節點的外部 ID 或節點 ID 的值進行比對的路由器，需設定條件在 router_expression 中
-- create_time 建立時間：設定為當下時間 current_timestamp
-- last_update_time 最後更新時間：設定為當下時間 current_timestamp
------------------------------------------------------------------------------

-- Default router sends all data from corp to store
-- 從 corp 同步所有資料到 store
insert into sym_router
(router_id,source_node_group_id,target_node_group_id,router_type,create_time,last_update_time)
values('corp_2_store', 'corp', 'store', 'default',current_timestamp, current_timestamp);

-- Default router sends all data from store to corp
-- 從 store 同步所有資料到 corp
insert into sym_router
(router_id,source_node_group_id,target_node_group_id,router_type,create_time,last_update_time)
values('store_2_corp', 'store', 'corp', 'default',current_timestamp, current_timestamp);

-- Column match router will subset data from corp to specific store
-- 從 corp 同步滿足條件的資料到 特定 store
insert into sym_router
(router_id,source_node_group_id,target_node_group_id,router_type,router_expression,create_time,last_update_time)
values('corp_2_one_store', 'corp', 'store', 'column','STORE_ID=:EXTERNAL_ID or OLD_STORE_ID=:EXTERNAL_ID',current_timestamp, current_timestamp);


------------------------------------------------------------------------------
-- Channels
-- sym_channel 通道表：設定哪些資料（表、檔案系統等）應該通過這些連接和路由器同步，有外部索引鍵關聯的表，一定要定義在同一通道中，才能進行關聯同步。
------------------------------------------------------------------------------
-- channel_id 通道編號：唯一的通道編號識別值，PK
-- processing_order 通道處理順序數值：1 表示升序處理
-- max_batch_size 通道批次處理的最大資料事件數：100000
-- enabled 通道是否啟用：1 表示啟用，0 表示停用
-- description 通道描述：通道描述
------------------------------------------------------------------------------

-- Channel "sale_transaction" for tables related to sales and refunds
insert into sym_channel
(channel_id, processing_order, max_batch_size, enabled, description)
values('sale_transaction', 1, 100000, 1, 'sale_transactional data from register and back office');

-- Channel "item" for tables related to items for purchase
insert into sym_channel
(channel_id, processing_order, max_batch_size, enabled, description)
values('item', 1, 100000, 1, 'Item and pricing data');

------------------------------------------------------------------------------
-- Triggers
-- sym_trigger 觸發器表：定義需要同步資料庫中的哪些表，注意有外部索引鍵關聯的表，通道值要相同
------------------------------------------------------------------------------
-- trigger_id 觸發器編號：唯一的觸發器編號識別值
-- source_table_name 來源資料表名稱：來源資料表名稱
-- channel_id 通道編號：通道編號
-- sync_on_insert 設定是否同步新增資料：1 表示啟用，0 表示啟用
-- sync_on_update 設定是否同步更新資料：1 表示啟用，0 表示啟用
-- sync_on_delete 設定是否同步刪除資料：1 表示啟用，0 表示啟用
-- last_update_time 最後更新時間：設定為當下時間 current_timestamp
-- create_time 建立時間：設定為當下時間 current_timestamp
------------------------------------------------------------------------------

-- Triggers for tables on "item" channel
insert into sym_trigger
(trigger_id,source_table_name,channel_id,last_update_time,create_time)
values('item_selling_price','item_selling_price','item',current_timestamp,current_timestamp);

insert into sym_trigger
(trigger_id,source_table_name,channel_id,last_update_time,create_time)
values('item','item','item',current_timestamp,current_timestamp);

-- Triggers for tables on "sale_transaction" channel
insert into sym_trigger
(trigger_id,source_table_name,channel_id,last_update_time,create_time)
values('sale_transaction','sale_transaction','sale_transaction',current_timestamp,current_timestamp);

insert into sym_trigger
(trigger_id,source_table_name,channel_id,last_update_time,create_time)
values('sale_return_line_item','sale_return_line_item','sale_transaction',current_timestamp,current_timestamp);

-- Triggers with capture disabled, so they are used for initial load only
insert into sym_trigger
(trigger_id,source_table_name,channel_id, sync_on_insert, sync_on_update, sync_on_delete,last_update_time,create_time)
values('sale_transaction_corp','sale_transaction','sale_transaction',0,0,0,current_timestamp,current_timestamp);

insert into sym_trigger
(trigger_id,source_table_name,channel_id, sync_on_insert, sync_on_update, sync_on_delete,last_update_time,create_time)
values('sale_return_line_item_corp','sale_return_line_item','sale_transaction',0,0,0,current_timestamp,current_timestamp);


------------------------------------------------------------------------------
-- Trigger Routers
-- sym_trigger_router 觸發器路由表：設定觸發時的資料流向，將觸發器對應到路由器
------------------------------------------------------------------------------
-- trigger_id 觸發器編號：唯一的觸發器編號識別值
-- router_id 路由編號：唯一的路由編號識別值
-- initial_load_order 初始負載順序：將初始負載發送到節點時此表的順序，如果多個表的這個值相同，則 SymmetricDS 將嘗試根據 FK 約束對錶進行排序
-- initial_load_select 初始負載條件：可選表達式，可用於減少在初始加載過程中從表中選擇的資料
-- last_update_time 最後更新時間：設定為當下時間 current_timestamp
-- create_time 建立時間：設定為當下時間 current_timestamp
------------------------------------------------------------------------------

-- Send all items to all stores
insert into sym_trigger_router
(trigger_id,router_id,initial_load_order,last_update_time,create_time)
values('item','corp_2_store', 100, current_timestamp, current_timestamp);

-- Send item prices to associated stores
insert into sym_trigger_router
(trigger_id,router_id,initial_load_order,initial_load_select,last_update_time,create_time)
values('item_selling_price','corp_2_one_store',100,'store_id=''$(externalId)''',current_timestamp,current_timestamp);

-- Send all sales transactions to corp
insert into sym_trigger_router
(trigger_id,router_id,initial_load_order,last_update_time,create_time)
values('sale_transaction','store_2_corp', 200, current_timestamp, current_timestamp);

insert into sym_trigger_router
(trigger_id,router_id,initial_load_order,last_update_time,create_time)
values('sale_return_line_item','store_2_corp', 200, current_timestamp, current_timestamp);

-- Send all sales transactions to store during initial load
insert into sym_trigger_router
(trigger_id,router_id,initial_load_order,last_update_time,create_time)
values('sale_transaction_corp','corp_2_store', 200, current_timestamp, current_timestamp);

insert into sym_trigger_router
(trigger_id,router_id,initial_load_order,last_update_time,create_time)
values('sale_return_line_item_corp','corp_2_store', 200, current_timestamp, current_timestamp);
```