---
title: 在 PowerApps 中控制对模型驱动应用程序窗体的访问 | MicrosoftDocs
description: 了解如何控制对主窗体的访问
ms.custom: ''
ms.date: 06/18/2019
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
ms.assetid: 15d123e0-b604-45dd-ab34-0b37787a04bb
caps.latest.revision: 33
ms.author: matp
manager: kvivek
tags: null
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="control-access-to-model-driven-app-forms"></a>控制对模型驱动应用程序窗体的访问

 有两种方式可以控制对主窗体的访问：  
  
- **停用主窗体**  
  
     可为主窗体设置活动或不活动状态。 加入此功能的主要目的是管理 Dynamics 365 customer engagement 组织升级时包括的新窗体，但也可以使用它来阻止用户使用任何主窗体。   
  
- **将安全角色分派给窗体**  
  
     使用使功能可使主窗体对特定的组可用。  
  
 组织中的不同人可以通过不同的方式与相同的数据交互。 经理可能需要快速扫描记录中信息的功能，服务人员可能需要能简化数据录入的窗体。 通过将窗体分派给不同的群体所属的安全角色，可以适应不同的要求。  
  
 有关分步过程，请参阅[向窗体分派安全角色](https://docs.microsoft.com/dynamics365/customer-engagement/admin/assign-security-roles-form)。  
  
 如果为实体定义了多个主窗体或其他窗体类型，您可以根据用户安全角色选择用户可以使用哪些窗体。 由于每个实体都必须能够针对任何用户显示窗体，因此必须至少将一个窗体指定为“回退”窗体，即，没有为其安全角色明确分派任何窗体的用户也可以看到的窗体。  
  
> [!NOTE]
>  不能向快速创建窗体、快速视图窗体和卡窗体分派安全角色。  
  
 您可以在“窗体”编辑器中或从“窗体”网格中将安全角色分派给主窗体。 但是，如果实体只有一个窗体，您将无法清除**分派安全角色**对话框中的**已启用回退**选项。 在这种情况下，即使您已将安全角色分派给窗体，与未包括的安全角色相关联的任何人仍将能够查看该窗体，因为已将其启用为回退窗体。  
  
 为实体创建第二个主窗体之后，您就可以针对其中一个窗体清除**已启用回退**选项。 系统始终会确保至少启用一个窗体作为回退窗体。  
  
 如果您具有多个主窗体，则可以指定窗体顺序来控制允许用户看到的哪个窗体将成为默认显示的窗体。 如果用户可以使用的窗体有多个，并且他们可以更改窗体，则他们选择的窗体将是其默认窗体，直到他们选择了其他窗体为止。 此首选项存在在用户的浏览器中。 如果他们使用了不同的计算机或浏览器，则将看到原来的默认窗体。  
  
## <a name="strategies-to-manage-the-fallback-form"></a>回退窗体的管理策略  
 用于管理回退窗体的策略包括以下内容：  
  
<a name="BKMK_DoNotUseMultipleForms"></a>   
### <a name="all-users-view-the-same-form"></a>所有用户查看同一个窗体。  
 如果某个实体不需要多个窗体，则不需要回退窗体。  
  
<a name="BKMK_Contingecyform"></a>   
### <a name="create-a-contingency-form"></a>创建应变窗体  
 如果您要限制他人可以查看或编辑的信息，所以要使用基于角色的窗体，请考虑创建显示的信息最少的窗体。 然后，在**分派安全角色**对话框中选择**只对这些所选的安全角色显示**，但是不要选择除“系统管理员”之外的任何角色，然后选择**已启用回退**。 结果是，除了系统管理员和其安全角色未与特定窗体相关联的人员之外，任何人都不能看到此窗体。 您可以在窗体中包含 HTML Web 资源，以告知用户为何窗体中几乎没有可见信息；还可以包含一个链接，指向介绍如何请求被添加到与窗体相关联的安全角色以便为窗体包含一个新安全角色的相关信息。  
  
> [!NOTE]
>  不能在窗体页眉或页脚中包括 Web 资源。  
  
<a name="BKMK_CreateGenericForm"></a>   
## <a name="create-a-generic-form"></a>创建通用窗体  
 如果您使用基于角色的窗体根据用户的角色提供自定义体验，则可以将专业化程度最低的窗体设置为回退窗体并将其配置为向所有人显示。 然后，针对特定的安全角色创建自定义窗体，并将这些窗体配置为只对需要它们的安全角色显示。 不要启用这些窗体作为回退窗体。 最后，在**窗体**列表中使用**窗体顺序**对话框按从专属性最强到专属性最弱的顺序指定要显示的窗体。 回退窗体将位于列表的底部。 实施此策略的结果是，人们会看到针对自己角色自定义的窗体显示为默认窗体，但是他们仍可以在需要时使用窗体选择器来选择最常用的窗体。 他们选择的任何窗体都将始终作为其默认窗体，直到他们选择了其他窗体时为止。  
  
<a name="BKMK_UseFormScripting"></a>   
## <a name="use-form-scripting"></a>使用窗体脚本  
客户端 API 窗体上下文 (formContext) 提供对窗体或窗体上的项目的引用，如快速视图控件或可编辑网格中的行，当前代码根据此引用执行。 详细信息：[客户端 API 窗体上下文](/dynamics365/customer-engagement/developer/clientapi/clientapi-form-context)

> [!IMPORTANT]
> 在 Dynamics 365 for Customer Engagement 应用版本 9.0 中，Xrm.Page 对象[已弃用](/dynamics365/get-started/whats-new/customer-engagement/important-changes-coming#some-client-apis-are-deprecated)，您应该使用在执行上下文对象中传递的 [getFormContext](/dynamics365/customer-engagement/developer/clientapi/reference/executioncontext/getformcontext) 方法返回对相应的窗体或窗体上的项目的引用。
<!-- 
 Finally, in the web application it is possible, but not recommended, for a developer to use scripts in the form Onload event to use the [Xrm.Page.ui.formSelector.items collection](http://go.microsoft.com/fwlink/p/?LinkID=513300) to query available forms and use the navigate method to direct users to a specific form. Remember that the [navigate method](http://go.microsoft.com/fwlink/p/?LinkID=513301) will cause the form to load again (and the Onload event to occur again). Your logic in the event handler should always check some condition before you use the navigate method to avoid an endless loop or unnecessarily restrict users options to navigate between forms.  
  
 This approach will not work for Dynamics 365 for tablets because multiple forms are not available for selection.  -->

### <a name="see-also"></a>另请参阅  

[将安全角色分派给窗体](https://docs.microsoft.com/dynamics365/customer-engagement/admin/assign-security-roles-form)
