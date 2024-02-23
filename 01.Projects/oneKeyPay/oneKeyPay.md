---
created: 2024-02-05T14:13
updated: 2024-02-23T10:33
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
│  .dockerignore                       
│  .env
│  .env.example
│  .gitignore
│  .sequelizerc
│  app.js
│  Dockerfile
│  ecosystem.config.js
│  Dockerfile
│  Helpers.js
│  package-lock.json
│  package.json
│  README.md
│  scheduleTasks.js
│  README.md
│  worker.js
│
├─config
│    casbinConfig.js
│    
├─logs
│  ├─error
│  │      
│  └─info
│
├─prisma
│  └─  schema.prisma
│
├─src
│  ├─api
│  │      dateTimeApi.js
│  │      
│  ├─base
│  │      base.controller.js
│  │      base.response.js
│  │      base.result.js
│  │
│  ├─casbin
│  │  ├─abac
│  │  │   abac_model.conf    
│  │  │   abac_policy.csv
│  │  │
│  │  └─rbac
│  │      rbac_model.conf    
│  │      rbac_policy.csv 
│  │      
│  ├─modules
│  │  └─public
│  │     ├─basic
│  │     │  ├─controller
│  │     │  │      loginController.js
│  │     │  │      logoutController.js
│  │     │  │      
│  │     │  ├─service
│  │     │  │      logoutService.js
│  │     │  │      verificationService.js
│  │     │  │      
│  │     │  └─validator
│  │     │          login.js
│  │     │          logout.js
│  │     │          verifyJWT.js
│  │     │
│  │     ├─customer
│  │     │  ├─controller
│  │     │  │      customerController.js
│  │     │  │      
│  │     │  ├─service
│  │     │  │      customerService.js
│  │     │  │      
│  │     │  └─validator
│  │     │          customer.js
│  │     │          deleteCustomer.js
│  │     │          findAllCustomer.js
│  │     │          findOneCustomer.js
│  │     │
│  │     ├─order
│  │     │  ├─controller
│  │     │  │      orderController.js
│  │     │  │      
│  │     │  ├─service
│  │     │  │      orderService.js
│  │     │  │      
│  │     │  └─validator
│  │     │          order.js
│  │     │          deleteOrder.js
│  │     │          findAllOrder.js
│  │     │          findOneOrder.js
│  │     │
│  │     ├─orderItem
│  │     │  ├─controller
│  │     │  │      orderItemController.js
│  │     │  │      
│  │     │  ├─service
│  │     │  │      orderItemService.js
│  │     │  │      
│  │     │  └─validator
│  │     │          orderItem.js
│  │     │          deleteOrderItem.js
│  │     │          findAllOrderItem.js
│  │     │          findOneOrderItem.js
│  │     │
│  │     ├─permissions
│  │     │  ├─controller
│  │     │  │      permissionsController.js
│  │     │  │      
│  │     │  ├─service
│  │     │  │      permissionsService.js
│  │     │  │      
│  │     │  └─validator
│  │     │          addPermissionForUser.js
│  │     │          addRoleForUser.js
│  │     │          deletePermissionForUser.js
│  │     │          deleteRoleForUser.js
│  │     │          getPermissionsForUser.js
│  │     │          getUsersForRole.js
│  │     │
│  │     ├─product
│  │     │  ├─controller
│  │     │  │      productController.js
│  │     │  │      
│  │     │  ├─service
│  │     │  │      productService.js
│  │     │  │      
│  │     │  └─validator
│  │     │          product.js
│  │     │          deleteProduct.js
│  │     │          findAllProduct.js
│  │     │          findOneProduct.js
│  │     │
│  │     └─user
│  │        ├─controller
│  │        │      userController.js
│  │        │      
│  │        ├─service
│  │        │      userService.js
│  │        │      
│  │        └─validator
│  │                user.js
│  │                deleteUser.js
│  │                findAllUser.js
│  │                findOneUser.js
│  │                updateOneUser.js
│  │
│  ├─ormService
│  │      prismaClientService.js
│  │      
│  ├─plugin
│  │      casbin.js
│  │      cors.js
│  │      enforcer.js
│  │      env.js
│  │      jwt.js
│  │      logger.js
│  │      router.js
│  │      
│  ├─routes
│  │  │  root.js
│  │  │  
│  │  └─api
│  │     │  
│  │     └─admin
│  │        ├─basic
│  │        │      basic.js
│  │        │
│  │        ├─customer
│  │        │      customer.js
│  │        │
│  │        ├─order
│  │        │      order.js
│  │        │
│  │        ├─orderItem
│  │        │      orderItem.js
│  │        │
│  │        ├─permissions
│  │        │      permissions.js
│  │        │
│  │        ├─product
│  │        │      product.js
│  │        │      
│  │        └─user
│  │               user.js
│  │      
│  ├─utils
│  │      errorInfo.js
│  │      sharedObject.js
│  └─     url.js
│
└─test
    │  config.js
    │  root.test.js
    │  
    └─unit
        │
        └─api
            │
            └─api
                   dateTimeApi.test.js  
```
