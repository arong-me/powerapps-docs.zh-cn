---
title: 自定义 SharePoint 列表窗体 | Microsoft Docs
description: 使用 PowerApps 自定义窗体，供用户创建和更新 SharePoint 列表中的条目。
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 04/04/2019
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 60d4fb21bc2f298b1dd2ce37c3e25f5355e881cb
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/07/2019
ms.locfileid: "71993132"
---
# <a name="customize-a-sharepoint-list-form-by-using-powerapps"></a>使用 PowerApps 自定义 SharePoint 列表窗体

在浏览器中打开 PowerApps，可轻松自定义 SharePoint 列表窗体。 不必编写传统代码（例如 C#）或下载其他应用（例如 InfoPath）。 发布更改时，窗体嵌入到 SharePoint 列表中，供其所有用户使用。 在 PowerApps 中，还可查看分析报告、轻松创建条件格式、连接到其他数据源。

若要按照本主题中的步骤操作，请创建一个简单列表，了解自定义的工作原理，然后可将相同的概念应用到你自己的列表。

> [!NOTE]
> 如果“自定义窗体”选项不可用或对你的列表无效，则它可能包含[ PowerApps 不支持](connections/connection-sharepoint-online.md#known-issues)的数据类型。 此外，不能将窗体移到其他列表或[环境](working-with-environments.md)。

## <a name="create-a-list"></a>创建列表

在 SharePoint 站点上创建一个列表，然后将这些列添加到该列表中：

- **Details**（是/否）
- **Price**（货币）
- **Availability**（不含时间的日期）
- **Color**（选项）

> [!div class="mx-imgBorder"]
> @no__t "> 新 >" 列表中的 "网站内容"，键入列表名称，然后选择 "创建"。 对于每个列，选择 "添加列"，指定列表类型（"是/否"、"货币"、"日期"、"选项"），指定列表名称（详细信息、价格、可用性、颜色），然后选择 "保存"。 ](./media/customize-list-form/create-list.gif)

## <a name="open-the-form"></a>打开窗体

1. 在命令栏中，选择 " **PowerApps**"，然后选择 "**自定义窗体**"。

    PowerApps Studio 在同一个浏览器选项卡中打开。

1. 如果打开“欢迎使用 PowerApps Studio”对话框，则选择“跳过”。

> [!div class="mx-imgBorder"]
> @no__t 0In 命令栏中，选择 "PowerApps"，然后选择 "自定义窗体"。 PowerApps Studio 在同一个浏览器选项卡中打开。如果 "欢迎使用 PowerApps Studio" 对话框打开，请选择 "跳过"。 ](./media/customize-list-form/create-form.gif)

## <a name="move-and-remove-a-field"></a>移动和删除字段

1. 将 "**可用性**" 字段拖到字段列表的底部。

    这些字段按您指定的顺序显示。

1. 将鼠标悬停在 "**附件**" 字段上，选择显示的省略号（...），然后选择 "**删除**"。

    您指定的字段将从窗体中消失。

> [!div class="mx-imgBorder"]
> ![Drag 字段列表底部的 "可用性" 字段。 将鼠标悬停在 "附件" 字段上，选择显示的省略号（...），然后选择 "删除"。 ](./media/customize-list-form/move-remove-fields.gif)

## <a name="set-conditional-formatting"></a>条件格式设置

仅当 Details 设置为“是”时，才能将 Price、Availability 和 Colors 字段配置为显示出来。

1. 在左侧导航栏中，展开 " **Details_DataCard1**"，并记下出现在 " **DataCardValue**" 末尾的数字。

1. 将**颜色**、**可用性**和**价格**卡的**Visible**属性设置为此公式（如有必要，请将数字替换为上一步中记下的数字）：

    **If （DataCardValue2 = true，true）**

1. 按住 Alt 键，（通过单击或点击）多次选择 Details 开关。

    你配置的三个字段将在窗体中显示和消失。

> [!div class="mx-imgBorder"]
> @no__t 左侧导航栏中，记下在 DataCardValue 末尾显示的数字。 将颜色、可用性和价格卡的 "可见性" 属性设置为此公式。 按下 Alt 键，并多次选择详细信息控件。 ](./media/customize-list-form/conditional-format.gif)

## <a name="save-and-publish-the-form"></a>保存并发布窗体

1. 打开“文件”菜单，选择“保存”，然后选择“发布到 SharePoint”两次。

1. 在左上角，选择返回箭头，然后选择“返回 SharePoint”。

> [!div class="mx-imgBorder"]
> @no__t 0Open "文件" 菜单上，选择 "保存"，并选择 "发布到 SharePoint" 两次。 在左上角，选择 "返回" 箭头，然后选择 "返回到 SharePoint"。 ](./media/customize-list-form/save-form.gif)

## <a name="further-customize-your-form"></a>进一步自定义窗体

1. 打开列表，在命令栏中选择 "**新建**"，然后选择窗体顶部附近的 "**自定义**"。

1. 以各种方式自定义窗体，例如这些主题所描述的内容：

    - 更改其大小和/或方向（例如，[加宽窗体](set-aspect-ratio-portrait-landscape.md)）。
    - [自定义一个或多个卡](working-with-cards.md)（例如，更改卡的显示文本或输入控件）。
    - 创建[查找字段](sharepoint-lookup-fields.md)。

    详细信息：[了解 SharePoint 窗体集成](sharepoint-form-integration.md)。

