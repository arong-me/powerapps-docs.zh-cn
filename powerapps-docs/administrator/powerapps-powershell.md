---
title: PowerShell 支持（预览版）| Microsoft Docs
description: 介绍不同的 PowerShell cmdlet，并演练如何安装和运行。
author: jamesol-msft
manager: kvivek
ms.service: powerapps
ms.component: pa-admin
ms.topic: reference
ms.date: 08/23/2018
ms.author: jamesol
search.audienceType:
- admin
search.app:
- D365CE
- PowerApps
- Powerplatform
ms.openlocfilehash: 0d5d2cee770e03c4e587db0bff624f34395ed92c
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/24/2018
ms.locfileid: "42864419"
---
# <a name="powershell-support-for-powerapps-preview"></a>对 PowerApps 的 PowerShell 支持（预览版）
随着面向应用创建者和管理员的 PowerShell cmdlet 预览版的推出，可以在 [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) 或 [PowerApps 管理中心](https://admin.powerapps.com)自动执行许多目前只能手动进行的监视和管理任务。

## <a name="installation"></a>安装
若要运行应用创建者 PowerShell cmdlet，请执行以下操作：

1. 下载 [PowerShell 脚本文件](https://go.microsoft.com/fwlink/?linkid=2006349)。

2. 将文件解压缩到文件夹。

3. 在此相同文件夹中，打开 PowerShell 命令窗口（以管理员身份）。

4. 运行以下一次性 PowerShell 命令（假定你从未在当前计算机上运行过 PowerShell 命令）：

    ```
    Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Force
    ```

5. 使用以下命令导入必要模块：

    ```
    Import-Module .\Microsoft.PowerApps.Administration.PowerShell.psm1 -Force
    Import-Module .\Microsoft.PowerApps.PowerShell.psm1 -Force
    ```

6.  这是现在的[已知问题](https://powerusers.microsoft.com/t5/Administering-PowerApps/Getting-errors-when-I-try-to-import-the-preview-powerapps/td-p/109036)，可能还需要使用以下命令手动解除锁定 PowerShell 文件：

    ```
    dir . | Unblock-File
    ```
7. 在访问任何命令之前，需要使用以下命令提供凭据。 这些凭据的刷新间隔长达 8 小时，然后才会要求再次登录以继续使用 cmdlet。

    ```
    # This call will open a prompt to collect the credentials (AAD account & password) that will be used by the commands
    Add-PowerAppsAccount
    ```

    ```
    # Here is how you can pass in credentials (avoiding opening a prompt)
    $pass = ConvertTo-SecureString "password" -AsPlainText -Force
    Add-PowerAppsAccount -Username foo@bar.com -Password $pass
    ```


## <a name="powerapps-cmdlets-for-app-creators-preview"></a>应用创建者 PowerApps cmdlet（预览版）

### <a name="prerequisite"></a>先决条件
具有有效 PowerApps 许可证的用户可以在这些 cmdlet 中执行此操作，但他们只能访问已创建或与之共享的资源（例如应用、流等）。

### <a name="cmdlet-list"></a>cmdlet 列表
> [!NOTE]
> 我们已在最新版本中更新某些 cmdlet 函数名称，添加相应的前缀以避免冲突。 请参阅下表，了解已更改内容的概述。

| 用途 | cmdlet |
| --- | --- |
| 读取环境 | Get-PowerAppEnvironment *（以前称为 Get-PowerAppsEnvironment）* <br> Get-FlowEnvironment
| 读取、更新和删除画布应用 | Get-PowerApp（以前称为 Get-App） <br> Remove-PowerApp（以前称为 Remove-App） <br> Publish-PowerApp（以前称为 Publish-App） <br> Set-AppDisplayName（以前称为 Set-PowerAppDisplayName）<br> Get-PowerAppVersion（以前称为 Get-AppVersion） <br> Restore-PowerAppVersion（以前称为 Restore-AppVersion）
| 读取、更新和删除画布应用权限 | Get-PowerAppRoleAssignment *（以前称为 Get-AppRoleAssignment）* <br> Set-PowerAppRoleAssignment *（以前称为 Set-AppRoleAssignment）* <br> Remove-PowerAppRoleAssignment *（以前称为 Remove-AppRoleAssignment）*
| 读取、更新和删除流 | Get-Flow <br> Get-FlowRun <br> Enable-Flow <br> Disable-Flow <br> Remove-Flow
| 读取、更新和删除流权限 | Get-FlowOwnerRole <br> Set-FlowOwnerRole <br> Remove-FlowOwnerRole
| 读取和响应流审批 | Get-FlowApprovalRequest <br> Get-FlowApproval <br> RespondTo-FlowApprovalRequest
| 读取和删除连接 | Get-PowerAppConnection *（以前称为 Get-Connection）* <br> Remove-PowerAppConnection *（以前称为 Remove-Connection）*
| 读取、更新和删除连接权限 | Get-PowerAppConnectionRoleAssignment *（以前称为 Get-ConnectionRoleAssignment）* <br> Set-PowerAppConnectionRoleAssignment *（以前称为 Set-ConnectionRoleAssignment）* <br> Remove-PowerAppConnectionRoleAssignment *（以前称为 Remove-ConnectionRoleAssignment）*
| 读取和删除连接器 | Get-PowerAppConnector *（以前称为 Get-Connector）* <br> Remove-PowerAppConnector *（以前称为 Remove-Connector）*
| 读取、更新和删除自定义连接器权限 | Get-PowerAppConnectorRoleAssignment *（以前称为 Get-ConnectorRoleAssignment）* <br> Set-PowerAppConnectorRoleAssignment *（以前称为 Set-ConnectorRoleAssignment）* <br> Remove-PowerAppConnectorRoleAssignment *（以前称为 Remove-ConnectorRoleAssignment）*


> [!NOTE]
> 使用以下命令了解语法并查看每个 cmdlet 的示例：
>```
>Get-Help Get-PowerAppEnvironment
>Get-Help Get-PowerAppEnvironment -Examples
>Get-Help Get-PowerAppEnvironment -Detailed
>```

## <a name="powerapps-cmdlets-for-administrators-preview"></a>管理员 PowerApps cmdlet（预览版）

### <a name="prerequisite"></a>先决条件
要在管理员 cmdlet 中执行管理操作，需要以下各项：

* PowerApps 计划 2 付费许可证，或 PowerApps 计划 2 试用许可证。 可以在 [http://web.powerapps.com/trial](http://web.powerapps.com/trial) 注册以获取 30 天试用许可证。 如果试用许可证已过期，可以续订。

* 如果需要搜索另一个用户的资源，还将需要 [Office 365 全局管理员](https://support.office.com/article/assign-admin-roles-in-office-365-for-business-eac4d046-1afd-4f1a-85fc-8219c79e1504)或 [Azure Active Directory 全局管理员](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal)权限。 （请注意，环境管理员仅能访问那些他们具有权限的环境和环境资源。）

### <a name="cmdlet-list"></a>cmdlet 列表
> [!NOTE]
> 我们已在最新版本中更新某些 cmdlet 函数名称，添加相应的前缀以避免冲突。 请参阅下表，了解已更改内容的概述。

| 用途 | cmdlet
| --- | ---
| 读取、更新和删除环境和 Common Data Service for Apps 数据库 | 新增-AdminPowerAppEnvironment **\*新增\*** <br> Set-AdminPowerAppEnvironmentDisplayName **\*新增\*** <br> Get-AdminPowerAppEnvironment *（以前称为 Get-AdminEnvironment）* <br> Remove-AdminPowerAppEnvironment *（以前称为 Remove-AdminEnvironment）* <br> 新增-AdminPowerAppCdsDatabase **\*新增\*** <br> Get-AdminPowerAppCdsDatabaseLanguages **\*新增\*** <br> Get-AdminPowerAppCdsDatabaseCurrencies **\*新增\*** <br> Get-AdminPowerAppEnvironmentLocations **\*新增\***
| 读取、更新和删除环境权限 <br><br> 这些 cmdlet 当前仅适用于没有 Common Data Service (CDS) for Apps 数据库的环境。 | Get-AdminPowerAppEnvironmentRoleAssignment *（以前称为 Get-AdminEnvironmentRoleAssignment）* <br> Set-AdminPowerAppEnvironmentRoleAssignment *（以前称为 Set-AdminEnvironmentRoleAssignment）* <br> Remove-AdminPowerAppEnvironmentRoleAssignment *（以前称为 Remove-AdminEnvironmentRoleAssignment）*
| 读取、更新和删除画布应用 | Get-AdminPowerApp *（以前称为 Get-AdminApp）* <br> Remove-AdminPowerApp *（以前称为 Remove-AdminApp）* <br> Get-AdminPowerAppConnectionReferences **\*新增\*** <br> Set-AdminPowerAppAsFeatured **\*新增\*** <br> Clear-AdminPowerAppAsFeatured **\*新增\*** <br> Set-AdminPowerAppAsHero **\*新增\*** <br> Clear-AdminPowerAppAsHero **\*新增\*** <br> Set-AdminPowerAppApisToBypassConsent **\*新增\*** <br> Clear-AdminPowerAppApisToBypassConsent **\*新增\***
| 读取、更新和删除画布应用权限 | Get-AdminPowerAppRoleAssignment *（以前称为 Get-AdminAppRoleAssignment）* <br> Remove-AdminPowerAppRoleAssignment *（以前称为 Remove-AdminAppRoleAssignment）* <br> Set-AdminPowerAppRoleAssignment *（以前称为 Set-AdminAppRoleAssignment）* <br> Set-AdminPowerAppOwner *（以前称为 Set-AdminAppOwner）*
| 读取、更新和删除流 | Get-AdminFlow <br> Enable-AdminFlow <br> Disable-AdminFlow <br> Remove-AdminFlow <br> Remove-AdminFlowApprovals **\*新增\***
| 读取、更新和删除流权限 | Get-AdminFlowOwnerRole <br> Set-AdminFlowOwnerRole <br> Remove-AdminFlowOwnerRole
| 读取和删除连接 | Get-AdminPowerAppConnection *（以前称为 Get-AdminConnection）* <br> Remove-AdminPowerAppConnection *（以前称为 Remove-AdminConnection）*
| 读取、更新和删除连接权限 | Get-AdminPowerAppConnectionRoleAssignment *（以前称为 Get-AdminConnectionRoleAssignment）* <br> Set-AdminPowerAppEnvironmentConnectionRoleAssignment *（以前称为 Set-AdminConnectionRoleAssignment）* <br> Remove-AdminPowerAppConnectionRoleAssignment *（以前称为 Remove-AdminConnectionRoleAssignment）*
| 读取和删除自定义连接器 | Get-AdminPowerAppConnector *（以前称为 Get-AdminConnector）* <br> Remove-AdminPowerAppConnector *（以前称为 Remove-AdminConnector）*
| 读取、更新和删除自定义连接器权限 | Get-AdminPowerAppConnectorRoleAssignment *（以前称为 Get-AdminConnectorRoleAssignment）*<br> Set-AdminPowerAppConnectorRoleAssignment *（以前称为 Set-AdminConnectorRoleAssignment）* <br> Remove-AdminPowerAppConnectorRoleAssignment *（以前称为 Remove-AdminConnectorRoleAssignment）*
| 读取用户的 PowerApps 用户设置、用户应用设置和通知 | Get-AdminPowerAppsUserDetails
| 读取和删除用户的 Microsoft Flow 设置，这些设置对用户不可见，但支持流执行 | Get-AdminFlowUserDetails <br> Remove-AdminFlowUserDetails
| 创建、读取、更新和删除组织的数据丢失防护策略 | Get-AdminDlpPolicy *（以前称为 Get-AdminApiPolicy）* <br> Add-AdminDlpPolicy *（以前称为 Add-AdminApiPolicy）* <br> Remove-AdminDlpPolicy *（以前称为 Remove-AdminApiPolicy）* <br> Set-AdminDlpPolicy *（以前称为 Set-AdminApiPolicy）* <br> Add-ConnectorToBusinessDataGroup <br>  Remove-ConnectorFromBusinessDataGroup

> [!NOTE]
> 使用以下命令了解语法并查看每个 cmdlet 的示例：
>```
>Get-Help Get-AdminPowerAppEnvironment
>Get-Help Get-AdminPowerAppEnvironment -Examples
>Get-Help Get-AdminPowerAppEnvironment -Detailed
>```

## <a name="version-history"></a>版本历史记录
| 版本 | Date | 更新 |
| --- | --- | --- |
| 1.0 | 2018 年 4 月 23 日 | <ol> <li> 最初发布的应用创建者 PowerApps cmdlet（预览版）包含面向环境、应用、流、流审批、连接和自定义连接器的管理 cmdlet </li> <li> 最初发布的管理员 PowerApps cmdlet（预览版）包含面向环境、应用和流的管理 cmdlet </li></ol>|
| 2.0 | 2018 年 5 月 24 日 | <ol> <li> 面向应用创建者和管理员的 cmdlet 的次要 Bug 修复 </li> <li> 添加了以下新的管理 cmdlet： <br> Get-AdminConnection <br> Remove-AdminConnection <br> Get-AdminConnectionRoleAssignment <br> Set-AdminConnectionRoleAssignment <br>Remove-AdminConnectionRoleAssignment <br>Get-AdminConnector  <br>Remove-AdminConnector <br>Set-AdminConnectorRoleAssignment  <br>Get-AdminConnectorRoleAssignment  <br>Remove-AdminConnectorRoleAssignment <br>Get-AdminPowerAppsUserDetails <br>Get-AdminFlowUserDetails <br>Remove-AdminFlowUserDetails <br>Get-AdminApiPolicy  <br>Add-AdminApiPolicy <br>Remove-AdminApiPolicy <br>Set-AdminApiPolicy <br>Add-ConnectorToBusinessDataGroup  <br>Remove-ConnectorFromBusinessDataGroup </li> </ol>
| 3.0 | 2018 年 7 月 30 日 | <ol> <li> 添加了相关功能以将凭据传递给 PowerAppsAccount（用于启用定期脚本） </li> <li>  面向应用创建者和管理员的 cmdlet 的次要 Bug 修复 </li> <li> 向应用创建者的每个 cmdlet 中添加了“PowerApp”或“Flow”前缀 </li> <li>  向管理员的每个 cmdlet 中添加了“AdminPowerApp”或“AdminFlow”前缀 </li> <li> 添加了以下新的管理 cmdlet： <br> New-AdminPowerAppEnvironment <br> Set-AdminPowerAppEnvironmentDisplayName <br> New-AdminPowerAppCdsDatabase <br> Get-AdminPowerAppCdsDatabaseLanguages <br> Get-AdminPowerAppCdsDatabaseCurrencies <br> Get-AdminPowerAppEnvironmentLocations <br> Get-AdminPowerAppConnectionReferences <br> Set-AdminPowerAppAsFeatured <br> Clear-AdminPowerAppAsFeatured <br> Set-AdminPowerAppAsHero <br> Clear-AdminPowerAppAsHero <br> Set-AdminPowerAppApisToBypassConsent <br> Clear-AdminPowerAppApisToBypassConsent <br> Remove-AdminFlowApprovals </li></ol>
| 4.0 | 2018 年 8 月 15 日 | 向 New-AdminPowerAppCdsDatabase 中添加了一个可选参数，以在默认情况下使函数同步（即，它不会返回，直到数据库已成功预配）
| 5.0 | 2018 年 8 月 24 日 | 修复了一个问题，即流管理员 cdmlet 未返回数据以根据安全设置进行使用

## <a name="questions"></a>有疑问？

如果有任何评论、建议或问题，请将它们发布到[管理 PowerApps 社区版块](https://powerusers.microsoft.com/t5/Administering-PowerApps/bd-p/Admin_PowerApps)。
