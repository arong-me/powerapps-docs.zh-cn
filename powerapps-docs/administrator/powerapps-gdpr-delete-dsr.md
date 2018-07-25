---
title: 响应对删除客户数据的数据主体权限 (DSR) 请求 | Microsoft Docs
description: 演练如何响应对删除 PowerApps 客户数据的数据主体权限 (DSR) 请求。
author: jamesol-msft
manager: kfile
ms.service: powerapps
ms.component: pa-admin
ms.topic: conceptual
ms.date: 05/23/2018
ms.author: jamesol
ms.openlocfilehash: d518cbf398d0f29b25da9dafcfa6e9026fcee88e
ms.sourcegitcommit: 79b8842fb0f766a0476dae9a537a342c8d81d3b3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2018
ms.locfileid: "37897170"
---
# <a name="responding-to-data-subject-rights-dsr-requests-to-delete-powerapps-customer-data"></a>响应对删除 PowerApps 客户数据的数据主体权限 (DSR) 请求

从组织的客户数据中删除个人数据的“删除权限”是欧盟 (EU) 一般数据保护条例 (GDPR) 中的关键保护。 删除个人数据包括删除系统生成的日志，但不包括审核日志信息。

PowerApps 允许用户生成业务线应用程序，这些应用程序是组织日常运营的关键部分。 当某位用户离开组织时，你将需要手动检查并确定是否删除此用户创建的某些数据和资源。 从 Azure Active Directory 删除用户帐户时，将自动删除其他个人数据。

以下是有关将自动删除的个人数据和哪些数据需手动检查和删除的明细：

需手动检查和删除 |   从 Azure Active Directory 中删除用户时自动删除
--- | ---
环境\** | 网关
环境权限\*** | 网关权限
画布应用\** | PowerApps 通知
画布应用权限 | PowerApps 用户设置
连接\** | PowerApps 用户应用设置
连接权限 |
自定义连接器\** |
自定义连接器权限 |  

\** 这些资源均包含带个人数据的“创建者”和“修改者”记录。 出于安全原因，将保留这些记录，直到删除这些资源。

\*** 对于包含 Common Data Service (CDS) for Apps 数据库的环境，环境权限（即向用户分配“环境创建者”和“管理员”角色）作为记录存储在此数据库中。 有关如何响应 CDS for Apps 用户的 DSR 的指导，请参阅[响应针对 Common Data Service for Apps 客户数据的数据主体权限 (DSR) 请求](common-data-service-gdpr-dsr-guide.md)。

对于需要手动检查的数据和资源，PowerApps 提供以下体验来重新分配（如有必要）或删除特定用户的个人数据：

