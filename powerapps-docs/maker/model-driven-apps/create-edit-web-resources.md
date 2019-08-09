---
title: 在 PowerApps 中创建或编辑模型驱动应用程序 Web 资源 | MicrosoftDocs
description: 了解如何创建或编辑 Web 资源
ms.custom: ''
ms.date: 06/02/2018
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
ms.assetid: ef4ba8df-9ba9-4066-b40d-def9761c7de2
caps.latest.revision: 21
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="create-or-edit-model-driven-app-web-resources-to-extend-an-app"></a>创建或编辑模型驱动应用程序 Web 资源以扩展应用程序

开发人员通常使用 Web 资源用于扩展应用，这些应用程序使用 Web 开发中用到的文件。 应用用户可能需要管理由开发人员或设计器提供的 Web 资源。  

> [!TIP]
> 有关 Web 资源的深入讨论，请参阅[开发人员文档：Customer Engagement 的 Web 资源](/dynamics365/customer-engagement/developer/web-resources)。<br /> 有关 PowerApps 中添加的 Web 资源依赖项的信息，请参阅[开发人员文档：Web 资源依赖项](/dynamics365/customer-engagement/developer/web-resources)。
   
<a name="BKMK_WhatAreWebResources"></a>

## <a name="what-are-web-resources"></a>什么是 Web 资源？  

Web 资源是存储在系统中的虚拟文件。 每个 Web 资源都有一个可以在 URL 中用来检索文件的唯一名称。 把它们认为是这样：如果访问过运行 Web 应用的实际 Web 服务器，您可以将文件复制到该网站。 但通过大多数联机服务，无法执行此操作。  相反，您可以使用 Web 资源将文件上载到系统然后使用名称来引用它们，请像将其复制为文件放到 Web 服务器上一样。  
  
例如，如果创建了一个 HTML 页并将其作为一个 Web 资源命名为“new_myWebResource.htm”，就可以使用如下 URL 在浏览器中打开该页：  
 
`<base URL>/WebResources/new_myWebResource.htm`
  
其中*\<基本 URL>* 是您用于查看以 `dynamics.com` 结尾的应用程序的 URL 的一部分。 由于 Web 资源是系统中的数据，所以只有您组织中的许可用户可以这样访问它们。 通常，Web 资源包含在窗体之中，而不能直接被引用。 最常见用法是对窗体脚本提供 JavaScript 库。  
    
由于 Web 资源是系统中的数据，并且与解决方案相关，所以可以通过将它们作为解决方案的一部分进行导出并将该解决方案导入到另一个组织中，从而将其移至不同的组织。 您必须使用解决方案资源管理器来处理 Web 资源。
  
## <a name="open-solution-explorer"></a>打开解决方案资源管理器

您创建的任何 Web 资源的名称中包含自定义项前缀。 这是根据您在其中工作的解决方案的解决方案发布商设置的。 如果您关心自定义项前缀，请确保在非托管解决方案中工作，其中的自定义项前缀是您需要的此 Web 资源的前缀。 详细信息：[更改解决方案发布商前缀](../common-data-service/change-solution-publisher-prefix.md) 

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

## <a name="view-web-resources"></a>查看 Web 资源

打开解决方案资源管理器，在**组件**下选择 **Web 资源**。

![查看 Web 资源](media/view-web-resources-solution-explorer.png)

<a name="BKMK_CreateAndEditWebResources"></a>

## <a name="create-or-edit-web-resources"></a>创建或编辑 Web 资源  

