---
title: 删除模型驱动应用 | MicrosoftDocs
description: 了解如何从 PowerApps 环境中删除模型驱动应用。
keywords: ''
ms.date: 05/31/2018
ms.service: crm-online
ms.custom: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.assetid: e82e7f64-37ad-41e5-acd7-16309881c6a2
author: Mattp123
ms.author: matp
manager: kvivek
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
caps.latest.revision: 9
topic-status: Drafting
ms.openlocfilehash: 9512c0b1c13f408b92c0c18f08946ea9afa1e62b
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39669128"
---
# <a name="delete-a-model-driven-app"></a>删除模型驱动应用

删除环境中过时的应用。

1. 登录 [PowerApps](https://web.powerapps.com/)。
2. 打开[解决方案资源管理器](advanced-navigation.md#solution-explorer)。 
3. 在解决方案窗口中的“组件”下，选择“应用”。
4. 选择想删除的应用，然后选择命令栏上的“删除”。

    ![删除应用](media/app-module-solution-window.png "删除应用")

5. 在出现的确认消息中选择“删除”。

   该应用随即从环境中删除。
  
如果组件具有依赖项（例如关系），则必须先删除这些依赖项才能删除该应用。 若要查看应用的依赖项，请选择该应用，然后选择命令栏上的“显示依赖项”。

> [!NOTE]
> 在删除应用时，建议删除其关联的站点地图。 如果不删除关联的站点地图，那么在首次尝试创建与其同名的另一个应用时，站点地图设计器会显示错误。 不过可以忽略该错误，再次尝试创建应用时将不再显示该错误。


