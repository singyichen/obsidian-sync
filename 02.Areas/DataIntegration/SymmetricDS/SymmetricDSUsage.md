---
title: SymmetricDS Usage
description: 
published: true
date: 2023-07-20T03:01:38.030Z
tags: symmetricds
editor: markdown
dateCreated: 2023-06-14T05:33:55.689Z
---

# SymmetricDS Usage
- [ ] [SymmetricDS 3.14 Tutorials](https://www.symmetricds.org/doc/3.14/html/tutorials.html#_install)
- [ ] [基於SymmetricDS的多主一從資料庫同步方案](https://www.cnblogs.com/killclock048/p/9817482.html)
- [ ] [[記事] MS SQL Server and MySQL replication - SymmetricDS](http://napmas.blogspot.com/2011/08/ms-sql-server-and-mysql-replication.html)
- [ ] [異質資料庫同步：SymmetricDS](https://sites.google.com/site/richchihlee/portal/eai/sym)
- [ ] [SymmetricDS SQL Server error while reading the database metadata](https://stackoverflow.com/questions/75664724/symmetricds-sql-server-error-while-reading-the-database-metadata)
- [ ] [合併多SQL檔案到單檔案](https://developer.aliyun.com/article/503445)
- [ ] [The growing pains of database architecture](https://www.figma.com/blog/how-figma-scaled-to-multiple-databases/#managing-migration)
- [ ] [SQL - DB 中，所有資料表的資料總筆數](https://blog.xuite.net/f8789/DCLoveEP/64839461)

# 使用原理
- 在 SymmetricDS 裡，一台 DB 要對應一個應用程式 SymmetricDS 執行同步的動作，需為每個應用程式寫好啟動的設定檔。
- 組態資料模型：對於各個伺服器，不管是主機還是從機，都需要組態 SymmetricDS 服務，用來監聽或執行動作等，並且是以節點代表伺服器來組態，至於觸發器更體現它的即時性，一方資料庫發生變化，首先被本機 SymmetricDS 服務監聽，同時向關聯的節點發起同步請求，關聯節點接收請求並做響應動作。
- 執行階段資料模型：當每個節點監聽到本機的資料事件(即資料變動)，會將變動的資料通過觸發器與關聯節點進行通迅。

# 架構：使用情境及相關設定

https://miro.com/app/board/uXjVPF_1HJ4=/?moveToWidget=3458764557142315227&cot=10

## SymmetricDS 安裝路徑
- 本機路徑：`D:\mandy\Project\symmetricds\mssql2postgres`
- 將壓縮檔放置到本機路徑 ➔ 解壓縮至此 ➔ 將 `symmetric-server-3.14.7` 中所有檔案移到 `mssql2postgres` 資料夾中 ➔ 刪除 `symmetric-server-3.14.7` 及解壓縮

## SymmetricDS 服務設定
- 設定檔路徑：`D:\mandy\Project\symmetricds\mssql2postgres\conf`
- 服務身份資訊檔案 `sym_service.conf`
	- wrapper.name=`SymmetricDS`
  - wrapper.displayname=`SymmetricDS`
- 服務 port 檔案 `symmetric-server.properties`
	- http.port=`31415`
  - https.port=`31417`

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
│     client-001.properties         ## 子節點資料庫連接資訊的屬性檔案 (使用 dbcompare 時所需)
│     server-000.properties         ## 根節點資料庫連接資訊的屬性檔案 (使用 dbcompare 時所需)
│     migration.sql                 ## 資料表的 schema (可使用 dbimport 執行)
│     config.sql                    ## 組態設定 (可使用 dbimport 執行)
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
├─engines                           # 自己服務的資料夾
│     client-001.properties         ## 子節點資料庫連接資訊的屬性檔案
│     server-000.properties         ## 根節點資料庫連接資訊的屬性檔案
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

## 目的資料
### 資料庫
- PostgreSQL
- IP：`192.168.25.59：5432`
### 資料庫名稱
- `A_SY004`	
### 節點：根節點
- 定義為：`server`
### server properties 設定
- 根節點資料庫連接資訊的屬性檔案：`server-000.properties`
```
// server-000.properties
engine.name=server-000
db.driver=org.postgresql.Driver
db.url=jdbc:postgresql://192.168.25.59:5432/A_SY004?stringtype=unspecified
db.user=11542
db.password=
# 留空白，因為為根服務器
registration.url= 
sync.url=http://localhost:31415/sync/server-000
group.id=server
external.id=000
job.purge.period.time.ms=7200000
job.routing.period.time.ms=5000
job.push.period.time.ms=10000
job.pull.period.time.ms=10000
auto.registration=true
initial.load.create.first=true
```
## 來源資料
### 資料庫
- SQL Server (MSSQL)
- IP：`192.168.25.21：1433`
### 資料庫名稱
- `Leader`：`A_SY004` 未持續更新的資料庫
### 節點：子節點
- 定義為：`client`
### client properties 設定
- 子節點資料庫連接資訊的屬性檔案：`client-001.properties`
- 在此連接資料庫的方式是使用 `jtds-1.3.1.jar`(壓縮檔案在資料夾 `lib` 中) ，需額外加入 `db.validation.query=Select 1` 的設定
```
// client-001.properties
engine.name=client-001
db.driver=net.sourceforge.jtds.jdbc.Driver
db.url=jdbc:jtds:sqlserver://192.168.25.21:1433/Leader;useCursors=true;bufferMaxMemory=10240;lobBuffer=5242880
db.user=sa
db.password=
db.validation.query=Select 1
registration.url=http://localhost:31415/sync/server-000
# 若有子服務器可設定如此，無子服務器可留空白
sync.url=http://localhost:31416/sync/client-001 
group.id=client
external.id=001
job.purge.period.time.ms=7200000
job.routing.period.time.ms=5000
# 設定每日 00:00:00 排程執行
job.push.cron=0 0 0 * * * 
job.pull.period.time.ms=10000
```

  
# 啟用服務步驟
## 到安裝執行檔資料夾
```shell
cd D:\mandy\Project\symmetricds\mssql2postgres\bin
```
## 安裝服務
```shell
.\sym_service install
```
## 啟用服務
```shell
.\sym_service start
```
- 啟用成功：會在 SymmetricDS 系統表中寫入節點的基本資料

## 查看服務狀態
```shell
.\sym_service status
```
## 啟動 SymmetricDS 實例
- 所有兩個節點都在同一個實例中運行
```shell
.\sym
```
## 初始加載 Initial Load
```
.\symadmin -e server-000 reload-node 001
```
## 測試是否成功連接資料庫
- 連接 PostgreSQL 測試
```shell
.\dbsql -e server-000
```
- 連接 PostgreSQL 成功
```
[] - ClientSymmetricEngine - Initializing connection to database
[] - JdbcDatabasePlatformFactory - Detected database 'postgres95', version '13', protocol 'postgresql'
[] - JdbcDatabasePlatformFactory - The IDatabasePlatform being used is org.jumpmind.db.platform.postgresql.PostgreSql95DatabasePlatform
```

- 連接 SQL Server 測試
```shell
.\dbsql -e client-001
```

- 連接 SQL Server 成功

```
[] - ClientSymmetricEngine - Initializing connection to database
[] - JdbcDatabasePlatformFactory - Detected database 'Microsoft SQL Server', version '10', protocol 'jtds'
[] - JdbcDatabasePlatformFactory - The IDatabasePlatform being used is org.jumpmind.db.platform.mssql.MsSql2008DatabasePlatform
```  


# 同步 server 與 client 的資料表
## 匯出 client 資料庫的 schema
- 建立一個資料夾 `migration` 放置產出的 SQL 檔案
- `--compatible`：postgres，表示輸出 postgres 型態的 schema
- `--no-data`：不匯出插入資料的語句
- `--dir`：匯出檔案的目錄，此處設定為 `D:\mandy\Project\symmetricds\mssql2postgres\migration`
- 產製不含 drop table sql
```shell
.\dbexport -e client-001 --compatible postgres --no-data --dir D:\mandy\Project\symmetricds\mssql2postgres\migration
```

- 產製含 drop table sql
```shell
.\dbexport -e client-001 --compatible postgres --no-data --add-drop-table --dir D:\mandy\Project\symmetricds\mssql2postgres\migration
```

- 並將 SQL 檔案整理如下資料夾分層結構
```
\\ migration                  
│
├─other                            # 其他 
│   ├─不含 drop sql
│   └─含 drop sql
│
├─sym                              # SymmetricDS 系統表
│   ├─不含 drop sql
│   └─含 drop sql
│
└─schema                           # mssql tables 
    ├─不含 drop sql
    └─含 drop sql
```

- 新增一個 `make_full_db.bat`，放置在要合併的 SQL 資料夾中，點兩下產製一個合併的 `migration.sql`
```bat
\\ make_full_db.bat
copy /a *.sql migration.sql
```

## 匯入 client 資料庫的 schema
- 在 server 建立 client 中 Leader 的所有表
- 將由 client 匯出的 `migration.sql` 放置到資料夾 `bin` 中
```shell
.\dbimport -e server-000 migration.sql
```

# 同步 server 與 client 的資料
## 匯出 client 資料
- 在資料夾 `migration` 中建立一個資料夾 `data` 放置產出的 SQL 檔案
- `--compatible`：postgres，表示輸出 postgres 型態的 schema
- `--no-create-info`：不匯出建表語句
- `--no-foreign-keys`：不匯出建立外鍵的語句
- `--no-indices`：不匯出建立索引的語句
- `--dir`：匯出檔案的目錄，此處設定為 `D:\mandy\Project\symmetricds\mssql2postgres\migration\data`
```shell
.\dbexport -e client-001 --compatible postgres --no-create-info --no-foreign-keys --no-indices --dir D:\mandy\Project\symmetricds\mssql2postgres\migration\data
```
## 匯入 client 資料
- 在 server 匯入 client 中 table 的資料
- 將由 client 匯出的 `ACRTC.sql` 放置到資料夾 `bin` 中
```shell
.\dbimport -e server-000 ACRTC.sql
```

## 使用工作排程器執行資料庫資料同步作業
參閱文件 [Task Scheduler](/軟體開發/學習心得/11542/DataIntegration/SymmetricDS/TaskScheduler)

# 資料驗證
## 使用 `dbcompare`，可搭配工作排程器執行
- 將屬性檔案(`client-001.properties`、`server-000.properties`)複製一份到資料夾 `bin` 中
```shell
.\dbcompare ACRTC -s client-001.properties -t server-000.properties
```

- 結果分析：server 與 client 的資料為一致

```
+---------------------------------------+---------------------------------------+------------+------------+------------+------------+------------+------------+------------+
+Source                                  Target                                  Source Rows  Target Rows  Matched      Different    Missing      Extra        Errors
+---------------------------------------+---------------------------------------+------------+------------+------------+------------+------------+------------+------------+
 ACRTC                                   ACRTC                                   6244         6244         6244         0            0            0            0
+---------------------------------------+---------------------------------------+------------+------------+------------+------------+------------+------------+------------+
```

![symmetricds dbcompare example results.png](http://192.168.25.60:8000/files/file_storage/f4f86346.png)

##  使用 SQL
- 查詢 client 端資料：所有 table 資料筆數
```sql
SELECT S.name '結構描述', O.name '資料表名稱', P.rows '列總數'
FROM sys.objects O INNER JOIN sys.schemas S
ON O.schema_id = S.schema_id
INNER JOIN sys.partitions P
ON O.object_id = P.object_id
WHERE (O.type = 'U') AND
(P.index_id IN (0,1))
ORDER BY S.name, O.name ASC;
```

- 查詢 server 端資料：所有 table 資料筆數
```sql
WITH tbl AS
  (SELECT table_schema,
          TABLE_NAME
   FROM information_schema.tables
   WHERE TABLE_NAME not like 'pg_%'
     AND table_schema in ('public'))
SELECT table_schema,
       TABLE_NAME,
       (xpath('/row/c/text()', query_to_xml(format('select count(*) as c from %I.%I', table_schema, TABLE_NAME), FALSE, TRUE, '')))[1]::text::int AS rows_n
FROM tbl
ORDER BY TABLE_NAME ASC;
```
# 組態設定
## 設定資料同步方式
- 查詢 table
```sql
-- 組態設定主要表格
select * from sym_node_group;
select * from sym_node;
select * from sym_node_group_link;
select * from sym_router;
select * from sym_channel;
select * from sym_trigger;
select * from sym_trigger_router;
select * from sym_node_host;

-- 查詢此處節點位置
select * from sym_node_identity;
select * from sym_node_security;

-- 驗證表格
select * from public."ACPTE";
```

- 將 `config.sql` 放置到資料夾 `bin` 中
```shell
.\dbimport -e server-000 config.sql
```

```sql
------------------------------------------------------------------------------
-- Clear and load SymmetricDS Configuration
-- 刪除系統表中的資料並匯入設定資料
------------------------------------------------------------------------------

--delete from sym_trigger_router;
--delete from sym_trigger;
delete from sym_router;
--delete from sym_channel;
--delete from sym_node_group_link;
--delete from sym_node_group;
--delete from sym_node_host;
--delete from sym_node_identity;
--delete from sym_node_security;
--delete from sym_node;

------------------------------------------------------------------------------
-- Node Groups
-- sym_node_group 節點群組表：設定節點群組
------------------------------------------------------------------------------
-- node_group_id 節點群組編號：唯一的節點群組識別值，PK，對應節點屬性檔案中(.properties)的 `group.id`
-- description 描述：節點群組的描述
-- 此表在跑節點屬性檔案時會自動匯入資料，故不需要額外再 insert 資料，但可以 update 資料
------------------------------------------------------------------------------

--insert into sym_node_group (node_group_id, description, create_time, last_update_by, last_update_time) values ('server', 'A server node', current_timestamp, '11542', current_timestamp);
--insert into sym_node_group (node_group_id, description, create_time, last_update_by, last_update_time) values ('client', 'A client node', current_timestamp, '11542', current_timestamp);
-- 更新 server
UPDATE sym_node_group
SET description = 'A server node', create_time = current_timestamp, last_update_by = '11542', last_update_time = current_timestamp
WHERE node_group_id = 'server';

-- 更新 client
UPDATE sym_node_group
SET description = 'A client node', create_time = current_timestamp, last_update_by = '11542', last_update_time = current_timestamp
WHERE node_group_id = 'client';

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
--insert into sym_node (node_id, node_group_id, external_id, sync_enabled) values ('000', 'server', '000', '1');
--insert into sym_node (node_id, node_group_id, external_id, sync_enabled) values ('001', 'client', '001', '1');

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

-- 允許 client 推送資料到 server
--insert into sym_node_group_link (source_node_group_id, target_node_group_id, data_event_action, sync_config_enabled) values ('client', 'server', 'P', 1);

-- 允許 client 從 server 拉取資料
--insert into sym_node_group_link (source_node_group_id, target_node_group_id, data_event_action, sync_config_enabled) values ('server', 'client', 'W', 1);

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
-- router_expression 路由描述：路由描述
-- sync_on_update 設定是否同步更新資料：1 表示啟用，0 表示停用
-- sync_on_insert 設定是否同步新增資料：1 表示啟用，0 表示停用
-- sync_on_delete 設定是否同步刪除資料：1 表示啟用，0 表示停用
-- create_time 建立時間：設定為當下時間 current_timestamp 
-- last_update_time 最後更新時間：設定為當下時間 current_timestamp
-- 此表在跑節點屬性檔案時會自動匯入資料，其實不需要額外再 insert 資料，但由於我們需要做額外設定，故自行 insert 資料
------------------------------------------------------------------------------

-- 從 client 同步所有資料到 server
insert into sym_router
(router_id, source_node_group_id, target_node_group_id, router_type, router_expression, sync_on_update, sync_on_insert, sync_on_delete, create_time, last_update_by, last_update_time)
values('client_to_server', 'client', 'server', 'default','client to server',1,1,1,current_timestamp, '', current_timestamp);

-- 從 server 同步所有資料到 client
-- 此處設定不同步更新資料、新增資料、刪除資料
insert into sym_router
(router_id, source_node_group_id, target_node_group_id, router_type, router_expression, sync_on_update, sync_on_insert, sync_on_delete, create_time, last_update_by, last_update_time)
values('server_to_client', 'server', 'client', 'default','server to client',0,0,0,current_timestamp, '', current_timestamp);

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

-- Channel "ACPMA" for tables related to items for purchase
insert into sym_channel
(channel_id, processing_order, max_batch_size, enabled, description)
values('ACPTE', 1, 100000, 1, 'ACPTE');

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

-- Triggers for tables on "ACPMA" channel
insert into sym_trigger
(trigger_id,source_table_name,channel_id, sync_on_insert, sync_on_update, sync_on_delete,last_update_time,create_time)
values('ACPTE','ACPTE','ACPTE',1,1,1,current_timestamp,current_timestamp);

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

-- Send all sales transactions to corp
insert into sym_trigger_router
(trigger_id,router_id,initial_load_order,last_update_time,create_time)
values('ACPTE','client_to_server', 200, current_timestamp, current_timestamp);
```

## 驗證 sql

```sql
-- 查詢 batch
select * from sym_incoming_batch order by batch_id desc;
select * from sym_outgoing_batch order by batch_id desc; 

-- 查詢資料
select * from ACPTE;

-- 刪除資料
delete from ACPTE where TE001='010101' AND TE002= '200808';
delete from ACPTE where TE001='010102' AND TE002= '200809';

-- 新增資料
INSERT INTO dbo.ACPTE
(COMPANY, CREATOR, USR_GROUP, CREATE_DATE, MODIFIER,MODI_DATE,FLAG,TE001,TE002,TE003,TE004,TE005,TE006)
values
('CKW','11542','DS','20230619','11542','20230619','2','010101','200808',0,0,0,0),
('CKW','11542','DS','20230619','11542','20230619','2','010102','200809',0,0,0,0);

-- 更新資料
UPDATE dbo.ACPTE
SET TE003=1
WHERE TE001='010101' AND TE002= '200808';

```