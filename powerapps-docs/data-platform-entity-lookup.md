---
title: "通过查找字段构建的实体关系 | Microsoft 文档"
description: "通过使用查找字段构建实体之间的关系。"
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
ms.date: 12/09/2016
ms.author: kfend
ms.openlocfilehash: 1aff4df6e314f50a67aff6a08298d3d7aa4a9cfa
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2017
---
# <a name="build-a-relationship-between-entities"></a>生成实体关系
一个实体中的数据通常与另一个实体中的数据相关。 例如，你可能有“Customers”和“Orders”实体，而“Orders”实体可能与“Customers”实体有查阅关系，以显示是哪个客户下达订单的。 可以使用查阅字段显示“Customers”实体中下达订单的用户的相关数据。 有关详细信息，请参阅[实体关系和查阅字段](https://docs.microsoft.com/en-us/common-data-service/entity-reference/relationships)。

## <a name="define-a-relationship"></a>定义关系
可以创建从一个实体到另一个实体（或实体与其自身之间）的几种类型的关系。 一个实体可以与多个实体有关系，并且一个实体可以与另一个实体有多种关系。 一些常见关系类型如下：

* **正常** - 这种关系存在于两个实体之间。
* **自身** - 这种关系存在于实体与其自身之间。
* **一对一** - 在这种关系中，实体 A 中的每条记录只能与实体 B 中的一条记录匹配，反之亦然。 最新版 Common Data Service 不支持具有这种关系的自定义实体。
* **一对多** - 在这种关系中，实体 A 中的每条记录可与实体 B 中的多条记录匹配，但实体 B 中的每条记录只能与实体 A 中的一条记录匹配。
* **多对多** - 在这种关系中，实体 A 中的每条记录可与实体 B 中的多条记录匹配，反之亦然。 最新版 Common Data Service 不支持这种关系。

## <a name="add-a-lookup-relation"></a>添加查阅关系
若要向实体添加查阅关系，请在“关系”选项卡下创建关系，并指定要与之有关系的实体。

1. 在 [powerapps.com](https://web.powerapps.com) 上，展开“Common Data Service”部分，然后单击或点击左侧导航窗格中的“实体”。
2. 在实体列表中，单击或点击某个实体即可显示其字段。 在列表上方的搜索栏中键入一个或多个字符可以筛选该列表。
3. 单击或点击屏幕顶部附近的“关系”。 此选项卡显示了实体的所有关系。 单击“新建关系”。
4. 在“创建关系”页面上，指定要与之有关系的相关实体，然后指定关系的名称和显示名称。
5. 单击或点击“**保存**”以提交更改。 此时，系统会自动创建同名的查阅字段。

## <a name="use-a-lookup-field-in-an-app"></a>在应用中使用查找字段
如果在包含查阅字段的实体的基础之上[自动创建应用](data-platform-create-app.md)，此实体会显示为“下拉列表”控件，折叠时其中包含引用实体的“主键”字段数据。 若要让展开的下拉列表显示两个字段，必须将“PrimaryId”字段和所选的第二个字段添加到查阅关系的相关实体的“默认查阅”字段组。

## <a name="delete-a-record-with-a-lookup-relation"></a>删除有查阅关系的记录
如果实体 A 与实体 B 有查阅关系：

* 可以无限制地删除实体 A 中的任何记录。
* 如果实体 B 中的一条记录与实体 A 中的一条或多条记录匹配，则必须先删除实体 A 中的所有匹配记录，然后才能删除实体 B 中的记录。

**注意**：当实体 B 是与实体 A 有父关系的标准实体时，如果从实体 A 中删除一条记录，也会删除实体 B 中的所有匹配记录。

有关如何删除字段的信息，请参阅 [管理字段](data-platform-manage-fields.md)。

## <a name="next-steps"></a>后续步骤
* [使用 Common Data Service 数据库生成应用](data-platform-create-app.md)
* [使用 Common Data Service 数据库从头开始创建应用](data-platform-create-app-scratch.md)

