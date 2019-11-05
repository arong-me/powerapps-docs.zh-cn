---
title: 将图表添加到门户中的网页 |MicrosoftDocs
description: 说明如何将在模型驱动的应用中创建的图表添加到门户中的网页。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 3cc2e390b988689e9a21317d80aa7d94d2ea9e6d
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2019
ms.locfileid: "73553868"
---
# <a name="add-a-chart-created-in-a-model-driven-app-to-a-webpage-in-portal"></a>将在模型驱动的应用中创建的图表添加到门户中的网页

使用名为[chart](../liquid/portals-entity-tags.md#chart)的液体标记将图表添加到网页。 您可以在网页上的 "**复制**" 字段中或在[Web 模板](../liquid/store-content-web-templates.md)的 "**源**" 字段中添加图表液体标记。
 
例如，{% chart id： EE3C733D-5693-DE11-97D4-00155DA3B01E%}

![图表示例](../media/dynamics365-chart-example.png "图表示例")

您还可以指定视图的 ID （已保存查询）来筛选查询。 例如：

<!—Leads by Source – Open Leads -->

{% chart id： "EE3C733D-5693-DE11-97D4-00155DA3B01E" viewid： "00000000-0000-0000-00AA-000010001006"%}

## <a name="get-the-id-of-a-chart"></a>获取图表的 ID

1.  转到目标实体，例如**销售** > **潜在顾客**。
2.  展开**图表**区。
3.  选择所需的图表。
4.  选择 "**更多命令**"，然后选择 "**导出图表**"。

    ![导出图表](../media/export-dynamics365-chart.png "导出图表")

5. 在文本编辑器中打开导出的图表的 XML 文件。
6. 复制 \<visualizationid\> 标记的值。

    ![获取图表的 chartid](../media/dynamics365-chart-chartid.png "获取图表的图表 ID")

7. 将 visualizationid 值粘贴到 "图表 ID" 参数的液体图标记声明中，例如：

    {% chart id： EE3C733D-5693-DE11-97D4-00155DA3B01E%}。

## <a name="get-the-id-of-a-view"></a>获取视图的 ID

您必须打开视图编辑器才能获取与液体图标记一起使用的视图 ID。
 
1.  转到目标实体，例如**销售** > **潜在顾客**。
2.  从 "视图" 下拉标题中选择所需的视图。
3.  从工具栏中选择 "**查看**"。 "视图" 窗口随即打开。

    ![查看视图编辑器中的潜在顾客](../media/dynamics365-chart-view.png "查看视图编辑器中的潜在顾客")

4. 从 "视图" 窗口的 URL 复制 " **id** " 值。

    ![从视图编辑器获取视图 id](../media/dynamics365-chart-viewid.png "从视图编辑器获取视图 ID")

5. 将此 ID 粘贴到 viewid 参数的液体图标记声明中，例如：

    <!—Leads by Source – Open Leads -->

    {% chart id： "EE3C733D-5693-DE11-97D4-00155DA3B01E" viewid： "00000000-0000-0000-00AA-000010001006"%}

## <a name="entity-permission-requirement"></a>实体权限要求

对于在图表中查询的目标实体，读取权限是断言的。 要使匿名用户或经过身份验证的用户能够查看图表，必须确保创建相应的[实体权限](assign-entity-permissions.md)记录，并将其分配给适用的[web 角色](create-web-roles.md)。 
 
如果未授予权限，则用户将看到 "拒绝访问" 消息。

## <a name="unsupported-charts-and-chart-types"></a>图表和图表类型不受支持

门户中当前不支持以下图表类型：
- 圆
- 符

下表列出了门户当前不支持的图表。

| 图表名称                              | 图表 ID                             | 实体类型      |
|-----------------------------------------|--------------------------------------|------------------|
| 按所有者标记的帐户图表           | be178262-6142-4b41-85b7-4ccedc62cfd9 | 账号          |
| 按所有者标记的活动图表         | c83b331e-87c7-488c-b8e7-89a6098ea102 | activitypointer  |
| 按优先级排序的活动-圆环图 | d3f6c1eb-2e4b-428b-8949-682a311ae057 | activitypointer  |
| 按帐户的联系人                     | 2ff3ebea-6310-4dde-b3a1-e1144ea42b7b | 联系          |
| 按国家/地区的联系人                     | ea89e2ad-2602-4333-8724-aa5775d66b77 | 联系          |
| 按首选联系方法的联系人    | 751b7456-308e-4568-a3a9-47135aae833a | 联系          |
| 目标进度（计数）                   | a93b8f7b-9c68-df11-ae90-00155d2e3002 | 目标             |
| 目标进度（金钱）                   | aec6d51c-ea67-df11-ae90-00155d2e3002 | 目标             |
| 今天的目标与实际值（计数）      | 1b697c8e-9a6f-df11-986c-00155d2e3002 | 目标             |
| 今天的目标与实际值（金钱）      | 1e697c8e-9a6f-df11-986c-00155d2e3002 | 目标             |
| 按帐户的事例                        | 38872e4f-ac99-e511-80da-00155dc1b253 | 事件         |
| 按优先级的事例                       | 0f0fb995-9d6f-453c-b26d-8f443e42e676 | 事件         |
| 按产品的事例                        | 17c3f166-5b22-4476-819b-b05da2e8d24f | 事件         |
| 按所有者终止本月的文章   | 47d696ad-7c3b-e511-80d1-00155db10d2b | knowledgearticle |
| 按所有者                                | 330068fd-833b-e511-80d1-00155db10d2b | knowledgearticle |
| 按主题                              | bcd3f9a5-913b-e511-80d1-00155db10d2b | knowledgearticle | 
| | |
