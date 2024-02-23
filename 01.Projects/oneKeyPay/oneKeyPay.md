---
created: 2024-02-05T14:13
updated: 2024-02-23T14:00
title: oneKeyPay
description: 
author: mandy
aliases: 
category: 
tags: 
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
# 🚀 oneKeyPay

- [ ] []()
- [ ] []()

```
├── app.js - 入口檔案
├── bin - 可執行檔案目錄 
│   └── www - www 檔案
├── config - 配置檔案目錄
├── controllers - 控制器目錄
│   ├── common - 公共控制器
│   ├── employee - 員工模組控制器
│   └── organisationAdmin - 組織管理模組控制器
├── docs - 文件目錄
├── helpers - 助手函數目錄
├── middleware - 中間件目錄 
├── migrations - 數據庫遷移腳本目錄
├── models - 模型目錄
├── public - 公共文件目錄 
├── requests - 請求驗證schema目錄
├── resources - 資源類目錄
├── routes - 路由目錄
├── seeders - 數據填充腳本目錄
├── services - 服務類目錄
├── storage - 儲存目錄
└── uploads - 上傳檔案目錄
```

```
├── app.js - 使用 express 初始化的應用入口 
├── bin - 存放www檔案的可執行腳本 
├── config - 配置檔案目錄 
│ ├── auth.js - 授權和認證相關配置 
│ ├── cors.js - 跨域相關配置 
│ ├── db.js - 數據庫連接配置 
│ └── etc - 其他 configs 
├── controllers - 處理路由並執行業務邏輯的控制器 
│ ├── common 
│ ├── employee 
│ └── organisationAdmin 
├── docs - 接口文檔目錄 
├── helpers - 可重用的輔助方法目錄 
├── middleware - express 中間件目錄 
│ ├── auth - 授權 authenticaton 驗證 
│ ├── validate - 請求數據驗證 
├── migrations - 數據庫遷移腳本目錄 
├── models - 數據庫模型與業務實體對象目錄 
├── public - 靜態文件目錄 
├── requests - 請求參數驗證 schema 目錄 
├── resources - controller 層輸出的資源對象目錄 
├── routes - 路由目錄 
│ ├── api 
│ │ ├── common 
│ │ ├── employee 
│ │ └── organisationAdmin 
├── services - 業務邏輯层服務 
├── storage - 本地文件系統存儲目錄 
├── uploads - 用戶上傳文件的存儲目錄
├── Dockerfile
```


```
├── .github                  
│   └──workflows            # 放置 CICD yml 設定檔
├── basicInfo               # 各系統業務邏輯相關的常數配置信息     
│   ├──backStage
│   ├──daydayAssess
│   └──ondkeyPay
├── bin                     # 存放 www 檔案，為程式進入點
├── config                  # 系統中參數進行可配置的限制設定，資料來源為 .env
├── controllers             # 處理路由並執行業務邏輯的控制器
│   ├──backStage
│   ├──daydayAssess
│   └──ondkeyPay
├── docker_compose          # 放置 docker-compose yml 設定檔
│   └── docker-compose.yml
├── docs                    # swagger 文件
│   ├──backStage
│   ├──daydayAssess
│   └──ondkeyPay
├── gcp_credentials         # GCP 部署設定檔
├── handlers                # 處理器
│   └── errorHandlers.js    # 應用層面的統一錯誤處理中心
├── helpers                 # 可重用的輔助方法
│   ├── logHelpers.js
│   ├── mailHelper.js
│   ├── queueHelper.js
│   ├── stringHelpers.js
│   └── timeHelper.js
├── logs                    # 日誌
├── middleware              # 中間件
├── migrations              # 數據庫遷移
├── models                  # Sequelize 模型，數據庫模型與業務實體對象
├── public                  # 
├── requests                # 請求參數驗證 schema 定義
│   ├──backStage
│   ├──daydayAssess
│   └──ondkeyPay
├── resources               # 回應的資料定義
│   ├──backStage
│   ├──daydayAssess
│   └──ondkeyPay
├── routes                  # 路由
│   ├──api
│   │   ├──backStage
│   │   ├──daydayAssess
│   │   └──ondkeyPay
│   └── index.js
├── salaryCalculation       # 薪資計算邏輯
├── scheduleJobs            # 排程
│   ├──backStage
│   ├──daydayAssess
│   └──ondkeyPay
├── seeders                 # 存放數據庫的初始或測試用的模擬數據
├── services                # 存儲客戶端對象實例化配置方式，用來與 Google Cloud Storage 進行交互
├── storage                 # 本地文件系統存儲資料夾 
├── tests                   # 測試資料夾
├── uploads                 # 用戶上傳文件的存儲資料夾
│   .dockerignore
│   .env
│   .env.example
│   .gitignore
│   .sequelizerc
│   app.js                  # 使用 express 初始化的應用入口 
│   Dockerfile
│   ecosystem.config.js
│   Helper.js
│   package-lock.json
│   package.json
│   README.md
│   scheduleTasks.js
│   worker.js
```

