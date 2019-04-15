---
title: 启动画布应用中的流 | Microsoft Docs
description: 创建一个流，该流在画布应用中发生某个事件（例如用户选择某个按钮）后执行一个或多个任务。
author: stepsic-microsoft-com
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 12/07/2018
ms.author: stepsic
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 5439399a22b47fcf4195cf878208e0e0bd4e0764
ms.sourcegitcommit: 6858f3786e960ca53a400e04734561400dcac5b1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/25/2019
ms.locfileid: "57802575"
---
# <a name="start-a-flow-in-a-canvas-app"></a>启动画布应用中的流

可以使用 Microsoft Flow 来创建逻辑，以便在画布应用中发生某个事件时执行一个或多个任务。 例如，配置一个按钮，以便用户选择它时在 SharePoint 列表中创建一个项、发送电子邮件或会议请求、将文件添加到云，或执行所有上述操作。 可以在应用中配置任何用于启动流的控件，该控件在关闭 PowerApps 的情况下仍会继续运行。

> [!NOTE]
> 当用户运行应用内的从一个流时，该用户必须具有执行指定的流中的任务的权限。 否则，流将失败。

## <a name="prerequisites"></a>先决条件

- [注册](../signup-for-powerapps.md) PowerApps。
- 了解如何[配置控件](add-configure-controls.md)。

## <a name="create-a-flow"></a>创建流

1. 登录 [PowerApps](http://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。

1. 在左侧的导航栏中，选择**业务逻辑**，然后选择**流动**。

1. 在的左上角**我的流**页上，选择**新建**，然后选择**从头开始创建**。

    ![用于在不使用模板的情况下创建流的选项](./media/using-logic-flows/create-from-blank.png)

1. 附近显示的页的底部，选择**搜索数百个连接和触发器**。

1. 在搜索框中，键入**PowerApps**，然后选择**PowerApps**图标。

    ![创建 PowerApps 触发器](./media/using-logic-flows/set-trigger.png)
    
1. 同样，在下一页上，选择 PowerApps 图标，然后选择**新步骤**。

1. 在框中**搜索连接器和操作**，指定你的流，如本例所示的一项操作：

   1. 类型**SharePoint**在中，然后选择**创建项**下的列表中**操作**。

       ![用于创建 SharePoint 项的选项](./media/using-logic-flows/create-sharepoint-item.png)

   1. 如果系统提示，请提供用于连接到 SharePoint 的凭据。

   1. 在“网站地址”框中，键入或粘贴包含列表的 SharePoint Online 网站的 URL。

       > [!NOTE]
       > 不向 URL 追加的列表的名称。

   1. 在中**列表名称**框中，指定你想要使用的列表。
   
       ![指定列表](./media/using-logic-flows/list-fields.png)

   1. 在列表中选择一个字段的输入的框 (如**标题**)，选择**查看更多**在动态内容窗格中，然后选择**在 PowerApps 中的询问**。 

       ![将“在 PowerApps 中询问”参数添加到“标题”字段](./media/using-logic-flows/ask-in-powerapps.png)

1. （可选）指定一个或多个其他步骤，如将审批邮件发送到您指定的地址，或在另一个数据源中创建相关的条目。

1. 左上角附近，键入或粘贴你的流的名称，然后选择**保存**右上角附近。

## <a name="add-a-flow-to-an-app"></a>向应用添加流
1. 在左侧的导航栏中，选择**创建**。

1. 将鼠标悬停**从空白画布应用**磁贴，并选择**将此应用程序**。

1. 添加 **[文本输入](controls/control-text-input.md)** 控件，将其命名为 **RecordTitle**。

1. 添加 **[按钮](controls/control-button.md)** 控件，将其移至 **RecordTitle** 下。

1. 选择 **[按钮](controls/control-button.md)** 控件后，在“操作”选项卡上选择“流”。

    ![“操作”选项卡上的“流”选项](./media/using-logic-flows/action-tab.png)

1. 在显示的窗格中，选择在前面的过程中创建的流。

    > [!NOTE]
   > 如果创建的流不可用，请确认是否已将 PowerApps 设置为在其中创建了流的环境。

    ![从自定义窗格添加流](./media/using-logic-flows/add-flow-from-pane.png)

1. 在公式栏中，在已自动添加的公式末尾键入或粘贴 **RecordTitle.Text)**。

    ![包含流的 OnSelect 属性](./media/using-logic-flows/onselect-with-flow.png)

## <a name="test-the-flow"></a>测试流
1. 双击**文本输入**控制，并键入或粘贴到其中的一些文本。

1. 按住 Alt 键，同时选择 **[按钮](controls/control-button.md)** 控件。

    在您使用文本指定其标题为指定列表中将创建一个 SharePoint 项。 如果列表在流运行时处于打开状态，可能需要刷新浏览器窗口，才能显示这些更改。
