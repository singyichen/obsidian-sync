---
title: SymmetricDS Tool
description: 
published: true
date: 2023-07-04T01:18:25.243Z
tags: symmetricds
editor: markdown
dateCreated: 2023-06-17T01:05:48.061Z
---

# SymmetricDS Tool
- [ ] [Data Migration](https://www.symmetricds.org/docs/how-to/data-migration)
- [ ] [Appendix H: Utilities](https://www.symmetricds.org/doc/3.14/html/user-guide.html#_utilities)

# 管理工具
- 以下說明資料夾 `bin` 可以使用的管理工具使用方式

```
// bin
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
└─                             
```

## sym_service
### 功能
> - 執行管理服務
### 用法
```shell
.\sym_service <子命令>
```
### 子命令
- `start`：啟動服務
- `stop`：停止服務
- `restart`：重新啟動服務，只要調整過任何設定皆須重啟服務
- `install`：安裝服務
- `uninstall`：卸載服務
- `status`：查詢服務狀態
- `console`：從控制台運行服務

## symadmin
### 功能 
> - 執行管理任務
### 用法
```shell
.\symadmin --engine [引擎名稱] [選項] [參數] <子命令>
```
```shell
.\symadmin --properties [屬性文件] [選項] [參數] <子命令>
```
### 子命令
- `backup-config`：備份配置文件
- `create-sym-tables`：建立 SymmetricDS 所需的表格
- `create-war`：建立 Web 存檔以進行部署
- `drop-triggers`：刪除資料庫觸發器
- `encrypt-text`：加密文本字符串
- `export-batch`：從資料庫中匯出批次 CSV 資料
- `export-properties`：匯出默認屬性
- `export-sym-tables`：匯出 SymmetricDS 所需的表格
- `import-batch`：將批次 CSV 資料匯入資料庫
- `list-engines`：列出在此實例上配置的引擎
- `module`：管理模塊以添加或刪除功能
- `obfuscate-text`：混淆文本字符串
- `open-registration`：開放節點註冊
- `reload-node`：重新載入節點的資料（或初始載入）
- `reload-table`：重新載入節點的表格資料
- `remove-node`：刪除指定節點（取消註冊並清理）提供的引擎
- `run-job`：立即運行作業
- `run-purge`：運行清除作業
- `send-schema`：將模式更改發送到節點
- `send-script`：將腳本發送到節點
- `send-sql`：將 SQL 語句發送到節點
- `sync-triggers`：建立資料庫觸發器
- `uninstall`：從資料庫中卸載所有 SymmetricDS 對象

## sym
### 功能 
> - 啟動引擎作為獨立的客戶端或服務器
### 用法
```shell
.\sym <子命令>
```
### 子命令 
- `-C,--client`：啟動嵌入式的 SymmetricDS 客戶端實例
- `--debug`：在日誌中打印調試信息
- `-e,--engine`：配置引擎的名稱，名稱應對應於引擎目錄中的一個屬性文件中的 `engine.name` 設置
- `-h,--help`：打印每個選項和說明的幫助
- `-H,--host`：可選地傳遞服務器應綁定到的網絡接口。如果未提供此選項，則服務器將綁定到所有接口
- `-I,--max-idle-time`：當連接強制關閉時的最大閒置時間（以毫秒為單位）[900000]
- `-ndb,--no-directbuffer`：不要為 NIO HTTP 連接器使用直接緩衝區
- `-nnio,--no-nio`：不要為 HTTP 連接器使用非阻塞 IO
- `--no-log-console`：不會向控制台輸出任何內容
- `--no-log-file`：不會向日誌文件輸出任何內容
- `-p,--properties`：SymmetricDS 引擎的設置屬性文件。如果未提供，則使用默認值， 然後使用 `classpath` 中的第一個 `symmetric.properties` 進行覆蓋， 然後使用 `user.home` 目錄中的 `symmetric.properties` 值進行覆蓋
- `-P,--port`：可選地傳遞服務器實例要使用的 HTTP 端口號。如果未傳遞此參數， 則將使用 `symmetric-server.properties` 文件中的端口號
- `-providerClass`：替代加密提供程序的類名
- `-Q,--secure-port`：可選地傳遞服務器實例要使用的 HTTPS 端口號。如果未傳遞此參數， 則將使用 `symmetric-server.properties` 文件中的端口號
- `-S,--server`：啟動一個嵌入式的 SymmetricDS 實例，該實例接受 HTTP 。在命令行上設置此選項將覆蓋 `symmetric-server.properties` 中的啟用設置
- `-storepass`：keystore的密碼 [changeit]
- `-storetype`：keystore格式的類型 [jks]
- `-T,--secure-server`：啟動一個嵌入式的 SymmetricDS 實例，該實例接受 HTTPS 。在命令行上設置此選項將覆蓋 `symmetric-server.properties` 中的啟用設置
- `-U,--mixed-server`：啟動一個嵌入式的 SymmetricDS 實例，該實例接受 HTTP/HTTPS。在命令行上設置此選項將覆蓋 `symmetric-server.properties` 中的啟用設置
- `-v,--verbose`：使用冗長格式輸出到控制台
- `-winxp,--winxp`：啟用緩解線程，以防止 Windows XP 上的系統時鐘加速

## setenv
### 功能
> - 設置環境變量和啟動引擎
> - setenv 是一個腳本文件，用於設置環境變量和啟動引擎
> - setenv 腳本會定義 JAVA_HOME 和 CLASSPATH 等環境變量，以便 SymmetricDS 可以在運行時訪問所需的 Java 環境和庫
> - setenv 腳本還可以定義其他引擎啟動選項，例如啟用嵌入式 Web 服務器或 JMX 監視。在啟動 SymmetricDS 引擎之前，需要運行 setenv 腳本，以確保引擎可以正確地訪問所需的資源。

### 用法
```shell
.\setenv
```

## jmx
### 功能
> - 提供一個命令行界面，以執行特定引擎的 JMX 方法。
### 用法
```shell
.\jmx <子命令>
```
### 子命令
- `--args`：JMX 方法需要的參數列表。默認情況下，分隔符是逗號。 可以使用 `--args-delimiter` 參數覆蓋分隔符
- `--args-delimiter`：用於參數的分隔符字符
- `--bean`：MessageKey：Jmx.Option.bean [null]
- `--debug`：在日誌中打印調試信息
- `-e,--engine`：配置引擎的名稱，名稱應對應於引擎目錄中的一個屬性文件中的 `engine.name` 設置
- `-h,--help`：打印每個選項和說明的幫助
- `--listbeans`：列出可用的 JMX bean
- `--listmethods`：列出特定 bean 上可用的 JMX 方法。需要指定 `--bean`
- `--method`：應當被調用的方法的名稱。需要指定 `--bean`。 如果該方法需要參數，則可以選擇性地提供 `--args`
- `--no-log-console`：不會向控制台輸出任何內容
- `--no-log-file`：不會向日誌文件輸出任何內容
- `-p,--properties`：SymmetricDS 引擎的設置屬性文件。如果未提供，則使用默認值， 然後使用 `classpath` 中的第一個 `symmetric.properties` 進行覆蓋， 然後使用 `user.home` 目錄中的 `symmetric.properties` 值進行覆蓋
- `-v,--verbose`：使用冗長格式輸出到控制台

## dbcompare
### 功能
> - 比對資料庫
### 用法
- 須將屬性文件複製一份到資料夾 `bin` 中
```shell
.\dbcompare [tablename...] <子命令>
```
- 範例
```shell
.\dbcompare ACPTA -s client-001.properties -t server-000.properties
```
### 子命令
- `--config <arg>`：引用包含 `dbcompare` 的其他配置參數的屬性文件路徑的參考。該屬性文件允許您包含表格特定的配置，並指定諸如 `whereclause` 和 `excludecolumns` 等參數。文件中的 `whereclause` 應格式化為 `[table].[source|target].whereclause`。例如，對於一個名為 `item` 的表，使用 `item.whereclause=field > now()-2`。如果您在 `whereclause` 之前沒有指定表格，那麼它將用於所有表格
- `--continue-after-error <arg>`：`true|false`。如果為 `true`，當在比較過程中出現解析錯誤時，比較將繼續進行。如果為 `false`，比較將退出。默認值為 `false`
- `--date-time-format <arg>`：比較日期時間值時要使用的格式。例如，使用格式 `yyyy-MM-dd HH:mm:ss` 會將日期時間值轉換為 `yyyy-MM-dd HH:mm:ss`，然後進行比較
- `--exclude <arg>`：要從比較中排除的表格名稱列表，用逗號分隔
- `-h,--help`：打印每個選項和描述的幫助信息
- `--numeric-scale <arg>`：在比較小數時，要考慮多少位小數。其餘的數字將四捨五入。默認值為 `3`
- `--output-sql <arg>`：用於 SQL 語句的輸出文件，如果在目標上執行這些語句，則應將其與源同步
- `-s,--source <arg>`：比較來源資料庫引擎的屬性文件
- `-t,--target <arg>`：比較目標資料庫引擎的屬性文件
- `--target-tables <arg>`：要在目標端上使用的表格名稱列表，用逗號分隔。如有需要，使用 `catalog.schema.table` 前綴。與 `use-sym-config=false` 一起使用
- `--use-sym-config <arg>`：`true|false`。如果為 `true`，將諮詢 `symtrigger`、`symtransform` 等來構建要比較的資料模型。默認值為 `true`
### 結果

![symmetricds dbcompare example results.png](http://192.168.25.60:8000/files/file_storage/df6a2cba.png)

```
+---------------------------------------+---------------------------------------+------------+------------+------------+------------+------------+------------+------------+
+Source                                  Target                                  Source Rows  Target Rows  Matched      Different    Missing      Extra        Errors
+---------------------------------------+---------------------------------------+------------+------------+------------+------------+------------+------------+------------+
[server-000] - DbCompare - Source comparison SQL: select "COMPANY", "CREATOR", "USR_GROUP", "CREATE_DATE", "MODIFIER", "MODI_DATE", "FLAG", "TC001", "TC002", "TC003", "TC004", "TC005", "TC006", "TC007", "TC008", "TC009", "TC010", "TC011", "TC012", "TC013", "TC014", "TC015", "TC016", "TC017", "TC018", "TC019", "TC020" from "Leader"."dbo"."ACRTC"  t where 1=1 ORDER BY "TC001","TC002"
[server-000] - DbCompare - Target comparison SQL: select "TC001", "TC002", "COMPANY", "CREATOR", "USR_GROUP", "CREATE_DATE", "MODIFIER", "MODI_DATE", "FLAG", "TC003", "TC004", "TC005", "TC006", "TC007", "TC008", "TC009", "TC010", "TC011", "TC012", "TC013", "TC014", "TC015", "TC016", "TC017", "TC018", "TC019", "TC020" from "public"."ACRTC"  t where 1=1 ORDER BY "TC001","TC002"
[server-000] - DbCompare - Completed table TableReport [sourceTable=ACRTC, targetTable=ACRTC, sourceRows=6244, targetRows=6244, matchedRows=6244, differentRows=0, missingRows=0, extraRows=0, errorRows=0].  Elapsed time: 1 second
 ACRTC                                   ACRTC                                   6244         6244         6244         0            0            0            0
+---------------------------------------+---------------------------------------+------------+------------+------------+------------+------------+------------+------------+
[server-000] - DbCompare - dbcompare complete.  Total Time: 1 second
[] - AbstractSymmetricEngine - Stopping SymmetricDS externalId=001 version=3.14.7 database=Microsoft SQL Server
[] - AbstractSymmetricEngine - Stopping SymmetricDS externalId=000 version=3.14.7 database=PostgreSQL
```

## dbexport
### 功能
> - 匯出資料庫
### 用法
```shell
.\dbexport [tablename...] <子命令>
```
### 子命令
- `--add-drop-table`：將刪除表格的語句添加到輸出中
- `--catalog <arg>`：指定要在哪個目錄下查找表格
- `--compatible <arg>`：設置匯出資料與目標資料庫的兼容性。支持的資料庫類型有：db2, db2zos, derby, firebird, greenplum, h2, hsqldb, hsqldb2, informix, interbase, mssql, mysql, oracle, postgres, sybase
- `--debug`：在日誌中打印調試信息
- `--dir <arg>`：指定匯出文件的目錄。如果指定了目錄，則每個表格的資料將匯出到目錄下的一個文件中
- `-e,--engine <arg>`：指定要使用的 SymmetricDS 引擎的名稱。該名稱應對應到引擎目錄中的某個配置文件中的 engine.name 設置
- `--exclude-columns <arg>`：指定要從匯出的表格中排除的列的列表，用逗號分隔
- `--format <arg>`：指定匯出的格式。支持的格式有：SQL、CSV、XML 和 SYM_XML
- `-h,--help`：打印每個選項和描述的幫助信息
- `-i,--comments`：在匯出的文件中添加註釋
- `--no-create-info`：不匯出建表語句
- `--no-data`：不匯出插入資料的語句
- `--no-foreign-keys`：不匯出建立外鍵的語句
- `--no-indices`：不匯出建立索引的語句
- `--no-log-console`：不將輸出信息顯示在控制台上
- `--no-log-file`：不將輸出信息寫入日誌文件
- `--no-qualifiers`：不將表格和列名用引號括起來
- `-p,--properties <arg>`：指定 SymmetricDS 引擎的配置文件。如果未提供，則使用默認配置，然後覆蓋為類路徑下的第一個 `symmetric.properties`，最後覆蓋為用戶 `home` 目錄下的 `symmetric.properties`
- `--schema <arg>`：指定要在哪個架構下查找表格
- `--sql <arg>`：指定用於選擇資料的自定義 SQL 語句
- `--symmetric`：消息鍵，DbExport.Option.symmetric[null]
- `--use-jdbc-timestamp-format <arg>`：當設置為 `true` 時，匯出的文件中日期和時間的格式將使用 `{ts 'yyyy-MM-dd hh:mm:ss.SSS'}`。默認為 `true`
- `--use-variable-dates`：允許使用格式 `${curdate+-millis}`進行日期替換
- `-v,--verbose`：使用詳細格式輸出信息到控制台
- `--where <arg>`：指定 SQL 的 WHERE 子句
  
## dbfill
### 功能
> - 使用隨機生成的資料填充資料庫表格
### 用法
```shell
.\dbfill [tablename...] <子命令>
``` 
### 子命令
- `--cascade`：包括表列表中未包含的依賴於外鍵的表
- `--catalog`：在目錄中查找表格
- `--commit`：每次提交為一個事務的行數
- `--commit-delay`：更改資料後等待的時間（毫秒）。預設為0
- `--continue`：忽略所有錯誤，繼續修改資料庫
- `--count`：在每個表中生成的行數
- `--debug`：在日誌中打印調試信息
- `-e,--engine`：配置引擎的名稱，名稱應對應於引擎目錄中的一個屬性文件中的engine.name設置
- `-h,--help`：打印每個選項和說明的幫助
- `--ignore`：一個或多個前綴，用於識別要忽略的表。此參數僅在未提供表名時起作用。 （例如，"sym，sys"）
- `--interval`：在資料庫中的每次交易之間等待的時間（毫秒）
- `--max-byte-size`：將放入二進制字段中的最大字節數。[32]
- `--max-text-size`：將放入文本字段中的最大字符數。 [32]
- `--no-log-console`：不會向控制台輸出任何內容
- `--no-log-file`：不會向日誌文件輸出任何內容
- `-p,--properties`：SymmetricDS 引擎的設置屬性文件。如果未提供，則使用默認值， 然後使用 `classpath` 中的第一個 `symmetric.properties` 進行覆蓋， 然後使用 `user.home` 目錄中的 `symmetric.properties` 值進行覆蓋
- `--prefixed`：包括表名的前綴
- `--print`：打印 DbFill 的 SQL 代碼，而不是填充表格
- `--rand`：隨機生成並提交行數
- `--repeat`：重複計數的次數
- `--rollback`：執行回滾的概率（0-100）
- `--schema`：在架構中查找表格
- `--select`：選擇滿足約束條件的外鍵依賴資料
- `--truncate`：在填充表格之前截斷表格
- `-v,--verbose`：使用詳細格式進行控制

## dbimport
### 功能
> - 匯入資料庫
### 用法
- 先將要執行的 `file` 放置到資料夾 `bin` 中
```shell
.\dbimport [filename...] <子命令>
```
### 子命令
- `--alter`：如果該表已存在，則嘗試更改以匹配匯入定義。僅適用於 `--format=XML`
- `--alter-case`：在建立表時改變大小寫以匹配資料庫的默認大小寫。僅適用於 `--format=XML`
- `--catalog`：在目錄中查找表格
- `--commit`：在提交資料之前匯入的行數。默認為 `10000`
- `--debug`：在日誌中打印調試信息
- `--drop-if-exists`：如果該表已存在，則在建立之前嘗試刪除它。僅適用於 `--format=XML`
- `-e,--engine`：配置引擎的名稱，名稱應對應於引擎目錄中的一個屬性文件中的 `engine.name` 設置
- `--filter-classes`：一個逗號分隔的 Java 類列表，這些類實現了 `org.jumpmind.symmetric.io.data.writer.IDataba seWriterFilter`。這些過濾器將應用於匯入
- `--force`：忽略所有錯誤，繼續處理匯入資料
- `--format`：輸入格式：SQL、CSV、XML 或 SYM_XML
- `-h,--help`：打印每個選項和說明的幫助
- `--ignore`：表示應忽略與現有行的衝突
- `--interval`：在交易提交之間等待的毫秒數
- `--no-log-console`：不會向控制台輸出任何內容
- `--no-log-file`：不會向日誌文件輸出任何內容
- `-p,--properties`：SymmetricDS 引擎的設置屬性文件。如果未提供，則使用默認值， 然後使用 `classpath` 中的第一個  `symmetric.properties` 進行覆蓋， 然後使用 `user.home` 目錄中的 `symmetric.properties` 值進行覆蓋
- `--replace`：表示應替換現有行。它們將被更新語句替換。僅適用於 `--format=CSV、SYM_XML`
- `--schema`：在架構中查找表格
- `--table`：指定要匯入的表格
- `--use-variable-dates`：允許使用格式 `${curdate+-millis}`進行日期替換
- `-v,--verbose`：使用詳細格式進行控制台輸出

## dbsql
### 功能
> - 連接資料庫，提供一個 sql shell，以便從命令與資料庫進行溝通。
### 用法
```shell
.\dbsql <子命令>
```
### 子命令
- `--debug`：在日誌中打印調試信息
- `-e,--engine`：配置引擎的名稱，名稱應對應於引擎目錄中的一個屬性文件中的 `engine.name`設置
- `-h,--help`：打印每個選項和說明的幫助
- `--no-log-console`：不會向控制台輸出任何內容
- `--no-log-file`：不會向日誌文件輸出任何內容
- `-p,--properties`：SymmetricDS 引擎的設置屬性文件。如果未提供，則使用默認值， 然後使用 `classpath`中的第一個 `symmetric.properties` 進行覆蓋， 然後使用 `user.home` 目錄中的 `symmetric.properties` 值進行覆蓋
- `--sql`：在 shell 中運行此 sql 語句
- `--sqlfile`：在指定的文件中運行每個以行為分隔符的 sql 語句
- `-v,--verbose`：使用詳細格式進行控制