在[查看 Web 资源](#view-web-resources)时，选择**新建**创建新 Web 资源或双击现有的 Web 资源进行编辑。

![新建 Web 资源窗体](media/new-web-resource-form.png)

完成此窗体以创建或编辑 Web 资源：
  
|字段|说明|  
|-----------|-----------------|  
|**名称**|*必需*。 这是此 Web 资源特有的名称。 保存 Web 资源之后，就不能对此进行更改。<br />&bull; 此名称只能包含字母、数字、句点和不连续的正斜杠 (“/”) 字符。<br /> &bull; 解决方案发布商的自定义前缀将附加到该 Web 资源的名称上。|  
|**显示名称**|如果您查看 Web 资源列表，则会显示该名称。|  
|**说明**|Web 资源说明。|  
|**类型**|*必需*。 这是 Web 资源的类型。 保存 Web 资源之后，就不能对此进行更改。|  
|**文本编辑器**|当 Web 资源类型表示一种文本文件时，请选择此按钮打开一个页面，使用文本编辑器编辑其内容。<br />详细信息：[正确使用文本编辑器](#use-the-text-editor-appropriately)| 
|**语言**|允许选择一种语言。 此选项仅标记存储 Web 资源数据的记录。 它不更改 Web 资源的行为。|  
|**上载文件**|选择**浏览…** 按钮选择要上载为 Web 资源的文件。<br />&bull; 在创建新 Web 资源或要覆盖现有的 Web 资源时，可上载文件。<br />&bull; 文件的文件名扩展必须与允许使用的扩展相匹配。<br />&bull;默认情况下，可以上载为 Web 资源的最大文件大小为 5MB。 可使用**系统设置** > **电子邮件**选项卡 > **设置附件的文件大小限制**设置来在 Dynamics 365 customer engagement 中修改此值。 更多信息：[“系统设置”对话框 -“电子邮件”选项卡](https://docs.microsoft.com/dynamics365/customer-engagement/admin/system-settings-dialog-box-email-tab) |  
|**URL**|保持 Web 资源之后，此处会显示访问该 Web 资源的 URL。 选择该链接，在浏览器中查看该 Web 资源。|  
  
添加了您的更改之后，选择**保存**，然后选择**发布**。  

> [!NOTE]
> 对 Web 资源进行的更改不会显示在应用程序中，除非您发布它。
  
<a name="BKMK_UsingTextEditor"></a>
   
### <a name="use-the-text-editor-appropriately"></a>正确使用文本编辑器

Web 资源的应用程序中提供的文本编辑器只能用于简单的文本文件的编辑。 您可以使用它创建和编辑 HTML Web 资源，但是，您只能编辑使用文本编辑器编辑的 HTML Web 资源。 文本编辑器适用于非常简单的 HTML 内容。 

> [!IMPORTANT]
> 如果 HTML Web 资源的内容并不是使用文本编辑器来创建的，就不要使用文本编辑器对其进行编辑。  
> 文本编辑器使用的控件可以以准许的编辑方式来修改 HTML 资源。 这些更改可以使浏览器中页面的表现行为有所不同，并导致更为复杂的代码停止工作。 使用文本编辑器打开一个 HTML Web 资源并将其不加任何更改地进行保存，这可能会破坏某些 HTML Web 资源。  详细信息：[开发人员文档：使用文本编辑器编辑 HTML Web 资源](/dynamics365/customer-engagement/developer/webpage-html-web-resources#use-the-text-editor-for-html-web-resources)
  
我们建议您使用外部编辑器编辑文本文件，然后将它们保存在本地，之后再使用**上载文件**按钮将它们上载。 如果需要返回到早期版本，使用这种方法就可以保留 Web 资源的副本。 可使用类似记事本的简单编辑器，但是，强烈建议您使用具有更加高级的功能的文本编辑器。 [Visual Studio 社区](https://www.visualstudio.com/vs/community/)和 [Visual Studio 代码](https://code.visualstudio.com/)是免费的，它为编辑 Web 资源所使用的基于文本的文件提供强大的功能。  

<a name="BKMK_CreateAndEditFormWebResources"></a>
 
## <a name="create-and-edit-a-web-resource-on-a-form"></a>在窗体中创建和编辑 Web 资源

您可以添加或编辑表单上的 web 资源，使其对用户而言更具吸引力或更有用。 

> [!NOTE]
> 不能在窗体页眉或页脚中包括 Web 资源。  

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

### <a name="navigate-to-a-form"></a>导航到窗体
打开解决方案资源管理器，在**组件**下，展开**实体**，然后展开工作时所需实体。

选择**窗体**，在列表中找到“主要”类型窗体，然后双击或点按打开和编辑窗体。

### <a name="add-or-edit-web-resource-in-a-form"></a>在窗体中添加或编辑 Web 资源

请参阅 [Web 资源属性](web-resource-properties-legacy.md)了解您可以在窗体中为 Web 资源设置的属性的信息。

### <a name="preview"></a>预览

预览主窗体的显示方式以及事件的运行方式：
- 在**主页**选项卡上，选择**预览**，然后选择**创建表单**、**更新表单**或**只读表单**。
- 若要关闭“预览”表单，请在**文件**菜单上，选择**关闭**。

### <a name="save"></a>保存

窗体编辑完成后，请在**主页**选项卡上，选择**保存并关闭**以关闭窗体。 

### <a name="publish"></a>Publish

完成自定义后，发布自定义项：
- 若只为您当前编辑的组件发布自定义项，在导航窗格中，选择您一直在处理的实体，然后选择**发布**。
- 若要同时为所有未发布组件发布自定义项，在导航窗格中，选择**实体**，然后在**操作**工具栏上选择**发布所有自定义项**。
   
  
### <a name="see-also"></a>另请参阅  

[Web 资源属性](web-resource-properties-legacy.md) <br /> 
[创建和设计窗体](create-design-forms.md) <br />
[了解模型驱动的应用程序组件](model-driven-app-components.md) <br /> 
[开发人员文档：Customer Engagement 的 Web 资源](/dynamics365/customer-engagement/developer/web-resources)
