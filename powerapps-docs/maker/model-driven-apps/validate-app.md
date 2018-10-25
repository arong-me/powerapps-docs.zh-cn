---
title: 使用应用程序设计器验证并发布模型驱动应用 | Microsoft Docs
description: 了解如何验证并发布模型驱动应用
keywords: ''
ms.date: 06/08/2018
ms.service: crm-online
ms.custom: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: 5a9ec120-9ddc-4d92-b48c-0fee8c57d3c3
ms.author: matp
manager: kvivek
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
caps.latest.revision: 10
topic-status: Drafting
ms.openlocfilehash: e3802ef423e7012974c24311c36b78cd56f8ed06
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39668542"
---
# <a name="validate-and-publish-a-model-driven-app-using-the-app-designer"></a>使用应用程序设计器验证和发布模型驱动应用

验证应用，以检查是否存在应用工作所必需的但尚未添加到应用的资产依赖项。 验证成功后即可发布应用。 
  
例如，你将客户服务绩效仪表板添加到了应用，它要使用类似于案例组合（按优先级）或案例解决趋势（以天计）的图表，而你尚未添加它们。 验证此应用时，就会收到所有缺失的必需资产列表。  
  
验证应用时，应用程序设计器画布会显示所缺失的资产的详细信息。  
  
1.  在应用程序设计器中，选择“验证”。  
  
     随即将出现一个通知栏，并显示应用中是否存在任何错误或警告。 例如，当实体没有窗体或视图，或应用不包含任何组件时，通知栏会显示警告。 如果未为应用配置站点地图，则可能会出现错误。 你可以在不处理警告的情况下发布应用，但错误必须予以修复才能发布应用。  
  
     ![显示应用中的警告的通知栏](media/app-designer-warning-notification.png "显示应用中的警告的通知栏")  
  
     此外，应用程序设计器还会在缺失必需资产的各个项目或资产磁贴上显示警告符号，并附带依赖项的数目。  
  
     ![应用程序设计器磁贴上的缺失组件警告](media/warning--button-on-app-designer-tile.png "应用程序设计器磁贴上的缺失组件警告")  
  
2.  若要添加必需的资产，请在画布右侧选择“必需”选项卡。 当应用中至少缺失一个必需资产时，就可以看到“必需”选项卡。  
  
     此选项卡会显示一个必需组件列表。  
  
     ![显示应用中缺失组件列表的“必需”选项卡](media/app-designer-required-components-tab.png "显示应用中缺失组件列表的“必需”选项卡")  
  
3.  选择要添加的资产，然后选择“添加依赖项”。 添加必需资产时，添加资产的相应磁贴上的计数会减少。  
  
    > [!NOTE]
    >  若某个通用资产是不同应用组件所必需的（例如窗体是仪表板和实体所必需的），而你仅从仪表板依赖项树中添加了该资产一次，则只有仪表板磁贴上的依赖项计数会减少，实体磁贴上的计数则不会减少。 但会同时为这两个磁贴解析此依赖项。  
    >   
    >  选择“获取最新依赖项”![应用程序设计器中的“获取最新依赖项”按钮](media/app-designer-get-latest-dependencies.png "应用程序设计器中的“获取最新依赖项”按钮")，或再次选择“验证”来获取最新的依赖项集。 只有在保存应用后才会看到这些按钮。  
  
     若不想添加建议的必需组件，则选择“隐藏依赖项”。 在应用程序设计器中打开应用并选择“验证”或“获取最新依赖项”![应用程序设计器中的“获取最新依赖项”按钮](media/app-designer-get-latest-dependencies.png "应用程序设计器中的“获取最新依赖项”按钮")时，将再次显示所有未解决的警告。  
  
    > [!NOTE]
    >  若现在隐藏依赖项，后面想要导出此应用时，所有的这些依赖项会再次出现。  
  
## <a name="publish-an-app-using-the-app-designer"></a>使用应用程序设计器发布应用

发布应用，以便用户可以使用它。  
  
 添加组件、验证并保存应用后，在命令栏上选择“发布”。 也可以从[我的应用](advanced-navigation.md#my-apps)页上相应的应用磁贴处发布应用。 在“正在编辑的应用”视图中想要发布的应用磁贴的右下角，选择“更多选项”按钮（“...”），然后选择“发布”。  
  
 应用状态会更改为“已发布”。 你可以在应用程序设计器的右上角看到此更改。 应用将从“正在编辑的应用”视图转到“已发布的应用”视图，并且应用磁贴上会显示发布日期。  
  
> [!NOTE]
> - 若应用验证出现错误，则可在通知栏上看到此错误。 直至解决此错误才可发布此应用。  
> - 保存应用后才能将其发布。  

## <a name="next-steps"></a>后续步骤  
[借助 PowerApps 共享模型驱动应用](https://docs.microsoft.com/powerapps/maker/model-driven-apps/share-model-driven-app) <br/>
 [在移动设备上运行模型驱动应用](https://docs.microsoft.com/powerapps/user/run-app-client-model-driven)   
 
