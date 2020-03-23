---
title: 删除模型驱动应用程序 | MicrosoftDocs
description: 了解如何从 Power Apps 环境中删除或移除模型驱动应用程序。
keywords: ''
ms.date: 02/14/2020
ms.service: powerapps
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
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 56510a744cfe010a3f52724e5b98a65a65e783e2
ms.sourcegitcommit: 97a36c9df2a7067a29fb6bd254975dadc2bc16fa
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/19/2020
ms.locfileid: "3072764"
---
# <a name="delete-a-model-driven-app"></a>删除模型驱动应用程序
删除或移除环境中已过时的应用程序。

> [!IMPORTANT]
> - 如果将模型驱动应用作为托管解决方案的一部分安装在默认解决方案中，请参阅[删除作为托管解决方案的一部分安装的模型驱动应用](#delete-a-model-driven-app-that-was-installed-as-part-of-a-managed-solution)。
> - 无法删除第一方模型驱动应用，例如 Dynamics 365 Sales、Dynamics 365 Customer Service 和 Dynamics 365 Field Service。 您可以通过删除分派给应用的安全角色来对用户隐藏这些应用。 请注意，在模型驱动应用实体中，这些应用仍将对具有环境制造者、系统管理员和系统定制员角色的用户或具有创建权限的任何用户可见。 

1. 登录到 [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。
2. 在左侧导航中，选择**应用**。 
3. 选择要删除的应用，然后在命令栏上选择**删除**。
4. 在显示的确认消息中，选择**删除**。

   将从环境中删除应用程序。
  
如果组件具有依赖项（如关系），则必须移除依赖项，然后才能删除应用。 若要查看应用的依赖项，请选择应用，然后在命令栏中选择**显示依赖项**。

> [!NOTE]
> 删除应用时，建议删除其关联站点地图。 如果不删除关联站点地图，首次尝试再创建一个同名应用时，站点地图设计器将显示错误。 但是，可忽略此错误，而您再次尝试创建该应用时，将不显示此错误。

## <a name="delete-a-model-driven-app-that-was-installed-as-part-of-a-managed-solution"></a>删除作为托管解决方案的一部分安装的模型驱动应用
要删除作为托管解决方案的一部分安装在环境中的模型驱动应用，请删除托管解决方案。 

### <a name="delete-a-managed-solution"></a>删除托管解决方案 
可以通过删除托管解决方案来删除该解决方案的所有组件。
1.  登录到 [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。 
2.  在左侧导航中，选择**解决方案**。
3.  在**解决方案**列表中，选择要删除的托管解决方案，然后在工具栏上选择**删除**。 

