---
title: 自定义 SharePoint 列表窗体 | Microsoft Docs
description: 使用 Power Apps 自定义用户在 SharePoint 列表中创建和更新条目的窗体。
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 10/24/2019
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 61cf2ad5926daf8b1b5bea6310b9fb29563208e2
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74731700"
---
# <a name="customize-a-sharepoint-list-form-by-using-power-apps"></a>使用 Power Apps 自定义 SharePoint 列表窗体

可以通过在浏览器中打开 Power Apps 来轻松地自定义 SharePoint 列表的窗体。 不必编写传统代码（例如 C#）或下载其他应用（例如 InfoPath）。 发布更改时，窗体嵌入到 SharePoint 列表中，供其所有用户使用。 在 Power Apps 中，你还可以查看分析报表、轻松创建条件格式以及连接到其他数据源。

若要按照本主题中的步骤操作，请创建一个简单列表，了解自定义的工作原理，然后可将相同的概念应用到你自己的列表。

> [!NOTE]
> - 如果 "**自定义窗体**" 选项不可用或不能正常用于列表，则它可能包含[Power Apps 不支持](connections/connection-sharepoint-online.md#known-issues)的数据类型。 此外，不能将窗体移到其他列表或[环境](working-with-environments.md)。 
> - 仅在泛型列表中支持列表的自定义窗体。 即将推出对一般文档库的支持。 当前不支持自定义列表和库模板;包括但不限于公告、联系人和任务等列表。

## <a name="create-a-list"></a>创建列表

在 SharePoint 站点上创建一个列表，然后将这些列添加到该列表中：

- **Details**（是/否）
- **Price**（货币）
- **Availability**（不含时间的日期）
- **Color**（选项）

> [!div class="mx-imgBorder"]
> !["> 新 >" 列表中选择 "站点内容"，键入列表名称，然后选择 "创建"。 对于每个列，选择 "添加列"，指定列表类型（"是/否"、"货币"、"日期"、"选项"），指定列表名称（详细信息、价格、可用性、颜色），然后选择 "保存"。](./media/customize-list-form/create-list.gif)

## <a name="open-the-form"></a>打开窗体

1. 在命令栏中，选择 " **PowerApps**"，然后选择 "**自定义窗体**"。

    Power Apps Studio 在同一浏览器选项卡中打开。

1. 如果 "**欢迎使用 Power Apps Studio** " 对话框打开，请选择 "**跳过**"。

> [!div class="mx-imgBorder"]
> ![在命令栏中，选择 "电源应用"，然后选择 "自定义窗体"。 Power Apps Studio 在同一浏览器选项卡中打开。如果 "欢迎使用 Power Apps Studio" 对话框打开，请选择 "跳过"。](./media/customize-list-form/create-form.gif)

## <a name="move-and-remove-a-field"></a>移动和删除字段

1. 将 "**可用性**" 字段拖到字段列表的底部。

    这些字段按您指定的顺序显示。

1. 将鼠标悬停在 "**附件**" 字段上，选择显示的省略号（...），然后选择 "**删除**"。

    您指定的字段将从窗体中消失。

> [!div class="mx-imgBorder"]
> ![将 "可用性" 字段拖到字段列表的底部。 将鼠标悬停在 "附件" 字段上，选择显示的省略号（...），然后选择 "删除"。](./media/customize-list-form/move-remove-fields.gif)

## <a name="set-conditional-formatting"></a>条件格式设置

仅当 Details 设置为“是”时，才能将 Price、Availability 和 Colors 字段配置为显示出来。

1. 在左侧导航栏中，展开 " **Details_DataCard1**"，并记下**DataCardValue**末尾显示的数字。

1. 将**颜色**、**可用性**和**价格**卡的**Visible**属性设置为此公式（如有必要，请将数字替换为上一步中记下的数字）：

    **If （DataCardValue2 = true，true）**

1. 按住 Alt 键，（通过单击或点击）多次选择 Details 开关。

    你配置的三个字段将在窗体中显示和消失。

> [!div class="mx-imgBorder"]
> ![在左侧导航栏中，记下 DataCardValue 末尾显示的数字。 将颜色、可用性和价格卡的 "可见性" 属性设置为此公式。 按下 Alt 键，并多次选择详细信息控件。](./media/customize-list-form/conditional-format.gif)

## <a name="save-and-publish-the-form"></a>保存并发布窗体

1. 打开“文件”菜单，选择“保存”，然后选择“发布到 SharePoint”两次。

1. 在左上角，选择返回箭头，然后选择“返回 SharePoint”。

> [!div class="mx-imgBorder"]
> ![打开 "文件" 菜单，选择 "保存"，然后选择两次 "发布到 SharePoint"。 在左上角，选择 "返回" 箭头，然后选择 "返回 SharePoint"。](./media/customize-list-form/save-form.gif)

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

    - **使用在 Power Apps 中创建的自定义窗体**-当用户打开列表并在命令栏中选择 "**新建**" 时，将显示自定义窗体。 （作为替代方法，可以在 Power Apps 中再次发布表单。）

    可以根据需要在选项之间反复切换。

    ![窗体设置选项](./media/customize-list-form/form-settings.png)

## <a name="delete-the-custom-form"></a>删除自定义窗体

1. 从 SharePoint 列表中，（通过选择右上角附近的齿轮图标）打开设置页，并选择“列表设置”。

1. 在“常规设置”下，选择“窗体设置”。

1. 在“窗体设置”页上，选择“使用默认 SharePoint 窗体”，然后选择“删除自定义窗体”。

    ![删除自定义窗体](./media/customize-list-form/use-default-sharepoint.png)

## <a name="q--a"></a>问 &

### <a name="forms-vs-apps"></a>窗体与应用

**问：** 自定义窗体与我从 SharePoint 或 Power Apps 创建的独立应用程序有何不同？

**答：** 如果自定义 SharePoint 列表的窗体，该窗体将不会在 Power Apps Studio 或 Power Apps Mobile 中显示为应用。 只能从为其创建窗体的列表打开该窗体。

问：何时应自定义窗体以管理 SharePoint 列表中的数据，何时应创建独立应用？

答：如果希望用户无需离开 SharePoint 即可管理数据（例如在桌面浏览器中），请自定义表单。 如果你希望用户在 SharePoint 外部（例如在移动设备上）管理数据，请创建应用。

问：对于同一列表，可以既自定义窗体又创建应用吗？

答：相同。

问：可以使用相同功能自定义窗体和创建应用吗？

答：相同。

问：可以在组织中的默认环境之外自定义窗体吗？

**答：** 不能。

### <a name="manage-your-custom-form"></a>管理自定义窗体

问：如何轻松与他人共享我的窗体？

**答：** 打开窗体，选择 "**复制链接**"，然后向要使用窗体的任何人发送链接。

问：能否更新窗体，而不让其他人看到我的更改？

答：相同。 可以根据需要多次进行更改和保存，但所做的更改对其他人不可见，除非你两次选择“发布到 SharePoint”。

问：如果我自定义列表窗体但出现一个错误，是否可以还原到以前的版本？

答：相同。

1. 打开列表，在命令栏上选择“PowerApps”，然后选择“自定义窗体”。

1. 在 Power Apps Studio 中，选择 "**文件**"，然后选择 "**查看所有版本**"。 “版本”页将在新的浏览器选项卡中打开。

    > [!NOTE]
    > 如果看不到“查看所有版本”按钮，请选择“保存”。 应会显示此按钮。

1. 如果没有关闭 "**版本**" 页或浏览器选项卡，请返回到其他浏览器选项卡中的 "**保存**" 页，单击或点击左侧导航窗格顶部的箭头，然后单击或点击 "**返回 SharePoint** " 来解锁窗体并关闭 Power Apps Studio。

1. 返回到其他浏览器选项卡中的“版本”页，找到你想要还原的版本，然后选择“还原”。

    > [!NOTE]
    > 如果收到一条错误消息，指出由于窗体被其他用户锁定而导致还原失败，请等待用户解除窗体锁定，然后重试。

问：能否将窗体从一个列表移动到另一个列表？

**答：** 不能。

### <a name="administer-your-custom-form"></a>管理自定义窗体

问：如何共享窗体？

**答：** 不需要共享窗体，该窗体从 SharePoint 列表继承权限。 完成自定义后，只需[将其发布回 SharePoint](customize-list-form.md#save-and-publish-the-form)，便可供其他人使用。

问：谁可以自定义窗体？

答：任何具有 SharePoint 权限的人员都可以管理、设计或编辑关联的列表。

**问：** 是否需要使用 Power Apps 许可证来创建或使用自定义列表窗体？

**答：** 需要[包含电源应用的 Office 365 计划](https://docs.microsoft.com/power-platform/admin/pricing-billing-skus#licenses)。

问：当来宾用户访问具有自定义窗体的列表时，会发生什么情况？

**答：** 如果来宾用户尝试访问已使用 Power Apps 自定义的列表窗体，会收到一条错误消息。

问：作为管理员，如何在组织中获取所有自定义窗体列表？

**答：** 如果你是适用于你的 Power Apps 的租户管理员，或者你对你的组织的默认电源应用环境具有环境管理员权限，请执行以下操作：

1. 在[Power Apps 管理中心](https://admin.powerapps.com)的环境列表中，选择你的组织的默认环境。

1. 在默认环境页顶部，选择“资源”。

1. 在应用列表中，查找具有**SharePoint 窗体**应用类型的应用-这些是自定义窗体。

    ![自定义窗体列表](./media/customize-list-form/all-customized-forms.png)
