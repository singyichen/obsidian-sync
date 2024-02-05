---
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
created: "{{date}} {{time}}"
modified: <% tp.file.last_modified_date("YYYY-MM-DD HH:mm:ss") %>
---
---
creation date: <% tp.file.creation_date() %> 
modification date: <% tp.file.last_modified_date("dddd Do MMMM YYYY HH:mm:ss") %>
---


![](https://pic.sopili.net/pub/emoji/twitter/2/72x72/1f4d6.png)
# {{title}}

- [ ] []()
- [ ] []()

<% tp.web.daily_quote() %>
