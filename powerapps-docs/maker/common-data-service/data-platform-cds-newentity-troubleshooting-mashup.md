---
title: Power Query 疑难解答 | Microsoft Docs
description: 解决了使用 Power Query 在 Common Data Service (CDS) for Apps 中创建自定义实体时遇到的问题。
author: mllopis
manager: kfile
ms.service: powerapps
ms.component: cds
ms.topic: conceptual
ms.date: 08/18/2017
ms.author: millopis
ms.openlocfilehash: d71349c90748b1820cd3430613e0925498ce9793
ms.sourcegitcommit: b3b6118790d6b7b4285dbcb5736e55f6e450125c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2018
---
# <a name="troubleshooting-power-query"></a>Power Query 疑难解答
使用 Power Query 创建包含外部数据源数据的自定义实体时，可能会看到以下错误消息：

`Your Azure Active Directory administrator has set a policy that prevents you from using this feature. Please contact your administrator, who can grant permissions for this feature on your behalf.`

如果 Power Query 无法访问组织在 PowerApps 或 ommon Data Service (CDS) for Apps 中的数据，此错误消息就会出现。 在下列两种情况下，可能会遇到此问题：

* Azure Active Directory (AAD) 租户管理员已禁止用户授权应用代表他们访问公司数据。
* 使用非托管 Active Directory 租户。 非托管租户是不含全局管理员的目录，旨在完成自助注册服务。 若要在这种情况下解决问题，用户必须先转换为托管租户，再使用以下部分中介绍的两个解决方案之一来解决此问题。

若要解决此问题，Azure Active Directory 管理员必须按照本主题稍后介绍的其中一个过程的步骤操作。

## <a name="allow-users-to-consent-to-apps-that-access-company-data"></a>允许用户授权应用访问公司数据
相较下一种方法，这种方法可能更简单，但授予的权限更宽泛。

1. 在 [https://portal.azure.com](https://portal.azure.com) 中，打开“Azure Active Directory”边栏选项卡，再选择“用户设置”。
2. 选中“用户可以同意应用代表他们访问公司数据”旁边的“是”，再选择“保存”。

## <a name="allow-power-query-to-access-company-data"></a>允许 Power Query 访问公司数据
另一种解决方案是让租户管理员授权 Power Query 访问公司数据，而不修改租户范围权限。

1. 安装 [Azure PowerShell](https://docs.microsoft.com/powershell/azure/install-azurerm-ps)。
2. 运行以下 PowerShell 命令：
   * Login-AzureRmAccount（并以租户管理员身份登录）
   * New-AzureRmADServicePrincipal -ApplicationId f3b07414-6bf4-46e6-b63f-56941f3f4128

与全租户解决方案相比，此方法的优势在于，这种解决方案非常具有针对性。 它仅预配 Power Query 服务主体，不会对租户进行其他任何权限更改。

