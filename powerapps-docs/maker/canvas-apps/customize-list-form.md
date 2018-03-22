---
title: 使用 PowerApps 自定义 SharePoint 列表窗体 | Microsoft 文档
description: 使用 PowerApps 自定义 SharePoint 中的列表窗体。
services: ''
suite: powerapps
documentationcenter: na
author: skjerland
manager: anneta
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 02/05/2018
ms.author: sharik
ms.openlocfilehash: 62c3050ecee4d068d5417fe3846abb3495990d8b
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2018
---
# <a name="customize-a-sharepoint-list-form-using-powerapps"></a>使用 PowerApps 自定义 SharePoint 列表窗体

现在可以在 PowerApps 中轻松自定义任何 SharePoint 列表窗体。 使用 InfoPath 自定义 SharePoint 列表窗体的大部分操作，现在都可以在 PowerApps 的浏览器中进行内联。 此外，PowerApps 还可以让你执行更多的操作！

PowerApps 与 SharePoint 直接集成 - 无需将另一个应用下载到计算机。 通过 PowerApps，可以创建高度自定义窗体而无需编写任何代码。 发布后，窗体将嵌入 SharePoint 列表，并且可供列表所有用户使用。

而且，由于 PowerApps 无缝集成到 SharePoint 中，因此，无需从两个位置来管理窗体：权限继承自 SharePoint 并在其中托管。 最重要的是，将 PowerApps 与 SharePoint 集成后，你可以访问许多强大的功能，例如分析报告、用于条件格式化的简单点击规则，以及与其他数据源的连接。

准备好开始进行自定义了吗？ 让我们开始吧！

## <a name="create-a-custom-list-form-app-in-powerapps"></a>在 PowerApps 中创建自定义列表窗体应用

> [!NOTE]
> 如果 SharePoint 列表包含 PowerApps 不支持的数据类型，则“自定义窗体”选项将不可用，或者可能无法正常工作。

在 SharePoint 列表中，单击或点击命令栏中的“PowerApps”，然后单击或点击“自定义窗体”。 此操作将使你进入浏览器中适用于 Web 的 PowerApps Studio，其中 PowerApps 会生成单屏幕窗体应用，如下例所示。

![单屏幕窗体应用](./media/customize-list-form/list-form-app.png)

若要随时返回到 SharePoint 列表，请单击或点击适用于 Web 的 PowerApps Studio 左上角的“返回 SharePoint”。

## <a name="customize-the-list-form"></a>自定义列表窗体

PowerApps 提供了多种自定义窗体的方法。 下面是一些示例：