## <a name="use-the-default-form"></a>使用默认窗体

1. 从 SharePoint 列表中，（通过选择右上角附近的齿轮图标）打开设置页，并选择“列表设置”。

2. 在“常规设置”下，选择“窗体设置”。

3. 在“窗体设置”页上，选择以下选项之一，然后选择“确定”。

    - **使用默认 SharePoint 窗体** - 当用户打开你的列表并在命令栏中选择“新建”时，将显示该列表的默认窗体。

    - **使用在 PowerApps 中创建的自定义窗体** - 当用户打开你的列表并在命令栏中选择“新建”时，将显示自定义窗体。 （或者，可以在 PowerApps 中再次发布窗体。）

    可以根据需要在选项之间反复切换。

    ![窗体设置选项](./media/customize-list-form/form-settings.png)

## <a name="delete-the-custom-form"></a>删除自定义窗体

1. 从 SharePoint 列表中，（通过选择右上角附近的齿轮图标）打开设置页，并选择“列表设置”。

1. 在“常规设置”下，选择“窗体设置”。

1. 在“窗体设置”页上，选择“使用默认 SharePoint 窗体”，然后选择“删除自定义窗体”。

    ![删除自定义窗体](./media/customize-list-form/use-default-sharepoint.png)

## <a name="q--a"></a>问 &AMP;

### <a name="forms-vs-apps"></a>窗体与应用

**：** 自定义窗体与我从 SharePoint 或 PowerApps 创建的独立应用程序有何不同？

**的**如果自定义 SharePoint 列表的窗体，则该窗体将不会在 PowerApps Studio 或 PowerApps Mobile 中显示为应用程序。 只能从为其创建窗体的列表打开该窗体。

**：** 何时应自定义窗体来管理 SharePoint 列表中的数据，以及何时创建独立应用？

**的**如果希望用户在不离开 SharePoint 的情况下（例如在桌面浏览器中）管理数据，请自定义窗体。 如果你希望用户在 SharePoint 外部（例如在移动设备上）管理数据，请创建应用。

**：** 能否为同一列表自定义表单和创建应用？

**的**可以。

**：** 能否自定义列表并使用相同的功能创建应用？

**的**可以。

**：** 我是否可以在组织中的默认环境以外的环境中自定义窗体？

**的**不。

### <a name="manage-your-custom-form"></a>管理自定义窗体

**：** 如何轻松地与他人共享我的窗体？

**的**打开窗体，选择 "**复制链接**"，然后向要使用窗体的任何人发送链接。

**：** 能否更新窗体，而不会使更改对其他人可见？

**的**可以。 可以根据需要多次进行更改和保存，但所做的更改对其他人不可见，除非你两次选择“发布到 SharePoint”。

**：** 如果自定义列表窗体并犯了错误，能否恢复到以前的版本？

**的**可以。

1. 打开列表，在命令栏上选择“PowerApps”，然后选择“自定义窗体”。

1. 在 PowerApps Studio 中，选择“文件”，然后选择“查看所有版本”。 “版本”页将在新的浏览器选项卡中打开。

    > [!NOTE]
    > 如果看不到“查看所有版本”按钮，请选择“保存”。 应会显示此按钮。

1. 无需关闭“版本”页或浏览器选项卡，返回到其他浏览器选项卡中的“保存”页，单击或点击左侧导航窗格顶部的箭头，然后单击或点击“返回 SharePoint”来解锁窗体，并关闭 PowerApps Studio。

1. 返回到其他浏览器选项卡中的“版本”页，找到你想要还原的版本，然后选择“还原”。

    > [!NOTE]
    > 如果收到一条错误消息，指出由于窗体被其他用户锁定而导致还原失败，请等待用户解除窗体锁定，然后重试。

**：** 是否可以将窗体从一个列表移到另一个列表？

**的**不。

### <a name="administer-your-custom-form"></a>管理自定义窗体

**：** 如何实现共享我的窗体？

**的**不需要共享窗体，该窗体从 SharePoint 列表继承权限。 完成自定义后，只需[将其发布回 SharePoint](customize-list-form.md#save-and-publish-the-form)，便可供其他人使用。

**：** 谁可以自定义窗体？

**的**具有 SharePoint 权限的任何用户管理、设计或编辑关联列表。

**：** 是否需要 PowerApps 许可证来创建或使用自定义列表窗体？

**的**需要[包含 PowerApps 的 Office 365 计划](https://docs.microsoft.com/power-platform/admin/pricing-billing-skus#licenses)。

**：** 当来宾用户访问具有自定义窗体的列表时会发生什么情况？

**的**如果来宾用户尝试访问已使用 PowerApps 自定义的列表窗体，会收到一条错误消息。

**：** 作为管理员，我如何获取组织中所有自定义窗体的列表？

**的**如果你是 PowerApps 的租户管理员，或者你对组织的默认 PowerApps 环境具有环境管理员权限，请执行以下操作：

1. 在 [PowerApps 管理中心](https://admin.powerapps.com)，从环境列表中选择组织的默认环境。

1. 在默认环境页顶部，选择“资源”。

1. 在应用列表中，查找具有**SharePoint 窗体**应用类型的应用-这些是自定义窗体。

    ![自定义窗体列表](./media/customize-list-form/all-customized-forms.png)
