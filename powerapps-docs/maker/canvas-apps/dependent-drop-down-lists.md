---
title: 在画布应用中创建依赖的下拉列表 |Microsoft Docs
description: 在 PowerApps 中，创建筛选器中的画布应用中的另一个下拉列表的下拉列表。
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 04/04/2019
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: dc1b3b87e2c1fdcd4ab7eb6634db7f9e7c049ec2
ms.sourcegitcommit: 38f91423933749ca19557f29e86cd8f5ad06e1eb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59042746"
---
# <a name="create-dependent-drop-down-lists-in-a-canvas-app"></a>创建依赖下拉列表中的画布应用

当您创建依赖 （或级联） 下拉列表时，用户在另一个列表中的筛选器选项列表中选择一个选项。 许多组织创建依赖列表，以帮助用户更高效地填写窗体。 例如，用户可能选择国家或地区进行筛选的城市，列表或用户可能会选择一个类别以显示该类别中仅的代码。

最佳做法是，创建数据源中的"父级"和"child"的值的独立于用户使用应用更新的数据源的列表 （例如，国家/地区和城市）。 如果采用此方法，可以在多个应用中，使用同一个父和子数据，并可以更新该数据而无需重新发布应用程序或使用它们的应用。 可以通过使用集合或静态数据，完成相同的结果，但它不建议用于企业方案。

本主题中的方案中，将存储到员工提交问题**事件**通过窗体的列表。 员工指定不只在应用商店的位置事件发生，但也该位置内的部门。 并非所有位置都的同一个部门，因此**位置**列表可确保员工不能指定的位置不都具有该部门的部门。

本主题使用 Microsoft SharePoint 列表作为数据源，但所有表格数据源的工作方式相同。

## <a name="create-data-sources"></a>创建数据源

一个**位置**列表显示了每个位置处的部门。

| Location | Department |
|----------------|------------------|
| Eganville      | 面包店           |
| Eganville      | 熟食店             |
| Eganville      | 生成          |
| Renfrew        | 面包店           |
| Renfrew        | 熟食店             |
| Renfrew        | 生成          |
| Renfrew        | 药房         |
| Renfrew        | 花卉           |
| Pembroke       | 面包店           |
| Pembroke       | 熟食店             |
| Pembroke       | 生成          |
| Pembroke       | 花卉           |

**事件**列表显示联系人信息以及有关每个事件的信息。 创建日期列作为**日期**列中，但创建的其他列**单行文本**列，以便简化配置并避免[委派](./delegation-overview.md)中的警告Microsoft PowerApps。

| 第一个名称 | 最后一个名称 | 电话号码     | Location | Department | 描述       | Date      |
|------------|-----------|------------------|----------------|------------|-------------------------|-----------|
| Tonya       | Cortez   | (206) 555 - 1022 | Eganville      | 生成    | 我在遇到了问题...   | 2/12/2019 |
| Moses     | Laflamme     | (425) 555 - 1044 | Renfrew        | 花卉     | 我遇到了问题... | 2/13/2019 |

默认情况下，包括自定义 SharePoint 列表**标题**列不能重命名或删除，并且它必须包含的数据，然后才能保存一个项列表中。 若要配置列，以便它不需要的数据：

1. 右上角附近选择齿轮图标，然后选择**列出设置**。
1. 上**设置**页上，选择**标题**列列表中。
1. 下**要求此列包含信息**，选择**否**。

