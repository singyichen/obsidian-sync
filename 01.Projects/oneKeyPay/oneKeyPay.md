---
created: 2024-02-05T14:13
updated: 2024-02-23T13:32
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
├── Dockerfile
├── Helpers.js
├── README.md
├── app.js
├── bin
│   └── www
├── config
│   ├── auth.js
│   ├── config.js
│   ├── cors.js
│   ├── employee.js
│   ├── googleStore.js
│   ├── limit.js
│   ├── mail.js
│   ├── queue.js
│   └── storage.js
├── controllers
│   ├── AuthController.js
│   ├── LocationController.js
│   ├── OrganisationController.js
│   ├── UserController.js
│   ├── employee
│   │   ├── BasicPointCategoryController.js
│   │   ├── BasicPointController.js
│   │   ├── BehaviorPointCategoryController.js
│   │   ├── BehaviorPointController.js
│   │   ├── DepartmentController.js
│   │   ├── EmployeeController.js
│   │   ├── InterviewController.js
│   │   ├── JobTenureRecordController.js
│   │   ├── JobTitleController.js
│   │   ├── OrganisationController.js
│   │   ├── PermissionController.js
│   │   ├── PermissionRoleController.js
│   │   ├── PointApplicationController.js
│   │   ├── SeniorityController.js
│   │   ├── SignedUrlController.js
│   │   ├── TaskCandidateController.js
│   │   ├── TaskController.js
│   │   └── TaskMemberController.js
│   └── organisationAdmin
│       ├── OrganisationController.js
│       └── OrganisationScaleController.js
├── docker_compose
│   └── docker-compose.yml
├── docs
│   ├── basicInfo.js
│   ├── common
│   │   ├── AuthController
│   │   ├── LocationController
│   │   ├── OrganisationController
│   │   ├── UserController
│   │   └── index.js
│   ├── components.js
│   ├── employee
│   │   ├── BasicPointCategoryController
│   │   ├── BasicPointController
│   │   ├── BehaviorPointCategoryController
│   │   ├── BehaviorPointController
│   │   ├── DepartmentController
│   │   ├── EmployeeController
│   │   ├── InterviewController
│   │   ├── JobTenureRecordsController
│   │   ├── JobTitleController
│   │   ├── OrganisationController
│   │   ├── PermissionController
│   │   ├── PermissionRoleController
│   │   ├── PointApplicationController
│   │   ├── SeniorityController
│   │   ├── SignedUrlController
│   │   ├── TaskCandidateController
│   │   ├── TaskController
│   │   ├── TaskMemberController
│   │   └── index.js
│   ├── index.js
│   ├── organisationAdmin
│   │   ├── OrganisationController
│   │   ├── OrganisationOfficialDataController
│   │   └── index.js
│   └── path.js
├── ecosystem.config.js
├── gcp_credentials
├── handlers
│   └── errorHandlers.js
├── helpers
│   ├── logHelpers.js
│   ├── mailHelper.js
│   ├── queueHelper.js
│   └── stringHelpers.js
├── logs
├── middleware
│   ├── authJwt.js
│   ├── customErrorHandler.js
│   ├── index.js
│   ├── validateReq.js
│   └── verifySignUp.js
├── migrations
│   ├── 20220317021155-create-user.js
│   ├── 20220319092358-create-locations.js
│   ├── 20220322084812-create-interview.js
│   ├── 20220324062909-create-organisation.js
│   ├── 20220324070713-create-organisation-scale.js
│   ├── 20220328081035-create-organisation-official-data.js
│   ├── 20220329230343-create-basic-point-category.js
│   ├── 20220330085520-create-employee.js
│   ├── 20220330090901-change-column-interview.js
│   ├── 20220330093202-create-department.js
│   ├── 20220401055052-add-column-interview.js
│   ├── 20220401063506-add-columns-in-users-table.js
│   ├── 20220404064545-create-employee-latest-number.js
│   ├── 20220406103107-create_queue_table.js
│   ├── 20220408040915-add-departmentId-in-employees-table.js
│   ├── 20220408092630-add-employee-quantity-in-departments-table.js
│   ├── 20220409090515-create-job-title.js
│   ├── 20220411033751-add-employeeState-in-employees-table.js
│   ├── 20220412020132-add-deletedAt-in-interviews-table.js
│   ├── 20220412033420-create-basic-point.js
│   ├── 20220413014222-change-employeeNumber-in-employees-table.js
│   ├── 20220413072234-remove-isManager-column-in-employees-table.js
│   ├── 20220419184625-create-seniority.js
│   ├── 20220420131136-drop-employee-quantity-in-departments-table.js
│   ├── 20220421023701-add-initPoint-in-employees-table.js
│   ├── 20220421062803-add-avatar-in-users.js
│   ├── 20220421083327-rename-interviews-change-Interviews-table.js
│   ├── 20220421094952-remove-deletedAt-in-Interviews-table.js
│   ├── 20220422025946-create-password-reset.js
│   ├── 20220424115442-create-permission-type.js
│   ├── 20220424115854-create-permission-type-permission-role.js
│   ├── 20220424120026-create-permission-role.js
│   ├── 20220424120040-create-permission.js
│   ├── 20220425073421-create-employee-basic-point.js
│   ├── 20220426045450-add-permissionRoleId-in-employees-table.js
│   ├── 20220426064942-add-permissionRoleDescription-in-permissionRoles-table.js
│   ├── 20220426073436-create-user-organisation.js
│   ├── 20220426073826-create-behavior-point-category.js
│   ├── 20220426110315-alter-userId-in-employees-table.js
│   ├── 20220426111731-create-behavior-point.js
│   ├── 20220427011936-create-employee-behavior-point.js
│   ├── 20220427071954-add-column-in-employees-table.js
│   ├── 20220428060116-create-basic-point-edit-record.js
│   ├── 20220429025056-alter-permission-type-permission-roles-table.js
│   ├── 20220503025245-change_body_length_in_oxen_queue.js
│   ├── 20220503052943-remove_password_reset_index.js
│   ├── 20220503074839-add-activation-identifier-in-employees-table.js
│   ├── 20220503090737-alter-employees-table.js
│   ├── 20220504115329-alter-employees-table.js
│   ├── 20220505045839-add-columns-in-employees-table.js
│   ├── 20220506095354-create-task.js
│   ├── 20220506104758-create-job-tenure-record.js
│   ├── 20220511080050-create-department-behavior-point.js
│   ├── 20220512030954-create-task-members.js
│   ├── 20220512031606-create-task-candidates.js
│   ├── 20220513080354-create-behavior-point-edit-records.js
│   ├── 20220516090921-add-organisationId-in-task-table.js
│   ├── 20220519110735-remove-candidateState-in-taskCandidates-table.js
│   ├── 20220519151417-create-task-point-items.js
│   ├── 20220524012718-add-memberState-in-taskMembers-table.js
│   ├── 20220526032421-create-point-application.js
│   └── 20220526032550-create-point-application-item.js
├── models
│   ├── basicpoint.js
│   ├── basicpointcategory.js
│   ├── basicpointeditrecord.js
│   ├── behaviorpoint.js
│   ├── behaviorpointcategory.js
│   ├── behaviorpointeditrecords.js
│   ├── department.js
│   ├── departmentbehaviorpoint.js
│   ├── employee.js
│   ├── employeebasicpoint.js
│   ├── employeebehaviorpoint.js
│   ├── employeelatestnumber.js
│   ├── index.js
│   ├── interview.js
│   ├── jobtenurerecord.js
│   ├── jobtitle.js
│   ├── location.js
│   ├── organisation.js
│   ├── organisationofficialdata.js
│   ├── organisationscale.js
│   ├── passwordreset.js
│   ├── permission.js
│   ├── permissionrole.js
│   ├── permissiontype.js
│   ├── permissiontypepermissionrole.js
│   ├── pointapplication.js
│   ├── pointapplicationitem.js
│   ├── seniority.js
│   ├── task.js
│   ├── taskcandidate.js
│   ├── taskmember.js
│   ├── taskpointitem.js
│   ├── user.js
│   └── userorganisation.js
├── package-lock.json
├── package.json
├── public
│   ├── index.html
│   └── stylesheets
│       └── style.css
├── requests
│   ├── common
│   │   ├── AuthController
│   │   └── UserController
│   ├── employee
│   │   ├── BasicPointCategoryController
│   │   ├── BasicPointController
│   │   ├── BehaviorPointCategoryController
│   │   ├── BehaviorPointController
│   │   ├── DepartmentController
│   │   ├── EmployeeController
│   │   ├── InterviewController
│   │   ├── JobTenureRecordController
│   │   ├── JobTitleController
│   │   ├── OrganisationController
│   │   ├── PermissionRoleController
│   │   ├── PointApplicationController
│   │   ├── SeniorityController
│   │   ├── SignedUrlController
│   │   ├── TaskCandidateController
│   │   ├── TaskController
│   │   └── TaskMemberController
│   ├── general.js
│   └── organisationAdmin
│       └── OrganisationController
├── resources
│   ├── AsyncResource.js
│   ├── BasicPointCategoryResource.js
│   ├── BasicPointEditRecordResource.js
│   ├── BasicPointResource.js
│   ├── BehaviorPointCategroyResource.js
│   ├── BehaviorPointEditRecordResource.js
│   ├── BehaviorPointResource.js
│   ├── BehaviorPointWithAvailableResource.js
│   ├── DepartmentResource.js
│   ├── EmployeeNameOnlyResource.js
│   ├── EmployeeResource.js
│   ├── EmployeeResourceInDetail.js
│   ├── InterviewResource.js
│   ├── JobTenureRecordResource.js
│   ├── JobTitleResource.js
│   ├── OrganisationIndexResource.js
│   ├── OrganisationOfficialDataResource.js
│   ├── OrganisationShowResource.js
│   ├── PermissionResource.js
│   ├── PermissionRoleResource.js
│   ├── PermissionRoleShowResource.js
│   ├── PermissionTypeResource.js
│   ├── PointApplicationItemResource.js
│   ├── PointApplicationResource.js
│   ├── SeniorityResource.js
│   ├── TaskCandidateResource.js
│   ├── TaskMemberResource.js
│   ├── TaskResource.js
│   ├── TaskResourceDetail.js
│   ├── UserResource.js
│   └── views
│       └── emails
├── routes
│   ├── api
│   │   ├── common
│   │   ├── employee
│   │   ├── index.js
│   │   └── organisationAdmin
│   └── index.js
├── scheduleTasks.js
├── seeders
│   ├── 20220320093134-seed-locations.js
│   ├── 20220324071003-seed-organisation-scales.js
│   ├── 20220424125441-seed-permission-types.js
│   └── 20220424131139-seed-permissions.js
├── services
│   └── CloudStorage.js
├── storage
│   └── temp
├── uploads
└── worker.js
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
├── controllers             # 控制器，主要放各系統的業務邏輯
│   ├──backStage
│   ├──daydayAssess
│   └──ondkeyPay
├── docker_compose          # 放置 docker-compose yml 設定檔
│   └── docker-compose.yml
├── docs                    # swagger jp
│   ├──backStage
│   ├──daydayAssess
│   └──ondkeyPay
├── gcp_credentials
├── handlers
├── helpers
├── logs
├── middleware
├── migrations
├── models
├── public
├── requests
│   ├──backStage
│   ├──daydayAssess
│   └──ondkeyPay
├── resources
│   ├──backStage
│   ├──daydayAssess
│   └──ondkeyPay
├── routes
│   ├──api
│   │   ├──backStage
│   │   ├──daydayAssess
│   │   └──ondkeyPay
│   └──index.js
├── salaryCalculation
├── scheduleJobs
│   ├──backStage
│   ├──daydayAssess
│   └──ondkeyPay
├── seeders
├── services
├── storage
├── tests
├── uploads
│   .dockerignore
│   .env
│   .env.example
│   .gitignore
│   .sequelizerc
│   app.js
│   Dockerfile
│   ecosystem.config.js
│   Helper.js
│   package-lock.json
│   package.json
│   README.md
│   scheduleTasks.js
│   worker.js

