---
title: PowerShell 支持 | Microsoft 文档
description: 介绍不同的 PowerShell cmdlet，并演练如何安装和运行
services: powerapps
suite: powerapps
documentationcenter: na
author: jamesol-msft
manager: kfile
editor: ''
tags: ''
ms-topic: article
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 04/23/2018
ms.author: jamesol
ms.openlocfilehash: 69508b2127c5c919db4a334045c6eed3bb9374af
ms.sourcegitcommit: 0a781b50a8551f2e61c22725ef1c43ba4fdf752a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/27/2018
---
# <a name="powershell-support-for-powerapps-preview"></a>对 PowerApps 的 PowerShell 支持（预览版）
随着面向应用创建者和管理员的 PowerShell cmdlet 预览版的推出，可以在 [PowerApps](https://web.powerapps.com) 或 [PowerApps 管理中心](https://admin.powerapps.com)自动执行许多目前只能手动进行的监视和管理任务。

## <a name="installation"></a>安装
要运行应用创建者 PowerShell cmdlet，请执行以下操作：

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

6. 在访问任何命令之前，需要使用以下命令提供凭据。 这些凭据的刷新间隔长达 8 小时，然后才会要求再次登录以继续使用 cmdlet。

    ```
    Add-PowerAppsAccount
    ```

7.  这是现在的[已知问题](https://powerusers.microsoft.com/t5/Administering-PowerApps/Getting-errors-when-I-try-to-import-the-preview-powerapps/td-p/109036)，可能还需要使用以下命令手动解除锁定 PowerShell 文件：

    ```
    dir . | Unblock-File
    ```

## <a name="powerapps-cmdlets-for-app-makers-preview"></a>应用程序创建者 PowerApps cmdlet（预览版）

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
| 读取、更新和删除流 | Get-AdminFlow <br> Enable-AdminFlow <br> Disable-AdminFlow <br> Remove-AdminFlow  <br> Remove-AdminFlowOwnerRole

> [!NOTE]
> 使用以下命令了解语法并查看每个 cmdlet 的示例：
>```
>Get-Help Get-AdminEnvironment
>Get-Help Get-AdminEnvironment -Examples
>Get-Help Get-AdminEnvironment -Detailed
>```

## <a name="questions"></a>有疑问？

如果有任何评论、建议或问题，请将它们发布到[管理 PowerApps 社区版块](https://powerusers.microsoft.com/t5/Administering-PowerApps/bd-p/Admin_PowerApps)。
