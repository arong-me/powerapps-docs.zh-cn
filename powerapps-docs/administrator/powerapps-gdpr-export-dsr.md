---
title: 响应对导出 PowerApps 客户数据的数据主体权限 (DSR) 请求 | Microsoft Docs
description: 演练如何响应对导出 PowerApps 客户数据的数据主体权限 (DSR) 请求。
author: jamesol-msft
manager: kfile
ms.service: powerapps
ms.component: pa-admin
ms.topic: conceptual
ms.date: 05/23/2018
ms.author: jamesol
ms.openlocfilehash: 000f15ea7b1fa4e11cbe49b44e57017daf973a89
ms.sourcegitcommit: 68fc13fdc2c991c499ad6fe9ae1e0f8dab597139
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2018
ms.locfileid: "34552958"
---
# <a name="responding-to-data-subject-rights-dsr-requests-to-export-powerapps-customer-data"></a>响应对导出 PowerApps 客户数据的数据主体权限 (DSR) 请求
“数据可移植性权限”允许数据主体以电子格式（这是一种结构化的、常用的、计算机可读和可互操作的格式）请求其个人数据副本，这些数据可能会传输给另一个数据控制者：

* 网站访问：[PowerApps 门户](https://web.powerapps.com)、[PowerApps 管理中心](https://admin.powerapps.com/)和 [Office 365 服务信任门户](https://servicetrust.microsoft.com/)

* PowerShell 访问：PowerApps [应用创建者 cmdlet](https://go.microsoft.com/fwlink/?linkid=871448)、[管理员 cmdlet](https://go.microsoft.com/fwlink/?linkid=871804) 和[本地网关 cmdlet](https://go.microsoft.com/fwlink/?linkid=872238)

以下汇总有关 PowerApps 可以为特定用户存储的个人数据类型，以及可以用来查找和导出数据的体验。

包含个人数据的资源 | 网站访问 |   PowerShell 访问
--- | --- | --
环境 | PowerApps 管理中心 |  PowerApps cmdlet
环境权限**   | PowerApps 管理中心    | PowerApps cmdlet
画布应用  | PowerApps 管理中心 <br> PowerApps 门户 |    PowerApps cmdlet
画布应用权限  | PowerApps 管理中心 <br> PowerApps 门户  | PowerApps cmdlet
网关 | PowerApps 门户***   | 本地网关 cmdlet
网关权限 | PowerApps 门户***   |
自定义连接器 | |    应用创建者：可用 <br> 管理员：可用
自定义连接器权限 | |    应用创建者：可用 <br> 管理员：可用
连接 | | 应用创建者：可用 <br> 管理员：可用
连接权限  | | 应用创建者：可用 <br> 管理员：可用
PowerApps 用户设置、用户应用设置和通知 | | 应用创建者：可用 <br> 管理员：可用

> ** 在引入 Common Data Service (CDS) for Apps 后，如果数据库是在环境中创建的，那么环境权限和模型驱动的应用权限会作为记录存储在 CDS for Apps 数据库实例中。 有关如何响应 CDS for Apps 用户的 DSR 请求的指导，请参阅[响应针对 Common Data Service for Apps 客户数据的数据主体权限 (DSR) 请求](common-data-service-gdpr-dsr-guide.md)。

> ***只有当资源所有者明确授予访问权限时，管理员才能从 [PowerApps 门户](https://web.powerapps.com)访问这些资源。 如果没有对管理员授予访问权限，则其需要利用 [PowerApps 管理员 PowerShell cdmlet](https://go.microsoft.com/fwlink/?linkid=871804)。

## <a name="prerequisites"></a>先决条件

### <a name="for-users"></a>对于用户
拥有有效 PowerApps 许可证的所有用户都可以使用 [PowerApps 门户](https://web.powerapps.com)或[应用创建者 cmdlet](https://go.microsoft.com/fwlink/?linkid=871448) 来执行本文档所述的用户操作。

### <a name="for-admins"></a>对于管理员
要使用 PowerApps 管理中心、Microsoft Flow 管理中心或 [PowerApps 管理员 PowerShell cmdlet](https://go.microsoft.com/fwlink/?linkid=871804) 来执行本文档所述的管理操作，将需要以下各项：

* PowerApps 计划 2 付费许可证，或 PowerApps 计划 2 试用许可证。 可以在 [http://web.powerapps.com/trial](http://web.powerapps.com/trial) 注册以获取 30 天试用许可证。 如果试用许可证已过期，可以续订。

* 如果需要搜索另一个用户的资源，还将需要 [Office 365 全局管理员](https://support.office.com/article/assign-admin-roles-in-office-365-for-business-eac4d046-1afd-4f1a-85fc-8219c79e1504)或 [Azure Active Directory 全局管理员](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal)权限。 （请注意，环境管理员仅能访问那些他们具有权限的环境和环境资源。）

## <a name="step-1-export-personal-data-contained-within-environments-created-by-the-user"></a>步骤 1：导出包含在由用户创建的环境中的个人数据

### <a name="powerapps-admin-center"></a>PowerApps 管理中心
管理员可以通过以下步骤从 [PowerApps 管理中心](https://admin.powerapps.com/)导出特定用户创建的所有环境：

1. 从 [PowerApps 管理中心](https://admin.powerapps.com/)选择组织中的每个环境。

    ![管理中心登陆页](./media/powerapps-gdpr-export-dsr/admin-center-landing.png)

2. 如果环境是由来自 DSR 请求的用户创建的，请转到**详细信息**页，复制详细信息，然后将它们粘贴到文档编辑器，如 Microsoft Word。

    ![环境详细信息](./media/powerapps-gdpr-export-dsr/environment-details.png)

### <a name="powershell-cmdlets-for-app-creators"></a>应用创建者 PowerShell cmdlet
用户可以使用 [PowerApps 应用创建者 PowerShell cmdlet](https://go.microsoft.com/fwlink/?linkid=871448) 中的 Get-PowerAppsEnvironment 函数来导出在 PowerApps 中有权访问的环境：

~~~~
Add-PowerAppsAccount
Get-PowerAppsEnvironment | ConvertTo-Json | Out-File -FilePath "UserDetails.json"
~~~~

### <a name="powershell-cmdlets-for-admins"></a>管理员 PowerShell cmdlet
管理员可以使用 [PowerApps 管理员 PowerShell cdmlet](https://go.microsoft.com/fwlink/?linkid=871804) 中的 Get-AdminEnvironment 函数导出由用户创建的所有环境：

~~~~
Add-PowerAppsAccount
$userId = "7557f390-5f70-4c93-8bc4-8c2faabd2ca0"
Get-AdminEnvironment -CreatedBy $userId | ConvertTo-Json | Out-File -FilePath "UserDetails.json"
~~~~
 
## <a name="step-2-export-the-users-environment-permissions"></a>步骤 2：导出用户的环境权限
可以在环境中向用户分配权限（如“环境管理员”、“环境创建者”等），这些权限作为“角色分配”保存在 PowerApps 中。 在引入 CDS for Apps 后，如果数据库是在环境中创建的，那么该“角色分配”会作为记录存储在 CDS for Apps 数据库实例中。 有关详细信息，请参阅[管理 PowerApps 中的环境](environments-administration.md)。

### <a name="for-environments-without-a-cds-for-apps-database"></a>对于没有 CDS for Apps 数据库的环境

#### <a name="powerapps-admin-center"></a>PowerApps 管理中心
管理员可以通过以下步骤，从 [PowerApps 管理中心](https://admin.powerapps.com/)导出用户的环境权限：

1. 从 [PowerApps 管理中心](https://admin.powerapps.com/)选择组织中的每个环境。 必须是 [Office 365 全局管理员](https://support.office.com/article/assign-admin-roles-in-office-365-for-business-eac4d046-1afd-4f1a-85fc-8219c79e1504)或 [Azure Active Directory 全局管理员](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal)才能查看组织中创建的所有环境。

    ![管理中心登陆页](./media/powerapps-gdpr-export-dsr/admin-center-landing.png)

2. 选择“安全”。

    如果环境中没有 CDS For Apps 数据库，你将看到有关“环境角色”的部分。

3. 分别选择“环境管理员”和“环境创建者”，然后使用搜索栏搜索用户名。

    ![环境角色页](./media/powerapps-gdpr-export-dsr/admin-environment-role-share-page.png)

4. 如果用户具有对任一角色的访问权限，请转到“用户”页，复制详细信息，然后将它们粘贴到文档编辑器，如 Microsoft Word。

#### <a name="powershell-cmdlets-for-admins"></a>管理员 PowerShell cmdlet
管理员可以使用 [PowerApps 管理员 PowerShell cmdlet](https://go.microsoft.com/fwlink/?linkid=871804) 中的 Get-AdminEnvironmentRoleAssignment 函数，在没有 CDS for Apps 数据库的所有环境中，导出用户的所有环境角色分配：

~~~~
Add-PowerAppsAccount
$userId = "0ecb1fcc-6782-4e46-a4c4-738c1d3accea"
Get-AdminEnvironmentRoleAssignment -UserId $userId | ConvertTo-Json | Out-File -FilePath "UserDetails.json"
~~~~

> [!IMPORTANT]
>  此函数仅在没有 CDS for Apps 数据库实例的环境中有效。
>
>

### <a name="for-environments-with-a-cds-for-apps-database"></a>对于有 CDS for Apps 数据库的环境
在引入 CDS for Apps 后，如果数据库是在环境中创建的，那么“角色分配”会作为记录存储在 CDS for Apps 数据库实例中。 有关如何从 CDS for Apps 数据库实例中移除个人数据的信息，请参阅 [Common Data Service 用户个人数据移除](https://go.microsoft.com/fwlink/?linkid=871886)。
 
## <a name="step-3-export-personal-data-contained-within-canvas-apps-created-by-the-user"></a>步骤 3：导出包含在由用户创建的画布应用中的个人数据

### <a name="powerapps-portal"></a>PowerApps 门户
用户可以从 [PowerApps 门户](https://web.powerapps.com)导出应用。 有关如何导出应用的分步说明，请参阅[导出应用](environment-and-tenant-migration.md#exporting-an-app)。

### <a name="powerapps-admin-center"></a>PowerApps 管理中心
管理员可以通过以下步骤，从 [PowerApps 管理中心](https://admin.powerapps.com/)开始导出由用户创建的应用：

1. 从 [PowerApps 管理中心](https://admin.powerapps.com/)选择组织中的每个环境。 必须是 [Office 365 全局管理员](https://support.office.com/article/assign-admin-roles-in-office-365-for-business-eac4d046-1afd-4f1a-85fc-8219c79e1504)或 [Azure Active Directory 全局管理员](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal)才能查看组织中创建的所有环境。

    ![管理中心登陆页](./media/powerapps-gdpr-export-dsr/admin-center-landing.png)

2. 选择“资源”，然后选择“应用”。

3. 使用搜索栏搜索用户名，将显示由该用户在此环境中创建的任何应用：

    ![搜索应用](./media/powerapps-gdpr-export-dsr/search-apps.png)

4. 为该用户创建的每个应用选择“共享”，并授予自己对应用的“可编辑”访问权限：

    ![选择应用共享](./media/powerapps-gdpr-export-dsr/select-share.png)

    ![授予用户访问](./media/powerapps-gdpr-export-dsr/grant-access.png)

5. 一旦有权访问用户的每个应用，即可从 [PowerApps 门户](https://web.powerapps.com)中导出应用。 有关如何导出应用的分步说明，请参阅[导出应用](environment-and-tenant-migration.md#exporting-an-app)。

### <a name="powershell-cmdlets-for-admins"></a>管理员 PowerShell cmdlet
管理员可以使用 [PowerApps 管理员 PowerShell cdmlet](https://go.microsoft.com/fwlink/?linkid=871804) 中的 Get-AdminApp 函数导出由用户创建的应用：

~~~~
Add-PowerAppsAccount
$userId = "0ecb1fcc-6782-4e46-a4c4-738c1d3accea"
Get-AdminApp -Owner $userId | ConvertTo-Json | Out-File -FilePath "UserDetails.json"
~~~~

## <a name="step-4-export-the-users-permissions-to-canvas-apps"></a>步骤 4：导出用户对画布应用的权限
每当与用户共享应用时，PowerApps 就会存储名为“角色分配”的记录，用于描述用户对应用的权限（CanEdit 或 CanUse）。 有关详细信息，请参阅[共享应用](../maker/canvas-apps/share-app.md#share-an-app)。

### <a name="powershell-cmdlets-for-app-creators"></a>应用创建者 PowerShell cmdlet
用户可以使用 [PowerApps 应用创建者 PowerShell cmdlet](https://go.microsoft.com/fwlink/?linkid=871448) 中的 Get-RoleAssignment 函数来导出有权访问的所有应用的应用角色分配：

~~~~
Add-PowerAppsAccount
Get-AppRoleAssignment | ConvertTo-Json | Out-File -FilePath "UserDetails.json"
~~~~

### <a name="powerapps-admin-center"></a>PowerApps 管理中心
管理员可以通过以下步骤，从 [PowerApps 管理中心](https://admin.powerapps.com/)导出用户的应用角色分配：

1. 从 [PowerApps 管理中心](https://admin.powerapps.com/)选择组织中的每个环境。 必须是 [Office 365 全局管理员](https://support.office.com/article/assign-admin-roles-in-office-365-for-business-eac4d046-1afd-4f1a-85fc-8219c79e1504)或 [Azure Active Directory 全局管理员](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal)才能查看组织中创建的所有环境。

    ![管理中心登陆页](./media/powerapps-gdpr-export-dsr/admin-center-landing.png)

2. 对于每个环境，选择“资源”，然后选择“应用”。

3. 为环境中的每个应用选择“共享”。

    ![选择应用共享](./media/powerapps-gdpr-export-dsr/select-admin-share-nofilter.png)

4. 如果用户具有对应用的访问权限，请转到应用的“共享”页，复制详细信息，然后将它们粘贴到文档编辑器，如 Microsoft Word。

    ![管理应用共享页](./media/powerapps-gdpr-export-dsr/admin-share-page.png)

### <a name="powershell-cmdlets-for-admins"></a>管理员 PowerShell cmdlet
管理员可以使用 [PowerApps 管理员 PowerShell cmdlet](https://go.microsoft.com/fwlink/?linkid=871804) 中的 Get-AdminAppRoleAssignment 函数，在租户的所有应用中，导出用户的所有应用角色分配：

~~~~
Add-PowerAppsAccount
$userId = "0ecb1fcc-6782-4e46-a4c4-738c1d3accea"
Get-AdminAppRoleAssignment -UserId $userId | ConvertTo-Json | Out-File -FilePath "UserDetails.json"
~~~~

## <a name="step-5-export-personal-data-contained-within-connections-created-by-the-user"></a>步骤 5：导出包含在由用户创建的连接中的个人数据
在与其他 API 和 SaaS 系统建立连接时，连接将与连接器结合使用。 连接包括对创建它们的用户的引用，因此可以将其删除以移除对用户的任何引用。

### <a name="powershell-cmdlets-for-app-creators"></a>应用创建者 PowerShell cmdlet
用户可以使用 [PowerApps 应用创建者 PowerShell cmdlet](https://go.microsoft.com/fwlink/?linkid=871448) 中的 Get-Connection 函数来导出其有权访问的所有连接：

~~~~
Add-PowerAppsAccount
Get-Connection | ConvertTo-Json | out-file -FilePath "UserDetails.json"
~~~~

### <a name="powershell-cmdlets-for-admins"></a>管理员 PowerShell cmdlet
管理员可以使用 [PowerApps 管理员 PowerShell cdmlet](https://go.microsoft.com/fwlink/?linkid=871804) 中的 Get-AdminConnection 函数来导出用户创建的所有应用：

~~~~
Add-PowerAppsAccount
$userId = "0ecb1fcc-6782-4e46-a4c4-738c1d3accea"
Get-AdminConnection -CreatedBy $userId | ConvertTo-Json | Out-File -FilePath "UserDetails.json"
~~~~
 
## <a name="step-6-export-the-users-permissions-to-shared-connections"></a>步骤 6：导出共享连接的用户权限

### <a name="powershell-cmdlets-for-app-creators"></a>应用创建者 PowerShell cmdlet
用户可以使用 [PowerApps 应用创建者 PowerShell cmdlet](https://go.microsoft.com/fwlink/?linkid=871448) 中的 Get-ConnectionRoleAssignment 函数来导出其有权访问的所有连接的连接角色分配：

~~~~
Add-PowerAppsAccount
Get-ConnectionRoleAssignment | ConvertTo-Json | Out-file -FilePath "UserDetails.json"
~~~~

### <a name="powershell-cmdlets-for-admins"></a>管理员 PowerShell cmdlet
管理员可以使用 [PowerApps 管理员 PowerShell cmdlet](https://go.microsoft.com/fwlink/?linkid=871804) 中的 Get-AdminConnectionRoleAssignment 函数来导出用户的所有连接角色分配：

~~~~
Add-PowerAppsAccount
$userId = "0ecb1fcc-6782-4e46-a4c4-738c1d3accea"
Get-AdminConnectionRoleAssignment -PrincipalObjectId $userId | ConvertTo-Json | Out-File -FilePath "UserDetails.json"
~~~~

## <a name="step-7-export-personal-data-contained-within-custom-connectors-created-by-the-user"></a>步骤 7：导出包含在由用户创建的自定义连接器中的个人数据
自定义连接器补充了现有连接器，并允许连接到其他 API、SaaS 和以自定义方式开发的系统。

### <a name="powerapps-app-creator-powershell-cmdlets"></a>PowerApps 应用创建者 PowerShell cmdlet
用户可以使用 [PowerApps 应用创建者 PowerShell cmdlet](https://go.microsoft.com/fwlink/?linkid=871448) 中的 Get-Connector 函数来导出他们创建的所有自定义连接器：

~~~~
Add-PowerAppsAccount  
Get-Connector -FilterNonCustomConnectors | ConvertTo-Json | Out-File -FilePath "UserDetails.json"
~~~~

### <a name="powershell-cmdlets-for-admins"></a>管理员 PowerShell cmdlet
管理员可以使用 [PowerApps 管理员 PowerShell cmdlet](https://go.microsoft.com/fwlink/?linkid=871804) 中的 Get-AdminConnector 函数来导出用户创建的所有自定义连接器：

~~~~
Add-PowerAppsAccount
$userId = "0ecb1fcc-6782-4e46-a4c4-738c1d3accea"
Get-AdminConnector -CreatedBy $userId | ConvertTo-Json | Out-File -FilePath "UserDetails.json"
~~~~

## <a name="step-8-export-the-users-permissions-to-custom-connectors"></a>步骤 8：导出自定义连接器的用户权限

### <a name="powershell-cmdlets-for-app-creators"></a>应用创建者 PowerShell cmdlet
用户可以使用 [PowerApps 应用创建者 PowerShell cmdlet](https://go.microsoft.com/fwlink/?linkid=871448) 中的 Get-ConnectorRoleAssignment 函数来导出有权访问的自定义连接器的所有连接器角色分配：

~~~~
Add-PowerAppsAccount  
Get-ConnectorRoleAssignment | ConvertTo-Json | Out-File -FilePath "UserDetails.json"
~~~~

### <a name="powershell-cmdlets-for-admins"></a>管理员 PowerShell cmdlet
管理员可以使用 [PowerApps 管理员 PowerShell cmdlet](https://go.microsoft.com/fwlink/?linkid=871804) 中的 Get-AdminConnectorRoleAssignment 函数来导出用户的所有自定义连接器角色分配：

~~~~
Add-PowerAppsAccount
$userId = "0ecb1fcc-6782-4e46-a4c4-738c1d3accea"
Get-AdminConnectorRoleAssignment -PrincipalObjectId $userId | ConvertTo-Json | Out-File -FilePath "UserDetails.json"
~~~~
 
## <a name="step-9-export-powerapps-notifications-user-settings-and-user-app-settings"></a>步骤 9：导出 PowerApps 通知、用户设置和用户应用设置
PowerApps 向用户发送几种类型的通知，包括与用户共享应用以及 CDS for Apps 导出操作完成时。 用户可以在 [PowerApps 门户](https://web.powerapps.com)中查看其通知历史记录。

PowerApps 还存储几个不同的用户首选项和设置，用于提供 PowerApps 运行时和门户体验，包括用户上一次打开应用、固定应用的时间等。

### <a name="powershell-cmdlets-for-app-creators"></a>应用创建者 PowerShell cmdlet
用户可以使用 [PowerApps 应用创建者 PowerShell cmdlet](https://go.microsoft.com/fwlink/?linkid=871448) 中的 Get-AdminPowerAppsUserDetails 函数来导出他们自己的 PowerApps 通知、用户设置和用户应用设置：

~~~~
Add-PowerAppsAccount  
Get-AdminPowerAppsUserDetails -WriteToFile -OutputFilePath "UserDetails.json"
~~~~

### <a name="powershell-cmdlets-for-admins"></a>管理员 PowerShell cmdlet
管理员可以使用 [PowerApps 管理员 PowerShell cmdlet](https://go.microsoft.com/fwlink/?linkid=871804) 中的 Get-AdminPowerAppsUserDetails 函数来导出用户的 PowerApps 通知、用户设置和用户应用设置：

~~~~
Add-PowerAppsAccount
$userId = "0ecb1fcc-6782-4e46-a4c4-738c1d3accea"
Get-AdminPowerAppsUserDetails -WriteToFile -OutputFilePath "UserDetails.json" -UserPrincipalName foobar@microsoft.com
~~~~

## <a name="step-10-export-personal-data-contained-for-a-user-stored-gateway-or-in-the-users-gateway-permissions"></a>步骤 10：导出用户存储网关所包含的个人数据或用户网关权限中的个人数据

### <a name="powerapps-portal"></a>PowerApps 门户
用户可以通过执行以下步骤从 [PowerApps 门户](https://web.powerapps.com)导出存储在网关服务中的个人数据：

1. 在 [PowerApps 门户](https://web.powerapps.com)中，在租户的默认环境中选择“网关”，然后选择有权访问的每个网关的“详细信息”。

    ![网关登陆页面](./media/powerapps-gdpr-export-dsr/gateway-select-details.png)

2. 在“详细信息”页，如果网关详细信息包含任何个人数据，则复制详细信息，然后将它们粘贴到文档编辑器，如 Microsoft Word。

    ![网关详细信息](./media/powerapps-gdpr-export-dsr/gateway-details-drillin.png)

3. 选择“共享”，复制页面内容，然后将其粘贴到文档编辑器，如 Microsoft Word。

    ![网关详细信息](./media/powerapps-gdpr-export-dsr/gateway-details-share.png)

### <a name="gateway-powershell-cmdlets"></a>网关 PowerShell cmdlet
还提供了 PowerShell cmdlet，可用于检索、管理和删除个人网关。 有关详细信息，请参阅[本地网关 cmdlet](https://go.microsoft.com/fwlink/?linkid=872238)。

### <a name="administrators"></a>管理员
请参阅[了解 Microsoft PowerApps 的本地数据网关](https://docs.microsoft.com/powerapps/maker/canvas-apps/gateway-reference#tenant-level-administration)一文中的“租户管理”部分，获取有关为组织管理网关的指导。

## <a name="step-11-export-the-users-personal-data-in-microsoft-flow"></a>步骤 11：导出 Microsoft Flow 中的用户个人数据
PowerApps 许可证始终包含 Microsoft Flow 功能。 除了包含在 PowerApps 许可证中以外，Microsoft Flow 还作为独立服务提供。 有关如何响应 Microsoft Flow 服务用户的 DSR 请求的指导，请参阅[响应针对 Microsoft Flow 的 GDPR 数据主体请求](https://go.microsoft.com/fwlink/?linkid=872250)。

> [!IMPORTANT]
>  建议管理员为 PowerApps 用户完成此步骤。
>
>

## <a name="step-12-export-the-users-personal-data-in-cds-for-apps-instances"></a>步骤 12：导出 CDS for Apps 实例中的用户个人数据
某些 PowerApps 许可证允许组织内的用户创建 CDS for Apps 以及创建和生成 CDS for Apps 应用，包括 PowerApps 社区计划，即允许用户在单独环境中试用 CDS for Apps 的免费许可证。 要了解每个 PowerApps 许可证随附的 CDS for Apps 功能，请参阅 [PowerApps 定价页](https://powerapps.microsoft.com/pricing)。

有关如何响应 CDS for Apps 用户的 DSR 请求的指导，请参阅[响应针对 Common Data Service for Apps 客户数据的数据主体权限 (DSR) 请求](common-data-service-gdpr-dsr-guide.md)。

> [!IMPORTANT]
>  建议管理员为 PowerApps 用户完成此步骤。
>
>
