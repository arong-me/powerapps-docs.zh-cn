---
title: 在画布应用中创建依赖项下拉列表 |Microsoft Docs
description: 在 PowerApps 中，创建一个下拉列表，用于筛选画布应用中的其他下拉列表。
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/04/2019
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 57abde44541a2a1e40e3a8ffc55a89e37a8c6478
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/07/2019
ms.locfileid: "71985749"
---
# <a name="create-dependent-drop-down-lists-in-a-canvas-app"></a>在画布应用中创建依赖项下拉列表

创建从属（或级联）下拉列表时，用户可以在列表中选择一个选项来筛选其他列表中的选项。 许多组织创建相关列表，以帮助用户更有效地填写表单。 例如，用户可能会选择国家或地区来筛选城市列表，或者用户可能选择类别来仅显示该类别中的代码。

作为最佳做法，请在 "父" 和 "子" 列表（例如，国家/地区和城市）中为值创建数据源，该数据源不同于用户使用该应用程序更新的数据源。 如果采用这种方法，则可以在多个应用程序中使用相同的父数据和子数据，并且可以更新这些数据，而无需重新发布使用这些数据的应用程序或应用。 您可以通过使用集合或静态数据来实现相同的结果，但不建议将其用于企业方案。

对于本主题中的方案，商店员工可以通过表单向**事件**列表提交问题。 员工不仅指定发生事件的商店的位置，还指定该位置中的部门。 并非所有位置都具有相同的部门，因此**位置**列表可确保员工不能为没有该部门的位置指定部门。

本主题使用 Microsoft SharePoint 列表作为数据源，但所有表格数据源的工作方式都相同。

## <a name="create-data-sources"></a>创建数据源

"**位置**" 列表显示每个位置处的部门。

| Location | Department |
|----------------|------------------|
| Eganville      | 面包店           |
| Eganville      | 传递             |
| Eganville      | 制品          |
| Renfrew        | 面包店           |
| Renfrew        | 传递             |
| Renfrew        | 制品          |
| Renfrew        | 药房         |
| Renfrew        | 花卉           |
| Pembroke       | 面包店           |
| Pembroke       | 传递             |
| Pembroke       | 制品          |
| Pembroke       | 花卉           |

"**事件**列表" 显示有关每个事件的联系信息和信息。 创建日期列作为**日期**列，但将其他列创建为**单行文本**列以简化配置，并避免在 Microsoft PowerApps 中产生[委托](./delegation-overview.md)警告。

| 名字 | 姓氏 | 电话号码     | Location | Department | 描述       | Date      |
|------------|-----------|------------------|----------------|------------|-------------------------|-----------|
| Tonya       | Cortez   | （206） 555-1022 | Eganville      | 制品    | 我遇到了问题 。   | 2/12/2019 |
| Moses     | Laflamme     | （425） 555-1044 | Renfrew        | 花卉     | 我遇到了问题 。 | 2/13/2019 |

默认情况下，自定义 SharePoint 列表包含您无法重命名或删除的**标题**列，并且它必须包含数据，才能在列表中保存项。 配置列以使其不需要数据：

1. 在右上角附近，选择齿轮图标，然后选择 "**列表设置**"。
1. 在 "**设置**" 页上，选择列列表中的 "**标题**"。
1. 在 "**要求此列包含信息**" 下，选择 "**否**"。

