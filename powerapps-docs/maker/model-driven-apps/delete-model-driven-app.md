---
title: 删除模型驱动应用程序 | MicrosoftDocs
description: 了解如何从 PowerApps 环境中删除或移除模型驱动应用程序。
keywords: ''
ms.date: 05/31/2018
ms.service: crm-online
ms.custom: null
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
ms.assetid: e82e7f64-37ad-41e5-acd7-16309881c6a2
author: Mattp123
ms.author: matp
manager: kvivek
ms.reviewer: null
ms.suite: null
ms.tgt_pltfrm: null
caps.latest.revision: 9
topic-status: Drafting
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="delete-a-model-driven-app"></a>删除模型驱动应用程序

删除或移除环境中已过时的应用程序。

1. 登录到 [PowerApps](https://web.powerapps.com/)。
2. 打开[解决方案资源管理器](advanced-navigation.md#solution-explorer)。 
3. 在解决方案窗口中，在**组件**下，选择**应用**。
4. 选择要删除的应用，然后在命令栏上选择**删除**。

    ![删除应用](media/app-module-solution-window.png "删除应用")

5. 在显示的确认消息中，选择**删除**。

   将从环境中删除应用程序。
  
如果组件具有依赖项（如关系），则必须移除依赖项，然后才能删除应用。 若要查看应用的依赖项，请选择应用，然后在命令栏中选择**显示依赖项**。

> [!NOTE]
> 删除应用时，建议删除其关联站点地图。 如果不删除关联站点地图，首次尝试再创建一个同名应用时，站点地图设计器将显示错误。 但是，可忽略此错误，而您再次尝试创建该应用时，将不显示此错误。


