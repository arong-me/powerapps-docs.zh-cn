---
title: 使用应用程序设计器验证和发布模型驱动应用 | MicrosoftDocs
description: 了解如何验证和发布模型驱动应用
keywords: ''
ms.date: 06/08/2018
ms.service: powerapps
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
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 2e6ae7ac84710e6558adde2949025868e6da6930
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "2710275"
---
# <a name="validate-and-publish-a-model-driven-app-using-the-app-designer"></a>使用应用程序设计器验证和发布模型驱动应用程序

可验证应用以检查应用要工作所需，但尚未为其添加的资产依赖项。 在成功验证后，发布应用程序。 
  
例如，您已向应用添加了“Customer Service 绩效”仪表板，该仪表板使用“案例组合(按类型)”或“案例解决趋势(以天计)”之类您尚未添加的图表。 验证此应用时，将生成所有必需但缺少的资产的列表。  
  
验证应用时，应用设计器区域显示有关缺少的资产的详细信息。  
  
1.  在应用程序设计器中，选择**验证**。  
  
     随即出现通知栏，为您显示应用是否有任何错误或警告。 实体无窗体或视图，或应用中不包含任何组件之类情况下，通知栏显示警告。 如果没有为应用配置站点地图，可能显示错误。 可以在不解决警告的情况下发布应用，但是必须修复错误才能发布。  
  
     ![应用中显示警告的导航栏](media/app-designer-warning-notification.png "应用中显示警告的导航栏")  
  
     应用设计器还显示一个警告符号，该警告符号带有缺少必需资产的每个项目或资产磁贴的依赖项数量。  
  
     ![应用设计器磁贴中的缺少组件警告](media/warning--button-on-app-designer-tile.png "应用设计器磁贴中的缺少组件警告")  
  
2.  若要添加必需资产，请选择区域右侧的**必需**选项卡。 应用中缺少至少一个必需资产时，显示**必需**选项卡。  
  
     此选项卡显示所需组件的列表。  
  
     ![显示应用中缺少的组件的列表的“必需”选项卡](media/app-designer-required-components-tab.png "显示应用中缺少的组件的列表的“必需”选项卡")  
  
3.  选择想要添加的资产，然后选择**添加依赖项**。 添加必需资产时，已向其添加了资产的磁贴中的计数将减少。  
  
    > [!NOTE]
    >  如果多个应用组件有一个共同需要的资产，如仪表板和实体需要一个窗体，并且您仅从“仪表板依赖项”树添加了一次该资产，则依赖项计数仅在“仪表板”磁贴中减少，不在“实体”磁贴中减少。 但是，将为两者解决依赖项。  
    >   
    >  选择**获取最新依赖项** ![应用程序设计器中的“获取最新依赖项”按钮](media/app-designer-get-latest-dependencies.png "应用程序设计器的“获取最新依赖项”按钮") 或再次选择**验证**以获取最新依赖项。 只有在保存应用后才看到这些按钮。  
  
     如果不希望添加建议的必需组件，请选择**隐藏依赖项**。 在应用程序设计器中打开应用并选择**验证**或**获取最新依赖项** ![应用程序设计器中的“获取最新依赖项”按钮](media/app-designer-get-latest-dependencies.png "应用程序设计器的“获取最新依赖项”按钮") 时，将再次显示未解决的警告。  
  
    > [!NOTE]
    >  如果您现在隐藏依赖项，但是以后希望导出此应用，将再次显示所有这些依赖项。  
  
## <a name="publish-an-app-using-the-app-designer"></a>使用应用程序设计器发布应用程序

发布应用以将其提供给用户。  
  
 添加组件，验证并保存应用之后，请在命令栏中选择**发布**。 也可以从[我的应用程序](advanced-navigation.md#apps)页面中的应用磁贴发布应用程序。 在**正在编辑的应用**视图中要发布的应用磁贴右下角，选择**更多选项**按钮 (**...**)，然后选择**发布**。  
  
 应用状态变为“已发布”。 可以在应用设计器右上角看到此状态。 应用从**正在编辑的应用**视图变为**已发布的应用**视图，并在应用磁贴中显示发布日期。  
  
> [!NOTE]
> - 如果您的应用存在验证错误，则会在通知栏中显示该错误。 只有在解决错误后，才能发布应用。  
> - 只有在保存应用后才能发布。  

## <a name="next-steps"></a>后续步骤  
[使用 PowerApps 共享模型驱动应用](https://docs.microsoft.com/powerapps/maker/model-driven-apps/share-model-driven-app) <br/>
 [在移动设备上运行模型驱动应用程序](https://docs.microsoft.com/powerapps/user/run-app-client-model-driven)   
 
