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
ms.openlocfilehash: ac4b57853e6dfc4c0969a4207538e15db0b58bc8
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2019
ms.locfileid: "2757520"
---
# <a name="create-a-relationship-between-entities"></a>创建实体之间的关系
一个实体中的数据通常与另一个实体中的数据相关。 例如，您可能有**教师**实体和**班级**实体，**班级**实体可能有与**教师**实体的查找关系来显示哪个教师教哪个班级。 您可以使用查找字段从**教师**实体显示数据。 这通常称为查找字段。

## <a name="define-a-relationship"></a>定义关系
您可以创建多个类型的一个实体到另一个实体（或实体与其自己）的关系。 每个实体可以有包含多个实体的关系，且每个实体可以与其他实体之间有多个关系。 某些常见的关系类型为：

* **多对一** - 在这种关系中，实体 A 中的每个记录都可以与实体 B 中的多个记录匹配，但是，实体 B 中的每个记录只能与实体 A 中的一个记录匹配。例如，班级有一个教室。 这是最常见的关系类型，其在字段列表中显示为**查找字段**。
* **一对多** - 在这种关系中，实体 B 中的每个记录都可以与实体 A 中的多个记录匹配，但是，实体 A 中的每个记录只能与实体 B 中的一个记录匹配。例如，一个教师教很多班级。
* **多对多** - 在这种关系中，实体 A 中的每个记录可以与实体 B 中的多个记录匹配，反之亦然。 例如，学生参加很多班级，每个班级可以有多名学生。

此外，您还可以在操作每次在父实体上执行时在多对一和一对多关系上设置高级的级联行为。

## <a name="add-a-lookup-field-many-to-one-relationship"></a>添加查找字段（多对一关系）

若要向实体添加查找关系，在**关系**选项卡下创建关系并指定要与其创建关系的实体。

1. 在 [powerapps.com](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) 上，展开**数据**部分并单击或点按左侧导航窗格中的**实体**。

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

1. 在 [powerapps.com](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) 上，展开**数据**部分并单击或点按左侧导航窗格中的**实体**。

2. 单击或点按现有实体或[创建新实体](data-platform-create-entity.md)

3. 单击**关系**。

4. 单击**添加关系**右侧的向下箭头，这将为您提供类型和关系的选择。 单击**一对多**，这将打开新面板供您选择要与其创建关系的实体。 从**相关实体**下拉列表中选择实体。
    > [!div class="mx-imgBorder"] 
    > ![一对多关系](./media/data-platform-cds-newrelationship/onetomany-1.png "一对多关系")

5. 在选择实体后，查找字段将显示在主要实体中，它们默认具有实体名称（在此示例中为“班级”），但您可以在需要时进行更改。

    > [!NOTE]
    > 如果是一对多关系，查找字段将在相关实体中创建，而不是您当前选择的实体。 如果需要在当前实体上查找，请创建多对一关系。

    > [!div class="mx-imgBorder"] 
    > ![一对多关系](./media/data-platform-cds-newrelationship/onetomany-2.png "一对多关系")

6. 单击**完成**将关系添加到实体，然后单击**保存实体**。

    > [!div class="mx-imgBorder"] 
    > ![一对多关系](./media/data-platform-cds-newrelationship/onetomany-3.png "一对多关系")

## <a name="add-a-many-to-many-relationship"></a>添加多对多关系
若要添加多对多关系，在**关系**选项卡下创建关系并指定要与其创建关系的实体。

1. 在 [powerapps.com](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) 上，展开**数据**部分并单击或点按左侧导航窗格中的**实体**。

2. 单击或点按现有实体或[创建新实体](data-platform-create-entity.md)

3. 单击**关系**。

4. 单击**添加关系**右侧的向下箭头，这将为您提供类型和关系的选择。 单击**多对多**，这将打开新面板供您选择要与其创建关系的实体。 从**相关实体**下拉列表中选择实体。

5. 在选择实体后，关系和关系实体的名称将显示。 它们将默认具有合并的实体的名称，但如果需要，您可以进行更改。

    > [!div class="mx-imgBorder"] 
    > ![多对多关系](./media/data-platform-cds-newrelationship/manytomany-1.png "多对多关系")

6. 单击**完成**将关系添加到实体，然后单击**保存实体**。


## <a name="add-advanced-relationship-behavior"></a>添加高级关系行为

在构建一对多或多对一关系时，您还可以设置高级行为。

![高级行为](./media/data-platform-cds-newrelationship/advanced-1.png "高级行为")

这些选项也称为级联行为，因为它们在相关实体的层次结构中级联。 例如，如果学生被从系统中删除，可能需要删除相关的学生测试和家庭作业。 此类行为称为父关系。

另一方面，您可能决定不希望操作向下级联到层次结构。 例如，在教师与班级关系中，您可能决定子实体（类）在父级（教师）被删除时*不*应删除。 这称为引用关系。

在通过创建自定义实体为业务数据建模时，或使用现有通用数据模型实体时，应考虑所需的行为以及该行为对相关实体的整个层次结构的影响，并在以下标准行为之间选择一个：

* **引用，删除链接：** 在两个实体之间的引用关系中，可以导航到任何相关实体，但对一个实体执行的操作并不会影响另一个实体。 例如，如果您有教师与班级之间的一对多关系，删除教师将不会影响相关类。

* **引用，限制删除：** 在两个实体之间的“引用，限制删除”关系中，您可以导航到任何相关记录。 对父记录执行的操作并不会应用到子记录，但是存在子记录时不能删除父记录。 如果您不希望子记录成为孤立项，这非常有用。 这会强制用户在删除父项前删除所有子项。

    > [!div class="mx-imgBorder"] 
    > ![引用，限制删除](./media/data-platform-cds-newrelationship/advanced-3.png "引用，限制删除")

* **父：** 在两个实体之间的父级关系中，对父实体记录执行的任何操作也可以对与父实体记录相关的所有子实体记录执行。 例如，当删除父项时，这会导致删除所有子记录。

* **自定义：** 在两个实体之间的自定义关系中，可选择与每一组可能的操作关联的行为。 

    > [!div class="mx-imgBorder"] 
    > ![自定义行为](./media/data-platform-cds-newrelationship/advanced-2.png "自定义行为")

有关默认行为和自定义行为的详细信息：[配置实体关系行为](entity-relationship-behavior.md)。



## <a name="use-a-lookup-field-in-an-app"></a>在应用程序中使用查找字段
如果从包含查找字段的实体[自动创建应用程序](../canvas-apps/data-platform-create-app.md)，它将显示为包含来自实体的**主要名称**字段的数据的**下拉**控件。

## <a name="add-1n-and-nn-relationships-for-canvas-apps"></a>为区域应用添加 1:N 和 N:N 关系
在 Common Data Service 中使用**关联**功能通过一对多或多对多关系链接两个记录。 详细信息：[PowerApps 中的关联和取消关联功能](../canvas-apps/functions/function-relate-unrelate.md)

## <a name="next-steps"></a>后续步骤
* [使用 Common Data Service 数据库生成应用](../canvas-apps/data-platform-create-app.md)
* [使用 Common Data Service 数据库从头开始创建应用](../canvas-apps/data-platform-create-app-scratch.md)