```

```
├── Dockerfile
├── Helpers.js
├── README.md
├── app.js
├── bin
│   └── www
├── config
│   ├── auth.js
│   ├── config.js
│   ├── cors.js
│   ├── employee.js
│   ├── googleStore.js
│   ├── limit.js
│   ├── mail.js
│   ├── queue.js
│   └── storage.js
├── controllers
│   ├── AuthController.js
│   ├── LocationController.js
│   ├── OrganisationController.js
│   ├── UserController.js
│   ├── employee
│   │   ├── BasicPointCategoryController.js
│   │   ├── BasicPointController.js
│   │   ├── BehaviorPointCategoryController.js
│   │   ├── BehaviorPointController.js
│   │   ├── DepartmentController.js
│   │   ├── EmployeeController.js
│   │   ├── InterviewController.js
│   │   ├── JobTenureRecordController.js
│   │   ├── JobTitleController.js
│   │   ├── OrganisationController.js
│   │   ├── PermissionController.js
│   │   ├── PermissionRoleController.js
│   │   ├── PointApplicationController.js
│   │   ├── SeniorityController.js
│   │   ├── SignedUrlController.js
│   │   ├── TaskCandidateController.js
│   │   ├── TaskController.js
│   │   └── TaskMemberController.js
│   └── organisationAdmin
│       ├── OrganisationController.js
│       └── OrganisationScaleController.js
├── docker_compose
│   └── docker-compose.yml
├── docs
│   ├── basicInfo.js
│   ├── common
│   │   ├── AuthController
│   │   │   ├── apiForgetPassword.js
│   │   │   ├── apiResetPassword.js
│   │   │   ├── apiSignIn.js
│   │   │   ├── apiSignInOrganisation.js
│   │   │   └── index.js
│   │   ├── LocationController
│   │   │   ├── apiGetCities.js
│   │   │   ├── apiGetDistricts.js
│   │   │   └── index.js
│   │   ├── OrganisationController
│   │   │   ├── apiIndex.js
│   │   │   └── index.js
│   │   ├── UserController
│   │   │   ├── apiMe.js
│   │   │   ├── index.js
│   │   │   └── updateMyself.js
│   │   └── index.js
│   ├── components.js
│   ├── employee
│   │   ├── BasicPointCategoryController
│   │   │   ├── apiIndex.js
│   │   │   ├── apiStore.js
│   │   │   └── index.js
│   │   ├── BasicPointController
│   │   │   ├── apiDestroy.js
│   │   │   ├── apiIndex.js
│   │   │   ├── apiIndexEditRecord.js
│   │   │   ├── apiShow.js
│   │   │   ├── apiStore.js
│   │   │   ├── apiUpdate.js
│   │   │   └── index.js
│   │   ├── BehaviorPointCategoryController
│   │   │   ├── apiIndex.js
│   │   │   ├── apiStore.js
│   │   │   └── index.js
│   │   ├── BehaviorPointController
│   │   │   ├── apiApplyDepartment.js
│   │   │   ├── apiApplyOrganisation.js
│   │   │   ├── apiDestroy.js
│   │   │   ├── apiIndex.js
│   │   │   ├── apiIndexEditRecord.js
│   │   │   ├── apiShow.js
│   │   │   ├── apiStore.js
│   │   │   ├── apiUpdate.js
│   │   │   └── index.js
│   │   ├── DepartmentController
│   │   │   ├── apiGetDepartmentTree.js
│   │   │   ├── apiGetValidParmentDepartments.js
│   │   │   ├── apiIndex.js
│   │   │   ├── apiRemove.js
│   │   │   ├── apiStore.js
│   │   │   ├── apiUpdate.js
│   │   │   └── index.js
│   │   ├── EmployeeController
│   │   │   ├── apiActivateEmployee.js
│   │   │   ├── apiBatchExport.js
│   │   │   ├── apiBatchImport.js
│   │   │   ├── apiBatchUpdate.js
│   │   │   ├── apiGetCurrentEmployee.js
│   │   │   ├── apiGetImportEmployeeTemplate.js
│   │   │   ├── apiIndex.js
│   │   │   ├── apiIndexAvailablyPerPermissionRole.js
│   │   │   ├── apiIndexPerDepartment.js
│   │   │   ├── apiIndexPerPermissionRole.js
│   │   │   ├── apiRemove.js
│   │   │   ├── apiSendActivationEmail.js
│   │   │   ├── apiShow.js
│   │   │   ├── apiStore.js
│   │   │   ├── apiUpdate.js
│   │   │   └── index.js
│   │   ├── InterviewController
│   │   │   ├── apiAgree.js
│   │   │   ├── apiAllList.js
│   │   │   ├── apiDelete.js
│   │   │   ├── apiIndex.js
│   │   │   ├── apiManage.js
│   │   │   ├── apiNotAgree.js
│   │   │   ├── apiShow.js
│   │   │   ├── apiStore.js
│   │   │   ├── apiUpdate.js
│   │   │   └── index.js
│   │   ├── JobTenureRecordsController
│   │   │   ├── apiIndexPerEmployee.js
│   │   │   ├── apiSync.js
│   │   │   └── index.js
│   │   ├── JobTitleController
│   │   │   ├── apiEliminate.js
│   │   │   ├── apiIndex.js
│   │   │   ├── apiStore.js
│   │   │   ├── apiUpdate.js
│   │   │   └── index.js
│   │   ├── OrganisationController
│   │   │   ├── apiGetCurrentOrganisation.js
│   │   │   ├── apiUpdateCurrentOrganisation.js
│   │   │   └── index.js
│   │   ├── PermissionController
│   │   │   ├── apiIndex.js
│   │   │   └── index.js
│   │   ├── PermissionRoleController
│   │   │   ├── apiAddEmployees.js
│   │   │   ├── apiIndex.js
│   │   │   ├── apiRemove.js
│   │   │   ├── apiRemoveEmployees.js
│   │   │   ├── apiShow.js
│   │   │   ├── apiStore.js
│   │   │   ├── apiUpdate.js
│   │   │   └── index.js
│   │   ├── PointApplicationController
│   │   │   ├── apiAudit.js
│   │   │   ├── apiAuditorCandidates.js
│   │   │   ├── apiIndex.js
│   │   │   ├── apiStore.js
│   │   │   └── index.js
│   │   ├── SeniorityController
│   │   │   ├── apiShow.js
│   │   │   ├── apiStore.js
│   │   │   ├── apiUpdate.js
│   │   │   └── index.js
│   │   ├── SignedUrlController
│   │   │   ├── apiStore.js
│   │   │   └── index.js
│   │   ├── TaskCandidateController
│   │   │   ├── apiApply.js
│   │   │   ├── apiApproval.js
│   │   │   ├── apiDelete.js
│   │   │   ├── apiIndex.js
│   │   │   └── index.js
│   │   ├── TaskController
│   │   │   ├── apiClose.js
│   │   │   ├── apiDelete.js
│   │   │   ├── apiIndex.js
│   │   │   ├── apiIndexMe.js
│   │   │   ├── apiReplaceSupervisor.js
│   │   │   ├── apiShow.js
│   │   │   ├── apiStore.js
│   │   │   ├── apiUpdate.js
│   │   │   └── index.js
│   │   ├── TaskMemberController
│   │   │   ├── apiDelete.js
│   │   │   ├── apiIndex.js
│   │   │   ├── apiRejectQuit.js
│   │   │   ├── apiStore.js
│   │   │   ├── apiUpdate.js
│   │   │   └── index.js
│   │   └── index.js
│   ├── index.js
│   ├── organisationAdmin
│   │   ├── OrganisationController
│   │   │   ├── apiGetScales.js
│   │   │   ├── apiStore.js
│   │   │   └── index.js
│   │   ├── OrganisationOfficialDataController
│   │   │   ├── apiGetOrganisationOfficialData.js
│   │   │   └── index.js
│   │   └── index.js
│   └── path.js
├── ecosystem.config.js
├── gcp_credentials
├── handlers
│   └── errorHandlers.js
├── helpers
│   ├── logHelpers.js
│   ├── mailHelper.js
│   ├── queueHelper.js
│   └── stringHelpers.js
├── logs
├── middleware
│   ├── authJwt.js
│   ├── customErrorHandler.js
│   ├── index.js
│   ├── validateReq.js
│   └── verifySignUp.js
├── migrations
│   ├── 20220317021155-create-user.js
│   ├── 20220319092358-create-locations.js
│   ├── 20220322084812-create-interview.js
│   ├── 20220324062909-create-organisation.js
│   ├── 20220324070713-create-organisation-scale.js
│   ├── 20220328081035-create-organisation-official-data.js
│   ├── 20220329230343-create-basic-point-category.js
│   ├── 20220330085520-create-employee.js
│   ├── 20220330090901-change-column-interview.js
│   ├── 20220330093202-create-department.js
│   ├── 20220401055052-add-column-interview.js
│   ├── 20220401063506-add-columns-in-users-table.js
│   ├── 20220404064545-create-employee-latest-number.js
│   ├── 20220406103107-create_queue_table.js
│   ├── 20220408040915-add-departmentId-in-employees-table.js
│   ├── 20220408092630-add-employee-quantity-in-departments-table.js
│   ├── 20220409090515-create-job-title.js
│   ├── 20220411033751-add-employeeState-in-employees-table.js
│   ├── 20220412020132-add-deletedAt-in-interviews-table.js
│   ├── 20220412033420-create-basic-point.js
│   ├── 20220413014222-change-employeeNumber-in-employees-table.js
│   ├── 20220413072234-remove-isManager-column-in-employees-table.js
│   ├── 20220419184625-create-seniority.js
│   ├── 20220420131136-drop-employee-quantity-in-departments-table.js
│   ├── 20220421023701-add-initPoint-in-employees-table.js
│   ├── 20220421062803-add-avatar-in-users.js
│   ├── 20220421083327-rename-interviews-change-Interviews-table.js
│   ├── 20220421094952-remove-deletedAt-in-Interviews-table.js
│   ├── 20220422025946-create-password-reset.js
│   ├── 20220424115442-create-permission-type.js
│   ├── 20220424115854-create-permission-type-permission-role.js
│   ├── 20220424120026-create-permission-role.js
│   ├── 20220424120040-create-permission.js
│   ├── 20220425073421-create-employee-basic-point.js
│   ├── 20220426045450-add-permissionRoleId-in-employees-table.js
│   ├── 20220426064942-add-permissionRoleDescription-in-permissionRoles-table.js
│   ├── 20220426073436-create-user-organisation.js
│   ├── 20220426073826-create-behavior-point-category.js
│   ├── 20220426110315-alter-userId-in-employees-table.js
│   ├── 20220426111731-create-behavior-point.js
│   ├── 20220427011936-create-employee-behavior-point.js
│   ├── 20220427071954-add-column-in-employees-table.js
│   ├── 20220428060116-create-basic-point-edit-record.js
│   ├── 20220429025056-alter-permission-type-permission-roles-table.js
│   ├── 20220503025245-change_body_length_in_oxen_queue.js
│   ├── 20220503052943-remove_password_reset_index.js
│   ├── 20220503074839-add-activation-identifier-in-employees-table.js
│   ├── 20220503090737-alter-employees-table.js
│   ├── 20220504115329-alter-employees-table.js
│   ├── 20220505045839-add-columns-in-employees-table.js
│   ├── 20220506095354-create-task.js
│   ├── 20220506104758-create-job-tenure-record.js
│   ├── 20220511080050-create-department-behavior-point.js
│   ├── 20220512030954-create-task-members.js
│   ├── 20220512031606-create-task-candidates.js
│   ├── 20220513080354-create-behavior-point-edit-records.js
│   ├── 20220516090921-add-organisationId-in-task-table.js
│   ├── 20220519110735-remove-candidateState-in-taskCandidates-table.js
│   ├── 20220519151417-create-task-point-items.js
│   ├── 20220524012718-add-memberState-in-taskMembers-table.js
│   ├── 20220526032421-create-point-application.js
│   └── 20220526032550-create-point-application-item.js
├── models
│   ├── basicpoint.js
│   ├── basicpointcategory.js
│   ├── basicpointeditrecord.js
│   ├── behaviorpoint.js
│   ├── behaviorpointcategory.js
│   ├── behaviorpointeditrecords.js
│   ├── department.js
│   ├── departmentbehaviorpoint.js
│   ├── employee.js
│   ├── employeebasicpoint.js
│   ├── employeebehaviorpoint.js
│   ├── employeelatestnumber.js
│   ├── index.js
│   ├── interview.js
│   ├── jobtenurerecord.js
│   ├── jobtitle.js
│   ├── location.js
│   ├── organisation.js
│   ├── organisationofficialdata.js
│   ├── organisationscale.js
│   ├── passwordreset.js
│   ├── permission.js
│   ├── permissionrole.js
│   ├── permissiontype.js
│   ├── permissiontypepermissionrole.js
│   ├── pointapplication.js
│   ├── pointapplicationitem.js
│   ├── seniority.js
│   ├── task.js
│   ├── taskcandidate.js
│   ├── taskmember.js
│   ├── taskpointitem.js
│   ├── user.js
│   └── userorganisation.js
├── package-lock.json
├── package.json
├── public
│   ├── index.html
│   └── stylesheets
│       └── style.css
├── requests
│   ├── common
│   │   ├── AuthController
│   │   │   ├── forgetPasswordSchema.js
│   │   │   ├── registerSchema.js
│   │   │   ├── resetPasswordSchema.js
│   │   │   ├── signInOrganisationSchema.js
│   │   │   └── signInSchema.js
│   │   └── UserController
│   │       └── updateMyselfSchema.js
│   ├── employee
│   │   ├── BasicPointCategoryController
│   │   │   └── storeSchema.js
│   │   ├── BasicPointController
│   │   │   ├── destroySchema.js
│   │   │   ├── indexEditRecordsParamsSchema.js
│   │   │   ├── indexEditRecordsQuerySchema.js
│   │   │   ├── indexSchema.js
│   │   │   ├── showSchema.js
│   │   │   ├── storeSchema.js
│   │   │   └── updateSchema.js
│   │   ├── BehaviorPointCategoryController
│   │   │   └── storeSchema.js
│   │   ├── BehaviorPointController
│   │   │   ├── applyDepartmentBodySchema.js
│   │   │   ├── applyDepartmentParamsSchema.js
│   │   │   ├── applyOrganisationSchema.js
│   │   │   ├── destroySchema.js
│   │   │   ├── indexEditRecordsParamsSchema.js
│   │   │   ├── indexEditRecordsQuerySchema.js
│   │   │   ├── indexSchema.js
│   │   │   ├── showSchema.js
│   │   │   ├── storeSchema.js
│   │   │   └── updateSchema.js
│   │   ├── DepartmentController
│   │   │   ├── getValidParentDepartmentsSchema.js
│   │   │   ├── patchParamsSchema.js
│   │   │   ├── patchSchema.js
│   │   │   ├── removeSchema.js
│   │   │   └── storeSchema.js
│   │   ├── EmployeeController
│   │   │   ├── activateSchema.js
│   │   │   ├── batchExportSchema.js
│   │   │   ├── batchUpdateSchema.js
│   │   │   ├── deleteSchema.js
│   │   │   ├── indexAvailablyPerPermissionRoleParamsSchema.js
│   │   │   ├── indexAvailablyPerPermissionRoleQuerySchema.js
│   │   │   ├── indexPerDepartmentSchema.js
│   │   │   ├── indexPerPermissionRoleParamsSchema.js
│   │   │   ├── indexSchema.js
│   │   │   ├── patchParamsSchema.js
│   │   │   ├── patchSchema.js
│   │   │   ├── sendActivationEmailSchema.js
│   │   │   ├── showSchema.js
│   │   │   └── storeSchema.js
│   │   ├── InterviewController
│   │   │   ├── allListSchema.js
│   │   │   ├── destroySchema.js
│   │   │   ├── indexSchema.js
│   │   │   ├── managerListSchema.js
│   │   │   ├── putParamsSchema.js
│   │   │   ├── showSchema.js
│   │   │   ├── storeSchema.js
│   │   │   └── updateSchema.js
│   │   ├── JobTenureRecordController
│   │   │   ├── indexPerEmployeeSchema.js
│   │   │   └── syncSchema.js
│   │   ├── JobTitleController
│   │   │   ├── deleteSchema.js
│   │   │   ├── storeSchema.js
│   │   │   └── updateSchema.js
│   │   ├── OrganisationController
│   │   │   └── updateCurrentOrganisationSchema.js
│   │   ├── PermissionRoleController
│   │   │   ├── addEmployeesParamsSchema.js
│   │   │   ├── addEmployeesSchema.js
│   │   │   ├── removeEmployeesParamsSchema.js
│   │   │   ├── removeEmployeesSchema.js
│   │   │   ├── removeSchema.js
│   │   │   ├── showSchema.js
│   │   │   ├── storeSchema.js
│   │   │   ├── updateParamsSchema.js
│   │   │   └── updateSchema.js
│   │   ├── PointApplicationController
│   │   │   ├── auditApplicationSchema.js
│   │   │   ├── getAuditorCandidatesSchema.js
│   │   │   ├── indexSchema.js
│   │   │   └── storeSchema.js
│   │   ├── SeniorityController
│   │   │   ├── storeSchema.js
│   │   │   └── updateSchema.js
│   │   ├── SignedUrlController
│   │   │   └── storeSchema.js
│   │   ├── TaskCandidateController
│   │   │   ├── approvalSchema.js
│   │   │   ├── destroySchema.js
│   │   │   ├── indexSchema.js
│   │   │   └── showSchema.js
│   │   ├── TaskController
│   │   │   ├── indexMeSchema.js
│   │   │   ├── indexSchema.js
│   │   │   ├── replaceSupervisorSchema.js
│   │   │   ├── showSchema.js
│   │   │   ├── storeSchema.js
│   │   │   └── updateSchema.js
│   │   └── TaskMemberController
│   │       ├── destroySchema.js
│   │       ├── indexParamsSchema.js
│   │       ├── indexSchema.js
│   │       ├── showSchema.js
│   │       ├── storeSchema.js
│   │       └── updateSchema.js
│   ├── general.js
│   └── organisationAdmin
│       └── OrganisationController
│           ├── getOrganisationOfficialDataSchema.js
│           └── storeSchema.js
├── resources
│   ├── AsyncResource.js
│   ├── BasicPointCategoryResource.js
│   ├── BasicPointEditRecordResource.js
│   ├── BasicPointResource.js
│   ├── BehaviorPointCategroyResource.js
│   ├── BehaviorPointEditRecordResource.js
│   ├── BehaviorPointResource.js
│   ├── BehaviorPointWithAvailableResource.js
│   ├── DepartmentResource.js
│   ├── EmployeeNameOnlyResource.js
│   ├── EmployeeResource.js
│   ├── EmployeeResourceInDetail.js
│   ├── InterviewResource.js
│   ├── JobTenureRecordResource.js
│   ├── JobTitleResource.js
│   ├── OrganisationIndexResource.js
│   ├── OrganisationOfficialDataResource.js
│   ├── OrganisationShowResource.js
│   ├── PermissionResource.js
│   ├── PermissionRoleResource.js
│   ├── PermissionRoleShowResource.js
│   ├── PermissionTypeResource.js
│   ├── PointApplicationItemResource.js
│   ├── PointApplicationResource.js
│   ├── SeniorityResource.js
│   ├── TaskCandidateResource.js
│   ├── TaskMemberResource.js
│   ├── TaskResource.js
│   ├── TaskResourceDetail.js
│   ├── UserResource.js
│   └── views
│       └── emails
│           ├── activateEmployee.js
│           └── resetPassword.js
├── routes
│   ├── api
│   │   ├── common
│   │   │   ├── index.js
│   │   │   ├── noToken
│   │   │   │   ├── auth.js
│   │   │   │   ├── index.js
│   │   │   │   └── permissions.js
│   │   │   ├── stepOneToken
│   │   │   │   ├── auth.js
│   │   │   │   ├── index.js
│   │   │   │   ├── locations.js
│   │   │   │   ├── organisations.js
│   │   │   │   └── users.js
│   │   │   └── stepTwoToken
│   │   │       └── index.js
│   │   ├── employee
│   │   │   ├── index.js
│   │   │   ├── noToken
│   │   │   │   ├── employees.js
│   │   │   │   └── index.js
│   │   │   ├── stepOneToken
│   │   │   │   └── index.js
│   │   │   └── stepTwoToken
│   │   │       ├── basicPointCategories.js
│   │   │       ├── basicPoints.js
│   │   │       ├── behaviorPointCategories.js
│   │   │       ├── behaviorPoints.js
│   │   │       ├── departments.js
│   │   │       ├── employees.js
│   │   │       ├── index.js
│   │   │       ├── interviews.js
│   │   │       ├── jobTenureRecords.js
│   │   │       ├── jobTitles.js
│   │   │       ├── organisations.js
│   │   │       ├── permissionRoles.js
│   │   │       ├── permissions.js
│   │   │       ├── pointApplications.js
│   │   │       ├── seniority.js
│   │   │       ├── signedUrl.js
│   │   │       ├── taskCandidates.js
│   │   │       ├── taskMembers.js
│   │   │       └── tasks.js
│   │   ├── index.js
│   │   └── organisationAdmin
│   │       ├── index.js
│   │       ├── noToken
│   │       │   └── index.js
│   │       ├── stepOneToken
│   │       │   ├── index.js
│   │       │   ├── organisationScales.js
│   │       │   └── organisations.js
│   │       └── stepTwoToken
│   │           └── index.js
│   └── index.js
├── scheduleTasks.js
├── seeders
│   ├── 20220320093134-seed-locations.js
│   ├── 20220324071003-seed-organisation-scales.js
│   ├── 20220424125441-seed-permission-types.js
│   └── 20220424131139-seed-permissions.js
├── services
│   └── CloudStorage.js
├── storage
│   └── temp
├── uploads
└── worker.js
```