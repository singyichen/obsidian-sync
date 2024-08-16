---
created: 2024-02-05T14:13
updated: 2024-08-16T13:32
title: Untitled
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
# 🚀 frontend

- [ ] []()
- [ ] []()

```
├── .github
│   └──workflows              # 放置 CICD yml 設定檔
├── .husky                    # Git hooks 設定
├── node_modules              # 相依套件
├── packages
│   ├── backstage             # 大後台
│	│   └── .env.development  ## 大後台開發環境環境變數檔案，通常放置開發環境後端URL，結尾為 /api/back-stage
│   ├── dayday-assess         # 日日考核
│	│   └── .env.development  ## 日日考核開發環境環境變數檔案，通常放置開發環境後端 URL，結尾為 /api
│   ├── onekey-pay            # 一鍵發薪
│		│   ├──dist               # 建置後的正式環境檔案
│		│   ├──node_modules       # 相依套件
│		│   ├──public             # 不需要經過 webpack 處理的靜態資源
│		│   ├──src                # 原始碼目錄
│		│		│   ├──assets         # 存放靜態資源檔案
│		│		│   │   ├──data       ## 導覽列項目設定檔
│		│		│   │   ├──fonts      ## 字型
│		│		│   │   ├──icons      ## 圖示
│		│		│   │   ├──images     ## 圖片
│		│		│   │   └──scss       ## scc
│		│		│   ├──components     # 可重複使用的 Vue 元件，依照模組分類
│		│		│   ├──composables    # 存放組合式函數，可以在多個元件之間共享邏輯
│		│		│   ├──const          # 存放常數值，依照模組分類，如：設定項目、列舉值
│		│		│   ├──locales        # 用於國際化(i18n)的語言檔案目錄，依照模組分類
│		│		│   ├──plugins        # Vue 外掛目錄，用於新增全域級功能到 Vue
│		│		│   ├──router         # 定義應用程式的路由結構，依照模組分類
│		│		│   ├──store          # Vuex 狀態管理相關檔案，用於集中管理應用程式的狀態，依照模組分類，介接 API 及回傳資料整理
│		│		│   ├──utils          # 工具函數目錄，重複使用的輔助函數
│		│		│   ├──views          # 視圖元件目錄，通常包含頁面級的 Vue 元件，依照模組分類
│		│		│   ├──App.vue        # 應用程式的根元件
│		│		│   └──main.js.       # 應用程式的入口檔案，在此建立 Vue 實例並掛載到 DOM
│		│   └──.env.development   ## 一鍵發薪開發環境環境變數檔案，通常放置開發環境後端 URL，結尾為 /api/onekey-pay
│   └── shared-library        # 存放可以在整個專案中共享的程式庫、工具函數和通用邏輯
│   .browserslistrc           # 瀏覽器支援列表設定
│   .eslintrc.cjs             # ESLint 設定檔
│   .gitignore.               # Git 忽略檔案設定
│   .gitkeep                  # 維護目錄結構
│   .npmrc                    # NPM 設定檔
│   .prettierrc.js            # Prettier 設定檔
│   commitlint.config.js.     # Commit 訊息規範設定
│   lerna.json.               # Lerna 設定檔
│   package.json              # 專案相依性和腳本設定
│   README.md                 # 專案說明文件
└── yarn.lock                 # Yarn 相依性鎖定檔案
```