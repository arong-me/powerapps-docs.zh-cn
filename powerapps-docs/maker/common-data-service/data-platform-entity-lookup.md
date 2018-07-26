---
title: 通过使用查找字段创建实体之间的关系 | Microsoft Docs
description: 有关如何使用查找字段在 PowerApps 中创建实体之间的关系的分步说明。
author: clwesene
manager: kfile
ms.service: powerapps
ms.component: cds
ms.topic: conceptual
ms.date: 03/21/2018
ms.author: clwesene
ms.openlocfilehash: 8562219c373a8880f7cc89f791b6c6373b6df0b3
ms.sourcegitcommit: 0b051bba173353d7ceda3b60921e7e009eb00709
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2018
ms.locfileid: "39217926"
---
# <a name="create-a-relationship-between-entities"></a>创建实体间的关系
一个实体中的数据通常与另一个实体中的数据相关。 例如，可能有“教师”和“班级”实体，而“班级”实体可能与“教师”实体间存在查找关系，以显示哪位教师负责这个班级。 可以使用查找字段显示“教师”实体中的数据。 这通常称为查找字段。

## <a name="define-a-relationship"></a>定义关系
可以创建从一个实体到另一个实体（或实体与其自身之间）的几种类型的关系。 一个实体可以与多个实体有关系，并且一个实体可以与另一个实体有多种关系。 一些常见关系类型如下：

* **多对一** - 在这种关系中，实体 A 中的每条记录可与实体 B 中的多条记录匹配，但是实体 B 中的每条记录只能与实体 A 中的一条记录匹配。例如，一个班级对应一个教室。 这是最常见的关系类型，并在字段列表中显示为查找字段
* **一对多** - 在这种关系中，实体 B 中的每条记录可与实体 A 中的多条记录匹配，但是实体 A 中的每条记录只能与实体 B 中的一条记录匹配。例如，一位老师负责很多班级。
* **多对多** - 在这种关系中，实体 A 中的每条记录可与实体 B 中的多条记录匹配，反之亦然。 例如，学生参加了很多学习班，每个学习班可以有多个学生。

## <a name="add-a-lookup-field-many-to-one-relationship"></a>添加查找字段（多对一关系）

若要向实体添加查阅关系，请在“关系”选项卡下创建关系，并指定要与之有关系的实体。

1. 在 [powerapps.com](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) 上，展开“数据”部分，然后单击或点击左侧导航窗格中的“实体”。

    ![实体详细信息](./media/data-platform-cds-create-entity/entitylist.png "实体列表")

2. 单击或点击现有实体，或者[创建新实体](data-platform-create-entity.md)

3. 单击“关系”

4. 单击“添加关系”后会打开一个新面板，用于选择要与其创建关系的实体。 从“相关实体”下拉列表中选择实体。

    ![多对一关系](./media/data-platform-cds-newrelationship/manytoone-1.png "多对一关系")

5. 选择实体后，查找字段会显示在主要实体上，其名称默认采用实体名称（此示例中为“教室”），可根据需要进行更改。

    ![多对一关系](./media/data-platform-cds-newrelationship/manytoone-2.png "多对一关系")

6. 单击“完成”将关系添加到实体，然后单击“保存实体”。

    ![多对一关系](./media/data-platform-cds-newrelationship/manytoone-3.png "多对一关系")

## <a name="add-a-one-to-many-relationship"></a>添加一对多关系

若要添加一对多关系，请在“关系”选项卡下创建关系，并指定要与之建立关系的实体。

1. 在 [powerapps.com](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) 上，展开“数据”部分，然后单击或点击左侧导航窗格中的“实体”。

    ![实体详细信息](./media/data-platform-cds-create-entity/entitylist.png "实体列表")

2. 单击或点击现有实体，或者[创建新实体](data-platform-create-entity.md)

3. 单击“关系”

4. 单击“添加关系”右侧的向下箭头，可以同时选择两种类型的关系。 单击“一对多”后会打开一个新窗格，用于选择想要与其创建关系的实体。 从“相关实体”下拉列表中选择实体。

    ![一对多关系](./media/data-platform-cds-newrelationship/onetomany-1.png "一对多关系")

5. 选择实体后，查找字段会显示在主要实体上，其名称默认采用实体名称（此示例中为“班级”），可根据需要进行更改。

    > [!NOTE]
    > 如果是一对多关系，查找字段会创建在相关实体上，而不是当前选择的实体上。 如果要在当前实体上创建，请创建多对一关系。

    ![一对多关系](./media/data-platform-cds-newrelationship/onetomany-2.png "一对多关系")

6. 单击“完成”将关系添加到实体，然后单击“保存实体”。

    ![一对多关系](./media/data-platform-cds-newrelationship/onetomany-3.png "一对多关系")

## <a name="add-a-many-to-many-relationship"></a>添加多对一关系

目前只能通过“高级”菜单使用。 在 PowerApps 主页上的左侧菜单中单击“高级”。 有关如何创建关系的信息，请参阅[创建 N:N 关系](/dynamics365/customer-engagement/customize/create-and-edit-nn-many-to-many-relationships)

## <a name="use-a-lookup-field-in-an-app"></a>在应用中使用查找字段
如果在包含查阅字段的实体的基础之上[自动创建应用](../canvas-apps/data-platform-create-app.md)，此实体会显示为“下拉列表”控件，其中包含实体的“主要名称”字段中的数据。

## <a name="next-steps"></a>后续步骤
* [使用 Common Data Service 数据库生成应用](../canvas-apps/data-platform-create-app.md)
* [使用 Common Data Service 数据库从头开始创建应用](../canvas-apps/data-platform-create-app-scratch.md)