* [更改大小和方向](set-aspect-ratio-portrait-landscape.md)
* [设置文本格式](controls/properties-text.md)
* [添加图像](add-images-pictures-audio-video.md)或[图表](use-line-pie-bar-chart.md)
* [添加自定义数据验证](functions/function-validate.md)
* [添加规则](working-with-rules.md)
* [创建其他视图](https://powerapps.microsoft.com/blog/separate-custom-forms/)

举例来说，假设需要在表单中隐藏“AccountID”字段。

![选择“AccountID”字段](./media/customize-list-form/select-card.png)

在 PowerApps 中隐藏该字段非常简单 - 只需在窗体自定义选项中清除“AccountID”复选框。

![清除“AccountID”复选框](./media/customize-list-form/checkbox.png)

有关如何隐藏字段和更改其他窗体的分步说明，请参阅[在 PowerApps 中自定义窗体](customize-forms-sharepoint.md)。 有关资源的完整列表，请参阅 [Microsoft PowerApps 文档](https://docs.microsoft.com/powerapps/)。

## <a name="save-and-publish-the-list-form-back-to-sharepoint"></a>保存并将列表窗体发布回 SharePoint

1. 完成后，单击或点击“文件”，然后单击或点击“保存”。 此操作会将你所做的更改保存到 PowerApps 窗体应用。

1. 若要将窗体发布回 SharePoint 以便其他人使用，单击或点击“发布到 SharePoint”。 无需担心共享窗体 - 窗体从 SharePoint 列表继承权限。

    ![发布到 SharePoint](./media/customize-list-form/publish-to-sharepoint.png)  

## <a name="view-your-list-form-in-sharepoint"></a>在 SharePoint 中查看列表窗体

1. 若要查看自定义窗体，请单击或点击“返回 SharePoint”，然后单击或点击 SharePoint 列表中的任何项。 窗体在浏览器窗口的右侧以内联方式打开。

    ![在 SharePoint 中以内联方式打开窗体](./media/customize-list-form/list-form-open.png)

1. 如果要[进一步自定义窗体](sharepoint-form-integration.md)，单击或点击“自定义”，然后进行更改。 完成后，请务必保存所做的更改。

    ![“自定义”按钮](./media/customize-list-form/customize-button.png)

    可以根据需要多次进行自定义和保存，但在单击或点击“发布到SharePoint”后，所做的更改才可以在 SharePoint 中看到。

## <a name="toggle-between-using-the-default-sharepoint-form-and-the-custom-form"></a>在使用默认 SharePoint 窗体和自定义窗体之间切换

1. 在 SharePoint 列表中，依次单击或点击“设置”、“列表设置”和“窗体设置”。

1. 在“窗体设置”页上，单击或点击以下内容之一，然后单击或点击“确定”。

    * 使用默认的 SharePoint 窗体 - SharePoint 将对列表使用默认的 SharePoint 窗体。

    * 使用在 PowerApps 中创建的自定义窗体 - SharePoint 将使用你在 PowerApps 中自定义的窗体。 （或者，你也可以在适用于 Web 的 PowerApps Studio 中的“保存”页上重新发布窗体。）

    可以根据需要在选项之间反复切换。

    ![窗体设置选项](./media/customize-list-form/form-settings.png)

## <a name="delete-the-custom-list-form"></a>删除自定义列表窗体

1. 在 SharePoint 列表中，依次单击或点击“设置”、“列表设置”和“窗体设置”。

1. 在“窗体设置”页上，单击或点击“使用默认的 SharePoint 窗体”，然后在“使用在 PowerApps 中创建的自定义窗体”选项下，单击或点击“删除自定义窗体”。 这将删除在 PowerApps 中创建的自定义窗体，并且你的窗体将恢复到默认 SharePoint 窗体。

    ![删除自定义窗体](./media/customize-list-form/use-default-sharepoint.png)

## <a name="top-questions-about-list-form-customization"></a>有关列表窗体自定义的常见问题

### <a name="customizing-forms-versus-creating-apps"></a>自定义窗体和创建应用

问：自定义的列表窗体与我从 SharePoint 或 PowerApps 创建的独立应用有何区别？

答：从 Sharepoint 创建的列表窗体应用是特殊类型的 PowerApps 应用，只能在 SharePoint 列表中使用。 这些列表窗体应用不会出现在适用于 Web 的 PowerApps Studio 或 PowerApps Mobile 的应用列表中，也无法在 SharePoint 列表之外运行它们。

问：应何时创建自定义的列表窗体，以及何时创建独立应用？

答：如果你希望用户使用 SharePoint 访问窗体，并且想要自定义它们创建、查看或编辑列表项的方式，我们建议在 SharePoint 中创建自定义列表窗体。 如果想要为用户创建独立于 SharePoint 网站可以单独使用的完全自定义体验，我们建议创建独立应用。

问：我可以自定义列表窗体并为相同列表创建独立应用吗？

答：可以。 独立应用和自定义列表窗体均相互独立；你可以自定义和单独管理它们。

问：用于自定义列表窗体的自定义功能是否与自定义独立应用的自定义功能相同？

答：相同。 你可以像对独立应用那样[添加和配置控件](add-configure-controls.md)、[连接到可用数据源](add-data-connection.md)，或[添加你自己的数据源](../canvas-apps/register-custom-api.md)。

问：在我的组织中，除了默认环境之外，我还能创建自定义列表窗体吗？

**答：**不能。 当前只能在组织的默认 PowerApps 环境中创建自定义列表窗体；不能在另一个环境中创建自定义列表窗体，也不能将它们迁移到另一个环境。

### <a name="managing-your-custom-list-form"></a>管理自定义列表窗体

问：如何获取可与他人共享的列表窗体的直接链接？

答：在 SharePoint 列表中打开窗体，然后单击或点击“复制链接”。

问：能否更新列表窗体，而不让其他人看到我的更改？

答：可以。 可以根据需要多次进行更改和保存，但所做的更改对其他人不可见，直到你单击或点击[发布到SharePoint](customize-list-form.md#save-and-publish-the-list-form-back-to-sharepoint)。

问：如果我自定义列表窗体但出现一个错误，是否可以还原到以前的版本？

答：可以。 如果你对窗体进行更改并保存这些更改，但随后发现出现了错误，可以使用 PowerApps 还原到窗体的以前版本：

1. 在 SharePoint 列表中，单击或点击命令栏中的“PowerApps”，然后单击或点击“自定义窗体”。

1. 在适用于 Web 的 PowerApps Studio 中，单击或点击“文件”，然后在“保存”页上，单击或点击“查看所有版本”。 “版本”页将在新的浏览器选项卡中打开。

    > [!NOTE]
    > 如果看不到“查看所有版本”按钮，单击或点击“保存”， 应会显示此按钮。

1. 无需关闭“版本”页或浏览器选项卡，返回到其他浏览器选项卡中的“保存”页，单击或点击左侧导航窗格顶部的箭头，然后单击或点击“返回 SharePoint”来解锁窗体，并退出适用于 Web 的 PowerApps Studio。

1. 返回到其他浏览器选项卡中的“版本”页，找到你想要还原的版本，然后单击“还原”。

    > [!NOTE]
    > 如果收到一条错误消息，指示由于窗体被另一个用户锁定而导致还原失败，请等待用户解锁窗体，然后重试。

问：能否将我的自定义列表窗体从一个列表移动到另一个列表？

**答：**不能。 当前不支持此功能。

### <a name="administering-custom-list-forms"></a>管理自定义列表表单

问：如何与其他人共享我的自定义列表窗体？

答：无需共享窗体 - 窗体从 SharePoint 列表继承权限。 完成自定义后，只需[将其发布回 SharePoint](customize-list-form.md#save-and-publish-the-list-form-back-to-sharepoint)，便可供其他人使用。

问：谁可以自定义列表窗体？

答：任何具有 SharePoint 权限的人员都可以管理、设计或编辑关联的列表。

**问：**是否需要使用 PowerApps 许可证才能创建或使用自定义列表表单？

**答：**若有任何[包含 PowerApps 的 Office 365 计划](../../administrator/pricing-billing-skus.md#licenses)，便可以创建或使用自定义列表表单。

问：当来宾用户访问具有自定义窗体的列表时，会发生什么情况？

答：如果来宾用户尝试访问已使用 PowerApps 自定义的列表窗体，将会收到一条错误消息。

问：作为管理员，如何在组织中获取所有自定义窗体列表？

答：如果你是 PowerApps 的租户管理员，或者对组织的默认 PowerApps 环境具有环境管理员权限，请执行以下操作：

1. 转到 [PowerApps 管理中心](https://admin.powerapps.com)，从环境列表中选择组织的默认环境。

1. 在默认环境页顶部，单击或点击“资源”。

1. 从应用的列表中，查找应用类型为 SharePoint 窗体的应用 - 这些是自定义窗体。

    ![自定义窗体列表](./media/customize-list-form/all-customized-forms.png)
