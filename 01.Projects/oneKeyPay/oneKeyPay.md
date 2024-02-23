---
created: 2024-02-05T14:13
updated: 2024-02-23T14:08
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
├── resources               # 回應的資料定義，controller 層輸出的資源對象
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
│   scheduleTasks.js        # 排程設定檔
│   worker.js。             # 排程設定檔
```

