---
title: "疑难解答 - 无法为此数据库创建或检索混合 | Microsoft 文档"
description: "通过让管理员更改 AAD 限制，解决无法使用 CDS 和 Power Query 创建自定义实体的问题。"
services: 
suite: powerapps
documentationcenter: na
author: mllopis
manager: kfend
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 08/18/2017
ms.author: millopis
ms.openlocfilehash: 230ad9f61185caff93fb3a5f56c62176b4f78c16
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2017
---
# <a name="troubleshooting---unable-to-create-or-retrieve-a-mashup-for-this-database"></a>疑难解答 - 无法为此数据库创建或检索混合
使用“根据数据新建实体(技术预览版)”功能时，可能会看到以下错误：

    *Unable to create or retrieve a mashup for the current database*

如果使用此功能，以利用 Power Query 根据外部数据源中的数据在 Common Data Service (CDS) 中创建自定义实体，可能会看到此错误。 当 Power Query 无法访问在 PowerApps 或 CDS 中访问组织数据时，便会触发此错误。 此错误分为两种情况：

* Azure Active Directory (AAD) 租户管理员已禁止用户同意应用代表他们访问公司数据。
* 使用非托管 Active Directory 租户。 非托管租户是不含全局管理员的目录，旨在完成自助注册服务。 若要解决这种情况的问题，用户必须先转换为托管租户，然后再使用以下部分中描述的两个解决方案之一解决此问题。

## <a name="how-to-fix-the-issue"></a>如何解决此问题
上述问题有两种解决方法：

* 让 AAD 管理员按照必要步骤操作，允许用户同意应用代表他们访问公司数据
* 让 AAD 管理员允许 Power Query 访问数据

下面介绍了这些解决方案的所有必要步骤。

### <a name="allowing-users-to-give-apps-consent-to-access-company-data"></a>允许用户同意应用代表他们访问公司数据
可以联系 AAD 管理员，让他/她按照下列步骤操作，允许用户同意任意应用代表他们访问公司数据：

1. 访问 [https://portal.azure.com](https://portal.azure.com)
2. 打开“Azure Active Directory”边栏选项卡。
3. 选择“用户设置”。
4. 选中“用户可以同意应用代表他们访问公司数据”旁边的“是”，再选择“保存”。
5. 完成此过程后，问题便会得到解决。

这可能是最简单的方法，但与下一种方法相比，允许的权限更为宽泛。

### <a name="allowing-power-query-to-access-company-data"></a>允许 Power Query 访问公司数据
另一种解决方案是让租户管理员允许 Power Query 访问公司数据，而不修改全租户权限。 为此，请让租户管理员按照下列步骤操作：

1. 安装 [Azure PowerShell](https://docs.microsoft.com/powershell/azure/install-azurerm-ps)
2. 运行以下 PowerShell 命令：
   * Login-AzureRmAccount（并以租户管理员身份登录）
   * New-AzureRmADServicePrincipal -ApplicationId f3b07414-6bf4-46e6-b63f-56941f3f4128

与全租户解决方案相比，此方法的优势在于，这种解决方案非常具有针对性。 它仅预配 Power Query 服务主体，不会对租户进行其他任何权限更改。

