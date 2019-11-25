---
title: 使用现有环境和统一接口验证旧 Web 客户端应用入门指南 | MicrosoftDocs
description: 了解如何规划和执行从旧 Web 客户端到统一接口的转换
ms.custom: ''
ms.date: 09/11/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: ''
caps.latest.revision: 25
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: e39cb11b9883e93d341232bcdcbb43dc17fa491a
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2019
ms.locfileid: "2759764"
---
# <a name="quick-start-for-using-an-existing-environment-to-validate-your-legacy-web-client-app-with-the-unified-interface"></a>使用现有环境和统一接口验证旧 Web 客户端应用入门指南
本快速入门指南介绍如何使用现有环境创建基于当前配置或默认解决方案的统一接口应用程序。 这样就可以在运行现有旧 Web 客户端应用程序的同时，探索和测试统一接口。 然后，用户可以在环境之间切换，以便进行并排查看。 

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE3JzyI]

有关演示如何创建新沙盒环境以隔离测试，并仅查看统一接口体验的类似说明，请参阅[从 Dynamics 365 应用程序旧 Web 客户端应用程序转换到统一接口的快速入门指南](transition-web-app.md)。

> [!IMPORTANT]
>  对于装有 Dynamics 365 Field Service 或 Dynamics 365 Project Service Automation 应用程序的环境，请参阅 [Dynamics 365 应用程序](transition-web-app.md#dynamics-365-apps)。

## <a name="prerequisites"></a>必备条件 
- 现有 Dynamics 365 Sales 或 Service 旧 Web 客户端应用程序。 
- 尽管不需要，我们还是建议使用非生产环境来测试应用程序。 详细信息：[管理沙盒实例](/dynamics365/customer-engagement/admin/manage-sandbox-instances) 

## <a name="overview"></a>概述 
本主题面向以下客户：正在使用旧 Web 客户端应用程序，但是需要计划和执行到统一接口的转换。 若要设置并行环境，请基于现有默认解决方案按原样创建一个新的应用程序。 可以在当前开发沙盒环境中执行此操作，这样就不会影响您的现有工作。

完成本主题中的步骤之后，具有相应角色的用户可以在 Dynamics 365 下拉应用程序列表或 Dynamics 365 主页 (https://home.dynamics.com) 中的应用程序列表内看到您的新应用程序。

![应用程序列表](media/app-list.png)

在开发环境中使用解决方案完成本主题中介绍的任务之后，可以将该解决方案导入测试环境，这样更多业务用户就可以在熟悉的环境中测试和比较该应用程序。 

请执行您的应用程序生命周期管理 (ALM) 和开发应用程序流程。 建议在解决方案环境内部执行介绍的所有步骤。 在开发环境中测试并验证应用程序之后，可以进一步测试该应用程序，方法是将该应用程序以试点计划的形式提供给更多用户，如在生产环境中。 通过将模型驱动应用程序和站点地图添加到解决方案内，可以按照环境管道中的现有流程将新应用程序从其创建环境继续导出。 

## <a name="process-for-validating-your-legacy-web-client-app-in-an-existing-environment"></a>在现有环境中验证旧 Web 客户端应用程序的流程
 
在现有环境中验证旧 Web 客户端应用程序的流程包括三个步骤：  

1.  创建基于默认解决方案的新解决方案
2.  创建新的模型驱动应用程序 
3.  配置应用程序属性  

如果当前已按照[从 Dynamics 365 旧 Web 客户端应用程序转换到统一接口的快速入门指南](transition-web-app.md)主题中的说明在开发环境中将**仅使用统一接口**模式切换为**开**，则必须将此设置切换回**关**，这样才能运行现有旧 Web 客户端应用程序。

### <a name="create-a-new-solution-thats-based-on-the-default-solution"></a>创建基于默认解决方案的新解决方案
1. 登录 [PowerApps 开发者门户](https://make.powerapps.com)。   
2. 从环境列表中选择所需环境。  
3. 在左侧导航窗格中，选择**解决方案**。 
4. 在菜单栏上，选择**新建解决方案**。 
5. 在**新建解决方案**窗格中，输入以下属性： 
   - **名称**. 输入解决方案的名称。 例如，*统一接口应用程序*。 
   - **发布者**。 选择您的组织使用的发布者。 请务必遵守贵组织对现有自定义项的管制。 这样可以确保模型驱动应用程序及其站点地图的架构名称符合现有标准的要求。 
   - **版本**。 此项应该按照您对解决方案的现有标准和管制设置。 
6. 选择**创建**。  
7. 将在解决方案列中创建这个新解决方案。 选择该解决方案将其打开并转到下一部分。 

### <a name="create-a-new-model-driven-app-in-the-new-solution"></a>在新解决方案中新建模型驱动应用程序
在此步骤中，将创建一个利用您的现有自定义项的新应用程序，以便在统一接口中体验这些自定义项。 在新解决方案（即在上一部分中创建的解决方案）中创建该应用程序。  

1. 在菜单栏上，选择**新建**，指向**应用程序**，然后选择**模型驱动应用程序**。
2. 在**创建新应用**页中，输入以下属性： 
   - **名称**. 为应用程序输入适合的名称。 例如，*您的应用程序名称* + *新建*或*统一接口测试*。 
   - **唯一名称**。 这是您的解决方案前缀和您指定的应用程序名称简化版的开头。 可以进行更改，也可以保持原样。  
   - **说明**。 添加应用程序的说明，如*用于我们解决方案的新统一接口的测试目的*。  
3. 选择**使用现有解决方案创建应用程序**，然后选择**下一步**。 
4. 在**选择解决方案**列表中，选择**默认解决方案**，在**选择站点地图**列表中，选择**站点地图**，然后选择**完成**。  

   > [!div class="mx-imgBorder"] 
   > ![选择现有解决方案](media/select-existing-solution.png "选择现有解决方案")

5. 将打开应用程序设计器，其中显示默认解决方案中包含的所有应用程序组件。 选择**发布**。  
6. 发布流程完成后，选择**播放**。  

将在浏览器中打开一个新窗口，其中包含您的新模型驱动应用程序，该应用程序内包含您的默认 Dynamics 365 应用程序中的所有实体、站点地图和站点地图自定义项。  

> [!div class="mx-imgBorder"] 
> ![新统一接口应用](media/new-unified-interface-app.png "新统一接口应用")

请注意，当您回到包含 PowerApps 开发者门户**解决方案**区域的浏览器选项卡中时，您会发现您创建的解决方案中同时包含您的新模型驱动应用程序和名称类似的站点地图客户端扩展。  

> [!div class="mx-imgBorder"] 
> ![解决方案资产](media/solution-assets.png "解决方案资产")

此步骤中，您在解决方案内部创建了一个新的模型驱动应用程序，可将其导入到测试环境或评估环境中。 可以立即开始体验这个新应用程序，但是开始前，需要为其配置一些设置。 这样就可以与其他用户共享这个应用程序。

### <a name="configure-app-properties"></a>配置应用程序属性
配置模型驱动应用程序属性需要执行的任务包括： 

- 分配新应用程序的用户角色，以便启用非管理员访问权限来使用该应用程序。  
- 自定义友好 URL，以便用户轻松共享和记住新应用程序的快捷方式，或将其设置为书签。 


1. 导航到*环境 URL*/**应用程序**。 该 URL 如下所示：https://*YourEnvironment*.crm.dynamics.com/apps。 执行此操作将打开一个列表，其中包含您的环境中的所有应用程序。 
2. 找到您新建的模型驱动应用程序。  
3. 在应用程序磁贴中，选择省略号，然后选择**管理角色**。   

   > [!div class="mx-imgBorder"] 
   > ![管理角色](media/select-app-ellipsis.png "管理角色")

4. 将在右侧窗格中列出可用角色区域。 根据需要选择角色，以便提供该应用程序的管理员用户访问权限。 

    > [!IMPORTANT]
    > 确保为所有用户至少授予一个包含**模型驱动应用程序**权限的**读**访问权限。 可以在安全角色内的“自定义”选项卡上找到此权限。 无此权限的用户在打开任何模型驱动应用程序时，将收到错误。  请注意，已经为系统管理员和系统定制员安全角色启用了此权限。 
 
   > [!div class="mx-imgBorder"] 
   > ![模型驱动应用特权](media/model-driven-app-privilege.png "模型驱动应用特权")

5. （可选）在**管理角色**窗格中，可扩展开**应用程序 URL 后缀**以自定义模型驱动应用程序的友好 URL。 请注意，几乎可以指定所有设置。 例如，如果输入*新建*，则预览将显示 URL *https://YourEnvironment.crm.dynamics.com/apps/new*。   

   > [!div class="mx-imgBorder"] 
   > ![应用 URL 后缀](media/app-url-suffix.png "应用 URL 后缀")

   这将成为要使用和共享的友好 URL，这样用户就可以直接启动并进入统一接口体验。 用户可将此链接设置为书签，以便使用。 

6. 选择**保存**。 

现在，具有相应角色的用户可以在 Dynamics 365 下拉应用程序列表或 Dynamics 365 主页 (https://home.dynamics.com) 中的应用程序列表内看到您的新应用程序。 
  
   ![应用程序列表](media/app-list.png "应用程序列表")

由于**仅使用统一接口**模式设置为**关**，所以当用户导航到您的环境的根 URL 时，他们仍然会和以前一样进入默认的 **Dynamics 365 – 自定义**应用程序。 如果您希望在测试和使用统一接口应用程序的同时继续支持现有旧 Web 客户端应用程序，这是正常现象。  

## <a name="compare-your-new-app-to-the-default-dynamics-365-app"></a>比较新应用程序和默认 Dynamics 365 应用程序  
现在您已准备就绪，可以启动该应用程序。 您可以使用相同的数据、用户角色、业务规则、工作流、插件等（因为它们在同一个环境中）将新的统一接口应用程序与 Dynamics 365 – 自定义应用程序进行比较。 这样您就可以告诉组织，说明仍然保留了所有核心的基本要素，同时可以开始探索新的统一接口增强功能。  

> [!TIP]
> 如果要在一台显示器上并排显示应用程序，可以同时按住 Windows 和左箭头键（或右箭头键）在同一台显示器上拆分浏览器窗口。 

> [!NOTE]
> 如果要继续在默认站点地图中创建自定义项（如更改导航方式或针对按钮和操作进行功能区深度定制），需要通过再创建一个模型驱动应用程序重复执行此过程，或在与您的模型驱动应用程序有关的新站点地图中创建相同的自定义项。  

## <a name="validate-your-new-app"></a>验证新应用程序  
当应用程序展示统一接口之后，可以开始验证应用程序、流程和自定义项，以便识别转换的外观。 建议您测试所有用例，但是可以从最重要的开始，或将其分组为设计逻辑模式。 由于统一接口基于响应式设计，所以建议您始终使用不同屏幕分辨率的不同设备来执行测试。 测试应用程序时，可以验证自定义项是否兼容统一接口，是否有任何功能需要重新设计或缺少功能。  

> [!IMPORTANT]
> Dynamics 365 中的 Common Data Service 和模型驱动应用程序的当前版本中仍然包含若干已弃用功能。 您应检查您的应用程序中是否有任何已弃用功能，并根据需要替换为新功能。 详细信息：[即将做出的重要更改（弃用）](/dynamics365/get-started/whats-new/customer-engagement/important-changes-coming)

> [!TIP]
> PowerApps 检查器工具可帮助对解决方案的组件进行质量检查。  详细信息：[在 PowerApps 中使用解决方案检查器验证模型驱动应用程序](../common-data-service/use-powerapps-checker.md)

## <a name="next-steps"></a>后续步骤
您的实施团队或合作伙伴可以根据您的发现预估将您的应用程序转换为统一接口所需工作量，以及识别潜在的可用性改进。 由于统一接口中有多项新特性和功能，所以有机会提升对应用程序用户的价值。 

对您而言，转换为统一接口是一个很好的机会，因为您可以创建现代的用户界面，并重新访问您的现有流程以便验证这些流程是否仍然有效，是否需要改进。 这也是很好的时机，您可以考虑您的应用程序是否体现了您的业务需求，以及是否可以将现有应用程序分发给不同团队和角色的多个应用程序。
更多信息：[使用应用程序设计器设计模型驱动应用程序](design-custom-business-apps-using-app-designer.md) 

### <a name="see-also"></a>另请参阅
<!-- Unified Interface transition community (link tbd) <br />  -->
[统一接口 Playbook](unified-interface-playbook.md) <br />
[实现用户体验和统一接口转换](approaching-unified-interface.md) <br />
[关于统一接口](/dynamics365/customer-engagement/admin/about-unified-interface) <br />
[PowerApps 中的模型驱动应用程序是什么？](model-driven-app-overview.md) <br />
[将您的应用程序更新为统一接口](/dynamics365/customer-engagement/admin/update-apps-to-unified-interface) <br />
[配置模型驱动应用程序的交互式体验仪表板](configure-interactive-experience-dashboards.md) <br />
[使用自定义控件实现模型驱动应用程序的数据可视化](use-custom-controls-data-visualizations.md) <br />
[PowerApps component framework 概述](/powerapps/developer/component-framework/overview) <br />
[适用于所有人的统一接口](/power-platform-release-plan/2019wave2/microsoft-powerapps/unified-interface-app-everybody)
