---
title: PowerShell 支持（预览版）| Microsoft Docs
description: 介绍不同的 PowerShell cmdlet，并演练如何安装和运行。
author: jamesol-msft
manager: kfile
ms.service: powerapps
ms.component: pa-admin
ms.topic: reference
ms.date: 05/23/2018
ms.author: jamesol
ms.openlocfilehash: 2cb1e1b83cffee2ccea0a4d4b563de44aaa3e68c
ms.sourcegitcommit: 79b8842fb0f766a0476dae9a537a342c8d81d3b3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2018
ms.locfileid: "37896181"
---
# <a name="powershell-support-for-powerapps-preview"></a>对 PowerApps 的 PowerShell 支持（预览版）
随着面向应用创建者和管理员的 PowerShell cmdlet 预览版的推出，可以在 [PowerApps](https://web.powerapps.com) 或 [PowerApps 管理中心](https://admin.powerapps.com)自动执行许多目前只能手动进行的监视和管理任务。

## <a name="installation"></a>安装
若要运行应用创建者 PowerShell cmdlet，请执行以下操作：

1. 下载 [PowerShell 脚本文件](https://go.microsoft.com/fwlink/?linkid=872358)。

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
    Add-PowerAppsAccount
    ```


## <a name="powerapps-cmdlets-for-app-creators-preview"></a>应用创建者 PowerApps cmdlet（预览版）

### <a name="prerequisite"></a>先决条件
具有有效 PowerApps 许可证的用户可以在这些 cmdlet 中执行此操作，但他们只能访问已创建或与之共享的资源（例如应用、流等）。

### <a name="cmdlet-list"></a>cmdlet 列表

| 用途 | cmdlet |
| --- | --- |
| 读取环境 | Get-PowerAppsEnvironment <br> Get-FlowEnvironment
| 读取、更新和删除画布应用 | Get-App <br> Remove-App <br> Publish-App <br> Set-AppDisplayName <br> Get-AppVersion <br> Restore-AppVersion
| 读取、更新和删除画布应用权限 | Get-AppRoleAssignment <br> Set-AppRoleAssignment <br> Remove-AppRoleAssignment
| 读取、更新和删除流 | Get-Flow <br> Get-FlowRun <br> Enable-Flow <br> Disable-Flow <br> Remove-Flow
| 读取、更新和删除流权限 | Get-FlowOwnerRole <br> Set-FlowOwnerRole <br> Remove-FlowOwnerRole
| 读取和响应流审批 | Get-FlowApprovalRequest <br> Get-FlowApproval <br> RespondTo-FlowApprovalRequest
| 读取和删除连接 | Get-Connection <br> Remove-Connection
| 读取、更新和删除连接权限 | Get-ConnectionRoleAssignment <br> Set-ConnectionRoleAssignment <br> Remove-ConnectionRoleAssignment
| 读取和删除连接器 | Get-Connector <br> Remove-Connector
| 读取、更新和删除自定义连接器权限 | Get-ConnectorRoleAssignment <br> Set-ConnectorRoleAssignment <br> Remove-ConnectorRoleAssignment


> [!NOTE]
> 使用以下命令了解语法并查看每个 cmdlet 的示例：
>```
>Get-Help Get-PowerAppsEnvironment
>Get-Help Get-PowerAppsEnvironment -Examples
>Get-Help Get-PowerAppsEnvironment -Detailed
>```

## <a name="powerapps-cmdlets-for-administrators-preview"></a>管理员 PowerApps cmdlet（预览版）

### <a name="prerequisite"></a>先决条件
要在管理员 cmdlet 中执行管理操作，需要以下各项：

* PowerApps 计划 2 付费许可证，或 PowerApps 计划 2 试用许可证。 可以在 [http://web.powerapps.com/trial](http://web.powerapps.com/trial) 注册以获取 30 天试用许可证。 如果试用许可证已过期，可以续订。

* 如果需要搜索另一个用户的资源，还将需要 [Office 365 全局管理员](https://support.office.com/article/assign-admin-roles-in-office-365-for-business-eac4d046-1afd-4f1a-85fc-8219c79e1504)或 [Azure Active Directory 全局管理员](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal)权限。 （请注意，环境管理员仅能访问那些他们具有权限的环境和环境资源。）

### <a name="cmdlet-list"></a>cmdlet 列表

| 用途 | cmdlet
| --- | ---
| 读取和删除环境 | Get-AdminEnvironment <br> Remove-AdminEnvironment
| 读取、更新和删除环境权限 <br><br> 这些 cmdlet 仅适用于没有 Common Data Service (CDS) for Apps 数据库的环境。 | Get-AdminEnvironmentRoleAssignment <br> Set-AdminEnvironmentRoleAssignment <br> Remove-AdminEnvironmentRoleAssignment
| 读取和删除画布应用 | Get-AdminApp <br> Remove-AdminApp
| 读取、更新和删除画布应用权限 | Get-AdminAppRoleAssignment <br> Remove-AdminAppRoleAssignment <br> Set-AdminAppRoleAssignment <br> Set-AdminAppOwner
| 读取、更新和删除流 | Get-AdminFlow <br> Enable-AdminFlow <br> Disable-AdminFlow <br> Remove-AdminFlow
| 读取、更新和删除流权限 | Get-AdminFlowOwnerRole <br> Set-AdminFlowOwnerRole <br> Remove-AdminFlowOwnerRole
| 读取和删除连接 | Get-AdminConnection <br> Remove-AdminConnection
| 读取、更新和删除连接权限 | Get-AdminConnectionRoleAssignment <br> Set-AdminConnectionRoleAssignment <br> Remove-AdminConnectionRoleAssignment
| 读取和删除自定义连接器 | Get-AdminConnector <br> Remove-AdminConnector
| 读取、更新和删除自定义连接器权限 | Get-AdminConnectorRoleAssignment <br> Set-AdminConnectorRoleAssignment <br> Remove-AdminConnectorRoleAssignment
| 读取用户的 PowerApps 用户设置、用户应用设置和通知 | Get-AdminPowerAppsUserDetails
| 读取和删除用户的 Microsoft Flow 设置，这些设置对用户不可见，但支持流执行 | Get-AdminFlowUserDetails <br> Remove-AdminFlowUserDetails
| 创建、读取、更新和删除组织的数据丢失防护策略 | Get-AdminApiPolicy <br> Add-AdminApiPolicy <br> Remove-AdminApiPolicy <br> Set-AdminApiPolicy <br> Add-ConnectorToBusinessDataGroup <br>  Remove-ConnectorFromBusinessDataGroup

> [!NOTE]
> 使用以下命令了解语法并查看每个 cmdlet 的示例：
>```
>Get-Help Get-AdminEnvironment
>Get-Help Get-AdminEnvironment -Examples
>Get-Help Get-AdminEnvironment -Detailed
>```

## <a name="questions"></a>有疑问？

如果有任何评论、建议或问题，请将它们发布到[管理 PowerApps 社区版块](https://powerusers.microsoft.com/t5/Administering-PowerApps/bd-p/Admin_PowerApps)。
