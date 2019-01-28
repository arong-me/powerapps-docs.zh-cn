---
title: PowerShell 支持（预览版）| Microsoft Docs
description: 介绍不同的 PowerShell cmdlet，并演练如何安装和运行。
author: jamesol-msft
manager: kvivek
ms.service: powerapps
ms.component: pa-admin
ms.topic: reference
ms.date: 01/18/2019
ms.author: jamesol
search.audienceType:
- admin
search.app:
- D365CE
- PowerApps
- Powerplatform
ms.openlocfilehash: 0152296adbe01abae2b831576c312a43d1f2a2b8
ms.sourcegitcommit: 3ce7c17f90f87756a072210c8abfbd93733a6d4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/18/2019
ms.locfileid: "54397758"
---
# <a name="powershell-support-for-powerapps-preview"></a>对 PowerApps 的 PowerShell 支持（预览版）
随着面向应用创建者和管理员的 PowerShell cmdlet 预览版的推出，可以在 [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) 或 [PowerApps 管理中心](https://admin.powerapps.com)自动执行许多目前只能手动进行的监视和管理任务。

## <a name="cmdlets"></a>cmdlet
[Cmdlet](https://docs.microsoft.com/powershell/developer/cmdlet/writing-a-windows-powershell-cmdlet) 是用 PowerShell 脚本语言编写的函数，用于在 Windows PowerShell 环境中执行命令。 运行这些 PowerApps cmdlet 将使你可以与业务应用程序平台进行交互，而无需通过 Web 浏览器中的管理门户。 你可以将这些 cmdlet 与其他 PowerShell 函数结合使用，以编写可以优化工作流的复杂脚本。 请注意，如果你不是租户的管理员，仍然可以使用 cmdlet，但将仅限于你所拥有的资源。 以“Admin”一词开头的 Cmdlet 旨在由管理用户帐户使用。

PowerShell 库中提供了两个独立模块的 Cmdlet： 
- [管理员](https://www.powershellgallery.com/packages/Microsoft.PowerApps.Administration.PowerShell/2.0.1)
- [创建者](https://www.powershellgallery.com/packages/Microsoft.PowerApps.PowerShell/1.0.1) 

## <a name="installation"></a>安装
若要运行应用创建者 PowerShell cmdlet，请执行以下操作：

1. 以管理员身份运行 PowerShell。

   > [!div class="mx-imgBorder"] 
   > ![以管理员身份运行 PowerShell](media/open-powershell-as-admin75.png "Run PowerShell as an administrator")

2. 使用以下命令导入必要模块：

    ```
    Install-Module -Name Microsoft.PowerApps.Administration.PowerShell
    Install-Module -Name Microsoft.PowerApps.PowerShell -AllowClobber
    ```
3. 如果系统提示你接受对存储库的“InstallationPolicy”值的更改，请通过键入“A”并按下 Enter 对每个模块接受“[A] Yes”。

   ![接受 InstallationPolicy 值](media/accept-installationpolicy-value75.png "Accept InstallationPolicy value")

4. 在访问任何命令之前，可以使用以下命令提供凭据。 这些凭据的刷新间隔长达 8 小时，然后才会要求再次登录以继续使用 cmdlet。

    ```
    # This call opens prompt to collect credentials (Azure Active Directory account and password) used by the commands 
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

### <a name="cmdlet-list---maker-cmdlets"></a>Cmdlet 列表 - 创建者 Cmdlet
> [!NOTE]
> 我们已在最新版本中更新某些 cmdlet 函数名称，添加相应的前缀以避免冲突。 请参阅下表，了解已更改内容的概述。

| 用途 | cmdlet |
| --- | --- |
| 读取环境 | Get-PowerAppEnvironment *（以前称为 Get-PowerAppsEnvironment）* <br> Get-FlowEnvironment |
| 读取、更新和删除画布应用 | Get-PowerApp（以前称为 Get-App） <br> Remove-PowerApp（以前称为 Remove-App） <br> Publish-PowerApp（以前称为 Publish-App） <br> Set-AppDisplayName（以前称为 Set-PowerAppDisplayName）<br> Get-PowerAppVersion（以前称为 Get-AppVersion） <br> Restore-PowerAppVersion（以前称为 Restore-AppVersion） |
| 读取、更新和删除画布应用权限 | Get-PowerAppRoleAssignment *（以前称为 Get-AppRoleAssignment）* <br> Set-PowerAppRoleAssignment *（以前称为 Set-AppRoleAssignment）* <br> Remove-PowerAppRoleAssignment *（以前称为 Remove-AppRoleAssignment）* |
| 读取、更新和删除流 | Get-Flow <br> Get-FlowRun <br> Enable-Flow <br> Disable-Flow <br> Remove-Flow |
| 读取、更新和删除流权限 | Get-FlowOwnerRole <br> Set-FlowOwnerRole <br> Remove-FlowOwnerRole |
| 读取和响应流审批 | Get-FlowApprovalRequest <br> Get-FlowApproval <br> RespondTo-FlowApprovalRequest |
| 读取和删除连接 | Get-PowerAppConnection *（以前称为 Get-Connection）* <br> Remove-PowerAppConnection *（以前称为 Remove-Connection）* |
| 读取、更新和删除连接权限 | Get-PowerAppConnectionRoleAssignment *（以前称为 Get-ConnectionRoleAssignment）* <br> Set-PowerAppConnectionRoleAssignment *（以前称为 Set-ConnectionRoleAssignment）* <br> Remove-PowerAppConnectionRoleAssignment *（以前称为 Remove-ConnectionRoleAssignment）* |
| 读取和删除连接器 | Get-PowerAppConnector *（以前称为 Get-Connector）* <br> Remove-PowerAppConnector *（以前称为 Remove-Connector）* |
| 读取、更新和删除自定义连接器权限 | Get-PowerAppConnectorRoleAssignment *（以前称为 Get-ConnectorRoleAssignment）* <br> Set-PowerAppConnectorRoleAssignment *（以前称为 Set-ConnectorRoleAssignment）* <br> Remove-PowerAppConnectorRoleAssignment *（以前称为 Remove-ConnectorRoleAssignment）* |

## <a name="powerapps-cmdlets-for-administrators-preview"></a>管理员 PowerApps cmdlet（预览版）

### <a name="prerequisite"></a>先决条件
要在管理员 cmdlet 中执行管理操作，需要以下各项：

* PowerApps 计划 2 付费许可证，或 PowerApps 计划 2 试用许可证。 可以在 [http://web.powerapps.com/trial](http://web.powerapps.com/trial) 注册以获取 30 天试用许可证。 如果试用许可证已过期，可以续订。

* 如果需要搜索另一个用户的资源，还将需要 [Office 365 全局管理员](https://support.office.com/article/assign-admin-roles-in-office-365-for-business-eac4d046-1afd-4f1a-85fc-8219c79e1504)或 [Azure Active Directory 全局管理员](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal)权限。 （请注意，环境管理员仅能访问那些他们具有权限的环境和环境资源。）

### <a name="cmdlet-list---admin-cmdlets"></a>Cmdlet 列表 - 管理员 Cmdlet

| 用途 | cmdlet
| --- | ---
| 读取、更新和删除环境和 Common Data Service for Apps 数据库 | New-AdminPowerAppEnvironment <br> Set-AdminPowerAppEnvironmentDisplayName <br> Get-AdminPowerAppEnvironment *（以前称为 Get-AdminEnvironment）* <br> Remove-AdminPowerAppEnvironment *（以前称为 Remove-AdminEnvironment）* <br> New-AdminPowerAppCdsDatabase <br> Get-AdminPowerAppCdsDatabaseLanguages <br> Get-AdminPowerAppCdsDatabaseCurrencies <br> Get-AdminPowerAppEnvironmentLocations |
| 删除 CDS 数据库 | Remove-LegacyCDSDatabase（新增）**\*\*** | 
| 读取、更新和删除环境权限 <br><br> 这些 cmdlet 当前仅适用于没有 Common Data Service (CDS) for Apps 数据库的环境。 | Get-AdminPowerAppEnvironmentRoleAssignment *（以前称为 Get-AdminEnvironmentRoleAssignment）* <br> Set-AdminPowerAppEnvironmentRoleAssignment *（以前称为 Set-AdminEnvironmentRoleAssignment）* <br> Remove-AdminPowerAppEnvironmentRoleAssignment *（以前称为 Remove-AdminEnvironmentRoleAssignment）* |
| 读取、更新和删除画布应用 | Get-AdminPowerApp *（以前称为 Get-AdminApp）* <br> Remove-AdminPowerApp *（以前称为 Remove-AdminApp）* <br> Get-AdminPowerAppConnectionReferences <br> Set-AdminPowerAppAsFeatured <br> Clear-AdminPowerAppAsFeatured <br> Set-AdminPowerAppAsHero <br> Clear-AdminPowerAppAsHero <br> Set-AdminPowerAppApisToBypassConsent <br> Clear-AdminPowerAppApisToBypassConsent |
| 读取、更新和删除画布应用权限 | Get-AdminPowerAppRoleAssignment *（以前称为 Get-AdminAppRoleAssignment）* <br> Remove-AdminPowerAppRoleAssignment *（以前称为 Remove-AdminAppRoleAssignment）* <br> Set-AdminPowerAppRoleAssignment *（以前称为 Set-AdminAppRoleAssignment）* <br> Set-AdminPowerAppOwner *（以前称为 Set-AdminAppOwner）* |
| 读取、更新和删除流 | Get-AdminFlow <br> Enable-AdminFlow <br> Disable-AdminFlow <br> Remove-AdminFlow <br> Remove-AdminFlowApprovals |
| 读取、更新和删除流权限 | Get-AdminFlowOwnerRole <br> Set-AdminFlowOwnerRole <br> Remove-AdminFlowOwnerRole |
| 读取和删除连接 | Get-AdminPowerAppConnection *（以前称为 Get-AdminConnection）* <br> Remove-AdminPowerAppConnection *（以前称为 Remove-AdminConnection）* |
| 读取、更新和删除连接权限 | Get-AdminPowerAppConnectionRoleAssignment *（以前称为 Get-AdminConnectionRoleAssignment）* <br> Set-AdminPowerAppEnvironmentConnectionRoleAssignment *（以前称为 Set-AdminConnectionRoleAssignment）* <br> Remove-AdminPowerAppConnectionRoleAssignment *（以前称为 Remove-AdminConnectionRoleAssignment）* |
| 读取和删除自定义连接器 | Get-AdminPowerAppConnector *（以前称为 Get-AdminConnector）* <br> Remove-AdminPowerAppConnector *（以前称为 Remove-AdminConnector）* |
| 读取、更新和删除自定义连接器权限 | Get-AdminPowerAppConnectorRoleAssignment *（以前称为 Get-AdminConnectorRoleAssignment）*<br> Set-AdminPowerAppConnectorRoleAssignment *（以前称为 Set-AdminConnectorRoleAssignment）* <br> Remove-AdminPowerAppConnectorRoleAssignment *（以前称为 Remove-AdminConnectorRoleAssignment）* |
| 读取用户的 PowerApps 用户设置、用户应用设置和通知 | Get-AdminPowerAppsUserDetails |
| 读取和删除用户的 Microsoft Flow 设置，这些设置对用户不可见，但支持流执行 | Get-AdminFlowUserDetails <br> Remove-AdminFlowUserDetails |
| 创建、读取、更新和删除组织的数据丢失防护策略 | Get-AdminDlpPolicy *（以前称为 Get-AdminApiPolicy）* <br> New-AdminDlpPolicy（以前称为 Add-AdminApiPolicy） <br> Remove-AdminDlpPolicy *（以前称为 Remove-AdminApiPolicy）* <br> Set-AdminDlpPolicy *（以前称为 Set-AdminApiPolicy）* <br> Add-ConnectorToBusinessDataGroup <br>  Remove-ConnectorFromBusinessDataGroup <br/>Add-CustomConnectorToPolicy<br/> Remove-CustomConnectorFromPolicy|

## <a name="tips"></a>提示

- 使用 Get-help CmdletName 获取示例列表。

     ![Get-Help 命令](media/get-help-cmdlet.png "Get-Help command")

- 要循环访问输入标记的可能选项，请先在 cmdlet 名称后键入短划线 (-) 字符，然后再单击 Tab。

示例命令：

```
Get-Help Get-AdminPowerAppEnvironment
Get-Help Get-AdminPowerAppEnvironment -Examples
Get-Help Get-AdminPowerAppEnvironment -Detailed
```

## <a name="operation-examples"></a>操作示例

以下是一些常见方案，用于演示如何使用新的和现有的 PowerApps cmdlet。

- [环境命令](#environments-commands)
- [PowerApps 命令](#powerapps-commands)
- [流命令](#flow-commands)
- [API 连接命令](#api-connection-commands)
- [数据丢失防护 (DLP) 策略命令](#data-loss-prevention-dlp-policy-commands)

### <a name="environments-commands"></a>环境命令

使用这些命令可以获取租户的详细信息并更新环境。

#### <a name="display-a-list-of-all-environments"></a>显示所有环境的列表

```
Get-AdminPowerAppEnvironment
```

返回租户中每个环境的列表，其中包含每个环境的详细信息（例如，环境名称 (guid)、显示名称、位置、创建者等）。

#### <a name="display-details-of-your-default-environment"></a>显示默认环境的详细信息

```
Get-AdminPowerAppEnvironment –Default
```

仅返回租户的默认环境的详细信息。

#### <a name="display-details-of-a-specific-environment"></a>显示特定环境的详细信息

```
Get-AdminPowerAppEnvironment –EnvironmentName ‘EnvironmentName’
```

**注意**：“EnvironmentName”字段是唯一标识符，该字段不同于“DisplayName”（请参阅下图中输出中的第一个和第二个字段）。

![Get-AdminEnvironment 命令](media/get-adminenvironment.png "Get-AdminEnvironment command")

### <a name="powerapps-commands"></a>PowerApps 命令

这些操作用于读取和修改租户中的 PowerApps 数据。

#### <a name="display-a-list-of-all-powerapps"></a>显示所有 PowerApps 的列表

```
Get-AdminPowerApp
```

返回租户中所有 PowerApps 的列表，其中包含每个 PowerApps 的详细信息（例如，应用程序名称 (guid)、显示名称、创建者等）。

#### <a name="display-a-list-of-all-powerapps-that-match-the-input-display-name"></a>显示与输入显示名称匹配的所有 PowerApps 的列表

```
Get-AdminPowerApp 'DisplayName'
```

返回租户中与显示名称匹配的所有 PowerApps 的列表。 

**注意**：在包含空格的输入值周围使用引号字符 (“)。

#### <a name="feature-an-application"></a>特别推荐应用程序

```
Set-AdminPowerAppAsFeatured –AppName 'AppName'
```

特别推荐应用程序被分组并推送到 PowerApps 移动播放机列表的顶部。

**注意**：与“环境”类似，“AppName”字段也是唯一标识符，该字段与“DisplayName”不同。 如果要根据显示名称执行操作，某些函数将允许使用管道（请参阅下一个函数）。

#### <a name="make-an-application-a-hero-app-using-the-pipeline"></a>使用管道将应用程序设为 Hero 应用

```
Get-AdminPowerApp 'DisplayName' | Set-AdminPowerAppAsHero
```

Hero 应用将出现在 PowerApps 移动播放机列表的顶部。 只能有一个 Hero 应用。

管道（在两个 cmdlet 之间表示为“|”字符）使用第一个 cmdlet 的输出，并将其作为第二个 cmdlet 的输入值传递，假设函数已编写适应管道的功能。

**注意**：在将应用更改为 hero 之前，应用必须已是特别推荐应用。

#### <a name="display-the-number-of-apps-each-user-owns"></a>显示每个用户拥有的应用数量

```
Get-AdminPowerApp | Select –ExpandProperty Owner | Select –ExpandProperty displayname | Group
```

可以将本机 PowerShell 函数与 PowerApps cmdlet 结合使用，以进一步处理数据。 此处我们使用 Select 函数将所有者属性（对象）与 Get-AdminApp 对象隔离开来。 然后，我们通过将输出管道连接到另一个 Select 函数来隔离所有者对象的名称。 最后，将第二个 Select 函数输出传递给组函数将返回一个不错的表，其中包含每个所有者应用数量的计数。

![Get-AdminPowerApp 命令](media/get-adminpowerapp.png "Get-AdminPowerApp command")

#### <a name="display-the-number-of-apps-in-each-environment"></a>显示每个环境中的应用数量

```
Get-AdminPowerApp | Select -ExpandProperty EnvironmentName | Group | %{ New-Object -TypeName PSObject -Property @{ DisplayName = (Get-AdminPowerAppEnvironment -EnvironmentName $_.Name | Select -ExpandProperty displayName); Count = $_.Count } }
```

![Get-AdminPowerApp 命令](media/get-adminpowerapp-environment.png "Get-AdminPowerApp command")

#### <a name="download-powerapps-user-details"></a>下载 PowerApps 用户详细信息

```
Get-AdminPowerAppsUserDetails -OutputFilePath '.\adminUserDetails.txt' –UserPrincipalName ‘admin@bappartners.onmicrosoft.com’
```

上述命令将在指定的文本文件中存储 PowerApps 用户详细信息（通过用户主体名称输入用户的基本使用情况信息）。 如果没有具有该名称的现有文件，该命令将创建一个新文件，并覆盖文本文件（如果已存在）。

#### <a name="set-logged-in-user-as-the-owner-of-a-powerapp"></a>将登录用户设置为 PowerApp 的所有者

```
Set-AdminPowerAppOwner –AppName 'AppName' -AppOwner $Global:currentSession.userId –EnvironmentName 'EnvironmentName'
```

将 PowerApp 的所有者角色更改为当前用户，并将原始所有者替换为“可以查看”角色类型。

**注意**：AppName 和 EnvironmentName 字段是唯一标识符 (guids)，而不是显示名称。

### <a name="flow-commands"></a>流命令

使用这些命令可以查看和修改与 Microsoft Flow 相关的数据。

#### <a name="display-all-flows"></a>显示所有流

```
Get-AdminFlow
```

返回租户中所有流的列表。

#### <a name="display-flow-owner-role-details"></a>显示流所有者角色详细信息

```
Get-AdminFlowOwnerRole –EnvironmentName 'EnvironmentName' –FlowName ‘FlowName’
```

返回指定流的所有者详细信息。

**注意**：与“环境”和“PowerApps”类似，“FlowName”也是唯一标识符 (guid)，它与流的显示名称不同。

#### <a name="display-flow-user-details"></a>显示流用户详细信息

```
Get-AdminFlowUserDetails –UserId $Global:currentSession.userId
```

返回有关流使用情况的用户详细信息。 在此示例中，我们使用 PowerShell 会话当前登录用户的用户 ID 作为输入。

#### <a name="remove-flow-user-details"></a>删除流用户详细信息

```
Remove-AdminFlowUserDetails –UserId 'UserId'
```

完全从 Microsoft 数据库中删除流用户的详细信息。 在清除流用户详细信息之前，必须删除输入用户拥有的所有流。

**注意**：UserId 字段是用户的 Azure Active Directory 记录的对象 ID，可以在 [Azure 门户](https://portal.azure.com)中的“Azure Active Directory” > “用户” > “配置文件” > “对象 ID”下找到。 必须是管理员才能从此处访问此数据。

#### <a name="export-all-flows-to-a-csv-file"></a>将所有流导出到 CSV 文件

```
Get-AdminFlow | Export-Csv -Path '.\FlowExport.csv'
```

将租户中的所有流导出到表格视图 .csv 文件中。

### <a name="api-connection-commands"></a>API 连接命令

查看和管理租户中的 API 连接。

#### <a name="display-all-native-connections-in-your-default-environment"></a>显示默认环境中的所有本机连接

```
Get-AdminPowerAppEnvironment -Default | Get-AdminConnection
```

显示默认环境中所有 API 连接的列表。 可以在创建者门户网站的“数据” > “连接”选项卡下找到本机连接。

#### <a name="display-all-custom-connectors-in-the-tenant"></a>显示租户中的所有自定义连接器

```
Get-AdminPowerAppConnector
```

返回租户中所有自定义连接器详细信息的列表。

### <a name="data-loss-prevention-dlp-policy-commands"></a>数据丢失防护 (DLP) 策略命令

这些 cmdlet 将控制租户的 DLP 策略。

#### <a name="display-all-policies"></a>显示所有策略

```
Get-AdminDlpPolicy
```

返回所有策略的列表。

#### <a name="display-a-filtered-list-of-policies"></a>显示已筛选的策略列表

```
Get-AdminDlpPolicy 'DisplayName'
```

使用显示名称筛选策略

#### <a name="display-all-business-data-only-api-connectors-in-a-policy"></a>显示策略中的所有“仅限业务数据”API 连接器

```
Get-AdminDlpPolicy 'PolicyName' | Select –ExpandProperty BusinessDataGroup
```

列出输入策略中“仅限业务数据”（或“BusinessDataGroup”）字段中的 API 连接。

#### <a name="add-a-connector-to-the-business-data-only-group"></a>将连接器添加到“仅限业务数据”组

```
Add-ConnectorToBusinessDataGroup -PolicyName 'PolicyName' –ConnectorName 'ConnectorName'
```

将连接器添加到给定 DLP 策略中的“仅限业务数据”组。 请在此处查看“DisplayName”和“ConnectorName”（用作输入）的连接器列表。

## <a name="version-history"></a>版本历史记录
| 版本 | Date | 更新 |
| --- | --- | --- |
| 1.0 | 2018 年 4 月 23 日 | <ol> <li> 最初发布的应用创建者 PowerApps cmdlet（预览版）包含面向环境、应用、流、流审批、连接和自定义连接器的管理 cmdlet </li> <li> 最初发布的管理员 PowerApps cmdlet（预览版）包含面向环境、应用和流的管理 cmdlet </li></ol>|
| 2.0 | 2018 年 5 月 24 日 | <ol> <li> 面向应用创建者和管理员的 cmdlet 的次要 Bug 修复 </li> <li> 添加了以下新的管理 cmdlet： <br> Get-AdminConnection <br> Remove-AdminConnection <br> Get-AdminConnectionRoleAssignment <br> Set-AdminConnectionRoleAssignment <br>Remove-AdminConnectionRoleAssignment <br>Get-AdminConnector  <br>Remove-AdminConnector <br>Set-AdminConnectorRoleAssignment  <br>Get-AdminConnectorRoleAssignment  <br>Remove-AdminConnectorRoleAssignment <br>Get-AdminPowerAppsUserDetails <br>Get-AdminFlowUserDetails <br>Remove-AdminFlowUserDetails <br>Get-AdminApiPolicy  <br>Add-AdminApiPolicy <br>Remove-AdminApiPolicy <br>Set-AdminApiPolicy <br>Add-ConnectorToBusinessDataGroup  <br>Remove-ConnectorFromBusinessDataGroup </li> </ol>
| 3.0 | 2018 年 7 月 30 日 | <ol> <li> 添加了相关功能以将凭据传递给 PowerAppsAccount（用于启用定期脚本） </li> <li>  面向应用创建者和管理员的 cmdlet 的次要 Bug 修复 </li> <li> 向应用创建者的每个 cmdlet 中添加了“PowerApp”或“Flow”前缀 </li> <li>  向管理员的每个 cmdlet 中添加了“AdminPowerApp”或“AdminFlow”前缀 </li> <li> 添加了以下新的管理 cmdlet： <br> New-AdminPowerAppEnvironment <br> Set-AdminPowerAppEnvironmentDisplayName <br> New-AdminPowerAppCdsDatabase <br> Get-AdminPowerAppCdsDatabaseLanguages <br> Get-AdminPowerAppCdsDatabaseCurrencies <br> Get-AdminPowerAppEnvironmentLocations <br> Get-AdminPowerAppConnectionReferences <br> Set-AdminPowerAppAsFeatured <br> Clear-AdminPowerAppAsFeatured <br> Set-AdminPowerAppAsHero <br> Clear-AdminPowerAppAsHero <br> Set-AdminPowerAppApisToBypassConsent <br> Clear-AdminPowerAppApisToBypassConsent <br> Remove-AdminFlowApprovals </li></ol>
| 4.0 | 2018 年 8 月 15 日 | 向 New-AdminPowerAppCdsDatabase 中添加了一个可选参数，以在默认情况下使函数同步（即，它不会返回，直到数据库已成功预配）
| 5.0 | 2018 年 8 月 24 日 | 修复了一个问题，即流管理员 cdmlet 未返回数据以根据安全设置进行使用
| 6.0 | 2019/01/09 | <ol><li>PowerShell 库中现提供了两个独立模块的 Cmdlet：管理员和创建者。</li> <li>已添加管理 cmdlet：Remove-LegacyCDSDatabase</li><li> 已添加操作示例</li><li>已添加管理 HTTP 和数据丢失防护 (DLP) 中的自定义连接器</li></ol>|

## <a name="questions"></a>有疑问？

如果有任何评论、建议或问题，请将它们发布到[管理 PowerApps 社区版块](https://powerusers.microsoft.com/t5/Administering-PowerApps/bd-p/Admin_PowerApps)。
