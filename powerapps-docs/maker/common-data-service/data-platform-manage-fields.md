---
title: 管理实体中的自定义字段快速入门 | Microsoft Docs
description: 创建、读取、更新及删除实体中自定义字段的快速入门。
documentationcenter: na
author: clwesene
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: cds
ms.date: 3/21/2018
ms.author: clwesene
ms.openlocfilehash: a2dfe95cd9e858326a9f014aaac4e595fb27be48
ms.sourcegitcommit: 8bd4c700969d0fd42950581e03fd5ccbb5273584
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2018
---
# <a name="quickstart-manage-custom-fields"></a>快速入门：管理自定义字段
可以在任意实体中创建和更新一个或多个自定义字段。 创建自定义字段时，可以指定一组属性，例如字段名称、其显示名称及其将包含的数据类型。 有关详细信息，请参阅[实体属性元数据](../../developer/common-data-service/entity-attribute-metadata.md)。

> [!NOTE]
> 每个实体都有 [系统字段]，如指示上次记录更新时间和更新人员的字段。 此外，[标准实体](data-platform-intro.md#system-fields)还包含标准（默认）字段。 无法修改或删除系统字段或标准字段。 如果创建自定义字段，则它应在这些内置字段上提供功能。

## <a name="create-a-field"></a>创建字段

1. 在 [powerapps.com](https://web.powerapps.com) 上，展开“数据”部分，然后单击或点击左侧导航窗格中的“实体”。

    ![实体详细信息](./media/data-platform-cds-create-entity/entitylist.png "实体列表")

2. 单击或点击现有实体，或者[创建新实体](data-platform-create-entity.md)

3. 通过单击“添加字段”将新建字段添加到实体。

4. 在新建字段面板中，输入字段的“显示名称”，“名称”将自动填充，并用作字段的唯一名称。 在向用户显示此字段时使用“显示名称”，在生成应用时，在表达式和公式中使用“名称”。

    > [!NOTE]
    > 可以随时更新“显示名称”字段以在应用中以不同方式显示，在保存实体后，“名称”字段不能更改，因为这可能导致现有应用中断。

    ![新建字段](./media/data-platform-cds-create-entity/newfieldpanel.png "新建字段面板")

5. 选择字段的“数据类型”，这将控制信息的存储方式以及在应用中的显示方式。 例如，文本的存储方式与小数或 URL 不同。 有关可用数据类型的详细信息，请参阅[实体属性元数据](../../developer/common-data-service/entity-attribute-metadata.md)。

    如果系统提示，则指定你所指定的数据类型的其他信息。 根据数据类型，将显示不同的字段。 如果要创建类型选项集或多选选项集的字段，则可以在创建字段时选择“新建选项集”并创建一个新选项集。 有关详细信息，请参阅[创建选项集](custom-picklists.md)

    ![新建字段](./media/data-platform-cds-create-entity/newfieldpanel-2.png "新建字段面板")


7. 如果根据应用的需要推荐使用此字段，请在“必需”下选中复选框。 这不会通过与 Common Data Service 的所有连接来提供硬实施。 如果需要确保填充此字段，可创建[业务规则](data-platform-create-business-rule.md)

8. 如果需要此字段在视图、图表、仪表板和高级查找中可用，请在“可搜索”下选中复选框。 在大多数情况下应选中此复选框。

9. 单击或点击“完成”以关闭字段面板，并返回到该实体。 可以为每个其他字段重复步骤 3-9。
   
    > [!IMPORTANT]
    > 在将更改保存到实体之前，尚未保存和创建字段。

10. 单击或点击“保存实体”以完成更改并将它们保存到 Common Data Service。

    该操作成功完成后，你将收到通知。 如果操作失败，错误消息会指示出现的问题以及修复方法。

## <a name="create-a-calculated-or-roll-up-field"></a>创建计算或汇总字段

计算字段可以自动执行业务流程中使用的手动计算。 例如，销售人员可能想知道商机的加权收入，它是基于商机乘以概率的预计收入。 或者，他们想要当订单超过 500 美元时自动应用折扣。 计算字段可以包含由简单的数学运算或条件运算（例如大于或 if-else）以及许多其他运算产生的值。 可以使用以下数据类型创建计算字段：

* 单行文本
* 选项集
* 两个选项
* 整数
* 小数
* 货币
* 日期和时间

有关支持的表达式类型和示例的详细信息，请参阅[定义计算字段](/dynamics365/customer-engagement/customize/define-calculated-fields)


## <a name="update-or-delete-a-field"></a>更新或删除字段
1. 在 [powerapps.com](https://web.powerapps.com) 上，展开“数据”部分，单击或点击左侧导航窗格中的“实体”，然后单击或点击实体。
2. 在所选实体的字段列表中，单击或点击一个字段，然后按照以下步骤之一操作：
   
   * 更改字段的一个或多个属性。
   * 单击或点击字段右边缘附近的省略号 (...)，然后单击或点击“删除”可删除该字段。

3. 单击或点击“保存实体”，提交所做更改。
   
    > [!IMPORTANT]
    > 如果在浏览器中打开其他页面或退出浏览器前未保存更改，所做更改将会丢失。

    该操作成功完成后，你将收到通知。 如果操作失败，错误消息会指示出现的问题以及修复方法。

## <a name="best-practices-and-restrictions"></a>最佳做法和限制
创建和修改字段时，请记住以下事项：

* 无法修改或删除系统字段或其值。
* 在标准实体中，不能修改或删除标准（默认）字段、添加需要数据的字段或做出可能破坏依赖于该实体的应用的任何其他更改。
* 在自定义实体中，应确保所做的更改不会破坏依赖于该实体的任何应用。
* 必须为每个自定义字段指定一个名称，该名称在实体中是唯一的，并且在创建该名称后不能重命名字段。

## <a name="next-steps"></a>后续步骤
* [定义实体之间的关系](data-platform-entity-lookup.md)
* [创建业务规则](data-platform-create-business-rule.md)
* [使用实体创建应用](../canvas-apps/data-platform-create-app.md)
* [使用 Common Data Service 数据库从头开始创建应用](../canvas-apps/data-platform-create-app-scratch.md)

## <a name="privacy-notice"></a>隐私声明
通过 Microsoft PowerApps 通用数据模型，我们收集自定义实体和字段名称并将其存储在诊断系统中。  我们利用这一知识来改进我们客户的通用数据模型。 创建者创建的实体和字段名称帮助我们了解 Microsoft PowerApps 社区中的常见方案，并确定服务标准实体范围中的缺口，如与组织相关的架构。 Microsoft 无法访问或使用数据库表中与这些实体相关联的数据，此类数据也无法在预配了数据库的区域之外进行复制。 不过，请注意，自定义实体和字段名称可能可以进行跨区域复制，并根据我们的数据保留策略进行删除。 Microsoft 致力于保护你的隐私安全，我们的[信任中心](https://www.microsoft.com/trustcenter/Privacy/default.aspx)对此进行了详述。

