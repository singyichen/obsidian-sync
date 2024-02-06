---
created: 2024-02-05T14:13
updated: 2024-02-06T23:39
title: TaskScheduler
description: 
author: mandy
aliases: 
category: data integration
tags:
  - task
  - schedule
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
# 🚀 Task Scheduler

- [ ] [使用工作排程器執行批次檔](https://snoopy30485.github.io/2019/01/23/%E4%BD%BF%E7%94%A8%E5%B7%A5%E4%BD%9C%E6%8E%92%E7%A8%8B%E5%99%A8%E5%9F%B7%E8%A1%8C%E6%89%B9%E6%AC%A1%E6%AA%94/)
- [ ] [Windows 工作排程](https://medium.com/coding-learning-sharing/windows-%E5%B7%A5%E4%BD%9C%E6%8E%92%E7%A8%8B-56989747a1ce)
- [ ] [PowerShell 練習 - 用 PowerShell 設定 Windows 排程跑 PowerShell](https://blog.darkthread.net/blog/psfaq-setup-schtask/)
- [ ] [PowerShell script won't execute as a Windows scheduled task](https://stackoverflow.com/questions/13015245/powershell-script-wont-execute-as-a-windows-scheduled-task/25172234#25172234)
- [ ] [[PowerShell] 如何撰寫以及執行 powershell script](https://medium.com/edward-hong-%E6%8A%80%E8%A1%93%E7%AD%86%E8%A8%98/powershell-%E5%A6%82%E4%BD%95%E6%92%B0%E5%AF%AB%E4%BB%A5%E5%8F%8A%E5%9F%B7%E8%A1%8C-powershell-script-51b6fc7cf099)
- [ ] [如何利用 PowerShell 自動將應用程式註冊到工作排程器 (Task Scheduler)](https://blog.miniasp.com/post/2021/09/13/PowerShell-with-Task-Scheduler-using-ScheduledTasks-Module)

# 需求
- 此文件說明如何使用工作排程器執行 PowerShell (以管理員身分)，執行 Symmetricds 做資料庫資料初始化

# 準備 Powershell 需要執行的檔案
## 撰寫 Powershell Script ( .ps1 檔案)
- 在資料夾 `bin` 中新增一個檔案 `insert_Leader_data.ps1`
- Get-Date：顯示時間

```ps1
\\ insert_Leader_data.ps1
Get-Date
cd D:\mandy\Project\symmetricds\mssql2postgres\bin
.\dbimport -e server-000 ACPMA.sql
.\dbimport -e server-000 ACPMB.sql
.\dbimport -e server-000 ACPTA.sql
.\dbimport -e server-000 ACPTB.sql
Get-Date
```

## 將所有由 client 匯出的 sql 檔案放置到資料夾 bin 中

![gh](https://raw.githubusercontent.com/singyichen/images/main/images/symmetricds-init-data-need-ps1-and-sql-files.png)


# 工作排程器 Task Scheduler
## 基本觀念
工作排程器 (Task Scheduler) 是 Windows 內建服務之一，可以用來控制在「指定時間或區間內」進行一連串的「工作」執行，這工作可能包含一些命令或應用程式執行。

基本上，工作排程器主要可以區分兩種「觸發條件」來啟動一份排程工作：

### 以時間為基礎的觸發條件 (time-based trigger)

你可以在特定時間點，或是特定時間區間，啟動一個或多個工作。可以只啟動一次工作，也可以週期性地啟動工作。

週期性的工作可以是每天、每週、每月、每年，而最短可從「每分鐘」啟動一次工作。

### 以事件為基礎的觸發條件 (event-based trigger)

你可以設定當系統發生特定事件時自動啟動工作，例如設定開機時、使用者登入時、工作站鎖定時、...等等，還可以設定事件記錄器中特定 事件來源 (Source) 或 事件編號 (Event ID) 發生時觸發。

## 開啟工作排程器並建立一個基本工作
- Windows 系統管理工具 ➔ 工作排程器 ➔ 工作排程器程式庫 ➔ 建立基本工作

![gh](https://raw.githubusercontent.com/singyichen/images/main/images/工作排程器-建立基本工作.png)

## 建立基本工作
- 名稱：`Leader_init_data_task`
- 描述：`從 mssql 的 DB Leader 匯入資料到 postgres`

![gh](https://raw.githubusercontent.com/singyichen/images/main/images/工作排程器-建立基本工作-輸入名稱及描述.png)


## 觸發程序
- 您想要工作在什麼時候開始執行：`僅一次`
- 資料庫資料初始化僅需要做一次即可

![gh](https://raw.githubusercontent.com/singyichen/images/main/images/工作排程器-工作觸發程序.png)

## 觸發程序設定執行時間
- 設定開始執行時間：`此處設定為休假日的時段`

![gh](https://raw.githubusercontent.com/singyichen/images/main/images/工作排程器-工作觸發程序-設定執行時間.png)

## 動作
- 您希望工作執行什麼動作：`啟動程式`

![gh](https://raw.githubusercontent.com/singyichen/images/main/images/工作排程器-動作.png)

## 啟動程式
- 程式或指令碼：`"C:\Program Files\PowerShell\7\pwsh.exe"`
- 新增引數：`
-NoExit -ExecutionPolicy Bypass -File "D:\mandy\Project\symmetricds\mssql2postgres\bin\insert_Leader_data.ps1"`
- 引數說明：
  - `-NoExit`：可檢視其輸出或錯誤訊息
  - `-ExecutionPolicy Bypass`：確保 `.ps1` 被允許執行
  - `-File "path"`：執行檔案路徑

![gh](https://raw.githubusercontent.com/singyichen/images/main/images/工作排程器-啟動程式.png)

## 摘要
- 勾選 `當我按完成時開啟這項工作內容對話方塊`

![gh](https://raw.githubusercontent.com/singyichen/images/main/images/工作排程器-摘要.png)

## 設定以管理員權限執行
- 工作設定完成會出現在列表中
- 勾選 `以最高權限執行`：表示會 `Run as Administrator` 執行

![gh](https://raw.githubusercontent.com/singyichen/images/main/images/工作排程器-任務內容-以最高權限執行.png)