该更改后，可以忽略**标题**列中，或者也可以[将其删除](https://support.office.com/article/edit-a-list-column-in-sharepoint-online-77130c2e-76d1-4f80-af8b-4c6f47b264b8)如果至少一个其他列显示的默认视图。

## <a name="open-the-form"></a>打开窗体

1. 打开**事件**列表，并选择**PowerApps** > **自定义窗体**。

    > [!div class="mx-imgBorder"]
    > ![打开事件列表中，并选择 PowerApps > 自定义窗体。](./media/dependent-drop-down-lists/open-form.png "打开事件列表中，并选择 PowerApps > 自定义窗体。")

    使用 PowerApps Studio 中的默认窗体打开一个浏览器选项卡。

1. （可选）在中**字段**窗格中，悬停**标题**字段中，选择省略号 （...），将出现，然后选择**删除**。

    如果已关闭**字段**窗格中，您可以再次打开它通过选择**SharePointForm1**在左侧的导航栏中，然后选择**编辑字段**上**属性**的右侧窗格的选项卡。

1. （可选）重复上述步骤以删除**附件**字段从窗体。

    只需将你添加的字段，会显示在窗体。

    > [!div class="mx-imgBorder"]
    > ![窗体没有标题和附件字段](./media/dependent-drop-down-lists/default-form.png)

## <a name="replace-the-controls"></a>替换的控件

1. 在中**字段**窗格中，选择箭头旁边**位置**。

    如果已关闭**字段**窗格中，您可以再次打开它通过选择**SharePointForm1**在左侧的导航栏中，然后选择**编辑字段**上**属性**的右侧窗格的选项卡。

1. 打开**控件类型**列表，并选择**允许值**。

    > [!div class="mx-imgBorder"]
    > ![允许的值](./media/dependent-drop-down-lists/change-control.png)

    输入的机制将变为**下拉列表**控件。

1. 重复这些步骤**部门**卡。

## <a name="add-the-locations-list"></a>添加位置列表

1. 选择**视图** > **数据源** > **添加数据源**。

1. 选择或创建 SharePoint 的连接，，然后指定包含的站点**位置**列表。

1. 选择该列表中，该复选框，然后选择**Connect**。

    > [!div class="mx-imgBorder"]
    > ![“数据”窗格](./media/dependent-drop-down-lists/select-list.png)

    连接显示的列表**事件**列表中，基于窗体和**位置**列表中，它将识别位置和窗体中的部门。

    > [!div class="mx-imgBorder"]
    > ![SharePoint 数据源](./media/dependent-drop-down-lists/data-sources.png)

## <a name="unlock-the-cards"></a>解锁卡

1. 选择**位置**卡，选择**高级**在右侧窗格中，选项卡，然后选择**解锁以更改属性**。

1. 重复上一步**部门**卡。

## <a name="rename-the-controls"></a>这些控件重命名

如果重命名您的控件，可以更轻松地识别和的示例是易于遵循。 若要发现其他最佳做法，请查看[编码标准和指导原则白皮书](https://aka.ms/powerappscanvasguidelines)。

1. 在中**位置**卡，选择**下拉列表**控件。

1. 在右侧窗格顶部附近将控件重命名所选通过键入或粘贴**ddLocation**。

    > [!div class="mx-imgBorder"]
    > ![重命名控件](./media/dependent-drop-down-lists/rename-control.png)

1. 重复前面的两个步骤**部门**卡重命名**下拉列表**控制对**ddDepartment**。

## <a name="configure-the-locations"></a>配置的位置

1. 设置**项**的属性**ddlocation**为以下公式：

    `Distinct(Locations, Location)`

1. （可选）按住 Alt 键，同时打开**ddLocation**，并确认该列表显示三个位置。

## <a name="configure-the-departments"></a>配置部门

1. 选择**ddDepartment**，然后在**属性**选项卡的右侧窗格中，选择**取决于。**

1. 下**控件的父级**，，请确保**ddLocation**出现在上面的列表和**结果**将出现在较低的列表。

    > [!NOTE]
    > 如果不想要匹配的字符串，但实际的数据行的 id，请选择**ID**而不是**结果**。

1. 下**匹配字段**，选择**位置**在上面的列表中，选择**位置**在下方的列表，然后选择**应用**。

    > [!div class="mx-imgBorder"]
    > ![取决于链接](./media/dependent-drop-down-lists/depends-on.png)

    **项**的属性**ddDepartment**设置为以下公式：

    `Filter(Locations, Location = ddLocation.Selected.Result)`

    此公式筛选中的项**ddDepartment**基于用户选择在**ddLocation**。 此类配置可确保部门的"子"列表以反映其"父级"位置的数据**位置**SharePoint 列表中的指定。

1. 上**属性**选项卡的右侧窗格中，打开列表旁边**值**，然后选择**部门**。

    此步骤中将显示文本设置为中的选项**部门**的列**位置**SharePoint 列表中的。

    > [!div class="mx-imgBorder"]
    > ![部门值](./media/dependent-drop-down-lists/dept-value.png)

## <a name="test-the-form"></a>测试窗体

而按下 Alt 键，打开的位置的列表，请选择其中一个，打开的部门，列表，然后选择一个。

位置和部门的列表中的信息将反映**位置**SharePoint 列表中的。

> [!div class="mx-imgBorder"]
> ![打开的位置的列表，将所选内容从 Renfrew 更改为 Pembroke，并打开部门列表](./media/dependent-drop-down-lists/dropdowns.gif)

## <a name="save-and-open-the-form-optional"></a>保存并打开窗体 （可选）

1. 打开**文件**菜单，并选择**保存** > **发布到 SharePoint** > **发布到 SharePoint**.

1. 在左上角，选择返回箭头，然后选择“返回 SharePoint”。

1. 在命令栏中，选择“新建”打开自定义窗体。

## <a name="faq"></a>常见问题

**我无法查看任何数据： 源均为空白或有错误的数据。**
确认是否要为您在任一种方式中的控件来显示正确的字段：

- 选择下拉列表，并选择**值**属性中的**属性**的右侧窗格的选项卡。

    > [!div class="mx-imgBorder"]
    > ![更改下拉列表](./media/dependent-drop-down-lists/drop-down-display-field.png)

- 选择一个组合框，并确保主要文本为你想要显示的字段。

    > [!div class="mx-imgBorder"]
    > ![更改组合框](./media/dependent-drop-down-lists/combo-box-display-field.png)

**我子下拉列表包含重复的项。**
此症状可能是由于使用**查找**在 SharePoint 中的列或**选择**PowerApps 中的函数。 若要移除重复项，包装**Distinct**正确返回数据的函数。 详细信息：[Distinct 函数](functions/function-distinct.md)。

## <a name="known-limitations"></a>已知的限制

此配置是可在上找到**下拉列表**控件，以及**组合框**并**列表框**允许一次一个的所选内容的控件。 不能使用**依赖**任何这些控件允许选择多个配置。 此方法不建议使用的选项集通用数据服务。

**依赖**配置不支持静态数据或集合。 若要配置这些源依赖下拉列表，请编辑直接在公式栏中的表达式。 此外，PowerApps 不支持使用而无需任何匹配的表的数据，在 SharePoint 中的两个选择字段并不能定义**匹配字段**此 UI 中。
