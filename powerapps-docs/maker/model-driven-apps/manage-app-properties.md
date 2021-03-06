---
title: 在 Power Apps 应用程序设计器中管理模型驱动应用程序的属性 | MicrosoftDocs
description: 了解如何管理您应用的属性
keywords: ''
ms.date: 02/05/2019
ms.service: powerapps
ms.custom: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: e773e60f-0211-4c4b-a1af-663be4997629
ms.author: matp
manager: kvivek
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
caps.latest.revision: 14
topic-status: Drafting
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: a2f0dc0130e8a698a4407d90f3f1ce51c9873c31
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/02/2019
ms.locfileid: "2860047"
---
# <a name="manage-model-driven-app-properties-in-the-app-designer"></a>在应用程序设计器中管理模型驱动应用程序的属性

应用程序属性定义该应用程序的重要详细信息，如其标题或 URL。 在创建应用程序时，定义应用程序属性。 如果您希望以后更改这些应用程序的属性，则可以在应用程序设计器中执行此操作。  
  
1.  在应用程序设计器中，在右侧，选择**属性**选项卡。  

    > [!div class="mx-imgBorder"] 
    > ![应用设计器的“属性”窗格](media/app-designer-properties-tab.png "应用设计器的“属性”窗格")  
  
2.  根据需要更改信息：  

    |属性|说明|  
    |--------------|-----------------|
    |**名称**|输入应用程序的唯一且有意义的名称。|  
    |**说明**|键入应用程序的简短说明。|  
    |**图标**|默认情况下，**使用默认应用**复选框已选中。 若要选择其他 Web 资源充当该应用的图标，请清除该复选框，然后从下拉列表选择一个图标。 此图标在应用程序的预览磁贴中显示。|
    |**唯一名称**| 您不能更改唯一名称。 可使用唯一名称查询表以从数据库获取数据。|
    |**应用 URL 后缀<sup>1</sup>**| 默认在此处显示您在创建该应用程序时选择的 URL。 可以在**管理应用程序**对话框中更改应用程序 URL。 请注意，目前不能通过解决方案导出或导入应用程序 URL 后缀。|
    |**选择应用程序的欢迎页**|此选项用于从环境中的可用 Web 资源进行选择。 创建的欢迎页可以包含对用户有用的信息，如视频的链接、升级说明或入门信息。 有关如何创建 Web 资源（如可用作欢迎页的 HTML 文件）的详细信息，请参阅[创建和编辑 Web 资源以扩展 Web 应用程序](create-edit-web-resources.md)。|
    |**启用 Mobile Offline**|此选项让应用在移动设备上可以对使用 **Mobile Offline 配置文件**下拉列表选择的配置文件脱机可用。|

    <sup>1</sup>当您创建新应用时，**客户端**和**应用 URL 后缀**属性不再可用。
3.  保存应用。  
  
## <a name="next-steps"></a>后续步骤  
 [创建或编辑应用](create-edit-app.md)
