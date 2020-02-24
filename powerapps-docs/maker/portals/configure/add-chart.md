---
title: 向门户网页添加图表 | MicrosoftDocs
description: 用于将模型驱动应用中创建的图表添加到门户网页的说明。
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 01/29/2020
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 3d9a2ec3ef4e2589c51717629213dfe73d3418eb
ms.sourcegitcommit: 4349eefb1fd788f5e27d91319bc878ee9aba7a75
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2020
ms.locfileid: "3012563"
---
# <a name="add-a-chart-created-in-a-model-driven-app-to-a-webpage-in-portal"></a>将模型驱动应用中创建的图表添加到门户网页

可使用名称为 [Chart](../liquid/portals-entity-tags.md#chart) 的 Liquid 标记向网页添加图表。 可在网页中的**复制**字段内或 [Web 模板](../liquid/store-content-web-templates.md)中的**源**字段内添加图表 Liquid 标记。
 
例如，{% chart id:EE3C733D-5693-DE11-97D4-00155DA3B01E %}

![图表示例](../media/dynamics365-chart-example.png "图表示例")

也可以指定视图（保存的查询）的 ID 以筛选查询。 例如：

<!—Leads by Source – Open Leads -->

{% chart id:"EE3C733D-5693-DE11-97D4-00155DA3B01E" viewid:"00000000-0000-0000-00AA-000010001006" %}

## <a name="get-the-id-of-a-chart"></a>获取图表的 ID

1.  转至目标实体，如**销售** > **潜在顾客**。
2.  展开**图表**区域。
3.  选择所需图表。
4.  选择**更多命令**，然后选择**导出图表**。

    ![导出图表](../media/export-dynamics365-chart.png "导出图表")

5. 在文本编辑器中打开所导出图表的 XML 文件。
6. 复制 \<visualizationid\> 标记的值。

    ![获取图表的 Chartid](../media/dynamics365-chart-chartid.png "获取图表的图表 ID")

7. 将 visualizationid 值粘贴到图表 ID 参数的 Liquid 图表标记声明中，如：

    {% chart id:EE3C733D-5693-DE11-97D4-00155DA3B01E %}。

## <a name="get-the-id-of-a-view"></a>获取视图的 ID

必须打开视图编辑器才能获取用于 Liquid 图表标记的视图 ID。
 
1. 转到 make.powerapps.com，然后选择相应环境。
1. 在左侧导航栏中，选择“数据 > 实体”。
1. 选择相应的实体，然后转到“视图”选项卡。
1. 您可以查看视图列表。 转到选项 (...)，然后选择“编辑视图”。
1. 从“视图”窗口的地址栏复制 id 值。

    ![查看窗体的 ID](../media/dynamics365-chart-viewid.png)

1. 将此 ID粘贴到 viewid 参数的 Liquid 图表标记声明中，如：

    ```
    <!—Leads by Source – Open Leads -->
    {% chart id:"EE3C733D-5693-DE11-97D4-00155DA3B01E" viewid:"00000000-0000-0000-00AA-000010001004" %}
    ```

## <a name="entity-permission-requirement"></a>实体权限要求

为图表中正在查询的目标实体声明了读取权限。 要让匿名用户或已经身份验证的用户可查看图表，必须确保创建适当的[实体权限](assign-entity-permissions.md)记录并分派给适宜的 [Web 角色](create-web-roles.md)。 
 
如果不授予权限，用户将看到拒绝访问消息。

## <a name="unsupported-charts-and-chart-types"></a>不受支持的图表和图表类型

门户中现在不支持以下图表类型：
- 圆环图
- 标记

下表列出了门户中现在不支持的图表。

| 图表名称                              | 图表 ID                             | 实体类型      |
|-----------------------------------------|--------------------------------------|------------------|
| 客户(按负责人) - 标记图           | be178262-6142-4b41-85b7-4ccedc62cfd9 | account          |
| 按负责人显示的活动 - 标记图         | c83b331e-87c7-488c-b8e7-89a6098ea102 | activitypointer  |
| 按优先级显示的活动 - 圆环图 | d3f6c1eb-2e4b-428b-8949-682a311ae057 | activitypointer  |
| 联系人(按客户)                     | 2ff3ebea-6310-4dde-b3a1-e1144ea42b7b | contact          |
| 按国家/地区显示的联系人                     | ea89e2ad-2602-4333-8724-aa5775d66b77 | contact          |
| 联系人(按首选联系方式)    | 751b7456-308e-4568-a3a9-47135aae833a | contact          |
| 目标进度(计数)                   | a93b8f7b-9c68-df11-ae90-00155d2e3002 | 目标             |
| 目标进度(金额)                   | aec6d51c-ea67-df11-ae90-00155d2e3002 | 目标             |
| 今天的目标值与实际值(计数)      | 1b697c8e-9a6f-df11-986c-00155d2e3002 | 目标             |
| 今天的目标值与实际值(金额)      | 1e697c8e-9a6f-df11-986c-00155d2e3002 | 目标             |
| 按客户显示的案例                        | 38872e4f-ac99-e511-80da-00155dc1b253 | 事件         |
| 按优先级显示的案例                       | 0f0fb995-9d6f-453c-b26d-8f443e42e676 | 事件         |
| 按产品显示的案例                        | 17c3f166-5b22-4476-819b-b05da2e8d24f | 事件         |
| 按负责人显示的本月将过期的文章   | 47d696ad-7c3b-e511-80d1-00155db10d2b | knowledgearticle |
| 按负责人                                | 330068fd-833b-e511-80d1-00155db10d2b | knowledgearticle |
| 按主题                              | bcd3f9a5-913b-e511-80d1-00155db10d2b | knowledgearticle | 
| | |