在此更改之后，您可以忽略**Title**列，或者，如果至少有一个列出现，则可以将其从默认视图中[删除](https://support.office.com/article/edit-a-list-column-in-sharepoint-online-77130c2e-76d1-4f80-af8b-4c6f47b264b8)。

## <a name="open-the-form"></a>打开窗体

1. 打开**事件**列表，然后选择**PowerApps** > **自定义窗体**。

    > [!div class="mx-imgBorder"]
    > ![打开 "事件" 列表，然后选择 "PowerApps > 自定义窗体"。](./media/dependent-drop-down-lists/open-form.png "打开 \"事件\" 列表，然后选择 \"PowerApps > 自定义窗体\"。")

    此时会打开一个浏览器选项卡，其中包含 PowerApps Studio 中的默认窗体。

1. 可有可无在 "**字段**" 窗格中，将鼠标悬停在 "**标题**" 字段上，选择显示的省略号（...），然后选择 "**删除**"。

    如果已关闭 "**字段**" 窗格，可以通过在左侧导航栏中选择 " **SharePointForm1** "，然后在右侧窗格的 "**属性**" 选项卡上选择 "**编辑字段**"，重新打开它。

1. 可有可无重复上述步骤，从窗体中删除 "**附件**" 字段。

    窗体只显示您添加的字段。

    > [!div class="mx-imgBorder"]
    > 不带 "标题" 和 "附件" 字段 @ no__t-1 的 @no__t 0Form

## <a name="replace-the-controls"></a>替换控件

1. 在 "**字段**" 窗格中，选择 "**位置**" 旁边的箭头。

    如果已关闭 "**字段**" 窗格，可以通过在左侧导航栏中选择 " **SharePointForm1** "，然后在右侧窗格的 "**属性**" 选项卡上选择 "**编辑字段**"，重新打开它。

1. 打开 "**控件类型**" 列表，然后选择 "**允许的值**"。

    > [!div class="mx-imgBorder"]
    > ![Allowed 值 @ no__t-1

    输入机制将更改为**下拉**控件。

1. 为 "**部门**" 卡重复这些步骤。

## <a name="add-the-locations-list"></a>添加位置列表

1. 选择 "**查看** >  个**数据源** > **添加数据源**"。

1. 选择或创建一个 SharePoint 连接，然后指定包含**位置**列表的站点。

1. 选中该列表的复选框，然后选择 "**连接**"。

    > [!div class="mx-imgBorder"]
    > ![Data pane @ no__t-1

    连接列表显示 "事件列表" （窗体基于的**事件**列表）和 "**位置**" 列表，它将在窗体中标识位置和部门。

    > [!div class="mx-imgBorder"]
    > @no__t 0SharePoint 数据源 @ no__t-1

## <a name="unlock-the-cards"></a>解锁卡

1. 选择 "**位置**" 卡，选择右侧窗格中的 "**高级**" 选项卡，然后选择 "**解锁" 以更改属性**。

1. 为 "**部门**" 卡重复前面的步骤。

## <a name="rename-the-controls"></a>重命名控件

如果重命名你的控件，你可以更轻松地识别它们，这些示例更易于理解。 若要了解其他最佳实践，请查看[编码标准和指南白皮书](https://aka.ms/powerappscanvasguidelines)。

1. 在 "**位置**" 卡中，选择**下拉**控件。

1. 在右侧窗格的顶部附近，通过键入或粘贴**ddLocation**来重命名所选的控件。

    > [!div class="mx-imgBorder"]
    > ![Rename a control @ no__t-1

1. 在 "**部门**" 卡中重复上述两个步骤，将**下拉**控件重命名为 " **ddDepartment**"。

## <a name="configure-the-locations"></a>配置位置

1. 将**ddlocation**的**Items**属性设置为以下公式：

    `Distinct(Locations, Location)`

1. 可有可无在按住 Alt 键的同时，打开**ddLocation**，并确认列表显示了三个位置。

## <a name="configure-the-departments"></a>配置部门

1. 选择 " **ddDepartment**"，然后在右侧窗格的 "**属性**" 选项卡上，选择 "**依赖于"。**

1. 在 "**父控件**" 下，确保**ddLocation**出现在上部列表中，**结果**显示在下方的列表中。

    > [!NOTE]
    > 如果您不希望对某个字符串进行匹配，但对该数据行的实际 ID 不匹配，请选择 " **ID**而不是**结果**"。

1. 在 "**匹配字段**" 下 **，选择上部列表中的**"位置"，选择下方列表中的 "**位置**"，然后选择 "**应用**"。

    > [!div class="mx-imgBorder"]
    > 0Depends on link @ no__t-1 @no__t

    **DdDepartment**的**Items**属性设置为以下公式：

    `Filter(Locations, Location = ddLocation.Selected.Result)`

    此公式根据用户在**ddLocation**中选择的内容筛选**ddDepartment**中的项。 此类配置可确保部门的 "子项" 列表反映其 "父" 位置的数据，因为 SharePoint 中的**位置**列表指定。

1. 在右侧窗格的 "**属性**" 选项卡上，打开 "**值**" 旁边的列表，然后选择 "**部门**"。

    此步骤将显示文本设置为 SharePoint 中 "**位置**" 列表的 "**部门**" 列中的选项。

    > [!div class="mx-imgBorder"]
    > ![Department 值 @ no__t-1

## <a name="test-the-form"></a>测试窗体

在按住 Alt 键的同时，打开位置列表，选择一个，打开部门列表，然后选择一个。

位置和部门列表反映了 SharePoint 中 "**位置**" 列表中的信息。

> [!div class="mx-imgBorder"]
> @no__t 0Open 位置列表，将所选内容从 Renfrew 更改为 Pembroke，然后打开部门列表 @ no__t-1

## <a name="save-and-open-the-form-optional"></a>保存并打开窗体（可选）

1. 打开 "**文件**" 菜单，然后选择 "**保存** > "**发布到 sharepoint**" > "**发布到 sharepoint**"。

1. 在左上角，选择返回箭头，然后选择“返回 SharePoint”。

1. 在命令栏中，选择“新建”打开自定义窗体。

## <a name="faq"></a>常见问题

**看不到任何数据：源全部为空白或包含错误数据。**
通过以下方式确认是否要显示控件的正确字段：

- 选择下拉列表，然后在右侧窗格的 "**属性**" 选项卡中选择 "**值**" 属性。

    > [!div class="mx-imgBorder"]
    > ![Change 下拉 @ no__t-1

- 选择组合框，然后确保主文本是要显示的字段。

    > [!div class="mx-imgBorder"]
    > ![Change 组合框 @ no__t-1

**我的子下拉列表包含重复项。**
此症状可能是由于使用 SharePoint 中的**查找**列或 PowerApps 中的**选项**函数导致的。 若要删除复制，请围绕正确返回的数据环绕**不同**的函数。 详细信息：[Distinct 函数](functions/function-distinct.md)。

## <a name="known-limitations"></a>已知的限制

此配置可用于**下拉**控件，以及允许一次选择一项的**组合框**和**列表框**控件。 如果允许多重选择，则不能对这些控件中的任何控件使用**取决**于配置。 对于使用 Common Data Service 中的选项集，不建议使用此方法。

**依赖于**配置不支持静态数据或集合。 若要配置具有这些源的从属下拉列表，请直接在编辑栏中编辑表达式。 此外，PowerApps 不支持在 SharePoint 中使用两个不包含任何匹配数据表的选项字段，也不能在此 UI 中定义**匹配字段**。
