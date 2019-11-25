---
title: Power Query 疑难解答 | Microsoft Docs
description: 通过使用 Power Query 在 Common Data Service 中创建自定义实体来解决问题。
author: mllopis
manager: kfile
ms.service: powerapps
ms.component: cds
ms.topic: conceptual
ms.date: 05/16/2018
ms.author: millopis
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 5679d82d6ec53d579567a778043ac9542099a20e
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "2706667"
---
# <a name="troubleshoot-power-query"></a>Power Query 疑难解答
当使用 Power Query for Excel 创建包含来自外部源的数据的自定义实体时，可能会出现此错误：

>“您的 Azure Active Directory 管理员设置了阻止您使用此功能的策略。 请与您的管理员联系，他可以代表您授予此功能的权限。”

如果 Power Query 无法访问 PowerApps 或 Common Data Service 中组织的数据时，将显示此错误。 此情况会在两组情形下出现：

* Azure Active Directory (Azure AD) 租户管理员已经禁用了用户同意应用程序代表他们访问公司数据的功能。
* 使用非托管 Active Directory 租户。 非托管租户是一个目录，没有为完成自助注册服务创建的全局管理员。 要修复此情形，用户必须首先转换为托管租户，然后按照解决这个问题的两个解决方案之一操作。 解决方案在下一部分介绍。

若要解决此问题，Azure Active Directory 管理员必须按照本文后面介绍的过程之一操作。

## <a name="allow-users-to-consent-to-apps-that-access-company-data"></a>允许用户同意应用程序访问公司数据
这种方法可能比下一个方法更简单，但允许更广泛的权限。

1. 在 [Azure 门户](https://portal.azure.com)中，打开 **Azure Active Directory** 窗格，然后选择**用户设置**。
2. 在**用户可以同意应用程序代表他们访问公司数据**旁边，选择**是**，然后选择**保存**。

## <a name="allow-power-query-to-access-company-data"></a>允许 Power Query 访问公司数据
作为替代方法，租户管理员可以向 Power Query 授予同意，而无需修改租户范围的权限。

1. 安装 [Azure PowerShell](https://docs.microsoft.com/powershell/azure/install-azurerm-ps)。
2. 运行以下 PowerShell 命令：
   * Login-AzureRmAccount（以租户管理员身份登录）
   * New-AzureRmADServicePrincipal -ApplicationId f3b07414-6bf4-46e6-b63f-56941f3f4128

此方法的优点（对比租户范围的解决方案）是此解决方案非常有针对性。 它仅设置 **Power Query** 服务主体，不对租户进行其他权限更改。

## <a name="update-personal-data"></a>更新个人数据

用户可以通过查询编辑器并通过可从查询编辑器访问的**选项**对话框更新混合 Web 应用程序及其他信息（如查询名称和混合 Web 应用程序元数据）。

在 PowerApps 中，通过执行以下操作访问查询编辑器：
1. 转到**数据**窗格，展开它，然后选择**实体**。 
2. 选择省略号 (...)，然后选择**编辑查询**。
3. 在功能区，选择**选项**按钮，然后选择**导出诊断**按钮。


## <a name="delete-personal-data"></a>删除个人数据

多数数据会在 30 天内自动删除。 对于有关混合 Web 应用程序的数据和元数据，用户必须通过 PowerApps 删除其所有混合 Web 应用程序。 所有关联数据和元数据将在 30 天内删除。

从 Power Apps 中删除混合 Web 应用程序：
1. 删除数据集成器项目，其可以从同名选项卡中删除。
2. 选择省略号 (...)，然后选择**删除**选项。

如果是通过“数据的新实体（技术预览）”功能创建的混合 Web 应用程序，则可以通过执行以下操作将其删除：
1. 选择省略号 (...)，然后选择**编辑查询**。
2. 在功能区，选择**选项**按钮。
3. 选择**删除所有查询**按钮。  
    在确认要删除查询后，它们将被删除。

## <a name="export-personal-data"></a>导出个人数据

若要导出个人数据，用户可以执行以下操作：
1. 打开“查询编辑器”。
2. 在功能区，选择**选项**按钮。
3. 选择**诊断导出**按钮。

在 PowerApps 中，可以通过执行以下操作访问查询编辑器：
1. 转到**数据**窗格，展开它，然后选择**实体**。
2. 选择省略号 (...)，然后选择**编辑查询**。 
3. 在功能区，选择**选项**按钮，然后选择**导出诊断**按钮。

系统生成的有关用户界面 (UI) 上的用户操作的日志可以在 Azure 门户访问。



