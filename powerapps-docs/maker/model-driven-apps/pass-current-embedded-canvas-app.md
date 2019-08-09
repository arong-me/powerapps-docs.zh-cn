---
title: 使用嵌入式区域应用作为数据上下文传递当前记录 | MicrosoftDocs
ms.custom: ''
ms.date: 06/25/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - PowerApps
author: Aneesmsft
ms.author: matp
manager: kvivek
tags:
  - PowerApps maker portal impact
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="pass-the-current-record-as-data-context-to-an-embedded-canvas-app"></a>将当前记录作为数据上下文传递到嵌入式区域应用
> [!IMPORTANT]
> 在模型驱动窗体中嵌入的区域应用现在已退出预览，已公开发布。 下面列出的步骤已过时，仅适用于在模型驱动窗体上嵌入的区域应用的公共预览版本。
> 有关最新版本的步骤的更新列表，请参阅：[在模型驱动窗体上添加嵌入式区域应用](embedded-canvas-app-add-classic-designer.md)

本主题介绍如何添加嵌入式区域应用并将当前（主窗体）记录作为数据上下文传递到该嵌入式区域应用。

假设您要在帐户主窗体上添加嵌入式区域应用并将当前帐户记录传递到该嵌入式区域应用。 为此，请按照以下步骤操作： 

1.  登录 [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)，然后打开实体（如客户实体）主窗体的窗体编辑器。 
2.  选择您希望嵌入式区域应用显示的窗体上的部分。
3.  使用字段资源管理器窗格，添加必填字段，如**帐户名称**。
      > [!IMPORTANT]
      > 请始终使用确定具有值的必填字段。 如果字段无值，则不会刷新嵌入式区域应用来响应主机模型驱动的窗体上的任何数据变化。
4.  选择字段后，在**主页**选项卡上的**编辑**组中，选择**更改属性**。
5.  在**字段属性**对话框中，选择**控件**选项卡。
6.  在**控件**选项卡上，选择**添加控件...**。
7.  在**添加控件**对话框上，在可用控件列表中，选择**区域应用**，然后选择**添加**。
8.  在**字段属性**对话框中，在控件列表中，选择**区域应用**，然后选择 **Web** 选项。
9.  在控件列表下面的部分，显示可用于区域应用控件的属性列表。
     - **实体名称**属性指定将向您的嵌入式区域应用提供数据的实体。 其将被设置为包含要在之前步骤中添加的字段的实体。
         - 请注意，即使此属性显示不可更改，对其进行更改也不会影响嵌入式区域应用。 这仅供您参考。
     - **应用 ID** 属性指定区域应用的 ID。 在创建区域应用时，将自动为您生成和填写应用 ID。
         - 请注意，对**应用 ID** 值进行更改将断开模型驱动型窗体与嵌入式区域应用的链接。
10. 选择**自定义**以创建或编辑区域应用。 这会在一个新选项卡中打开 PowerApps Studio。
       > [!NOTE]
       > 如果打开 PowerApps Studio 被 Web 浏览器弹出窗口阻止程序阻止，您必须启用 web.powerapps.com 网站或暂时禁用弹出窗口阻止程序，然后再次选择**自定义**。
11. 在 PowerApps Studio 中，请注意左侧窗格中有一个特殊的 **ModelDrivenFormIntegration** 控件。 此控件负责将上下文数据从主机模型驱动的窗体带入嵌入式区域应用。
12. 选择 **Gallery1** 控件并观察**项目**属性是否设置为 **ModelDrivenFormIntegration.Data**。
      > [!NOTE]
      > ModelDrivenFormIntegration.Data 是一列记录。 在此示例中，它只有一个记录。 若要直接引用记录，可使用 First 函数。 例如，*First(ModelDrivenFormIntegration.Data).Name*。
13. 在右侧的属性窗格中，在**字段**旁边，选择**编辑**。
14. 在数据窗格中，将映射到 **Title1** 控件的字段更改为**名称**或包含数据的其他字段。
15. 观察此库是否显示数据正在通过 ModelDrivenFormIntegration 控件从主机模型驱动的窗体传递到库。 关闭数据窗格。
16. 选择**文件**选项卡，然后选择**应用设置**。
17. 在**高级设置**选项卡上，在**试验功能**部分，将**启用应用的嵌入用户体验**设置为**开**。
18. 选择**保存**。 
19. 选择**云**选项卡。为应用提供唯一名称，然后选择右下方的**保存**。 请注意以下事项： 
    -  第一次保存应用时将自动发布应用。
      -  在以后的保存中，选择**发布**，然后选择**发布此版本**可以让更改生效。
20. 在菜单上选择**返回**，然后选择窗体编辑器已打开的浏览器标签页。 观察区域应用控件的**应用 ID** 属性现在是否有自动填充的值。 请注意以下事项： 
    -   窗体编辑器包含之前步骤中在其他浏览器中打开的 PowerApps Studio 的直接链接。
    -   窗体编辑器“侦听”向其发送的**应用 ID**。
    -   在保存应用后，**应用 ID** 将发送到窗体编辑器。
21. 在**字段属性**对话框中，选择**显示**选项卡。
22. 清除窗体上的**显示标签**，然后选择**确定**。
    -   如果您在此窗体上已有嵌入的区域应用，将显示消息“一个窗体中只能启用一个区域应用”。 若要添加新区域应用，您必须先[禁用当前的嵌入式区域应用](embedded-canvas-app-guidelines.md#disable-an-embedded-canvas-app)。 然后，[启用新的嵌入式区域应用](embedded-canvas-app-guidelines.md#enable-an-embedded-canvas-app)。
23. 在**主页**选项卡上，选择**保存**，然后选择**发布**。

将嵌入式区域应用添加到模型驱动的窗体之后，与其他用户共享嵌入式区域应用。 详细信息：[共享嵌入式区域应用](share-embedded-canvas-app.md)。

当用户打开包含您修改后的窗体的模型驱动应用（仅统一接口）时，他们将在窗体上看到嵌入的区域应用。 更改主窗体上显示的记录将更改传递到窗体的数据上下文，嵌入应用将刷新以显示相关数据。

本主题说明了如何开始在模型驱动窗体中嵌入区域应用。 您可以进一步自定义嵌入的区域应用以连接和引入来自各种数据源的数据。 使用筛选、搜索和查找功能以及从主机模型驱动窗体传入的上下文来筛选或查找那些数据源中的特定记录。 使用 WYSIWYG 区域应用编辑器轻松设计界面以满足您的要求。

## <a name="see-also"></a>另请参阅
[在模型驱动的窗体上嵌入区域应用](embed-canvas-app-in-form.md) <br />
[在模型驱动窗体上添加嵌入式区域应用](embedded-canvas-app-add-classic-designer.md) <br />
[编辑在模型驱动窗体上嵌入的区域应用](embedded-canvas-app-edit-classic-designer.md) <br />
[自定义在模型驱动窗体上嵌入的区域应用的屏幕尺寸和方向](embedded-canvas-app-customize-screen.md) <br />
[从嵌入的区域应用内在主机窗体上执行预定义操作](embedded-canvas-app-actions.md) <br />
[ModelDrivenFormIntegration 控件的属性和操作](embedded-canvas-app-properties-actions.md) <br />
[共享嵌入式区域应用](share-embedded-canvas-app.md) <br />
[嵌入式区域应用使用指南](embedded-canvas-app-guidelines.md) <br />
[迁移使用最新的公共预览版本创建的模型驱动窗体上的嵌入式区域应用](embedded-canvas-app-migrate-from-preview.md) <br />
