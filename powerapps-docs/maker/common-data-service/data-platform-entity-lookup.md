---
title: 使用查找字段创建实体之间的关系 | Microsoft Docs
description: 如何使用查找字段在 PowerApps 中创建实体之间的关系的分步说明。
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.component: cds
ms.topic: conceptual
ms.date: 02/21/2019
ms.author: lanced
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="create-a-relationship-between-entities"></a>创建实体之间的关系
一个实体中的数据通常与另一个实体中的数据相关。 例如，您可能有**教师**实体和**班级**实体，**班级**实体可能有与**教师**实体的查找关系来显示哪个教师教哪个班级。 您可以使用查找字段从**教师**实体显示数据。 这通常称为查找字段。

## <a name="define-a-relationship"></a>定义关系
您可以创建多个类型的一个实体到另一个实体（或实体与其自己）的关系。 每个实体可以有包含多个实体的关系，且每个实体可以与其他实体之间有多个关系。 某些常见的关系类型为：

* **多对一** - 在这种关系中，实体 A 中的每个记录都可以与实体 B 中的多个记录匹配，但是，实体 B 中的每个记录只能与实体 A 中的一个记录匹配。例如，班级有一个教室。 这是最常见的关系类型，其在字段列表中显示为**查找字段**。
* **一对多** - 在这种关系中，实体 B 中的每个记录都可以与实体 A 中的多个记录匹配，但是，实体 A 中的每个记录只能与实体 B 中的一个记录匹配。例如，一个教师教很多班级。
* **多对多** - 在这种关系中，实体 A 中的每个记录可以与实体 B 中的多个记录匹配，反之亦然。 例如，学生参加很多班级，每个班级可以有多名学生。

## <a name="add-a-lookup-field-many-to-one-relationship"></a>添加查找字段（多对一关系）

若要向实体添加查找关系，在**关系**选项卡下创建关系并指定要与其创建关系的实体。

1. 在 [powerapps.com](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) 上，展开**数据**部分并单击或点按左侧导航窗格中的**实体**。

    ![实体详细信息](./media/data-platform-cds-create-entity/entitylist.png "实体列表")

2. 单击或点按现有实体或[创建新实体](data-platform-create-entity.md)

3. 单击**关系**。

4. 单击**添加关系**，这将打开新面板供您选择要与其创建关系的实体。 从**相关实体**下拉列表中选择实体。

    > [!div class="mx-imgBorder"] 
    > ![多对一关系](./media/data-platform-cds-newrelationship/manytoone-1.png "多对一关系")

5. 在选择实体后，查找字段将显示在主要实体中，它们默认具有实体名称（在此示例中为“教室”），但您可以在需要时进行更改。

    ![多对一关系](./media/data-platform-cds-newrelationship/manytoone-2.png "多对一关系")

6. 单击**完成**将关系添加到实体，然后单击**保存实体**。

    > [!div class="mx-imgBorder"] 
    > ![多对一关系](./media/data-platform-cds-newrelationship/manytoone-3.png "多对一关系")

## <a name="add-a-one-to-many-relationship"></a>添加一对多关系

若要添加一对多关系，在**关系**选项卡下创建关系并指定要与其创建关系的实体。

1. 在 [powerapps.com](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) 上，展开**数据**部分并单击或点按左侧导航窗格中的**实体**。

    ![实体详细信息](./media/data-platform-cds-create-entity/entitylist.png "实体列表")

2. 单击或点按现有实体或[创建新实体](data-platform-create-entity.md)

3. 单击**关系**。

4. 单击**添加关系**右侧的向下箭头，这将为您提供类型和关系的选择。 单击**一对多**，这将打开新面板供您选择要与其创建关系的实体。 从**相关实体**下拉列表中选择实体。

    ![一对多关系](./media/data-platform-cds-newrelationship/onetomany-1.png "一对多关系")

5. 在选择实体后，查找字段将显示在主要实体中，它们默认具有实体名称（在此示例中为“班级”），但您可以在需要时进行更改。

    > [!NOTE]
    > 如果是一对多关系，查找字段将在相关实体中创建，而不是您当前选择的实体。 如果需要在当前实体上查找，请创建多对一关系。

    > [!div class="mx-imgBorder"] 
    > ![一对多关系](./media/data-platform-cds-newrelationship/onetomany-2.png "一对多关系")

6. 单击**完成**将关系添加到实体，然后单击**保存实体**。

    > [!div class="mx-imgBorder"] 
    > ![一对多关系](./media/data-platform-cds-newrelationship/onetomany-3.png "一对多关系")

## <a name="add-a-many-to-many-relationship"></a>添加多对多关系

当前这只通过“高级”菜单提供。 从 PowerApps 主页上，单击左侧菜单的“高级”。 有关如何创建关系的信息，请参阅[创建 N:N 关系](/dynamics365/customer-engagement/customize/create-and-edit-nn-many-to-many-relationships)

## <a name="use-a-lookup-field-in-an-app"></a>在应用程序中使用查找字段
如果从包含查找字段的实体[自动创建应用程序](../canvas-apps/data-platform-create-app.md)，它将显示为包含来自实体的**主要名称**字段的数据的**下拉**控件。

## <a name="add-1n-and-nn-relationships-for-canvas-apps"></a>为区域应用添加 1:N 和 N:N 关系
在 Common Data Service 中使用**关联**功能通过一对多或多对多关系链接两个记录。 详细信息：[PowerApps 中的关联和取消关联功能](../canvas-apps/functions/function-relate-unrelate.md)

## <a name="next-steps"></a>后续步骤
* [使用 Common Data Service 数据库生成应用程序](../canvas-apps/data-platform-create-app.md)
* [使用 Common Data Service 数据库从头创建应用程序](../canvas-apps/data-platform-create-app-scratch.md)

