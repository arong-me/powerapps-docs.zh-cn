---
title: "在浏览器中创建或编辑应用 | Microsoft 文档"
description: "使用适用于 Web 的 PowerApps Studio 在浏览器中创建或编辑应用。"
services: 
suite: powerapps
documentationcenter: na
author: karthik-1
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/06/2017
ms.author: karthikb
ms.openlocfilehash: 3c675e84f03e008a7f478d358a99fe3fff602002
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2017
---
# <a name="create-or-edit-apps-in-powerapps-studio-for-web"></a>在适用于 Web 的 PowerApps Studio 中创建或编辑应用
使用适用于 Web 的 PowerApps Studio 在 Windows 或其他平台上的浏览器中创建和编辑应用。

**先决条件**

* [注册](signup-for-powerapps.md) PowerApps。
* 在运行 Windows 或 Mac 的计算机上安装 Microsoft Edge、Google Chrome 或 Internet Explorer 11。

## <a name="open-powerapps-studio-for-web"></a>打开适用于 Web 的 PowerApps Studio
1. 登录到 [powerapps.com](http://go.microsoft.com/fwlink/p/?LinkId=708209)。
2. 在左下角单击或点击“新建应用”。
   
    ![左侧导航栏中的“新建应用”](./media/create-app-browser/left-nav.png)

适用于 Web 的 PowerApps Studio 随即在浏览器的新选项卡中打开，你可以像在适用于 Windows 的 PowerApps Studio 中一样在其中创建和编辑应用。

## <a name="next-steps"></a>后续步骤
* 根据 [Excel](get-started-create-from-data.md) 或 [SharePoint](app-from-sharepoint.md) 等数据源中的数据自动生成应用 。
* 了解如何[添加控件并设置属性](add-configure-controls.md)，这将决定应用的外观和行为。
* [从头开始创建应用](get-started-create-from-blank.md)，充分发挥你的创造力。

## <a name="known-limitations"></a>已知的限制
1. **创建连接。**
   
    若要对需要服务身份验证的数据源[创建连接](add-manage-connections.md)，请使用 [powerapps.com](https://web.powerapps.com)，然后在 PowerApps Studio for web 中向应用[添加该连接](add-data-connection.md)。
2. **在本地编辑并保存应用**。
   
    为达到最佳效果，可使用 PowerApps Studio for Windows 在本地编辑并保存应用。 在浏览器中，无法保存对本地应用的更改；若要保存更改，必须保存新文件，而不是替换已打开的文件。
3. **使用信号函数。**
   
    [Acceleration 和 Compass](functions/signals.md) 函数会在已发布的应用中返回准确的值，但如果正在浏览器中创建或修改应用，这些函数则返回零值。
4. **导出和导入数据。**
   
    可以在已发布的应用中[导出和导入数据](controls/control-export-import.md)，但如果正在浏览器中创建或修改应用，则无法执行此操作。
5. **在两个会话之间复制控件。**
   
    无法将控件从一个适用于 Web 的 PowerApps Studio 会话复制到另一个适用于 Web 的 PowerApps Studio 会话。
