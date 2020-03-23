---
title: 在模型驱动应用视图中创建或编辑筛选器 | MicrosoftDocs
description: 了解如何为应用创建和编辑筛选器或视图
keywords: 表达式生成器
ms.date: 2/04/2020
ms.service: powerapps
ms.custom: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.assetid: ''
author: iangpgh
ms.author: v-iapr
manager: matp
ms.reviewer: srihas
ms.suite: ''
ms.tgt_pltfrm: ''
caps.latest.revision: 25
topic-status: Drafting
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 7645910490aee24b7f3c2b239f1a6dd841b67df2
ms.sourcegitcommit: eda3382ade50efe66611518c8f36e3a2ada7a91d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/15/2020
ms.locfileid: "3060208"
---
# <a name="create-or-edit-filters-in-model-driven-app-views"></a>在模型驱动应用视图中创建或编辑筛选器

<a name="BKMK_CreateOrEditViewFilters"></a>   

Power Apps 视图中的筛选器对视图提供的值很重要。 您应用的筛选器确定哪些记录默认显示在列表中。 您可以通过选择列并选择**筛选依据**来为包含在视图中的列添加或编辑筛选器。 您也可以使用视图设计器中的表达式生成器。 使用表达式生成器可为当前视图中实体的任何字段或相关实体中的任何字段添加或编辑筛选器。 

在本主题中，您通过执行以下任务创建或编辑筛选器：

-   [编辑或删除筛选器条件](create-edit-view-filters.md#edit-or-remove-a-filter-condition)

-   [打开表达式生成器](create-edit-view-filters.md#open-the-expression-builder)

-   [向筛选器添加条件](create-edit-view-filters.md#add-conditions-to-a-filter)

-   [向筛选器添加组条件](create-edit-view-filters.md#add-a-group-condition-to-a-filter)

-   [将相关实体添加到条件](create-edit-view-filters.md#add-a-related-entity-to-a-condition)

-   [筛选器的组条件](create-edit-view-filters.md#group-conditions-of-a-filter)

## <a name="edit-or-remove-a-filter-condition"></a>编辑或删除筛选器条件

1. 登录到 [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。  

2. 展开**数据**，选择**实体**，选择所需实体，然后选择**视图**选项卡。

3. 选择一个视图以将其打开。 视图属性面板会列出现有的筛选器。

    > [!div class="mx-imgBorder"] 
    > ![视图面板筛选器](media/views-panel-filters.png "视图面板筛选器")

4. 在视图属性面板中，选择一个筛选条件。

    > [!div class="mx-imgBorder"] 
    > ![编辑筛选器](media/edit-filter-viewpanel.png "编辑筛选器")

5. 选择要使用的条件运算符。

6. 输入或选择条件的比较值。

7. 选择**应用**。

8. 要删除条件，请选择**关闭**。 条件将删除，但不进行确认。

### <a name="open-the-expression-builder"></a>打开表达式生成器

- 在视图属性面板中，选择**编辑筛选器**。

    > [!div class="mx-imgBorder"] 
    > ![表达式生成器](media/edit-create-filters.png "表达式生成器")

### <a name="add-conditions-to-a-filter"></a>向筛选器添加条件

1. 在表达式生成器中，选择**添加** > **添加行**。

2. 为条件选择字段。

3. 选择条件运算符。

4. 选择比较值。  

    某些筛选条件不需要条件的比较值。 例如，运算符 **Contains data** 不需要比较值。 对于其他筛选条件，您可以从选项集选择比较值。 例如，**状态**字段具有包含**可用**和**停用**值的选项集。

    > [!div class="mx-imgBorder"] 
    > ![筛选条件](media/add-condition-filter.png "筛选条件")

5. 选择**确定**。

### <a name="add-a-group-condition-to-a-filter"></a>向筛选器添加组条件

1. 在表达式生成器中，选择**添加** > **添加组**。

2. 为组选择关系运算符 **Or**。 **And** 是默认的关系运算符。

3. 指定分组条件的第一个子句。 选择字段、条件运算符和比较值。

4. 选择**添加** > **添加组**

5. 指定分组条件的第二个子句。

    > [!div class="mx-imgBorder"] 
    > ![组条件筛选器](media/add-group-filter.png "组条件筛选器")

    您可以选择**折叠**将组显示为条件表达式。

### <a name="add-a-related-entity-to-a-condition"></a>将相关实体添加到条件

1. 在表达式生成器中，选择**添加** > **添加相关实体**。

2. 从当前实体中选择与另一个实体相关的字段。 与此字段相关的实体将显示在括号中。 您可以选择与相关实体之间具有多对一、一对多或多对多关系的字段。

3. 为条件选择相关实体的字段。

4. 选择条件运算符。

5. 选择或输入比较值。

    > [!div class="mx-imgBorder"] 
    > ![相关实体筛选器](media/add-relatedentity-filter.png "相关实体筛选器")

### <a name="group-conditions-of-a-filter"></a>筛选器的组条件

1. 在表达式生成器中，选中要分组的条件所对应的复选框。

2. 选择其中一个条件的**更多命令** (...)，然后选择**生成组**。

3. 要取消分组，请选择组的**更多命令** (...)，然后选择**取消组合**

    > [!div class="mx-imgBorder"] 
    > ![分组条件筛选器](media/group-conditions-filter.png "分组条件筛选器")

### <a name="next-steps"></a>后续步骤
[选择和配置活动](choose-and-configure-columns.md)  
[编辑筛选条件](edit-filter-criteria.md)  
[创建 1:N（一对多）或 N:1（多对一）关系](../common-data-service/create-edit-1n-relationships.md)