* 网站访问：[PowerApps 站点](https://web.powerapps.com)、[PowerApps 管理中心](https://admin.powerapps.com/)和 [Office 365 服务信任门户](https://servicetrust.microsoft.com/)

* PowerShell 访问：用于[应用创建者](https://go.microsoft.com/fwlink/?linkid=871448)和[管理员](https://go.microsoft.com/fwlink/?linkid=871804)的 PowerApps cmdlet，以及用于[本地网关](https://go.microsoft.com/fwlink/?linkid=872238)的 cmdlet。

以下是可以用于删除包含个人数据的各类资源的体验明细：

包含个人数据的资源 | 网站访问 | PowerShell 访问
--- | --- | ---
环境 | PowerApps 管理中心 |  PowerApps cmdlet
环境权限**   | PowerApps 管理中心 | PowerApps cmdlet
画布应用  | PowerApps 管理中心 <br> PowerApp| PowerApps cmdlet
画布应用权限  | PowerApps 管理中心 | PowerApps cmdlet
连接 | | 应用创建者：可用 <br> 管理员：可用
连接权限 | | 应用创建者：可用 <br> 管理员：可用
自定义连接器 | | 应用创建者：可用 <br> 管理员：可用
自定义连接器权限 | | 应用创建者：可用 <br> 管理员：可用

\** 在引入 CDS for Apps 后，如果数据库是在环境中创建的，那么环境权限和模型驱动应用权限就会作为记录存储在该数据库实例中。 有关如何响应 CDS for Apps 用户的 DSR 的指导，请参阅[响应针对 Common Data Service for Apps 客户数据的数据主体权限 (DSR) 请求](common-data-service-gdpr-dsr-guide.md)。

## <a name="prerequisites"></a>先决条件

### <a name="for-users"></a>对于用户
任何具有有效 PowerApps 许可证的用户都可以使用 [PowerApps](https://web.powerapps.com) 或[应用创建者的 PowerShell cmdlet](https://go.microsoft.com/fwlink/?linkid=871448) 来执行本文档所述的用户操作。

#### <a name="unmanaged-tenant"></a>非托管租户
如果你是[非托管租户](https://docs.microsoft.com/azure/active-directory/domains-admin-takeover)的成员（即你的 Azure AD 租户没有全局管理员），则仍将能够按照本文中所述的步骤来删除自己的个人数据。  但是，由于你的租户没有全局管理员，因此你将需要按照下面[步骤 11：从 Azure Active Directory 中删除用户](#step-11-delete-the-user-from-azure-active-directory)中所述的说明从租户中删除自己的帐户。

若要确定你是否是非托管租户的成员，请按以下步骤操作：

1. 在浏览器中打开以下 URL，确保在 URL 中替换电子邮件地址： https://login.windows.net/common/userrealm/foobar@contoso.com?api-version=2.1

2. 如果你是“非托管租户”的成员，则将会在响应中看到 `"IsViral": true`。
   ```
   {
   ...
   "Login": "foobar@unmanagedcontoso.com",
   "DomainName": "unmanagedcontoso.com",
   "IsViral": true,
   ...
   }
   ```

3. 否则，你就属于“托管的租户”。

### <a name="for-administrators"></a>对于管理员
要使用 [PowerApps 管理中心](https://admin.powerapps.com/)、Microsoft Flow 管理中心，或 [PowerApps 管理员 PowerShell cmdlet](https://go.microsoft.com/fwlink/?linkid=871804) 来执行本文档所述的管理员操作，将需要以下各项：

* PowerApps 计划 2 付费许可证，或 PowerApps 计划 2 试用许可证。 可以在 [http://web.powerapps.com/trial](http://web.powerapps.com/trial) 注册以获取 30 天试用许可证。 如果试用许可证已过期，可以续订。

* 如果需要搜索另一个用户的资源，还将需要 [Office 365 全局管理员](https://support.office.com/article/assign-admin-roles-in-office-365-for-business-eac4d046-1afd-4f1a-85fc-8219c79e1504)或 [Azure Active Directory 全局管理员](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal)权限。 （请注意，环境管理员仅能访问那些他们具有权限的环境和环境资源。）

## <a name="step-1-delete-or-reassign-all-environments-created-by-the-user"></a>步骤 1：删除或重新分配由用户创建的所有环境
作为管理员，在处理用户创建的每个环境的 DSR 删除请求时，需要作出两个决定：

1. 如果确定组织中没有其他人使用环境，可以选择删除环境。

2. 如果确定环境仍然是必需的，可以选择不删除环境，并将自己（或组织中的另一个用户）添加为“环境管理员”。

> [!IMPORTANT]
> 删除环境将永久删除环境中的所有资源，包括所有应用、流、连接等。因此，请在删除前检查环境中的内容。

### <a name="give-access-to-a-users-environments-from-the-powerapps-admin-center"></a>从 PowerApps 管理中心提供对用户环境的访问权限
管理员可以通过以下步骤，从 [PowerApps 管理中心](https://admin.powerapps.com/)授予对特定用户创建的环境的管理访问权限：

1. 从 [PowerApps 管理中心](https://admin.powerapps.com/)，选择组织中的每个环境。

    ![管理中心登录页](./media/powerapps-gdpr-delete-dsr/admin-center-landing.png)

2. 如果环境由 DSR 请求的用户创建，请选择“安全”，并继续执行在[管理环境](environments-administration.md)中列出的步骤，为你自己或组织中的另一个用户提供管理权限。

    ![环境安全](./media/powerapps-gdpr-delete-dsr/share-environment.png)

### <a name="delete-environments-created-by-a-user-from-the-powerapps-admin-center"></a>从 PowerApps 管理中心删除由用户创建的环境
管理员可以通过以下步骤，从 [PowerApps 管理中心](https://admin.powerapps.com/)查看并删除特定用户创建的环境：

1. 从 [PowerApps 管理中心](https://admin.powerapps.com/)，选择组织中的每个环境。

    ![管理中心登录页](./media/powerapps-gdpr-delete-dsr/admin-center-landing.png)

2. 如果环境由 DSR 请求的用户创建，选择“删除”，然后继续执行相关步骤以删除环境：

    ![删除环境](./media/powerapps-gdpr-delete-dsr/delete-environment.png)

### <a name="give-access-to-a-users-environments-using-powershell"></a>使用 PowerShell 提供对用户环境的访问权限
管理员可以通过 [PowerApps 管理员 PowerShell cmdlet](https://go.microsoft.com/fwlink/?linkid=871804) 中的 Set-AdminEnvironmentRoleAssignment 函数，向自己（或组织内的另一个用户）分配对用户创建的所有环境的访问权限：

```
Add-PowerAppsAccount
$deleteDsrUserId = "0ecb1fcc-6782-4e46-a4c4-738c1d3accea"
$myUserId = $global:currentSession.UserId

#Assign yourself as an admin to each environment created by the user
Get-AdminEnvironment -CreatedBy $deleteDsrUserId | Set-AdminEnvironmentRoleAssignment -RoleName EnvironmentAdmin -PrincipalType User -PrincipalObjectId $myUserId

#Retrieve the environment role assignments to confirm
Get-AdminEnvironment -CreatedBy $deleteDsrUserId | Get-AdminEnvironmentRoleAssignment
```

> [!IMPORTANT]
> 此函数仅在没有 CDS for Apps 数据库实例的环境中有效。

### <a name="delete-environments-created-by-a-user-using-powershell"></a>使用 PowerShell 删除由用户创建的环境
 管理员可以通过 [PowerApps 管理员 PowerShell cmdlet](https://go.microsoft.com/fwlink/?linkid=871804) 中的 Remove-AdminEnvironment 函数删除由用户创建的所有环境：

```
Add-PowerAppsAccount
$deleteDsrUserId = "0ecb1fcc-6782-4e46-a4c4-738c1d3accea"

# Retrieve all environments created by the user and then delete them
Get-AdminEnvironment -CreatedBy $deleteDsrUserId | Remove-AdminEnvironment
```

## <a name="step-2-delete-the-users-permissions-to-all-other-environments"></a>步骤 2：删除针对所有其他环境的用户权限
可以在环境中向用户分配权限（如“环境管理员”和“环境创建者”），这些权限作为“角色分配”保存在 PowerApps 服务中。
在引入 CDS for Apps 后，如果数据库是在环境中创建的，那么这些“角色分配”就会作为记录存储在该数据库实例中。
有关详细信息，请参阅[管理环境](environments-administration.md)。

### <a name="for-environments-without-a-cds-for-apps-database"></a>对于没有 CDS for Apps 数据库的环境

#### <a name="powerapps-admin-center"></a>PowerApps 管理中心
管理员可通过以下步骤，从 [PowerApps 管理中心](https://admin.powerapps.com/)开始删除用户的环境权限：

1. 从 [PowerApps 管理中心](https://admin.powerapps.com/)选择组织中的每个环境。

    必须是 [Office 365 全局管理员](https://support.office.com/article/assign-admin-roles-in-office-365-for-business-eac4d046-1afd-4f1a-85fc-8219c79e1504)或 [Azure Active Directory 全局管理员](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal)才能查看已在组织中创建的所有环境。

    ![管理中心登录页](./media/powerapps-gdpr-delete-dsr/admin-center-landing.png)

2. 选择“安全”。

    如果环境中没有 CDS for Apps 数据库，你将看到有关“环境角色”的部分。

3. 在“环境角色”中，分别选择“环境管理员”和“环境创建者”，并使用搜索栏搜索用户名。

    ![环境角色页](./media/powerapps-gdpr-delete-dsr/admin-environment-role-share-page.png)

5.  如果用户有权访问任一角色，从“用户”屏幕中，删除其权限，然后选择“保存”。

#### <a name="powershell"></a>PowerShell
管理员可以通过 [PowerApps 管理员 PowerShell cmdlet](https://go.microsoft.com/fwlink/?linkid=871804) 中的 Remove-AdminEnvironmentRoleAssignment 函数，在没有 CDS for Apps 数据库的所有环境中，删除用户的所有环境角色分配：

```
Add-PowerAppsAccount
$deleteDsrUserId = "0ecb1fcc-6782-4e46-a4c4-738c1d3accea"

#find all environment role assignments for the user for environments without a CDS for Apps instance and delete them
Get-AdminEnvironmentRoleAssignment -UserId $deleteDsrUserId | Remove-AdminEnvironmentRoleAssignment
```

> [!IMPORTANT]
> 此函数仅在没有 CDS for Apps 数据库实例的环境中有效。

### <a name="for-environments-with-a-cds-for-apps-database"></a>对于有 CDS for Apps 数据库的环境
在引入 CDS for Apps 后，如果数据库是在环境中创建的，那么这些“角色分配”就会作为记录存储在该数据库实例中。 请参考下面的文档，介绍了如何从 CDS for Apps 数据库实例中删除个人数据：删除 Common Data Service 用户个人数据

## <a name="step-3-delete-or-reassign-all-canvas-apps-owned-by-a-user"></a>步骤 3：删除或重新分配用户所拥有的所有画布应用

### <a name="reassign-a-users-canvas-apps-using-the-powerapps-admin-powershell-cmdlets"></a>使用 PowerApps 管理员 PowerShell cmdlet 重新分配用户的画布应用
如果管理员决定不删除用户的画布应用，他们可以通过 [PowerApps 管理员 PowerShell cdmlet](https://go.microsoft.com/fwlink/?linkid=871804) 中的 Set-AdminAppOwner 函数重新分配用户所拥有的应用：

```
Add-PowerAppsAccount
$deleteDsrUserId = "0ecb1fcc-6782-4e46-a4c4-738c1d3accea"
$newAppOwnerUserId = "72c272b8-14c3-4f7a-95f7-a76f65c9ccd8"

#find all apps owned by the DSR user and assigns them a new owner
Get-AdminApp -Owner $deleteDsrUserId | Set-AdminAppOwner -AppOwner $newAppOwnerUserId
```

### <a name="delete-a-users-canvas-app-using-the-powerapps-site"></a>使用 PowerApps 站点删除用户的画布应用
用户可以从 [PowerApps 站点](https://web.powerapps.com)删除应用。 有关如何删除应用的完整步骤，请参阅“删除应用”。

### <a name="delete-a-users-canvas-app-using-the-powerapps-admin-center"></a>使用 PowerApps 管理中心删除用户的画布应用
管理员可通过以下步骤，从 [PowerApps 管理中心](https://admin.powerapps.com/)开始删除由用户创建的应用：

1. 从 [PowerApps 管理中心](https://admin.powerapps.com/)选择组织中的每个环境。

    必须是 [Office 365 全局管理员](https://support.office.com/article/assign-admin-roles-in-office-365-for-business-eac4d046-1afd-4f1a-85fc-8219c79e1504)或 [Azure Active Directory 全局管理员](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal)才能查看已在组织中创建的所有环境。

    ![管理中心登录页](./media/powerapps-gdpr-delete-dsr/admin-center-landing.png)

2. 选择“资源” > “应用”。

3. 使用搜索栏搜索用户名，将显示已由该用户在此环境中创建的任何应用：

    ![搜索应用](./media/powerapps-gdpr-delete-dsr/search-apps.png)

4. 选择“详细信息”查看归用户所有的每个应用：

    ![选择应用详细信息](./media/powerapps-gdpr-delete-dsr/select-app-details.png)

5. 选择“删除”以删除每个应用：

### <a name="delete-a-users-canvas-app-using-the-powerapps-admin-powershell-cmdlets"></a>使用 PowerApps 管理员 PowerShell cmdlet 删除用户的画布应用
如果管理员决定删除用户所拥有的所有画布应用，他们可以使用 [PowerApps 管理员 PowerShell cmdlet](https://go.microsoft.com/fwlink/?linkid=871804) 中的 Remove-AdminApp 函数来完成此操作：

```
Add-PowerAppsAccount
$deleteDsrUserId = "0ecb1fcc-6782-4e46-a4c4-738c1d3accea"

#find all apps owned by the DSR user and deletes them
Get-AdminApp -Owner "0ecb1fcc-6782-4e46-a4c4-738c1d3accea" | Remove-AdminApp
```

## <a name="step-4-delete-the-users-permissions-to-canvas-apps"></a>步骤 4：删除针对画布应用的用户权限
每当与用户共享应用时，PowerApps 就会存储名为“角色分配”的记录，用于描述用户对应用的权限（CanEdit 或 CanUse）。 有关详细信息，请参阅“共享应用”一文。

> [!NOTE]
> 删除应用时，也将删除应用的角色分配。

> [!NOTE]
> 应用所有者的角色分配只能通过为应用分配新所有者进行删除。

### <a name="powerapps-admin-center"></a>PowerApps 管理中心
管理员可通过以下步骤，从 [PowerApps 管理中心](https://admin.powerapps.com/)开始删除用户的应用角色分配：

1. 从 [PowerApps 管理中心](https://admin.powerapps.com/)选择组织中的每个环境。

    必须是 [Office 365 全局管理员](https://support.office.com/article/assign-admin-roles-in-office-365-for-business-eac4d046-1afd-4f1a-85fc-8219c79e1504)或 [Azure Active Directory 全局管理员](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal)才能查看已在组织中创建的所有环境。

    ![管理中心登录页](./media/powerapps-gdpr-delete-dsr/admin-center-landing.png)

2. 对于每个环境，请选择“资源” > “应用”。

3. 为环境中的每个应用选择“共享”：

    ![选择应用共享](./media/powerapps-gdpr-delete-dsr/select-admin-share-nofilter.png)

4. 如果用户有权访问应用，则从应用的“共享”屏幕中，删除其权限，然后选择“保存”。

    ![管理应用共享页](./media/powerapps-gdpr-delete-dsr/admin-share-page.png)

### <a name="powershell-cmdlets-for-admins"></a>管理员 PowerShell cmdlet
管理员可以通过使用 [PowerApps 管理员 PowerShell cmdlet](https://go.microsoft.com/fwlink/?linkid=871804) 中的 Remove-AdminAppRoleAssignmnet 函数，删除所有用户的画布应用角色分配：

```
Add-PowerAppsAccount
$deleteDsrUserId = "0ecb1fcc-6782-4e46-a4c4-738c1d3accea"

#find all app role assignments for the DSR user and deletes them
Get-AdminAppRoleAssignment -UserId $deleteDsrUserId | Remove-AdminAppRoleAssignment
```

## <a name="step-5-delete-connections-created-by-a-user"></a>步骤 5：删除用户创建的连接
在与其他 API 和 SaaS 系统建立连接时，连接将与连接器结合使用。  连接包括对创建它们的用户的引用，因此可以将其删除以删除对用户的任何引用。

### <a name="powershell-cmdlets-for-app-creators"></a>应用创建者 PowerShell cmdlet
用户可以通过使用 [应用创建者 PowerShell cmdlet](https://go.microsoft.com/fwlink/?linkid=871448) 中的 Remove-Connection 函数删除其所有连接：

```
Add-PowerAppsAccount

#Retrieves all connections for the calling user and deletes them
Get-Connection | Remove-Connection
```

### <a name="powershell-cmdlets-for-powerapps-administrators"></a>PowerApps 管理员 PowerShell cmdlet
管理员可通过使用 [PowerApps 管理员 PowerShell cmdlet](https://go.microsoft.com/fwlink/?linkid=871804) 中的 Remove-AdminConnection 函数来删除用户的所有连接：

```
Add-PowerAppsAccount
$deleteDsrUserId = "0ecb1fcc-6782-4e46-a4c4-738c1d3accea"

#Retrieves all connections for the DSR user and deletes them
Get-AdminConnection -CreatedBy $deleteDsrUserId | Remove-AdminConnection
```

## <a name="step-6-delete-the-users-permissions-to-shared-connections"></a>步骤 6：删除针对共享连接的用户权限

### <a name="powershell-cmdlets-for-app-creators"></a>应用创建者 PowerShell cmdlet
用户可以通过使用 [应用创建者 PowerShell cmdlet](https://go.microsoft.com/fwlink/?linkid=871448) 中的 Remove-ConnectionRoleAssignment 函数删除其共享连接的所有连接角色分配：

```
Add-PowerAppsAccount

#Retrieves all connection role assignments for the calling users and deletes them
Get-ConnectionRoleAssignment | Remove-ConnectionRoleAssignment
```
> [!NOTE]
> 不删除连接资源，就无法删除所有者角色分配。

### <a name="powershell-cmdlets-for-admins"></a>管理员 PowerShell cmdlet
管理员可通过使用 [PowerApps 管理员 PowerShell cmdlet](https://go.microsoft.com/fwlink/?linkid=871804) 中的 Remove-AdminConnectionRoleAssignment 函数来删除用户的所有连接角色分配：

```
Add-PowerAppsAccount
$deleteDsrUserId = "0ecb1fcc-6782-4e46-a4c4-738c1d3accea"

#Retrieves all connection role assignments for the DSR user and deletes them
Get-AdminConnectionRoleAssignment -PrincipalObjectId $deleteDsrUserId | Remove-AdminConnectionRoleAssignment
```

## <a name="step-7-delete-custom-connectors-created-by-the-user"></a>步骤 7：删除用户创建的自定义连接器
自定义连接器补充了现有连接器，并允许连接到其他 API、SaaS 和以自定义方式开发的系统。 你可能想要将自定义连接器所有权转让给其他组织中的用户或删除自定义连接器。

### <a name="powershell-cmdlets-for-app-creators"></a>应用创建者 PowerShell cmdlet
用户可以通过使用 [应用创建者 PowerShell cmdlet](https://go.microsoft.com/fwlink/?linkid=871448) 中的 Remove-Connector 函数删除其所有自定义连接：

```
Add-PowerAppsAccount

#Retrieves all custom connectors for the calling user and deletes them
Get-Connector -FilterNonCustomConnectors | Remove-Connector
```

### <a name="powershell-cmdlets-for-admins"></a>管理员 PowerShell cmdlet
管理员可通过使用 [PowerApps 管理员 PowerShell cmdlet](https://go.microsoft.com/fwlink/?linkid=871804) 中的 Remove-AdminConnector 函数来删除用户创建的所有自定义连接器：

```
Add-PowerAppsAccount
$deleteDsrUserId = "0ecb1fcc-6782-4e46-a4c4-738c1d3accea"

#Retrieves all custom connectors created by the DSR user and deletes them
Get-AdminConnector -CreatedBy $deleteDsrUserId | Remove-AdminConnector
```

## <a name="step-8-delete-the-users-permissions-to-shared-custom-connectors"></a>步骤 8：删除针对共享自定义连接器的用户权限

### <a name="powershell-cmdlets-for-app-creators"></a>应用创建者 PowerShell cmdlet
用户可以通过使用 [应用创建者 PowerShell cmdlet](https://go.microsoft.com/fwlink/?linkid=871448) 中的 Remove-ConnectorRoleAssignment 函数删除其共享自定义连接器的所有连接器角色分配：

```
Add-PowerAppsAccount

#Retrieves all connector role assignments for the calling users and deletes them
Get-ConnectorRoleAssignment | Remove-ConnectorRoleAssignment
```

> [!NOTE]
> 不删除连接资源，就无法删除所有者角色分配。

### <a name="powershell-cmdlets-for-admins"></a>管理员 PowerShell cmdlet
管理员可通过使用 [PowerApps 管理员 PowerShell cmdlet](https://go.microsoft.com/fwlink/?linkid=871804) 中的 Remove-AdminConnectorRoleAssignment 函数来删除用户的所有自定义连接器角色分配：

```
Add-PowerAppsAccount
$deleteDsrUserId = "0ecb1fcc-6782-4e46-a4c4-738c1d3accea"

#Retrieves all custom connector role assignments for the DSR user and deletes them
Get-AdminConnectorRoleAssignment -PrincipalObjectId $deleteDsrUserId | Remove-AdminConnectorRoleAssignment
```

## <a name="step-9-delete-the-users-personal-data-in-microsoft-flow"></a>步骤 9：删除 Microsoft Flow 中的用户个人数据
PowerApps 许可证始终包含 Microsoft Flow 功能。 除了包含在 PowerApps 许可证中以外，Microsoft Flow 还作为独立服务提供。 有关如何响应 Microsoft Flow 服务用户的 DSR 的指导，请参阅[响应针对 Microsoft Flow 的 GDPR 数据主体请求](https://go.microsoft.com/fwlink/?linkid=872250)。

> [!IMPORTANT]
> 建议管理员为 PowerApps 用户完成此步骤。

## <a name="step-10-delete-the-users-personal-data-in-instances-of-cds-for-apps"></a>步骤 10：删除 CDS for Apps 实例中用户的个人数据
某些 PowerApps 许可证（包括 PowerApps 社区计划）让组织中的用户可以创建 CDS for Apps 实例，并在 CDS for Apps 上创建和生成应用。 PowerApps 社区计划为免费许可证，用户可在单独环境中试用 CDS for Apps。 有关每个 PowerApps 许可证随附的功能，请参阅“PowerApps 定价页”。

有关如何响应 CDS for Apps 用户的 DSR 的指导，请参阅[响应针对 Common Data Service for Apps 客户数据的数据主体权限 (DSR) 请求](common-data-service-gdpr-dsr-guide.md)。

> [!IMPORTANT]
> 建议管理员为 PowerApps 用户完成此步骤。

## <a name="step-11-delete-the-user-from-azure-active-directory"></a>步骤 11：从 Azure Active Directory 中删除用户
完成上述步骤后，最后一步是删除用户的 Azure Active Directory 帐户。

### <a name="managed-tenant"></a>托管租户
托管 Azure AD 租户的管理员可按照 [Office 365 服务信任门户](https://servicetrust.microsoft.com/ViewPage/GDPRDSR)中的“Azure 数据主体请求 GDPR”文档中所述的步骤来删除用户帐户。

### <a name="unmanaged-tenant"></a>非托管租户
如果你是非托管租户的成员，则需要遵循以下步骤才能从 Azure AD 租户中删除帐户：

> [!NOTE]
> 请参阅以上[非托管租户](#unmanaged-tenant)部分，了解如何检测你是非托管租户还是托管租户的成员。

1. 导航到[工作和学校隐私页](https://go.microsoft.com/fwlink/?linkid=87312)，并使用 Azure AD 帐户登录。

2. 选择“关闭帐户”并按照说明从 Azure AD 租户中删除帐户。

    ![选择应用共享](./media/powerapps-gdpr-delete-dsr/close-account.png)
