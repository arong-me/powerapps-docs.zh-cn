---
title: 从旧 Web 客户端应用程序转换到统一接口的快速入门指南 | MicrosoftDocs
description: 了解如何从旧 Web 客户端应用程序转换到统一接口
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
ms.assetid: 14c4c18c-927c-4ea2-ba66-0531285a99a7
caps.latest.revision: 25
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="quick-start-for-transitioning-your-legacy-web-client-application-to-unified-interface"></a>从旧 Web 客户端应用程序转换到统一接口的快速入门指南

此统一接口框架使用响应式 Web 设计原则，为任何屏幕尺寸、设备或方向提供最佳的查看和交互体验。 此快速入门指南主题介绍如何使用新的非生产环境将旧 Web 客户端应用程序转换为统一接口。 

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE3JwWU]

若要使用现有非生产环境转换 Web 客户端应用程序，请参阅[使用现有环境和统一接口验证旧 Web 客户端应用入门指南](transition-web-app-existing.md)。 
## <a name="prerequisites"></a>必备条件
- 旧 Web 客户端应用程序。 
- 尽管不是必需，但是我们还是建议使用非生产环境测试应用程序并确保不影响当前部署或开发周期。 详细信息：[管理沙盒实例](/dynamics365/admin/manage-sandbox-instances)

## <a name="prepare-the-environment"></a>准备环境
首先，选择一个非生产环境并启用**将使用统一接口**模式，该模式对环境中的所有模型驱动应用程序都使用统一接口。 其中还包含最初为旧 Web 客户端配置的所有 Dynamics 365 应用程序模块。

1. 登录 [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)，选择**环境**，然后选择一个沙盒环境。 

2. 选择**设置** > **行为**，然后打开**仅使用统一接口**。

   > [!div class="mx-imgBorder"] 
   > ![仅使用统一接口设置](media/use-unified-interface-only-pac.png)

您还可以在设置区域中设置此项。 转到**设置** > **管理** > **系统设置**，然后将**常规**选项卡上的**仅启用统一接口**设置为**是**。

> [!div class="mx-imgBorder"] 
> ![仅使用新统一接口](media/use-unified-interface-only.png "仅使用新统一接口")


> [!NOTE]
> 如果需要将环境切换回之前的状态，可以切换统一接口设置以恢复为原始接口。 详细信息：[仅启用统一接口](/dynamics365/customer-engagement/admin/enable-unified-interface-only)

## <a name="run-and-validate-your-application-in-the-unified-interface"></a>在统一接口中运行和验证应用程序
运行最初为 Web 客户端应用程序的应用程序。 请注意，开启**仅使用统一接口**之后，环境中的所有可用应用程序都将使用统一接口，即使应用程序最初是针对 Web 客户端配置的也不例外。

若要运行您的应用程序，请登录 [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)，选择**应用程序**，然后选择要运行的应用程序。 也可以直接访问**我的应用程序**页面，如 *https://contoso.crm.dynamics.com/apps/*。

### <a name="validate-your-app-processes-and-customizations"></a>验证您的应用程序、流程和自定义项 
建议测试所有用例。 可以从最关键的用例开始，或将其分组为设计逻辑模式。 由于统一接口基于响应式设计，所以建议您使用不同屏幕分辨率的不同设备来执行测试。 测试应用程序时，可以验证自定义项是否兼容统一接口，是否有任何功能需要重新设计或缺少功能。 指定计划来检查这些元素，并在社区论坛发布问题和反馈。 

> [!IMPORTANT]
> Dynamics 365 中的 Common Data Service 和模型驱动应用程序的当前版本中仍然包含若干已弃用功能。 您应检查您的应用程序中是否有任何已弃用功能，并根据需要替换为新功能。 详细信息：[即将做出的重要更改（弃用）](/dynamics365/get-started/whats-new/customer-engagement/important-changes-coming)

### <a name="dynamics-365-apps"></a>Dynamics 365 应用程序
如果使用 Dynamics 365 Field Service 或 Dynamics 365 Project Service Automation 应用程序，并希望测试统一接口，则在统一接口中验证这些应用程序之前，必须设置新的沙盒环境，并为生产环境创建副本或将其升级为最新的 Field Service 版本和 Project Service Automation 版本。 为此，请按照以下步骤操作：

1. 从 [Power Platform 管理中心](https://admin.powerplatform.microsoft.com/environments)或 [Dynamics 365 管理中心](https://port.crm.dynamics.com/)创建一个新的沙盒环境。 详细信息：[向订阅中添加实例](/dynamics365/customer-engagement/admin/add-instance-subscription)

2. 将具有 Dynamics 365 Field Service 或 Dynamics 365 Project Service Automation 应用程序的生产环境复制到新的沙盒环境中。 方法是，在 Power Platform 管理中心打开您的生产环境，然后选择**复制**。

    > [!div class="mx-imgBorder"] 
    > ![复制环境](media/ppac-copy-environment.png "复制环境")

3. 在**复制环境**页中，选择**所有内容**，从**选择要覆盖的环境**列表中选择您的新沙盒环境，然后选择**复制**。 

    > [!div class="mx-imgBorder"] 
    > ![覆盖环境](media/ppac-copy-overwrite.png "覆盖环境")

4. 将显示**覆盖环境**对话框。 确保已选择正确环境和正确选项，然后选择**确认**。 

5. 复制成功后，将显示确认通知。 

6. 在菜单栏中，选择**管理解决方案**以打开**解决方案**区域。 

    > [!div class="mx-imgBorder"] 
    > ![管理解决方案](media/ppac-manage-solutions.png "管理解决方案")

    > [!IMPORTANT]
    > 如果启用了**管理模式**，必须先将其禁用，这样才能查看**解决方案**区域。 详细信息：[管理模式](/power-platform/admin/sandbox-environments#administration-mode)

7. 找到 Field Service 或 Project Service Automation 解决方案并选择。 **升级**选项应可用。 选择以升级解决方案。 

    > [!div class="mx-imgBorder"] 
    > ![升级解决方案](media/ppac-upgrade-solution.png "升级解决方案")
    
> [!NOTE]
> 默认情况下，统一接口中的最新 Field Service 和 Project Service Automation 版本仅对新建的实例可用。 如果要升级安装了较早版本的现有环境，必须联系 [Microsoft 客户支持](https://go.microsoft.com/fwlink/?LinkId=853505)申请升级。 

详细信息：[Dynamics 365 for Field Service 最新版本](/dynamics365/customer-engagement/field-service/version-history#latest-versions)和 [Dynamics 365 for Project Service Automation 升级主页](/dynamics365/customer-engagement/project-service/upgrade-psa-home-page)

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

