---
title: "从 SharePoint 中生成应用 | Microsoft 文档"
description: "无论站点是在本地还是在云中，都可以生成三屏应用来管理 SharePoint 列表中的项。"
services: 
suite: powerapps
documentationcenter: na
author: skjerland
manager: kfile
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 01/21/2017
ms.author: sharik
ms.openlocfilehash: e5299b12e3034978b14c70193151440626267c5a
ms.sourcegitcommit: 91851aebdf650e99d15374478901b3762d2b4a4b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2018
---
# <a name="generate-an-app-from-within-sharepoint-using-powerapps"></a>使用 PowerApps 从 SharePoint 中生成应用

在 PowerApps 中自动生成应用，以便用户管理自定义 SharePoint Online 列表中的项。 应用将有三个屏幕，用户可以在其中执行以下操作：

* 浏览列表中的所有记录 (**BrowseScreen1**)
* 查看特定记录的所有字段 (**DetailsScreen1**)
* 创建或编辑记录 (**EditScreen1**)

如果从 SharePoint Online 命令栏创建自定义列表的应用，则应用会显示为该列表的视图。 除了 Web 浏览器，还可以在 Windows Phone、iOS 或 Android 设备上运行应用。

> [!IMPORTANT]
> PowerApps 并不支持所有类型的 SharePoint 数据。 有关详细信息，请参阅 [已知问题](connections/connection-sharepoint-online.md#known-issues)。

## <a name="generate-an-app"></a>生成应用
1. 在 SharePoint Online 中打开自定义列表，单击或点击命令栏中的“PowerApps”，然后单击或点击“创建应用”。
   
    ![](./media/generate-app-from-sharepoint-list-interface/generate-new-app.png)
2. 在显示的面板中，键入应用的名称，然后单击或点击“创建”。
   
    ![](./media/generate-app-from-sharepoint-list-interface/enter-app-name.png)
   
    此时会在 Web 浏览器中出现一个新的选项卡，其中显示根据你的 SharePoint 列表自动生成的应用。
   
    ![](./media/generate-app-from-sharepoint-list-interface/powerapp-studio-for-web.png)  
3. 单击或点击 SharePoint 列表的浏览器选项卡，然后单击或点击“打开”。
   
    > [!NOTE]
> 可能需要先刷新浏览器窗口（例如，按 F5 刷新），然后应用才会打开。
   
    ![](./media/generate-app-from-sharepoint-list-interface/open-app-in-browser.png)
   
    将在单独的浏览器选项卡中打开应用。
   
    ![](./media/generate-app-from-sharepoint-list-interface/open-app.png)

## <a name="manage-the-app"></a>管理应用
![](./media/generate-app-from-sharepoint-list-interface/command-bar.png)

* 如果单击或点击“在 PowerApps 中编辑”，应用会在单独的浏览器选项卡中打开，你可以在 Web 版 PowerApps Studio 中更新应用。
* 如果单击或点击“将此视图公开”，组织中的其他人员就可以查看它。 默认情况下，只有你可以看到你创建的视图。 若要允许他人编辑你的应用，则需[与之共享该应用](share-app.md)然后授予其“参与者”权限。
* 如果单击或点击“删除此视图”，会将此视图从 SharePoint 中删除，但应用仍会留在 PowerApps 中，除非[删除它](delete-app.md)。

## <a name="next-steps"></a>后续步骤
* 若要添加或更新列表中的项，请参阅[从 SharePoint Online 列表打开应用](open-app-embedded-in-sharepoint.md)中的“使用应用管理列表”部分。
* 要自定义浏览屏幕（默认情况下会显示），请参阅 [自定义布局](customize-layout-sharepoint.md)。
* 要自定义详细信息或编辑屏幕，请参阅 [自定义窗体](customize-forms-sharepoint.md)。
* 若要删除该应用，请从 SharePoint 中删除视图，然后从 PowerApps 中[删除应用](delete-app.md)。

