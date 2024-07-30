---
created: 2024-02-05T14:13
updated: 2024-07-30T16:18
title: devops
description: 
author: mandy
aliases: 
category: software development
tags:
  - devops
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
# 🚀 devops

- [ ] [# [教學] 產生SSH Key並且透過KEY進行免密碼登入](https://xenby.com/b/220-%E6%95%99%E5%AD%B8-%E7%94%A2%E7%94%9Fssh-key%E4%B8%A6%E4%B8%94%E9%80%8F%E9%81%8Ekey%E9%80%B2%E8%A1%8C%E5%85%8D%E5%AF%86%E7%A2%BC%E7%99%BB%E5%85%A5)
- [ ] []()

## 設定 ssh 連線各專案

- 使用 `ssh-keygen`  產生 ssh Key 並且透過 Key 進行免密碼登入
```bash
ssh-keygen
```
- 存放 key 的路徑
```bash
cd .ssh
```
- 取得公鑰 `.pub` ，並於 GCP 的 `安全殼層金鑰` 進行設定