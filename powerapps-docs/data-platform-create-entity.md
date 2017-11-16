---
title: "创建自定义实体 | Microsoft 文档"
description: "创建以其他实体为基础的自定义实体或从头开始创建自定义实体。"
services: powerapps
documentationcenter: na
author: kfend
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
ms.openlocfilehash: 5d927e84144da8e3b011bb4e4a7ac107aedac74f
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2017
---
# <a name="create-a-custom-entity"></a>创建自定义实体
可以创建自定义实体来存储特定于组织的数据。 然后可通过开发引用该实体的应用来显示该数据。

创建实体的方法有两种：

* 从头开始创建实体。 默认情况下，实体仅包含[四个系统字段和一个记录标题字段](data-platform-create-entity.md#system-and-record-title-fields)。
* 复制另一实体的字段和设置，但不复制数据，从而在此实体的基础上创建新实体。

在这两种情况下，Microsoft PowerApps 都会自动存储并帮助保护数据。 创建实体后，可以[创建或修改实体的一个或多个字段](data-platform-manage-fields.md)，以及 [构建实体之间的关系](data-platform-entity-lookup.md)。

**注意：**创建实体之前，请参阅[标准实体列表](data-platform-intro.md#standard-entities)。 这些实体涵盖典型的方案，如客户和联系人。 如果有符合你要求的现成实体或仅需稍加更改的实体，可使用该实体以节省时间。

## <a name="create-an-entity"></a>创建实体
1. 1. 在 [powerapps.com](https://web.powerapps.com) 上，展开“Common Data Service”部分，单击或点击左侧导航窗格中的“实体”。
2. 如果尚未创建数据库，需要创建一个数据库。 有关详细信息，请参阅[创建 Common Data Service 数据库](create-database.md)。
3. 在右上角附近，单击或点击“新建实体”。
4. 在“实体名称”字段中，输入实体的名称。 确保实体名称清楚且有意义，因为创建该实体后无法再进行更改。 开发应用时，将通过此名称在公式中引用该实体。
5. 为实体指定一个显示名称和（可选）说明，然后单击或点击“下一步”。
6. 可选：将“标题”字段中的值更改为对数据更有意义的值。
7. 单击或点击“**创建**”，创建实体。

实体将出现在数据库的实体列表中。 若要在列表顶部显示实体，请单击或点击“类型”列标题。 实体将按类型排序，且所有自定义实体将显示在所有标准实体上方。

## <a name="system-fields-and-the-record-title-field"></a>系统字段和记录标题字段
所有实体均包含五个系统字段。 这些字段为只读。 因此，无法更改或删除这些字段，且无法为它们赋值。

| 显示名称 | 系统字段名称 | 数据类型 | 说明 |
| --- | --- | --- | --- |
| ID |系统字段名称 |大整数 |记录的唯一标识符。 |
| 创建者 |CreatedByUser |文本 |创建记录的用户。 |
| 记录创建日期 |CreatedOnDateTime |日期/时间 |创建记录的日期和时间。 |
| 上次修改者 |LastModifiedByUser |文本 |最近修改记录的用户。 |
| 记录修改日期 |LastModifiedDateTime |日期/时间 |最近修改记录的日期和时间。 |

如果从头开始创建实体，它还包含名为“标题”的自定义字段。 将此字段设置为记录的“标题”字段。 “标题”字段值是记录的易用标识符（无论何时在应用中使用该记录都是如此）。 可以将任意字段更改为“标题”字段，但每个实体都必须有一个“标题”字段。

## <a name="next-steps"></a>后续步骤
* [管理实体中的字段](data-platform-manage-fields.md)
* [定义实体之间的关系](data-platform-entity-lookup.md)
* [使用 Common Data Service 数据库生成应用](data-platform-create-app.md)
* [使用 Common Data Service 数据库从头开始创建应用](data-platform-create-app-scratch.md)

## <a name="privacy-notice"></a>隐私声明
通过 Microsoft PowerApps 通用数据模型，我们收集自定义实体和字段名称并将其存储在诊断系统中。  我们利用这一知识来改进我们客户的通用数据模型。 创建者创建的实体和字段名称帮助我们了解 Microsoft PowerApps 社区中的常见方案，并确定服务标准实体范围中的缺口，如与组织相关的架构。 Microsoft 无法访问或使用数据库表中与这些实体相关联的数据，此类数据也无法在预配了数据库的区域之外进行复制。 不过，请注意，自定义实体和字段名称可能可以进行跨区域复制，并根据我们的数据保留策略进行删除。 Microsoft 致力于保护你的隐私安全，我们的[信任中心](https://www.microsoft.com/trustcenter/Privacy/default.aspx)对此进行了详述。

