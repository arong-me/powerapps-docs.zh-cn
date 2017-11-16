---
title: "创建 Common Data Service 数据库 | Microsoft 文档"
description: "创建 Common Data Service 数据库。"
services: powerapps
documentationcenter: na
author: nimakms
manager: kfend
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 12/06/2016
ms.author: kfend
ms.openlocfilehash: a2224d97c9cfc1261e43f7d30c8d8bdd2dd6e86b
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2017
---
# <a name="create-a-common-data-service-database"></a>创建 Common Data Service 数据库
可以将 Common Data Service 用作数据存储，从而创建数据库并生成应用。 可以创建你自己的自定义实体，也可以使用预定义的实体。 若要创建数据库，要么必须先创建一个环境，要么必须以管理员身份分配到现有环境。 此外，还必须分配有相应的许可证。 若要了解如何购买 Common Data Service 使用套餐，请参阅[定价信息](pricing-billing-skus.md)。

数据库创建方法有三种：

* 在管理中心内
* 在 powerapps.com 的“开始”窗格中
* 在 powerapps.com 的“实体”窗格中

## <a name="create-a-database-in-the-admin-center"></a>在管理中心内创建数据库
1. 在[“管理中心”](https://admin.powerapps.com)的左侧导航窗格中，单击“环境”。
2. 选择环境或新建一个环境（如果需要的话）。
3. 单击“数据库”选项卡上的“创建数据库”。 创建的数据库默认处于开放访问模式。
4. 若要强制执行安全规范，请选中“限制访问”。

## <a name="create-a-database-in-the-home-pane-of-powerappscom"></a>在 powerapps.com 的“开始”窗格中创建数据库
1. 在 [powerapps.com](https://web.powerapps.com) 上的左侧导航窗格中，单击“开始”。
2. 在“使用 Microsoft Common Data Service”部分中，查找“创建数据库”或“开始使用”按钮。 具体查找哪个按钮名称视你的许可证和权限分配而定。 可能无法在当前环境中创建数据库。

### <a name="create-database-in-current-environnmet"></a>在当前环境中创建数据库
1. 单击“创建数据库”。
2. 若要强制执行安全规范，请选中对话框中的“限制对数据库的访问”复选框。
3. 单击“创建我的数据库”。

### <a name="get-started-by-creating-a-new-environment"></a>从新建环境开始
1. 单击“开始使用”。
2. 在对话框中，单击“创建新环境”，开始新建环境和数据库。
3. 在“环境名称”字段中，输入一个独一无二的名称。 在“区域”字段中，选择相应的区域。
4. 若要强制执行安全规范，请选中“限制对数据库的访问”复选框。
5. 单击“创建”。

## <a name="create-a-database-in-the-entities-pane-of-powerappscom"></a>在 powerapps.com 的“实体”窗格中创建数据库
1. 在 [powerapps.com](https://web.powerapps.com) 上，展开“Common Data Service”部分，然后单击或点击左侧导航窗格中的“实体”。
2. 单击“开始使用”。 创建的数据库处于开放访问模式。

## <a name="open-and-restricted-databases"></a>开放式和受限式数据库
创建的数据库默认处于开放访问模式。 在此模式下，并未强制执行安全规范来限制对实体的访问。 环境管理员可以将数据库设为处于限制访问模式。 在此模式下，将根据权限集和角色，强制执行安全规范来限制对实体的访问。

1. 在[“管理中心”](https://admin.powerapps.com)的左侧导航窗格中，单击“环境”。
2. 选择环境。
3. 在“数据库”选项卡上，执行下列步骤之一：
   * 若要强制执行安全规范，请选中“限制访问”。
   * 若要禁用安全规范，请选中“开放访问”。

## <a name="license-and-security-permissions"></a>许可证和安全权限
必须是选定环境中的管理员，并且分配有相应的许可证，才能创建数据库。 在环境中，可以使用“安全”选项卡进一步配置其他用户的安全权限。有关详细信息，请参阅[配置数据库安全设置](database-security.md)和[安全模型](https://docs.microsoft.com/en-us/common-data-service/entity-reference/security-model)。

## <a name="privacy-notice"></a>隐私声明
通过 Microsoft PowerApps 通用数据模型，我们收集自定义实体和字段名称并将其存储在诊断系统中。  我们利用这一知识来改进我们客户的通用数据模型。 创建者创建的实体和字段名称帮助我们了解 Microsoft PowerApps 社区中的常见方案，并确定服务标准实体范围中的缺口，如与组织相关的架构。 Microsoft 无法访问或使用数据库表中与这些实体相关联的数据，此类数据也无法在预配了数据库的区域之外进行复制。 不过，请注意，自定义实体和字段名称可能可以进行跨区域复制，并根据我们的数据保留策略进行删除。 Microsoft 致力于保护你的隐私安全，我们的[信任中心](https://www.microsoft.com/trustcenter/Privacy/default.aspx)对此进行了详述。

