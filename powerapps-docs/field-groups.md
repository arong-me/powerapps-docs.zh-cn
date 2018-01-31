---
title: "使用字段组创建应用 | Microsoft 文档"
description: "使用字段组在数据库中实现应用创建标准化。"
services: powerapps
documentationcenter: na
author: aneesmsft
manager: kfend
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 03/11/2017
ms.author: aneesa
ms.openlocfilehash: d791d04965873c133be85013feb181dc5a1e1bad
ms.sourcegitcommit: 6afca7cb4234d3a60111c5950e7855106ff97e56
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2018
---
# <a name="use-field-groups"></a>使用字段组
字段组提供了一种对实体的一个或多个字段进行分组的方法。 这个功能还可以帮助你提高创建和维护应用的速度，同时降低难度。 一个字段组可以包含一个或多个字段，而一个字段可以出现在任意多个的字段组中。 但一个字段在同一个字段组中不能出现多次。

字段组存储在实体中，并且可供使用同一实体的所有应用共享。 在特定时间，可能有许多不同的应用使用同一个实体和实体中的字段组。 字段组的这种集中式管理和共享机制有助于实现一致性，因为不管在何处使用，字段组总是会显示相同的字段。 同时，这也可以简化维护工作，因为对一个字段组进行更改后，所有使用该字段组的位置都会自动更新。 利用字段组可以提高应用编程和自定义流程效率，因为应用程序作者可以直接使用一组字段，而不需要逐一处理。

## <a name="default-field-groups"></a>默认字段组
Common Data Service 的实体中包括几个默认字段组。 这些字段组位于多个位置，可用于提高创建和自定义应用的速度，同时降低难度。

| 默认字段组名称 | 说明 |
| --- | --- |
| DefaultList |用于以表形式显示记录列表。 |
| DefaultCard |用于以卡片形式显示记录列表。 |
| DefaultDetails |用于在视图和编辑窗格中显示单条记录的详细信息。 |
| DefaultLookup |用于显示查找控件以选择记录。 |

## <a name="view-a-field-group"></a>查看字段组
1. 登录到 [powerapps.com](https://web.powerapps.com)。
2. 如果你可以访问多个环境，请确保使用上栏中的环境选择器选择正确的环境。
3. 展开“Common Data Service”分区，并单击或点击左侧导航窗格中的“实体”。
4. 在实体列表中，单击或点击要查看其中的字段组的实体。
5. 在字段列表上方的标题位置，单击或点击“字段组”。 现在即可查看实体中当前存在的所有字段组。
6. 在字段组列表中，单击或点击要查看其详细信息的字段组。
7. 在字段组详细信息位置，可以看到并列的两个列表。 一个列表的标题是“实体字段”，其中列出了实体中的所有字段。 另一个列表的标题是“字段组字段”，其中列出了字段组中包含的字段。

## <a name="modify-a-field-group"></a>修改字段组
1. 查看要修改的字段组。
2. 要添加字段，请在“实体字段”列表中双击字段名称。 你也可以将字段从“实体字段”列表中拖放到“字段组字段”列表中。
3. 要删除字段组，请在“字段组字段”列表中单击字段名称旁的“X”。
4. 单击或点击“保存”按钮。

> [!NOTE]
> 暂不支持修改[标准实体](guided-learning/manage-data.yml#step-2)的字段组，但可以修改自定义实体的字段组。*

## <a name="creating-a-field-group"></a>创建字段组
创建实体时，PowerApps 会自动创建默认字段组。 目前不支持创建其他字段组。

## <a name="delete-a-field-group"></a>删除字段组
目前不支持删除字段组。

## <a name="view-and-edit-field-group-data-in-microsoft-excel"></a>在 Microsoft Excel 中查看和编辑字段组数据
1. 查看要检查其数据的实体的字段组。
2. 每个字段组旁有一个 Excel 图标。 只有当字段组包含字段时，才会启用 Excel 图标。
3. 单击要在 Excel 中打开的字段组的 Excel 图标。 随即会生成一个工作簿，其中包含实体字段列表、Excel 加载项和一个指示环境的指针。
4. 打开浏览器中生成的工作簿。
5. 打开后，启用编辑。 Excel 加载项随即会将数据读取到工作簿中。 有关详细信息，请参阅[在 Excel 中打开实体数据](data-platform-interactive-excel.md)。

## <a name="field-group-usage"></a>字段组使用方法
使用默认字段组可以提高应用程序编程和自定义的速度。 目前可以查看活动字段组的位置包括：

* **实体表单控件** - 实体表单控件使用默认字段组显示动态表单，可以帮助提高应用编程效率，改善一致性，同时简化维护工作。 有关详细信息，请参阅[使用实体表单控件](entity-form-control.md)。
* **查找控件** - 如果屏幕上有一个添加的字段引用了另一个关联的实体，则该字段会显示为查找控件（选择列表）。 当用户单击查找控件以从关联的实体中选择记录时，显示的字段由关联实体上的 **DefaultLookup** 字段组决定。 只会使用 **DefaultLookup** 字段组的前两个字段。
* **创建应用** - 通过从数据中选择创建应用的选项来生成应用时，会自动创建所选实体的屏幕。 “显示”屏幕上的“显示表单”控件和“编辑”屏幕上的“编辑表单”控件使用 **DefaultDetails** 字段组来确定默认添加到这些屏幕上的字段。

