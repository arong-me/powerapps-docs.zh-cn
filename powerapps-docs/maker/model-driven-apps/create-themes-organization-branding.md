---
title: 更改颜色方案或添加徽标以匹配您组织的品牌 | MicrosoftDocs
ms.custom: ''
ms.date: 02/19/2019
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
author: Mattp123
ms.assetid: 21a166a0-d25e-4260-a1e4-2ddc528787c2
caps.latest.revision: 17
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="create-a-theme"></a>创建主题

您可以通过更改未自定义系统中的默认颜色和视觉元素来为您的应用创建自定义外观和感觉（主题）。 例如，您可以创建自己的个人产品，方法是通过添加公司徽标并提供特定于实体的颜色。 使用用户界面的自定义工具创建主题，无需开发人员专门编写代码。 您可以创建、更改或删除在您的组织中使用的主题。 Dynamics 365 for Outlook 的 Web 窗体支持主题自定义功能。 您可以定义多个主题，但只由一个能被设置并发布为默认主题。  
  
<a name="UseThemes"></a>   
## <a name="use-themes-to-enhance-the-user-interface-and-create-your-product-branding"></a>使用主题加强用户界面，创建您的产品  
 主题化用于增强应用用户界面，不会进行大幅修改。 主题颜色在整个应用程序的全局范围内应用。 例如，可以增强以下 UI 的可视元素：  
  
-   更改产品徽标和导航颜色以创建产品  
  
-   调整主题色，例如悬停或选择颜色  
  
-   提供特定于实体的颜色  
    
-   徽标  
  
-   徽标工具提示  
  
-   导航栏颜色  
  
-   导航条颜色

-   统一接口中的主命令栏颜色
  
-   标题颜色  
  
-   全局链接颜色  
  
-   选定链接的效果  
  
-   鼠标悬停链接的效果  
  
-   旧版主题色（流程控件的主背景）  
  
-   默认实体颜色  
  
-   默认自定义实体颜色  
  
-   控件阴影  
  
-   控件边框  
  
<a name="Solution"></a>   
## <a name="solution-awareness"></a>解决方案知名度  
 主题不是可识别解决方案。 从组织导出的解决方案不包括为组织主题所做的更改。 数据存储在可以导出并可以重新导入其他环境的主题实体中。 导入的主题必须发布才能生效。  
  
<a name="CloneAlter"></a>   
## <a name="copy-and-alter-the-existing-theme"></a>复制并修改现有主题  
 最简单、最快捷的新主题创建方法是克隆和修改现有主题，然后保存它，进行预览和发布。 
 
1.  登录到 [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。

2.  选择**模型驱动**（左下方）。 

3.  选择![“设置”图标](../model-driven-apps/media/powerapps-gear.png)（右上角）>**高级自定义**。 

4. 在**主题**下选择**所有主题**。 

5. 选择 **CRM 默认主题**。 

以下屏幕截图显示默认主题设置的一部分。  

> [!div class="mx-imgBorder"] 
> ![默认主题](media/default-theme.png) 
  
 我们克隆了默认主题并更改了颜色。 以下屏幕截图显示了导航和突出显示颜色。 您还可以为产品选择新的徽标。  
  
 以下屏幕截图显示新导航颜色。  
 
 > [!div class="mx-imgBorder"] 
 > ![淡绿色主题颜色](media/theme-gentle-green.png "淡绿色主题颜色")  
  
 以下屏幕截图显示具有突出显示颜色的客户实体网格。  
 
 > [!div class="mx-imgBorder"] 
 > ![淡绿色主题客户网格](media/themes-gentle-green-account-grid.png "淡绿色主题客户网格")  
  
<a name="Publish"></a>   
## <a name="preview-and-publish-a-theme"></a>预览并发布主题  
 若要预览和发布主题，请执行以下步骤：  
  
-   从头开始创建新主题或克隆现有主题。  
  
-   通过选择命令栏上的**预览**来预览新主题。 要退出预览模式，请选择命令栏上**预览**按钮旁边的**退出预览**。  
  
-   发布主题。 在命令栏上，选择**发布主题**。  
  
 以下屏幕截图显示命令栏上的预览和发布按钮。  
  
 ![使用预览按钮进入/退出预览模式](media/themes-preview-buttons.PNG "使用预览按钮进入/退出预览模式")  
  
<a name="BestPracticies"></a>   
## <a name="best-practices"></a>最佳实践  
 以下是针对设计主题对比度和选择颜色的一些建议。  
  
### <a name="theme-contrast"></a>主题对比度  
 建议使用以下方法提供对比色：  
  
-   请仔细选择对比色。 面向应用程序的 Common Data Service 的现成默认主题拥有正确的对比度可以确保最佳使用。 为您的新主题使用类似的比率。  
  
-   对于高对比度模式，请使用默认的颜色设置。  
  
### <a name="theme-colors"></a>主题颜色  
 我们建议不要使用大量不同颜色。 虽然您可以为每个实体设置不同的颜色，建议您采用两种模式之一：  
  
-   对所有实体使用中性色，并突出显示关键实体。  
  
-   对类似的实体或相关实体使用相同颜色，如队列和队列项或产品目录实体。 保持较少的组总数。  
  
<a name="Considerations"></a>   
## <a name="custom-theme-considerations"></a>自定义主题注意事项  
 在规划自定义主题的使用时您应考虑以下问题：  
  
-   大多数更新的用户界面 (UI) 区域将显示为自定义主题颜色。  
  
-   即使主题颜色会全局应用于整个应用程序，有些旧 UI 区域（例如渐变按钮）仍会保留默认颜色。  
  
-   某些区域必须使用暗色或亮色以与默认图标颜色形成对比。 图标颜色不可自定义。  
  
-   实体不能在不同的站点地图节点下显示为不同颜色。  
  
-   站点地图节点颜色不可自定义。  
  
## <a name="see-also"></a>另请参阅  
         
 [视频：Dynamics 365 Customer Engagement 中的主题](http://go.microsoft.com/fwlink/p/?LinkId=529568) [查询和编辑组织主题](https://docs.microsoft.com/dynamics365/customer-engagement/developer/customize-dev/query-and-edit-an-organization-theme)

