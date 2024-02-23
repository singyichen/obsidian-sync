---
created: 2024-02-05T14:13
updated: 2024-02-23T11:09
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
├─.gitgub
│  └─workflows
│      dev.yml
│      playground.yml
│      pro.yml 
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

```
**

├── Dockerfile
├── Helpers.js
├── README.md
├── app.js
├── bin
│   └── www
├── config
│   ├── auth.js
│   ├── config.js
│   ├── cors.js
│   ├── employee.js
│   ├── googleStore.js
│   ├── limit.js
│   ├── mail.js
│   ├── queue.js
│   └── storage.js
├── controllers
│   ├── AuthController.js
│   ├── LocationController.js
│   ├── OrganisationController.js
│   ├── UserController.js
│   ├── employee
│   │   ├── BasicPointCategoryController.js
│   │   ├── BasicPointController.js
│   │   ├── BehaviorPointCategoryController.js
│   │   ├── BehaviorPointController.js
│   │   ├── DepartmentController.js
│   │   ├── EmployeeController.js
│   │   ├── InterviewController.js
│   │   ├── JobTenureRecordController.js
│   │   ├── JobTitleController.js
│   │   ├── OrganisationController.js
│   │   ├── PermissionController.js
│   │   ├── PermissionRoleController.js
│   │   ├── PointApplicationController.js
│   │   ├── SeniorityController.js
│   │   ├── SignedUrlController.js
│   │   ├── TaskCandidateController.js
│   │   ├── TaskController.js
│   │   └── TaskMemberController.js
│   └── organisationAdmin
│       ├── OrganisationController.js
│       └── OrganisationScaleController.js
├── docker_compose
│   └── docker-compose.yml
├── docs
│   ├── basicInfo.js
│   ├── common
│   │   ├── AuthController
│   │   │   ├── apiForgetPassword.js
│   │   │   ├── apiResetPassword.js
│   │   │   ├── apiSignIn.js
│   │   │   ├── apiSignInOrganisation.js
│   │   │   └── index.js
│   │   ├── LocationController
│   │   │   ├── apiGetCities.js
│   │   │   ├── apiGetDistricts.js
│   │   │   └── index.js
│   │   ├── OrganisationController
│   │   │   ├── apiIndex.js
│   │   │   └── index.js
│   │   ├── UserController
│   │   │   ├── apiMe.js
│   │   │   ├── index.js
│   │   │   └── updateMyself.js
│   │   └── index.js
│   ├── components.js
│   ├── employee
│   │   ├── BasicPointCategoryController
│   │   │   ├── apiIndex.js
│   │   │   ├── apiStore.js
│   │   │   └── index.js
│   │   ├── BasicPointController
│   │   │   ├── apiDestroy.js
│   │   │   ├── apiIndex.js
│   │   │   ├── apiIndexEditRecord.js
│   │   │   ├── apiShow.js
│   │   │   ├── apiStore.js
│   │   │   ├── apiUpdate.js
│   │   │   └── index.js
│   │   ├── BehaviorPointCategoryController
│   │   │   ├── apiIndex.js
│   │   │   ├── apiStore.js
│   │   │   └── index.js
│   │   ├── BehaviorPointController
│   │   │   ├── apiApplyDepartment.js
│   │   │   ├── apiApplyOrganisation.js
│   │   │   ├── apiDestroy.js
│   │   │   ├── apiIndex.js
│   │   │   ├── apiIndexEditRecord.js
│   │   │   ├── apiShow.js
│   │   │   ├── apiStore.js
│   │   │   ├── apiUpdate.js
│   │   │   └── index.js
│   │   ├── DepartmentController
│   │   │   ├── apiGetDepartmentTree.js
│   │   │   ├── apiGetValidParmentDepartments.js
│   │   │   ├── apiIndex.js
│   │   │   ├── apiRemove.js
│   │   │   ├── apiStore.js
│   │   │   ├── apiUpdate.js
│   │   │   └── index.js
│   │   ├── EmployeeController
│   │   │   ├── apiActivateEmployee.js
│   │   │   ├── apiBatchExport.js
│   │   │   ├── apiBatchImport.js
│   │   │   ├── apiBatchUpdate.js
│   │   │   ├── apiGetCurrentEmployee.js
│   │   │   ├── apiGetImportEmployeeTemplate.js
│   │   │   ├── apiIndex.js
│   │   │   ├── apiIndexAvailablyPerPermissionRole.js
│   │   │   ├── apiIndexPerDepartment.js
│   │   │   ├── apiIndexPerPermissionRole.js
│   │   │   ├── apiRemove.js
│   │   │   ├── apiSendActivationEmail.js
│   │   │   ├── apiShow.js
│   │   │   ├── apiStore.js
│   │   │   ├── apiUpdate.js
│   │   │   └── index.js
│   │   ├── InterviewController
│   │   │   ├── apiAgree.js
│   │   │   ├── apiAllList.js
│   │   │   ├── apiDelete.js
│   │   │   ├── apiIndex.js
│   │   │   ├── apiManage.js
│   │   │   ├── apiNotAgree.js
│   │   │   ├── apiShow.js
│   │   │   ├── apiStore.js
│   │   │   ├── apiUpdate.js
│   │   │   └── index.js
│   │   ├── JobTenureRecordsController
│   │   │   ├── apiIndexPerEmployee.js
│   │   │   ├── apiSync.js
│   │   │   └── index.js
│   │   ├── JobTitleController
│   │   │   ├── apiEliminate.js
│   │   │   ├── apiIndex.js
│   │   │   ├── apiStore.js
│   │   │   ├── apiUpdate.js
│   │   │   └── index.js
│   │   ├── OrganisationController
│   │   │   ├── apiGetCurrentOrganisation.js
│   │   │   ├── apiUpdateCurrentOrganisation.js
│   │   │   └── index.js
│   │   ├── PermissionController
│   │   │   ├── apiIndex.js
│   │   │   └── index.js
│   │   ├── PermissionRoleController
│   │   │   ├── apiAddEmployees.js
│   │   │   ├── apiIndex.js

│   │   │   ├── apiRemove.js

│   │   │   ├── apiRemoveEmployees.js

│   │   │   ├── apiShow.js

│   │   │   ├── apiStore.js

│   │   │   ├── apiUpdate.js

│   │   │   └── index.js

│   │   ├── PointApplicationController

│   │   │   ├── apiAudit.js

│   │   │   ├── apiAuditorCandidates.js

│   │   │   ├── apiIndex.js

│   │   │   ├── apiStore.js

│   │   │   └── index.js

│   │   ├── SeniorityController

│   │   │   ├── apiShow.js

│   │   │   ├── apiStore.js

│   │   │   ├── apiUpdate.js

│   │   │   └── index.js

│   │   ├── SignedUrlController

│   │   │   ├── apiStore.js

│   │   │   └── index.js

│   │   ├── TaskCandidateController

│   │   │   ├── apiApply.js

│   │   │   ├── apiApproval.js

│   │   │   ├── apiDelete.js

│   │   │   ├── apiIndex.js

│   │   │   └── index.js

│   │   ├── TaskController

│   │   │   ├── apiClose.js

│   │   │   ├── apiDelete.js

│   │   │   ├── apiIndex.js

│   │   │   ├── apiIndexMe.js

│   │   │   ├── apiReplaceSupervisor.js

│   │   │   ├── apiShow.js

│   │   │   ├── apiStore.js

│   │   │   ├── apiUpdate.js

│   │   │   └── index.js

│   │   ├── TaskMemberController

│   │   │   ├── apiDelete.js

│   │   │   ├── apiIndex.js

│   │   │   ├── apiRejectQuit.js

│   │   │   ├── apiStore.js

│   │   │   ├── apiUpdate.js

│   │   │   └── index.js

│   │   └── index.js

│   ├── index.js

│   ├── organisationAdmin

│   │   ├── OrganisationController

│   │   │   ├── apiGetScales.js

│   │   │   ├── apiStore.js

│   │   │   └── index.js

│   │   ├── OrganisationOfficialDataController

│   │   │   ├── apiGetOrganisationOfficialData.js

│   │   │   └── index.js

│   │   └── index.js

│   └── path.js

├── ecosystem.config.js

├── gcp_credentials

├── handlers

│   └── errorHandlers.js

├── helpers

│   ├── logHelpers.js

│   ├── mailHelper.js

│   ├── queueHelper.js

│   └── stringHelpers.js

├── logs

├── middleware

│   ├── authJwt.js

│   ├── customErrorHandler.js

│   ├── index.js

│   ├── validateReq.js

│   └── verifySignUp.js

├── migrations

│   ├── 20220317021155-create-user.js

│   ├── 20220319092358-create-locations.js

│   ├── 20220322084812-create-interview.js

│   ├── 20220324062909-create-organisation.js

│   ├── 20220324070713-create-organisation-scale.js

│   ├── 20220328081035-create-organisation-official-data.js

│   ├── 20220329230343-create-basic-point-category.js

│   ├── 20220330085520-create-employee.js

│   ├── 20220330090901-change-column-interview.js

│   ├── 20220330093202-create-department.js

│   ├── 20220401055052-add-column-interview.js

│   ├── 20220401063506-add-columns-in-users-table.js

│   ├── 20220404064545-create-employee-latest-number.js

│   ├── 20220406103107-create_queue_table.js

│   ├── 20220408040915-add-departmentId-in-employees-table.js

│   ├── 20220408092630-add-employee-quantity-in-departments-table.js

│   ├── 20220409090515-create-job-title.js

│   ├── 20220411033751-add-employeeState-in-employees-table.js

│   ├── 20220412020132-add-deletedAt-in-interviews-table.js

│   ├── 20220412033420-create-basic-point.js

│   ├── 20220413014222-change-employeeNumber-in-employees-table.js

│   ├── 20220413072234-remove-isManager-column-in-employees-table.js

│   ├── 20220419184625-create-seniority.js

│   ├── 20220420131136-drop-employee-quantity-in-departments-table.js

│   ├── 20220421023701-add-initPoint-in-employees-table.js

│   ├── 20220421062803-add-avatar-in-users.js

│   ├── 20220421083327-rename-interviews-change-Interviews-table.js

│   ├── 20220421094952-remove-deletedAt-in-Interviews-table.js

│   ├── 20220422025946-create-password-reset.js

│   ├── 20220424115442-create-permission-type.js

│   ├── 20220424115854-create-permission-type-permission-role.js

│   ├── 20220424120026-create-permission-role.js

│   ├── 20220424120040-create-permission.js

│   ├── 20220425073421-create-employee-basic-point.js

│   ├── 20220426045450-add-permissionRoleId-in-employees-table.js

│   ├── 20220426064942-add-permissionRoleDescription-in-permissionRoles-table.js

│   ├── 20220426073436-create-user-organisation.js

│   ├── 20220426073826-create-behavior-point-category.js

│   ├── 20220426110315-alter-userId-in-employees-table.js

│   ├── 20220426111731-create-behavior-point.js

│   ├── 20220427011936-create-employee-behavior-point.js

│   ├── 20220427071954-add-column-in-employees-table.js

│   ├── 20220428060116-create-basic-point-edit-record.js

│   ├── 20220429025056-alter-permission-type-permission-roles-table.js

│   ├── 20220503025245-change_body_length_in_oxen_queue.js

│   ├── 20220503052943-remove_password_reset_index.js

│   ├── 20220503074839-add-activation-identifier-in-employees-table.js

│   ├── 20220503090737-alter-employees-table.js

│   ├── 20220504115329-alter-employees-table.js

│   ├── 20220505045839-add-columns-in-employees-table.js

│   ├── 20220506095354-create-task.js

│   ├── 20220506104758-create-job-tenure-record.js

│   ├── 20220511080050-create-department-behavior-point.js

│   ├── 20220512030954-create-task-members.js

│   ├── 20220512031606-create-task-candidates.js

│   ├── 20220513080354-create-behavior-point-edit-records.js

│   ├── 20220516090921-add-organisationId-in-task-table.js

│   ├── 20220519110735-remove-candidateState-in-taskCandidates-table.js

│   ├── 20220519151417-create-task-point-items.js

│   ├── 20220524012718-add-memberState-in-taskMembers-table.js

│   ├── 20220526032421-create-point-application.js

│   └── 20220526032550-create-point-application-item.js

├── models

│   ├── basicpoint.js

│   ├── basicpointcategory.js

│   ├── basicpointeditrecord.js

│   ├── behaviorpoint.js

│   ├── behaviorpointcategory.js

│   ├── behaviorpointeditrecords.js

│   ├── department.js

│   ├── departmentbehaviorpoint.js

│   ├── employee.js

│   ├── employeebasicpoint.js

│   ├── employeebehaviorpoint.js

│   ├── employeelatestnumber.js

│   ├── index.js

│   ├── interview.js

│   ├── jobtenurerecord.js

│   ├── jobtitle.js

│   ├── location.js

│   ├── organisation.js

│   ├── organisationofficialdata.js

│   ├── organisationscale.js

│   ├── passwordreset.js

│   ├── permission.js

│   ├── permissionrole.js

│   ├── permissiontype.js

│   ├── permissiontypepermissionrole.js

│   ├── pointapplication.js

│   ├── pointapplicationitem.js

│   ├── seniority.js

│   ├── task.js

│   ├── taskcandidate.js

│   ├── taskmember.js

│   ├── taskpointitem.js

│   ├── user.js

│   └── userorganisation.js

├── package-lock.json

├── package.json

├── public

│   ├── index.html

│   └── stylesheets

│       └── style.css

├── requests

│   ├── common

│   │   ├── AuthController

│   │   │   ├── forgetPasswordSchema.js

│   │   │   ├── registerSchema.js

│   │   │   ├── resetPasswordSchema.js

│   │   │   ├── signInOrganisationSchema.js

│   │   │   └── signInSchema.js

│   │   └── UserController

│   │       └── updateMyselfSchema.js

│   ├── employee

│   │   ├── BasicPointCategoryController

│   │   │   └── storeSchema.js

│   │   ├── BasicPointController

│   │   │   ├── destroySchema.js

│   │   │   ├── indexEditRecordsParamsSchema.js

│   │   │   ├── indexEditRecordsQuerySchema.js

│   │   │   ├── indexSchema.js

│   │   │   ├── showSchema.js

│   │   │   ├── storeSchema.js

│   │   │   └── updateSchema.js

│   │   ├── BehaviorPointCategoryController

│   │   │   └── storeSchema.js

│   │   ├── BehaviorPointController

│   │   │   ├── applyDepartmentBodySchema.js

│   │   │   ├── applyDepartmentParamsSchema.js

│   │   │   ├── applyOrganisationSchema.js

│   │   │   ├── destroySchema.js

│   │   │   ├── indexEditRecordsParamsSchema.js

│   │   │   ├── indexEditRecordsQuerySchema.js

│   │   │   ├── indexSchema.js

│   │   │   ├── showSchema.js

│   │   │   ├── storeSchema.js

│   │   │   └── updateSchema.js

│   │   ├── DepartmentController

│   │   │   ├── getValidParentDepartmentsSchema.js

│   │   │   ├── patchParamsSchema.js

│   │   │   ├── patchSchema.js

│   │   │   ├── removeSchema.js

│   │   │   └── storeSchema.js

│   │   ├── EmployeeController

│   │   │   ├── activateSchema.js

│   │   │   ├── batchExportSchema.js

│   │   │   ├── batchUpdateSchema.js

│   │   │   ├── deleteSchema.js

│   │   │   ├── indexAvailablyPerPermissionRoleParamsSchema.js

│   │   │   ├── indexAvailablyPerPermissionRoleQuerySchema.js

│   │   │   ├── indexPerDepartmentSchema.js

│   │   │   ├── indexPerPermissionRoleParamsSchema.js

│   │   │   ├── indexSchema.js

│   │   │   ├── patchParamsSchema.js

│   │   │   ├── patchSchema.js

│   │   │   ├── sendActivationEmailSchema.js

│   │   │   ├── showSchema.js

│   │   │   └── storeSchema.js

│   │   ├── InterviewController

│   │   │   ├── allListSchema.js

│   │   │   ├── destroySchema.js

│   │   │   ├── indexSchema.js

│   │   │   ├── managerListSchema.js

│   │   │   ├── putParamsSchema.js

│   │   │   ├── showSchema.js

│   │   │   ├── storeSchema.js

│   │   │   └── updateSchema.js

│   │   ├── JobTenureRecordController

│   │   │   ├── indexPerEmployeeSchema.js

│   │   │   └── syncSchema.js

│   │   ├── JobTitleController

│   │   │   ├── deleteSchema.js

│   │   │   ├── storeSchema.js

│   │   │   └── updateSchema.js

│   │   ├── OrganisationController

│   │   │   └── updateCurrentOrganisationSchema.js

│   │   ├── PermissionRoleController

│   │   │   ├── addEmployeesParamsSchema.js

│   │   │   ├── addEmployeesSchema.js

│   │   │   ├── removeEmployeesParamsSchema.js

│   │   │   ├── removeEmployeesSchema.js

│   │   │   ├── removeSchema.js

│   │   │   ├── showSchema.js

│   │   │   ├── storeSchema.js

│   │   │   ├── updateParamsSchema.js

│   │   │   └── updateSchema.js

│   │   ├── PointApplicationController

│   │   │   ├── auditApplicationSchema.js

│   │   │   ├── getAuditorCandidatesSchema.js

│   │   │   ├── indexSchema.js

│   │   │   └── storeSchema.js

│   │   ├── SeniorityController

│   │   │   ├── storeSchema.js

│   │   │   └── updateSchema.js

│   │   ├── SignedUrlController

│   │   │   └── storeSchema.js

│   │   ├── TaskCandidateController

│   │   │   ├── approvalSchema.js

│   │   │   ├── destroySchema.js

│   │   │   ├── indexSchema.js

│   │   │   └── showSchema.js

│   │   ├── TaskController

│   │   │   ├── indexMeSchema.js

│   │   │   ├── indexSchema.js

│   │   │   ├── replaceSupervisorSchema.js

│   │   │   ├── showSchema.js

│   │   │   ├── storeSchema.js

│   │   │   └── updateSchema.js

│   │   └── TaskMemberController

│   │       ├── destroySchema.js

│   │       ├── indexParamsSchema.js

│   │       ├── indexSchema.js

│   │       ├── showSchema.js

│   │       ├── storeSchema.js

│   │       └── updateSchema.js

│   ├── general.js

│   └── organisationAdmin

│       └── OrganisationController

│           ├── getOrganisationOfficialDataSchema.js

│           └── storeSchema.js

├── resources

│   ├── AsyncResource.js

│   ├── BasicPointCategoryResource.js

│   ├── BasicPointEditRecordResource.js

│   ├── BasicPointResource.js

│   ├── BehaviorPointCategroyResource.js

│   ├── BehaviorPointEditRecordResource.js

│   ├── BehaviorPointResource.js

│   ├── BehaviorPointWithAvailableResource.js

│   ├── DepartmentResource.js

│   ├── EmployeeNameOnlyResource.js

│   ├── EmployeeResource.js

│   ├── EmployeeResourceInDetail.js

│   ├── InterviewResource.js

│   ├── JobTenureRecordResource.js

│   ├── JobTitleResource.js

│   ├── OrganisationIndexResource.js

│   ├── OrganisationOfficialDataResource.js

│   ├── OrganisationShowResource.js

│   ├── PermissionResource.js

│   ├── PermissionRoleResource.js

│   ├── PermissionRoleShowResource.js

│   ├── PermissionTypeResource.js

│   ├── PointApplicationItemResource.js

│   ├── PointApplicationResource.js

│   ├── SeniorityResource.js

│   ├── TaskCandidateResource.js

│   ├── TaskMemberResource.js

│   ├── TaskResource.js

│   ├── TaskResourceDetail.js

│   ├── UserResource.js

│   └── views

│       └── emails

│           ├── activateEmployee.js

│           └── resetPassword.js

├── routes

│   ├── api

│   │   ├── common

│   │   │   ├── index.js

│   │   │   ├── noToken

│   │   │   │   ├── auth.js

│   │   │   │   ├── index.js

│   │   │   │   └── permissions.js

│   │   │   ├── stepOneToken

│   │   │   │   ├── auth.js

│   │   │   │   ├── index.js

│   │   │   │   ├── locations.js

│   │   │   │   ├── organisations.js

│   │   │   │   └── users.js

│   │   │   └── stepTwoToken

│   │   │       └── index.js

│   │   ├── employee

│   │   │   ├── index.js

│   │   │   ├── noToken

│   │   │   │   ├── employees.js

│   │   │   │   └── index.js

│   │   │   ├── stepOneToken

│   │   │   │   └── index.js

│   │   │   └── stepTwoToken

│   │   │       ├── basicPointCategories.js

│   │   │       ├── basicPoints.js

│   │   │       ├── behaviorPointCategories.js

│   │   │       ├── behaviorPoints.js

│   │   │       ├── departments.js

│   │   │       ├── employees.js

│   │   │       ├── index.js

│   │   │       ├── interviews.js

│   │   │       ├── jobTenureRecords.js

│   │   │       ├── jobTitles.js

│   │   │       ├── organisations.js

│   │   │       ├── permissionRoles.js

│   │   │       ├── permissions.js

│   │   │       ├── pointApplications.js

│   │   │       ├── seniority.js

│   │   │       ├── signedUrl.js

│   │   │       ├── taskCandidates.js

│   │   │       ├── taskMembers.js

│   │   │       └── tasks.js

│   │   ├── index.js

│   │   └── organisationAdmin

│   │       ├── index.js

│   │       ├── noToken

│   │       │   └── index.js

│   │       ├── stepOneToken
│   │       │   ├── index.j
│   │       │   ├── organisationScales.js
│   │       │   └── organisations.js
│   │       └── stepTwoToken
│   │           └── index.js
│   └── index.js
├── scheduleTasks.js
├── seeders
│   ├── 20220320093134-seed-locations.js
│   ├── 20220324071003-seed-organisation-scales.js
│   ├── 20220424125441-seed-permission-types.js
│   └── 20220424131139-seed-permissions.js
├── services
│   └── CloudStorage.js
├── storage
│   └── temp
├── uploads
└── worker.js

**
```