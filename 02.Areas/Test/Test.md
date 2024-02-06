---
created: 2024-02-05T14:13
updated: 2024-02-06T15:20
title: Test
description: 測試
author: mandy
aliases: 
category: software development
tags:
  - test
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
# 🚀 Test

- [ ] [Paradigm Shift: How Developer to Tester Ratio Changed From 1:1 to 100:1](https://blog.bytebytego.com/p/ep68-top-architectural-styles?utm_source=profile&utm_medium=reader2)
- [ ] [A compilation of outstanding testing articles (with JavaScript)](https://practica.dev/blog/a-compilation-of-outstanding-testing-articles-with-javaScript/)
- [ ] [Testing in software development: A practical guide](https://learningdaily.dev/testing-in-software-development-a-practical-guide-f2b4d9d51cae)
- [ ] [Best ways to test system functionality](https://blog.bytebytego.com/p/ep82-open-sourcing-over-100-byte?utm_source=profile&utm_medium=reader2)
- [ ] [EP83: Explaining 9 Types of API Testing](https://blog.bytebytego.com/p/ep83-explaining-9-types-of-api-testing?utm_source=profile&utm_medium=reader2)
- [ ] [軟體測試方法](https://ellis-wu.github.io/2015/09/04/test-method-introduction/)
- [ ] [初嚐軟體測試(Software Testing) ](https://medium.com/jimmy-wang/%E5%88%9D%E5%98%97%E8%BB%9F%E9%AB%94%E6%B8%AC%E8%A9%A6-software-testing-3c7d786525a9)
- [ ] [《軟體工程篇 - 5》 — 軟體測試方法 (Software Testing)](https://ithelp.ithome.com.tw/articles/10337526)
- [ ] [軟體測試分類和方法](https://www.796t.com/content/1542985090.html)
- [ ] [測試二三事（上）｜還記得你說，要和我寫測試](https://hackmd.io/@Heidi-Liu/learn-about-testing)

# Types

![gh](https://raw.githubusercontent.com/singyichen/images/main/images/UnitTest-three-types-of-test.png)

![gh](https://raw.githubusercontent.com/singyichen/images/main/images/The-9-Testing-Types.gif)

![gh](https://raw.githubusercontent.com/singyichen/images/main/images/Explaining-9-types-of-API-testing.gif)

# 比較表

| 測試類型 |          單元測試          |        整合測試        |          端對端測試           |          壓力測試          |                負載測試                |            效能測試            |
|:--------:|:--------------------------:|:----------------------:|:-----------------------------:|:--------------------------:|:--------------------------------------:|:------------------------------:|
| 測試目的 | 測試程式碼最小單元的正確性 | 測試模組間互動是否正確 | 模擬真實情境,測試系統整體功能 | 測試系統在極限負載下的能力 | 測試系統在預期負載下的回應時間和穩定性 | 測試回應時間、吞吐量等效能指標 |
|   粒度   |            最細            |          中等          |             最粗              |             -              |                   -                    |               -                |
|   速度   |            最快            |           快           |             最慢              |             -              |                   -                    |               -                |
| 涵蓋範圍 |    只覆蓋當前單元程式碼    |      模組間的互動      |           整個系統            |             -              |                   -                    |               -                |
| 用例範例 |  使用測試框架測試一個函式。使用 Mocha、Jest 等框架測試一個函式的輸入輸出。  | 測試路由與控製器的串接。測試 Express 的 Router 中間件路由是否正確。 | 使用 Selenium 模擬瀏覽器操作  |  模擬萬量級使用者同時訪問  |        模擬百量級使用者同時訪問        |   使用高頻請求測試最大吞吐量   |

在不同的測試類型中，所需要保護的面向不太相同，以下是不同測試類型的大致介紹：

## α測試 ( Alpha Testing )

> - α測試主要由內部人員進行,測試新功能是否符合預期並發現早期問題。

### 定義
    - 在開發團隊內部進行的第一階段測試。
### 測試目的
    - 測試新功能是否符合需求規格
    - 發現功能或介面問題
### 測試對象:
    - 主要由開發人員進行測試
    - 有時會加入 product manager
### 測試環境:
    - 內部測試環境
    - 模擬真實使用環境
### 測試內容
    - 單元測試、整合測試
    - 使用者介面測試



## 冒煙測試 ( Smoke Testing )

> - 主要快速檢測關鍵功能在部署後是否正常,以確定後續測試是否可行。

### 定義
    - 對軟體建置、部署後的關鍵功能進行快速測試的一種測試方法。
### 測試目的
    - 驗證關鍵功能在部署後是否正常運作
    - 發現軟體最基本的功能缺陷
### 測試方式
    - 執行軟體關鍵工作流,檢查返回結果
    - 重點是測試範圍廣,操作快速
### 常用時機
    - 新版本軟體首次部署上線時
    - 軟體緊急修復Bug後
### 測試指標
    - 軟體關鍵功能的可用性
    - 基本操作的正確性
    - 加載時間
    - UI Rendering


## 單元測試 ( Unit Testing )

> - 主要的是在程式碼基礎上構建測試用例,以提高程式碼的可靠性與可維護性。

### 定義
    - 對軟體中最小的測試單元進行測試,包括個別函式、方法、類別等。
### 測試目的
    - 驗證每個模組的功能是否符合設計
    - 提高程式碼的可維護性
    - 提高程式碼重構的靈活性
    - 促進程式碼的重用
### 測試方式
    - 針對函式的輸入輸出進行測試
    - 模擬調用函式並測試返回結果
    - 隔離外部依賴進行測試
### 常用框架
    - JUnit
    - PyUnit
    - Mocha
    - Jest 等
### 測試指標
    - 測試覆蓋率
    - 代碼錯誤
    - 運行時異常等



## 整合測試 ( Integration Testing )

> - 主要是檢測單個模組單獨測試通過後,組合起來的整體系統是否能正確運行和互動。
### 定義
    - 測試已經單獨測試過的模組組合到一起後,模組間介面的正確性。
### 測試目的
    - 驗證模組或組件之間的介面連接是否正確
    - 發現整合後的問題
### 測試方式
    - Bottom-Up 整合測試
    - Top-Down 整合測試
    - Big-Bang 整合測試
### 測試用例
    - 測試兩個模組之間的資料交換
    - 測試多個模組之間的介面
### 測試指標
    - 模組間的互通性
    - 系統功能的正確性
    - 效能指標如延遲和吞吐量等


## 回歸測試（ Regression Test ）

> - 主要是修改程式碼後重新執行測試,減少修改對原功能造成的風險。

### 定義
    - 修改了原有程式碼後,再次執行測試來驗證原有功能是否受到影響的一種測試技術。
### 測試目的
    - 驗證程式碼或組態變更是否導致現有功能出錯
    - 減少程式碼修改對現有功能造成的影響
### 測試方式
    - 重新跑一次整套測試用例
    - 針對修改部分進行重點回歸測試
### 常用時機
    - 新增功能後
    - 程式碼大規模Refactoring後
    - 系統更新和遷移後
### 測試指標
    - 現有功能的正確性
    - 回歸測試用例是否涵蓋足夠
    - 程式碼品質


## 負載測試 ( Load Testing )

> - 主要是模擬實際負載情況,測試系統整體性能表現是否達標。
> - 負載測試相對於壓力測試的負載更接近系統在現實中的運行環境。

### 定義
    - 負載測試是驗證系統在預期負載條件下性能表現的一種測試方法。
### 測試目的
    - 測試軟硬體在預期負載下的性能
    - 找出系統瓶頸以優化系統
    - 驗證系統穩定性和可靠性
### 測試方式
    - 模擬多個虛擬用戶同時發送請求
    - 持續一定時間向服務器發送請求
    - 請求模式接近實際情境
### 常用工具
    - LoadRunner
    - Apache JMeter
    - Visual Studio Load Test
    - WebLOAD 等
### 測試指標
    - 平均響應時間
    - 峰值響應時間
    - 錯誤率
    - 吞吐量等


## 壓力測試 ( Stress Testing )

> - 主要是通過模擬大量請求造成系統極端壓力,測試系統瓶頸和極限。

### 定義
    - 壓力測試是一種測試軟體在極端負載情況下的穩定性和可靠性的測試方法。
### 測試目的
    - 驗證軟體在突發大量請求的情況下系統的穩定性
    - 找出軟體的瓶頸所在以及極限容量
    - 測試硬體設備在高負載下的性能
### 測試方式
    - 模擬多個虛擬用戶同時發送大量請求
    - 持續不間斷地向服務器發送請求數據包
    - 造成極大的並發讀寫操作
### 常用工具
    - Apache JMeter
    - LoadRunner
    - WebLOAD
    - NeoLoad
### 測試指標
    - 響應時間
    - 錯誤率
    - 吞吐量
    - CPU/內存使用率

## 端對端測試 ( End-to-end Testing )

> - 主要是從用戶角度模擬整個業務流程,測試應用系統的核心功能是否能夠按預期運行。

### 定義
    - 從開始到結束,模擬真實用戶場景測試整個系統的一種測試方法。
### 測試目的
    - 驗證整個系統的工作流是否符合預期
    - 確保核心功能正常運作
### 測試方式
    - 使用真實瀏覽器進行測試
    - 模擬用戶操作驗證各個介面功能
### 常用框架與工具
    - Selenium
    - Cucumber
    - Protractor
    - Cypress
### 測試指標
    - 系統端對端工作流正確性
    - 介面功能正確性
    - 系統穩定性與相容性


## 效能測試 ( Performance Testing )

> - 主要測試系統在標準或峰值負載下系統回應和處理能力的指標,比較優化前後的差異。

### 定義
    - 測試軟硬體系統在預定負載下的性能指標如響應時間、吞吐量等。
### 測試目的
    - 評估系統速度、可擴展性、穩定性
    - 找出效能瓶頸
    - 比較效能優化前後的差異
### 測試指標
    - 響應時間
    - 每秒事務數
    - 吞吐量
    - 錯誤率
    - 並發用戶數等
### 測試方式
    - 在真實硬體環境中注入預定負載
    - 建立模擬環境進行測試
### 常用工具
    - LoadRunner
    - JMeter
    - LoadNinja
    - NeoLoad
    - LoadView 等


## 安全性測試（ Security Testing ) 

> - 主要通過模擬不同方式的攻擊測試系統安全性和防護能力。

### 定義
    - 對系統進行滲透測試和漏洞評估,以發現系統在安全性方面的缺陷。
### 測試目的
    - 發現系統可能存在的安全漏洞
    - 防止系統被非法訪問或破壞
### 測試方式
    - SQL隱碼攻擊、跨站腳本、撞庫攻擊等滲透測試
    - 掃描工具自動檢測漏洞
    - 網站應用程式防火牆測試
### 常見測試項目
    - 驗證/授權系統
    - 資料庫存儲安全性
    - 網路層安全性
    - 應用介面的安全性
### 測試指標
    - 系統漏洞數量和等級分類
    - 入侵檢測率
    - 網站應用程式防火牆封鎖效能


## 模糊測試 ( Fuzz Testing )

> - 主要是通過輸入無效參數的方式測試系統的容錯能力與健壯性。

### 定義
    - 使用隨機無效輸入數據來測試系統健壯性的一種測試方法。
### 測試目的
    - 測試系統面對無效輸入的響應能力
    - 發現未知的系統漏洞
### 測試方式
    - 生成大量隨機不合法輸入
    - 分析系統對模糊輸入的響應
    - 反覆模糊測試發現問題模式
### 常見測試項目
    - 介面輸入欄位測試
    - API參數及返回值測試
    - 檔案上傳測試
### 測試指標
    - 系統崩潰率
    - 發現系統漏洞數
    - 輸入Cases覆蓋範圍






