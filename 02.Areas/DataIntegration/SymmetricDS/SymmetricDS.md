---
created: 2024-02-05T14:13
updated: 2024-02-06T15:42
title: SymmetricDS
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
published: true
---
# 🚀 SymmetricDS

- [ ] [symmetricds](https://www.symmetricds.org/)
- [ ] [解決方案評估](https://sites.google.com/site/richchihlee/portal/eai/sym/eval)
- [ ] [Clustering SymmetricDS](https://www.jumpmind.com/blog/blog/how-to/clustering-symmetricds/)

# 關於 SymmetricDS


![gh](https://raw.githubusercontent.com/singyichen/images/main/images/symmetricds-logo.png)


SymmetricDS 是從大型 POS 開發專案衍生出來的開源資料庫同步軟體，支援單向複製，多主機複製，過濾同步和轉換。使用 web 和資料庫技術，它可以作為一個非同步複製資料或接近即時操作。可以擴展到大量的資料庫和不同平台之間的操作，它可以在低頻寬連接和經得起時間的網路故障。

SymmetricDS 目前提供免費版與收費 PRO 版，兩種版本功能實現上相同，但 PRO 版另外提供 Web 管理介面，可以設置與監管各端點。

## 運作原理

- SymmetricDS 是一個可以獨立運作的服務，不見得要跟資料庫裝在同套環境內，但因 SymmetricDS 體積小負載低，通常會裝在同一環境內，會取得最佳的效能。
- SymmetricDS 透過 JDBC 跟資料庫連線，資料會先壓縮過再透過 HTTP/HTTPS 跟其他 Node 傳輸同步。
- 每個 SymmetricDS Node 都會指定 `群組名稱(Group)` 及 `對外ID(External ID)` ， `Group+External ID＝Node` 辨識唯一值。
- SymmetricDS Server 在首次使用時會在 Database 中建立供資料同步相關 Table (共 41 個 SYM 開頭的 Table )，而 Client 在首次連線時，會同步建立 Server 所有 SYM Table 與 Data 。


![gh](https://raw.githubusercontent.com/singyichen/images/main/images/symmetricds-working-principle.png)



![gh](https://raw.githubusercontent.com/singyichen/images/main/images/symmetricds-working-structure.png)


## 節點間的資料同步方式
### Push (P)
- 讓來源節點群組( Source Node Group )提出 HTTP PUT 要求且把資料推送到目標節點群組( Target Node Group )。


![gh](https://raw.githubusercontent.com/singyichen/images/main/images/symmetricds-push-job.png)

### Wait for pull (W)
- 目標節點群組會主動透過 HTTP GET 來跟來源節點群組拉資料，在這之前來源節點群組會一直等待 HTTP GET 的要求。

![gh](https://raw.githubusercontent.com/singyichen/images/main/images/symmetricds-pull-job.png)


### oute-only (R)
- 表示資料不會由 SymmetricDS 來傳送。

## 部署示意圖
雙箭頭代表可以雙向同步，而不是簡單的單向複製


![gh](https://raw.githubusercontent.com/singyichen/images/main/images/symmetricds-deployment-diagram.png)


## 組態資料模型 Configuration Data Model
- 對於各個服務器，不管是 Server 還是 Client，都需要組態 SymmetricDS 服務，主要用來進行監聽與執行動作。並且是以 Node 來代表服務器進行設置。
- Trigger 是為了實現系統的即時性，系統持續在監聽資料庫，當發生變化時，會同時向關連的 Node 發起 Sync Request，關連的 Node 接收 Request 後做出對應的動作。


![gh](https://raw.githubusercontent.com/singyichen/images/main/images/symmetricds-configuration-data-model.png)

## 運行時資料模型 Runtime Data Model
當每個 Node 監聽到本機的 Data change event，會把變動的數據通過 Trigger 與關連 Node 進行通訊。


![gh](https://raw.githubusercontent.com/singyichen/images/main/images/symmetricds-runtime-data-model.png)


# 特性 Features
## 跨平台的 Cross Platform
可在大多數操作系統上運行，包括移動設備，並可將任何支援的數據庫同步到任何其他資料庫。

## 多執行緒 Multi-Threaded
多執行緒架構提取、轉移和平行載入資料。

## 通道 Channels
表格被分組為獨立的通道，有自己的執行緒同步佇列。

## 自動回復機制 Automatic Recovery
批次中的錯誤會重試，直到成功，因此同步可以從網絡中斷中恢復。

## 交易處理 Transaction Aware
資料更改按相同順序記錄並回放在同一事務中。

## 多主機 Multi-Master
同一表格可以在避免更新循環的情況下從主機系統同步。

## 傳輸時做篩選、轉換 Transformation
在提取或加載階段過濾、子集和轉換數據。

## 衝突檢測 Conflict Detection
在多主同步期間檢測衝突並自動解決。

## 表結構 Table Schema
可選地允許創建和升級數據庫架構。

## 初始資料載入 Initial Data Load
使用初始數據加載準備遠程數據庫。也可以發送部分初始加載的特定表格和行。

## 中央配置 Central Configuration
所有配置都從中央註冊服務器接收並保持同步。

## 多種部署選項 Multiple Deployment Options
使用獨立引擎、Web應用程序（WAR）或嵌入在應用程序中進行部署。

## 通訊方法 Communication Methods
推（流回數據）或拉（流式輪詢數據）更改以通過防火牆進行通信。

## HTTP/S 通訊 HTTP/S Transport
可插拔的傳輸協議默認為 REST 風格的HTTP/S服務。

## 高效協議 Efficient Protocol 
快速流式數據格式易於生成、解析和加載。傳輸也默認為壓縮。

## 監控 Monitoring
監控器可監視批次錯誤或積壓等問題，並通過電子郵件發送通知。

## 遠端管理 Remote Management
通過命令行工具、REST API和Java Management Extensions（JMX）控制台進行管理。

## 插件 API Plug-In API
通過擴展和插件點添加自定義功能。

## 可嵌入 Embeddable 
大小足夠小，可嵌入或啟動在其他應用程式中（例如 POS 應用程式）。

# 優缺點
## 優點
- 同步即時，基於推拉雙機制的同步，對於數據的及時性完整性有保障。關於事件的併發與線程管理已封裝。表結構變動對於組態好的數據欄位的同步影響不大，但對於新增的欄位如果也需要同步的話，需要重新註冊節點，並重啓服務。
## 缺點
- 每個節點都需要組態服務代碼，且比較複雜。會在每個節點數據庫中生成 41 張同步系統表，業務的控制體現在表數據中。適合用於固定或長期穩定的網絡通道的機房環境。如果整合進產品往外推廣，組態複雜後期維護也麻煩，適合本公司內部服務器的應用。

# 支援不同的資料庫

|              資料庫              |        版本        |
|:--------------------------------:|:------------------:|
|              MySQL               |  5.0.2及以上版本   |
|             MariaDB              |     及以上版本     |
|              Oracle              |   10g及以上版本    |
|            PostgreSQL            |  8.2.5及以上版本   |
|            Sql Server            |   2005及以上版本   |
|         Sql Server Azure         |                    |
|              HSQLDB              |        2.x         |
|                H2                |        1.x         |
|           Apache Derby           | 10.3.2.1及以上版本 |
|             IBM DB2              |   9.5及以上版本    |
|             Firebird             |   2.0及以上版本    |
|            Interbase             |   2009及以上版本   |
|            Greenplum             |  8.2.15及以上版本  |
|              SQLite              |    3及以上版本     |
| Sybase Adaptive ServerEnterprise |   12.5及以上版本   |
|       Sybase SQL Anywhere        |    9及以上版本     |

# 使用案例 Use Case
## 負載平衡 Load Balancer


![gh](https://raw.githubusercontent.com/singyichen/images/main/images/symmetricds-cluster-diagram-with-a-load-balancer.png)


涉及 SymmetricDS 集群的最常見用例是通過負載平衡器來支持多個客戶端節點。這有助於將中央資料庫擴展到可複製到數百甚至數千個客戶端節點。它還可以作為高可用性用例，以便即使中央 SymmetricDS 節點關閉，複製到中央節點仍然繼續進行。

這種設置的關鍵在於負載平衡器後面的所有節點都使用相同的同步 URL。這個同步 URL 是負載平衡器的終點，也是所有客戶端節點通信的 URL，用於訪問中央節點。因此，在這個設置中確保負載平衡器後面的所有節點的同步 URL 都是相同的。

## 無負載平衡器（僅限多宿主） No Load Balancer (multi-homed only)

![gh](https://raw.githubusercontent.com/singyichen/images/main/images/symmetricds-cluster-diagram-without-a-load-balancer.png)


如果要複製的所有資料庫都在同一個網路上（而不是通過廣域網路），那麼所有節點/引擎都可以在單個 SymmetricDS 安裝下運行（多宿主）。如果是這種情況，可以在沒有負載平衡器的情況下集群更多的 SymmetricDS 安裝。這既提供了高可用性，如果一個伺服器失敗，也提供了一些工作負載的分發。

這種設置的關鍵在於所有引擎的 sync.url 和 registration.url 值都應該使用本地主機名。這確保了在伺服器 A 上的節點 1 和節點 2 之間的請求將保持在伺服器 A 上，而不需要通過負載平衡器發送。

然而，基本的集群原則仍然適用。所有引擎的 property 檔案中必須設置 Cluster enabled 參數為 true，並且代表同一節點的引擎檔案必須全部匹配。因此，引擎 1 的 property 檔案將在下面的所有 SymmetricDS 伺服器中完全相同。這也意味著原始安裝的 security 資料夾應該用於所有未來的集群添加，以便可以解密 db.password。


## 雙負載平衡器 Dual Load Balancer


![gh](https://raw.githubusercontent.com/singyichen/images/main/images/symmetricds-cluster-diagram-with-dual-load-balancers.png)


在集群設置中，也可以使用兩個負載平衡器或兩個負載平衡器終點。以下是一個簡單的雙向複製設置的範例，包含每側的負載平衡器。這將為兩個高流量關鍵節點提供高可用性和擴展性。同樣，所有其他原則都適用於設置集群啟用等。此時，兩個節點 1 引擎的 sync.url 將匹配並且是左側負載平衡器的 URL。通過將右側端點的負載平衡器提供為節點 2 引擎檔案的 sync.url，也會發生類似的設置。

## 零售店兩層部署範例


![gh](https://raw.githubusercontent.com/singyichen/images/main/images/symmetricds-Two-Tier-Retail-Store-Deployment-Example.png)


展示的零售示例代表了一個樹形層次結構，其中一個中央辦公室節點通過連線與一個或多個子節點（ POS 工作站）相連。資訊從中央辦公室節點流向個別的註冊機，反之亦然，但從不在註冊機之間流動。


## 零售店三層部署範例 - 商店伺服器


![gh](https://raw.githubusercontent.com/singyichen/images/main/images/symmetricds-Three-Tier-In-Store-Server-Retail-Store-Deployment-Example.png)



也可以使用更複雜的組織架構。例如，如果擴展相同的零售示例以在每個商店中包含商店伺服器來執行開店、對賬註冊機、分配員工等任務，可以使用一種新的配置方法來創建三層層次結構。最高層是集中式資料庫，與每個商店伺服器的資料庫相連接。商店伺服器轉而與商店中的個別銷售點工作站通信。這樣，每個註冊機的資料可以在商店伺服器上累積，然後發送到中央辦公室。同樣，來自中央辦公室的資料可以在商店伺服器中暫存，然後根據註冊機進行過濾，再發送到每個註冊機。


## 零售店三層部署範例 - 區域伺服器


![gh](https://raw.githubusercontent.com/singyichen/images/main/images/symmetricds-Three-Tier-Regional-Server-Retail-Store-Deployment-Example.png)


最後一個範例再次擴展了我們最初的零售店兩層架構，按世界上的“地區”來組織商店。這種三層架構將引入新的區域伺服器（和相應的區域資料庫），其將整合區域伺服器負責的商店的特定資訊。因此，這種情況下的層級是中央辦公室伺服器、區域伺服器和個別商店註冊機。


這些只是如何在 SymmetricDS 中組織節點的三個常見範例。儘管上面的範例是針對零售業的，但它們可以應用於各種應用領域的組織架構。