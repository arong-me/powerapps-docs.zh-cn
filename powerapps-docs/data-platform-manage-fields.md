---
title: "管理实体中的自定义字段 | Microsoft 文档"
description: "创建、读取、更新及删除实体中的自定义字段。"
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
ms.date: 10/20/2017
ms.author: kfend
ms.openlocfilehash: f5d769459f9d10e1d0f4bab2c1cc182407865053
ms.sourcegitcommit: e827813cd898ca9a1046b5952ea5e32ce2989a65
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="manage-custom-fields"></a>管理自定义字段
可以在任意实体中创建和更新一个或多个自定义字段。 创建自定义字段时，可以指定一组属性，例如字段名称、其显示名称及其将包含的数据类型。 有关详细信息，请参阅 [Enity field data types](https://docs.microsoft.com/common-data-service/entity-reference/field-data-types)（实体字段数据类型）和 [Entity field properties](https://docs.microsoft.com/common-data-service/entity-reference/field-properties)（实体字段属性）。

> [!NOTE]
> 每个实体都有[系统字段](data-platform-create-entity.md#system-fields-and-the-record-title-field)，如指示上次记录更新时间和更新人员的字段。 此外，[标准实体](data-platform-intro.md#standard-entities)还包含标准（默认）字段。 无法修改或删除系统字段或标准字段。 如果创建自定义字段，则它应在这些内置字段上提供功能。

## <a name="create-a-field"></a>创建字段

1. 在 [powerapps.com](https://web.powerapps.com) 上，展开“Common Data Service”部分，单击或点击左侧导航窗格中的“实体”。 将显示实体列表。 若要在列表顶部显示自定义实体，请单击或点击“类型”列标题。 此外，在搜索栏中键入一个或多个字符可筛选列表。

2. 单击或点击实体，然后单击或点击屏幕顶部附近的“**添加字段**”。

3. 在“显示名称”下，指定可为用户识别字段的文本字符串。 有关详细信息，请参见[创建应用](data-platform-create-app.md)。

4. 在“名称”下，指定将用于引用字段的文本字符串，例如生成应用时的公式。
   
    > [!IMPORTANT]
    > 请指定唯一、明确的有意义名称，因为创建字段后便无法再更改名称。

5. 在“类型”下，指定该字段将包含的数据类型，例如**文本**或**数字**。
   
    > [!IMPORTANT]
    > 请慎重指定此属性，因为在字段包含数据后便无法再更改它。 有关可以指定的数据类型的信息，请参阅 [了解实体](data-platform-intro.md#custom-fields)。

6. 如果系统提示，则指定你所指定的数据类型的其他信息。

7. 如果每条记录必须包含此字段中的唯一值，请选中“唯一”复选框。

8. 如果每条记录必须包含此字段中的一个值，请选中“必需”复选框。
   
    > [!IMPORTANT]
    > 无法要求标准实体中的自定义字段必须包含数据。 此限制可以保护依赖于该实体的任何应用。

9. 单击或点击“**保存**”，提交所做更改。
   
    > [!IMPORTANT]
    > 如果在浏览器中打开其他页面或退出浏览器前未保存更改，所做更改将会丢失。

该操作成功完成后，你将收到通知。 如果操作失败，错误消息会指示出现的问题以及修复方法。

## <a name="update-or-delete-a-field"></a>更新或删除字段
1. 在 [powerapps.com](https://web.powerapps.com) 上，依次单击或点击“**管理**”、“**实体**”，然后单击或点击实体。
2. 在所选实体的字段列表中，单击或点击一个字段，然后按照以下步骤之一操作：
   
   * 更改字段的一个或多个属性。 请记住[最佳做法和限制](data-platform-manage-fields.md#best-practices-and-restrictions)。
     
       要选择下一个属性，请按 Tab 键。要撤消对某个字段的所有更改，请单击或点击该字段的省略号 (...)，然后单击或点击“**撤消**”。
   * 单击或点击字段右边缘附近的省略号 (...)，然后单击或点击“删除”可删除该字段。
3. 单击或点击“**保存**”，提交所做更改。
   
    > [!IMPORTANT]
    > 如果在浏览器中打开其他页面或退出浏览器前未保存更改，所做更改将会丢失。

该操作成功完成后，你将收到通知。 如果操作失败，错误消息会指示出现的问题以及修复方法。

## <a name="best-practices-and-restrictions"></a>最佳做法和限制
创建和修改字段时，请记住以下事项：

* 无法修改或删除系统字段或其值。
* 在标准实体中，不能修改或删除标准（默认）字段、添加需要数据的字段或做出可能破坏依赖于该实体的应用的任何其他更改。
* 在自定义实体中，应确保所做的更改不会破坏依赖于该实体的任何应用。
* 必须为每个自定义字段指定一个名称，该名称在实体中是唯一的，并且在创建该名称后不能重命名字段。
* 如果字段尚未包含数据，可以更改字段的数据类型。 在字段已经包含数据的情况下，如果所有现有数据均满足新的数据类型要求，则可以更改数据类型。 例如，可以将字段的数据类型从**数字**更改为**字符串**，但如果字段包含非数值数据，则无法将数据类型从**字符串**更改为**数字**。
* 如果通过以下一种或多种方式修改实体中的字段，则可能会破坏使用该实体的应用：
  * 更改字段的数据类型。
  * 需要值，但一条或多条记录不包含该字段中的值。
  * 需要唯一值，但两条或更多记录包含该字段中的同一个值。

## <a name="next-steps"></a>后续步骤
* [定义实体之间的关系](data-platform-entity-lookup.md)
* [使用实体创建应用](data-platform-create-app.md)
* [使用 Common Data Service 数据库从头开始创建应用](data-platform-create-app-scratch.md)

## <a name="privacy-notice"></a>隐私声明
通过 Microsoft PowerApps 通用数据模型，我们收集自定义实体和字段名称并将其存储在诊断系统中。  我们利用这一知识来改进我们客户的通用数据模型。 创建者创建的实体和字段名称帮助我们了解 Microsoft PowerApps 社区中的常见方案，并确定服务标准实体范围中的缺口，如与组织相关的架构。 Microsoft 无法访问或使用数据库表中与这些实体相关联的数据，此类数据也无法在预配了数据库的区域之外进行复制。 不过，请注意，自定义实体和字段名称可能可以进行跨区域复制，并根据我们的数据保留策略进行删除。 Microsoft 致力于保护你的隐私安全，我们的[信任中心](https://www.microsoft.com/trustcenter/Privacy/default.aspx)对此进行了详述。

