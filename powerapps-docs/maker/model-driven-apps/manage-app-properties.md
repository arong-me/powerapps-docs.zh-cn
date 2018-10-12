---
title: 在 PowerApps 应用设计器中管理模型驱动应用属性 | MicrosoftDocs
description: 了解如何管理应用属性
keywords: ''
ms.date: 06/27/2018
ms.service: crm-online
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
ms.openlocfilehash: 62129690a0f5969b6f0f749e110eca001f2c0c8b
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39668435"
---
# <a name="manage-model-driven-app-properties-in-the-app-designer"></a>在应用设计器中管理模型驱动应用属性

应用属性定义了有关应用的重要详细信息，例如标题或 URL。 创建应用时可定义应用属性。 如果希望以后更改这些属性，可在应用设计器中执行相关操作。  
  
1.  在应用设计器的右侧，选择“属性”选项卡。  
  
    ![应用设计器“属性”窗格](media/app-designer-properties-tab.png "App designer Properties pane")  
  
2.  根据需要更改信息：  

    |属性|描述|  
    |--------------|-----------------|
    |**名称**|为应用输入唯一且有意义的名称。|  
    |**Description**|键入应用的简短说明。|  
    |**图标**|默认情况下，“使用默认应用”复选框处于选中状态。 若要选择其他 Web 资源作为应用的图标，请清除该复选框，然后从下拉列表中选择一个图标。 此图标会在应用的预览磁贴上显示。|
    |**唯一名称**| 无法更改唯一名称。 使用唯一名称，可以查询表，以从数据库获取数据。| 
    |**客户端**|定义应用将用于的客户端类型。<br/>-  **Web：** 这是经典的 Dynamics 365 客户参与 Web 浏览器客户端。<br/>-  **统一接口：** 这是新的 Web 浏览器客户端，在电脑和移动设备上具有类似的接口。|
    |**应用 URL 后缀**| 默认情况下，创建应用时选择的 URL 会在此处显示。 可以在“管理应用”对话框中更改应用 URL。 请注意，此时无法通过解决方案导出或导入应用 URL 后缀。|
    |**选择应用的欢迎页**|借助此选项，可从环境中的可用 Web 资源中进行选择。 创建的欢迎页可包含对用户有用的信息，例如视频、升级说明或入门信息的链接。 有关如何创建 Web 资源（例如可用作欢迎页的 HTML 文件）的详细信息，请参阅[创建和编辑 Web 资源以扩展 Web 应用](create-edit-web-resources.md)。|
    |**启用 Mobile Offline**|此选项使应用可以在移动设备上脱机使用，用于通过“Mobile Offline 配置文件”下拉列表选择的配置文件。|
  
3.  保存应用。  
  
## <a name="next-steps"></a>后续步骤  
 [创建或编辑应用](create-edit-app.md)
