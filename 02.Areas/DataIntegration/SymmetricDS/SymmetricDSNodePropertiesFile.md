---
title: SymmetricDS Node Properties File
description: 
published: true
date: 2023-06-20T07:18:09.028Z
tags: symmetricds
editor: markdown
dateCreated: 2023-06-17T01:21:11.605Z
---

# SymmetricDS Node Properties File
- [ ] [Spring 的 CRON 支援](https://docs.spring.io/spring-framework/docs/3.0.x/javadoc-api/org/springframework/scheduling/support/CronSequenceGenerator.html)
- [ ] [Connect to the Database](https://www.symmetricds.org/docs/how-to/connect-to-database)

# 節點屬性檔案
- 節點屬性檔案：`.properties`
- 參閱官網 [節點屬性文件](https://www.symmetricds.org/doc/3.14/html/user-guide.html#_node_properties_file)
- 所有節點都需要一個包含身份資訊和數據庫連接資訊的屬性檔案。

## engine.name
- 引擎名稱：當前節點服務的名稱，用於使用 HTTP URL 訪問特定引擎
- 在 engines 目錄中組態的每個節點都必須具有唯一的引擎名稱

## db.driver
- 資料庫的 JDBC 驅動名稱
- 選擇一個，其他註解
- driver 的壓縮檔在資料夾 `lib` 中

## db.url
- 資料庫連接地址 JDBC URL
- 選擇一個，其他註解

## db.user
- 資料庫使用者名稱

## db.password
- 資料庫密碼

## db.validation.query
- 驗證資料庫連接的 SQL 查詢語句
>  連接資料庫 `mssql` 時需使用驗證查詢語句
> `db.validation.query=Select 1` 
{.is-warning}

## registration.url
- 上一級節點的註冊地址

## sync.url
- 本節點的同步註冊網址：可以聯繫此節點以進行同步的 URL
- 格式：`http://{hostname}:{port}/{webcontext}/sync/{engine.name}`
- `{webcontext}` 對於獨立部署是空白的。它通常是應用程序服務器部署的 war 檔案的名稱。
- 若此節點無子節點，則可以不用設定同步註冊網址，就預設為空

## group.id
- 節點群組 id：此節點所屬的節點群組
- 同步是在節點組之間指定的，這表示只需為同一組中的多個節點指定一次。
- 須在系統表 `sym_node_group` 中設定

## external.id
- 外部 id：此節點的外部 ID
- 可用於條件和子集數據同步的表達式中，每個節點都有一個唯一的序列號，用於跟蹤同步事件
- 通過上面的 `group.id` 和 `external.id` 可以定位到唯一的節點

## job.purge.period.time.ms
- 設定清理作業執行的間隔時間的參數，其值表示清理作業之間的時間間隔（以毫秒為單位）
- 未設定的默認值 86400000（即每隔 1 天執行一次清理作業）

## job.routing.period.time.ms
- 設定路由作業執行的間隔時間的參數，其值表示路由作業之間的時間間隔（以毫秒為單位）
- 未設定的默認值 10000（即每隔 10 秒執行一次路由作業）

> - `job.push.period.time.ms` 與 `job.push.cron` 擇一設定
> - `job.pull.period.time.ms` 與 `job.pull.cron` 擇一設定
{.is-info}

## job.push.period.time.ms
- 推送作業執行的間隔時間的參數，其值表示推送作業之間的時間間隔（以毫秒為單位）
- 未設定的默認值為 60000（即一分鐘執行一次推送作業）

## job.push.cron
- 設定 cron 表達式的定期推送作業
- cron 表達式：`* * * * * *`
```
第一個字段表示秒（0-59）
第二個字段表示分鐘（0-59）
第三個字段表示小時（0-23）
第四個字段表示日期（1-31）
第五個字段表示月份（1-12）
第六個字段表示星期幾（0-6，0 表示星期日）
```
## job.pull.period.time.ms
- 拉取作業執行的間隔時間的參數，其值表示拉取作業之間的時間間隔（以毫秒為單位）
- 未設定的默認值為 60000（即一分鐘執行一次拉取作業）

## job.pull.cron
- 設定 cron 表達式的定期拉取作業
- cron 表達式：`* * * * * *`
```
第一個字段表示秒（0-59）
第二個字段表示分鐘（0-59）
第三個字段表示小時（0-23）
第四個字段表示日期（1-31）
第五個字段表示月份（1-12）
第六個字段表示星期幾（0-6，0 表示星期日）
```

## auto.registration
- 用於控制節點自動註冊的參數
- 設定為 `true`，則節點將自動註冊到 SymmetricDS 系統中，而不需要手動設置節點的配置信息

## initial.load.create.first
- 用於控制同步作業是否在首次同步時從來源資料庫中複製現有資料的參數
- 設定為 `true`，則同步作業將在首次同步時從來源資料庫中複製現有的資料到目標資料庫中。

# 根節點/主節點 ( Master Node )
- 根節點/主節點：第一個節點，主節點是管理組態的地方。
- 其他節點通常向主節點註冊以獲取其初始組態。
- 節點註冊後，在主節點上所做的其他組態更改會自動同步到註冊節點。
- samples/`corp-000.properties`：根節點資料庫連接資訊的屬性檔案說明
```
// corp-000.properties

# 引擎名稱：當前節點服務的名稱，用於使用 HTTP URL 訪問特定引擎
# 在 engines 目錄中組態的每個節點都必須具有唯一的引擎名稱
engine.name=corp-000

# 資料庫的 JDBC 驅動名稱
# 選擇一個，其他註解
db.driver=org.h2.Driver

# 資料庫連接地址 JDBC URL
# 選擇一個，其他註解
db.url=jdbc:h2:corp;AUTO_SERVER=TRUE;LOCK_TIMEOUT=60000

# 資料庫使用者名稱
db.user=symmetric

# 資料庫密碼
db.password=

# 上一級節點的註冊地址
# 如果是根節點，就預設為空
registration.url=

# 本節點的同步註冊網址：可以聯繫此節點以進行同步的 URL
# 格式：http://{hostname}:{port}/{webcontext}/sync/{engine.name}
# {webcontext} 對於獨立部署是空白的。它通常是應用程序服務器部署的 war 檔案的名稱。
# 若此節點無子節點，則可以不用設定同步註冊網址，就預設為空
sync.url=http://localhost:31415/sync/corp-000

# 節點群組 id：此節點所屬的節點群組
# 同步是在節點組之間指定的，這表示只需為同一組中的多個節點指定一次。
# 須在系統表 sym_node_group 中設定
group.id=corp

# 外部 id：此節點的外部 ID
# 可用於條件和子集數據同步的表達式中，每個節點都有一個唯一的序列號，用於跟蹤同步事件
# 通過上面的 group.id 和 external.id 可以定位到唯一的節點
external.id=000

# 後面的參數是對服務運行參數的組態，保持默認就好
job.purge.period.time.ms=7200000
job.routing.period.time.ms=5000
job.push.period.time.ms=10000
job.pull.period.time.ms=10000
auto.registration=true
initial.load.create.first=true
```

# 子節點
## 第一子節點
- 第一子節點資料庫連接資訊的屬性檔案：samples/`store-002.properties`

```
// store-001.properties

# 引擎名稱：當前節點服務的名稱，用於使用 HTTP URL 訪問特定引擎
# 在 engines 目錄中組態的每個節點都必須具有唯一的引擎名稱
engine.name=store-001

# 資料庫的 JDBC 驅動名稱
# 選擇一個，其他註解
db.driver=org.h2.Driver

# 資料庫連接地址 JDBC URL
# 選擇一個，其他註解
db.url=jdbc:h2:store001;AUTO_SERVER=TRUE;LOCK_TIMEOUT=60000

# 資料庫使用者名稱
db.user=symmetric

# 資料庫密碼
db.password=

# 上一級節點的註冊地址
# 如果是根節點，就預設為空
registration.url=http://localhost:31415/sync/corp-000

# 本節點的同步註冊網址：可以聯繫此節點以進行同步的 URL
# 格式：http://{hostname}:{port}/{webcontext}/sync/{engine.name}
# {webcontext} 對於獨立部署是空白的。它通常是應用程序服務器部署的 war 檔案的名稱。
# 若此節點無子節點，則可以不用設定同步註冊網址，就預設為空
sync.url=

# 節點群組 id：此節點所屬的節點群組
# 同步是在節點組之間指定的，這表示只需為同一組中的多個節點指定一次。
# 須在系統表 sym_node_group 中設定
group.id=store

# 外部 id：此節點的外部 ID
# 可用於條件和子集數據同步的表達式中，每個節點都有一個唯一的序列號，用於跟蹤同步事件
# 通過上面的 group.id 和 external.id 可以定位到唯一的節點
external.id=001

# 後面的參數是對服務運行參數的組態，保持默認就好
job.routing.period.time.ms=5000
job.push.period.time.ms=10000
job.pull.period.time.ms=10000
```

## 第二子節點
- 第二子節點資料庫連接資訊的屬性檔案：samples/`store-002.properties`

```
// store-002.properties

# 引擎名稱：當前節點服務的名稱，用於使用 HTTP URL 訪問特定引擎
# 在 engines 目錄中組態的每個節點都必須具有唯一的引擎名稱
engine.name=store-002

# 資料庫的 JDBC 驅動名稱
# 選擇一個，其他註解
db.driver=org.h2.Driver

# 資料庫連接地址 JDBC URL
# 選擇一個，其他註解
db.url=jdbc:h2:store002;AUTO_SERVER=TRUE;LOCK_TIMEOUT=60000

# 資料庫使用者名稱
db.user=symmetric

# 資料庫密碼
db.password=

# 上一級節點的註冊地址
# 如果是根節點，就預設為空
registration.url=http://localhost:31415/sync/corp-000

# 本節點的同步註冊網址：可以聯繫此節點以進行同步的 URL
# 格式：http://{hostname}:{port}/{webcontext}/sync/{engine.name}
# {webcontext} 對於獨立部署是空白的。它通常是應用程序服務器部署的 war 檔案的名稱。
# 若此節點無子節點，則可以不用設定同步註冊網址，就預設為空
sync.url=

# 節點群組 id：此節點所屬的節點群組
# 同步是在節點組之間指定的，這表示只需為同一組中的多個節點指定一次。
# 須在系統表 sym_node_group 中設定
group.id=store

# 外部 id：此節點的外部 ID
# 可用於條件和子集數據同步的表達式中，每個節點都有一個唯一的序列號，用於跟蹤同步事件
# 通過上面的 group.id 和 external.id 可以定位到唯一的節點
external.id=002

# 後面的參數是對服務運行參數的組態，保持默認就好
job.routing.period.time.ms=5000
job.push.period.time.ms=10000
job.pull.period.time.ms=10000
```



