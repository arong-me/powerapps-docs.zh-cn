---
title: 自定义 SharePoint 列表窗体 | Microsoft Docs
description: 使用 PowerApps 自定义窗体，供用户创建和更新 SharePoint 列表中的条目。
author: AFTOwen
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 06/11/2018
ms.author: anneta
ms.openlocfilehash: 3e552d9338c457ba6076e0f34c91311e54d0c18d
ms.sourcegitcommit: dfa0e1a7981814e15e6ca4720e2a5f930e859db1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/13/2018
ms.locfileid: "39019126"
---
# <a name="customize-a-sharepoint-list-form-by-using-powerapps"></a>使用 PowerApps 自定义 SharePoint 列表窗体

在浏览器中打开 PowerApps，可轻松自定义 SharePoint 列表窗体。 不必编写传统代码（例如 C#）或下载其他应用（例如 InfoPath）。 发布更改时，窗体嵌入到 SharePoint 列表中，供其所有用户使用。 在 PowerApps 中，还可查看分析报告、轻松创建条件格式、连接到其他数据源。

若要按照本主题中的步骤操作，请创建一个简单列表，了解自定义的工作原理，然后可将相同的概念应用到你自己的列表。

> [!NOTE]
> 如果“自定义窗体”选项不可用或对你的列表无效，则它可能包含[ PowerApps 不支持](connections/connection-sharepoint-online.md#known-issues)的数据类型。 此外，不能将窗体移到其他列表或[环境](working-with-environments.md)。

## <a name="prerequisites"></a>先决条件

在 SharePoint 站点上创建包含以下列的列表：

- **ProductName**（单行文本）
- **Details**（是/否）
- **Price**（货币）
- **Availability**（不含时间的日期）
- **Color**（选项）

## <a name="open-the-form-in-powerapps"></a>在 PowerApps 中打开窗体

1. 打开你创建的列表，然后在命令栏中选择“新建”。

    窗体将会打开，并显示你添加的字段，以及 Title 和 Attachments。

1. 在窗体顶部附近，选择“自定义”。

    PowerApps Studio 在同一个浏览器选项卡中打开。

1. 如果打开“欢迎使用 PowerApps Studio”对话框，则选择“跳过”。

## <a name="hide-extra-fields"></a>隐藏额外字段

在屏幕中央，PowerApps 会显示你的窗体，但它包含你可能不想显示的字段。

- 在“数据”窗格中，清除这些字段的复选框。

  - **Title**
  - **Modified**
  - **Created**
  - **Created By**
  - **Modified By**
  - **ID**

    这些字段会从窗体中消失，只留下你创建的字段。

    ![字段列表](./media/customize-list-form/field-list.png)

## <a name="set-conditional-formatting"></a>条件格式设置

仅当 Details 设置为“是”时，才能将 Price、Availability 和 Colors 字段配置为显示出来。

1. 通过单击或点击选择 Price 卡。

    ![选择 Availability 卡](./media/customize-list-form/select-card.png)

1. 在属性列表中，选择“Visible”。

    ![选择 Visible 属性](./media/customize-list-form/select-property.png)

1. 在编辑栏中，键入或粘贴以下公式：

    **If(DataCardValue3.Value = true, true)**

    ![设置 Visible 属性的值](./media/customize-list-form/build-formula.png)

1. 对 Availablity 和 Color 卡重复最后三个步骤。

1. 按住 Alt 键，（通过单击或点击）多次选择 Details 开关。

    你配置的三个字段将在窗体中显示和消失。

1. （可选）用其他多种方法自定义窗体，包括：

    - 更改其大小和/或方向（例如，[加宽窗体](set-aspect-ratio-portrait-landscape.md)）。
    - 添加一个控件，以便用户可以[上传附件](controls/properties-text.md)。
    - 创建[查找字段](sharepoint-lookup-fields.md)。

## <a name="save-publish-and-show-the-form"></a>保存、发布和显示窗体

1. 打开“文件”菜单，选择“保存”，然后选择“发布到 SharePoint”两次。

1. 在左上角，选择返回箭头，然后选择“返回 SharePoint”。

1. 在命令栏中，选择“新建”打开自定义窗体。

1. 多次选择“Details”开关，隐藏和显示最后三个字段。

若要[进一步自定义窗体](sharepoint-form-integration.md)，请打开它，在窗体顶部附近选择“自定义”，然后进行、保存和发布更改。

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

## <a name="q--a"></a>问题解答

### <a name="forms-vs-apps"></a>窗体与应用

问：自定义窗体与从 SharePoint 或 PowerApps 创建的独立应用有何区别？

答：如果为 SharePoint 列表自定义窗体，窗体不会在 PowerApps Studio 或 PowerApps Mobile 中显示为应用。 只能从为其创建窗体的列表打开该窗体。

问：何时应自定义窗体以管理 SharePoint 列表中的数据，何时应创建独立应用？

答：如果希望用户无需离开 SharePoint 即可管理数据（例如在桌面浏览器中），请自定义表单。 如果你希望用户在 SharePoint 外部（例如在移动设备上）管理数据，请创建应用。

问：对于同一列表，可以既自定义窗体又创建应用吗？

答：可以。

问：可以使用相同功能自定义窗体和创建应用吗？

答：可以。

问：可以在组织中的默认环境之外自定义窗体吗？

**答：** 不能。

### <a name="manage-your-custom-form"></a>管理自定义窗体

问：如何轻松与他人共享我的窗体？

答：打开窗体，选择“复制链接”，并将链接发送给你希望其使用窗体的任何人。

问：能否更新窗体，而不让其他人看到我的更改？

答：可以。 可以根据需要多次进行更改和保存，但所做的更改对其他人不可见，除非你两次选择“发布到 SharePoint”。

问：如果我自定义列表窗体但出现一个错误，是否可以还原到以前的版本？

答：可以。

1. 打开列表，在命令栏上选择“PowerApps”，然后选择“自定义窗体”。

1. 在 PowerApps Studio 中，选择“文件”，然后选择“查看所有版本”。 “版本”页将在新的浏览器选项卡中打开。

    > [!NOTE]
    > 如果看不到“查看所有版本”按钮，请选择“保存”。 应会显示此按钮。

1. 无需关闭“版本”页或浏览器选项卡，返回到其他浏览器选项卡中的“保存”页，单击或点击左侧导航窗格顶部的箭头，然后单击或点击“返回 SharePoint”来解锁窗体，并关闭 PowerApps Studio。

1. 返回到其他浏览器选项卡中的“版本”页，找到你想要还原的版本，然后选择“还原”。

    > [!NOTE]
    > 如果收到一条错误消息，指示由于窗体被另一个用户锁定而导致还原失败，请等待用户解锁窗体，然后重试。

问：能否将窗体从一个列表移动到另一个列表？

**答：** 不能。

### <a name="administer-your-custom-form"></a>管理自定义窗体

问：如何共享窗体？

答：无需共享窗体 - 窗体从 SharePoint 列表继承权限。 完成自定义后，只需[将其发布回 SharePoint](customize-list-form.md#save-and-publish-the-list-form-back-to-sharepoint)，便可供其他人使用。

问：谁可以自定义窗体？

答：任何具有 SharePoint 权限的人员都可以管理、设计或编辑关联的列表。

**问：** 是否需要使用 PowerApps 许可证才能创建或使用自定义列表表单？

答：需要[包含 PowerApps 的 Office 365 计划](../../administrator/pricing-billing-skus.md#licenses)。

问：当来宾用户访问具有自定义窗体的列表时，会发生什么情况？

答：如果来宾用户尝试访问已使用 PowerApps 自定义的列表窗体，将会收到一条错误消息。

问：作为管理员，如何在组织中获取所有自定义窗体列表？

答：如果你是 PowerApps 的租户管理员，或者对组织的默认 PowerApps 环境具有环境管理员权限，请执行以下操作：

1. 在 [PowerApps 管理中心](https://admin.powerapps.com)，从环境列表中选择组织的默认环境。

1. 在默认环境页顶部，选择“资源”。

1. 从应用的列表中，查找应用类型为 SharePoint 窗体的应用 - 这些是自定义窗体。

    ![自定义窗体列表](./media/customize-list-form/all-customized-forms.png)
