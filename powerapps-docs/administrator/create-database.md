---
title: 创建 Common Data Service (CDS) for Apps 数据库 | Microsoft Docs
description: 有关如何创建 Common Data Service (CDS) for Apps 的演练。
services: powerapps
author: manasmams
manager: kvivek
ms.service: powerapps
ms.component: pa-admin
ms.topic: conceptual
ms.date: 10/03/2018
ms.author: manasma
search.audienceType:
- admin
search.app:
- D365CE
- PowerApps
- Powerplatform
ms.openlocfilehash: c7de26bff38ee0425e8bb3f9bc0da72317f0a6cf
ms.sourcegitcommit: 6e2fa2665ded6ac6fd271e1a12f4e3227ebc8865
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/03/2018
ms.locfileid: "48246111"
---
# <a name="create-a-common-data-service-for-apps-database"></a>创建 Common Data Service for Apps 数据库
可以将 Common Data Service (CDS) for Apps 用作数据存储，从而创建数据库并生成应用。 可以创建你自己的自定义实体，也可以使用预定义的实体。 若要创建数据库，要么必须先创建一个环境，要么必须以“环境管理员”身份分配到现有环境。此外，还必须分配有相应的许可证。 若要了解如何购买 CDS for Apps 使用套餐，请参阅[定价信息](pricing-billing-skus.md)。

创建数据库的方法有多种：

* 在 PowerApps 管理中心中
* 在 powerapps.com 的“实体”窗格中

## <a name="create-a-database-in-the-admin-center"></a>在管理中心内创建数据库
1. 在[管理中心](https://admin.powerapps.com)的左侧导航窗格中，单击“环境”。
    
2. 选择要在其中创建数据库的环境。
    
    ![](./media/create-database/environment-list-new.png)

3. 单击“详细信息”选项卡上的“创建数据库”。 
    
    ![](./media/create-database/Create-DB-From-Details.png)

4. 选择货币和语言，继续创建数据库。 
    
    ![](./media/create-database/DB-Choose-options.png)



## <a name="create-a-database-in-the-entities-pane-of-powerapps"></a>在 PowerApps 的“实体”窗格中创建数据库
1. 在 [powerapps.com](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) 上，展开“数据”部分，然后单击或点击左侧导航窗格中的“实体”。

2. 单击“创建数据库”以创建数据库。

    ![](./media/create-database/Create-DB-From-Entities.png)

> [!NOTE]
> 目前，不能在 Azure AD 区域外部创建数据库。 在不久的将来，可以在不同于 Azure AD 主区域的其他区域创建数据库，但现在，请确保在具有与 Azure AD 主区域相同区域的环境中创建数据库。

## <a name="security-model-for-the-databases"></a>数据库的安全模型
创建数据库后，具有环境角色的用户继续保有相应权限。  
    具有“环境管理员”角色的用户现分配到“系统管理员”角色。 具有“环境创建者”角色的用户保留该角色。

可将更多用户分配到预定义的角色，甚至可创建[自定义角色][1]。 有关详细信息，请参阅[数据库安全性](database-security.md)。

> [!NOTE]
> 创建数据库时，分配给环境管理员或环境创建者角色的任何安全组将失效。 目前，数据库中的权限分配不支持 AAD 安全组。


## <a name="license-and-security-permissions"></a>许可证和安全权限
必须是选定环境中的管理员，并且分配有相应的许可证，才能创建数据库。 在环境中，可以使用“安全”选项卡进一步配置其他用户的安全权限。有关详细信息，请参阅[配置数据库安全性](database-security.md)。

## <a name="privacy-notice"></a>隐私声明
通过 Microsoft PowerApps 通用数据模型，我们收集自定义实体和字段名称并将其存储在诊断系统中。  我们利用这一知识来改进我们客户的通用数据模型。 创建者创建的实体和字段名称帮助我们了解 Microsoft PowerApps 社区中的常见方案，并确定服务标准实体范围中的缺口，如与组织相关的架构。 Microsoft 无法访问或使用数据库表中与这些实体相关联的数据，此类数据也无法在预配了数据库的区域之外进行复制。 不过，请注意，自定义实体和字段名称可能可以进行跨区域复制，并根据我们的数据保留策略进行删除。 Microsoft 致力于保护你的隐私安全，我们的[信任中心](https://www.microsoft.com/trustcenter/Privacy/default.aspx)对此进行了详述。


<!--Reference links in article-->
[1]: https://technet.microsoft.com/library/dn531130.aspx
