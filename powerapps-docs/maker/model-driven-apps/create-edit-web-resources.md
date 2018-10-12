---
title: 在 PowerApps 中创建或编辑模型驱动应用 Web 资源 | MicrosoftDocs
description: 了解如何创建或编辑 Web 资源
ms.custom: ''
ms.date: 06/02/2018
ms.reviewer: ''
ms.service: crm-online
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
ms.openlocfilehash: 8d9414ba4c900f98ac26010e4e6d7240b336e2d7
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39669131"
---
# <a name="create-or-edit-model-driven-app-web-resources-to-extend-an-app"></a>创建或编辑模型驱动应用 Web 资源以扩展应用

开发人员通常使用 Web 资源来扩展使用 Web 开发中所用文件的应用。 应用用户可能需要管理开发人员或设计人员提供的 Web 资源。  

> [!TIP]
> 有关 Web 资源的深入介绍，请参阅[开发人员文档：用于 Customer Engagement 的 Web 资源](/dynamics365/customer-engagement/developer/web-resources)。<br /> 有关在 PowerApps 中添加的 Web 资源依赖项的信息，请参阅[开发人员文档：Web 资源依赖项](/dynamics365/customer-engagement/developer/web-resources)。
   
<a name="BKMK_WhatAreWebResources"></a>

## <a name="what-are-web-resources"></a>什么是 Web 资源？  

Web 资源是存储在系统中的虚拟文件。 每个 Web 资源都有一个唯一的名称，可以在 URL 中使用该名称来检索文件。 可以这么说：如果有权访问运行 Web 应用的实际 Web 服务器，就可以将文件复制到该网站。 但在使用大多数联机服务时，无法执行此操作。  而使用 Web 资源时，可以将文件上载到系统，然后按名称引用它们，就像已经将它们作为文件复制到 Web 服务器一样。  
  
例如，如果将 HTML 页面创建为名为“new_myWebResource.htm”的 Web 资源，则可以使用如下 URL 在浏览器中打开该页面：  
 
`<base URL>/WebResources/new_myWebResource.htm   `
  
其中 *\<base URL>* 是用来查看以 `dynamics.com` 结尾的应用的 URL 的一部分。 由于该 Web 资源是系统中的数据，因此只有贵组织的许可用户才能以这种方式访问​​它们。 通常情况下，Web 资源包含在窗体中，而不是直接引用。 最常见的用法是为窗体脚本提供 JavaScript 库。  
    
由于 Web 资源是系统中的数据并且可以识别解决方案，因此可以将它们作为解决方案的一部分导出并将解决方案导入其他组织，从而将它们移至其他组织。 必须使用解决方案资源管理器来处理 Web 资源。
  
## <a name="open-solution-explorer"></a>打开解决方案资源管理器

所创建的任何 Web 资源的名称中都包含自定义前缀。 这是根据所用解决方案的解决方案发布者设置的。 如果很在意自定义前缀，请确保使用的是非托管解决方案，其中自定义前缀是你希望此 Web 资源使用的前缀。 详细信息：[更改解决方案发布者前缀](../common-data-service/change-solution-publisher-prefix.md) 

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

## <a name="view-web-resources"></a>查看 Web 资源

打开解决方案资源管理器后，在“组件”下选择“Web 资源”。

![查看 Web 资源](media/view-web-resources-solution-explorer.png)

<a name="BKMK_CreateAndEditWebResources"></a>

## <a name="create-or-edit-web-resources"></a>创建或编辑 Web 资源  

[查看 Web 资源](#view-web-resources)时，可选择“新建”创建新的 Web 资源，或双击现有 Web 资源进行编辑。

![“新建 Web 资源”窗体](media/new-web-resource-form.png)

填写窗体以创建或编辑 Web 资源：
  
|字段|描述|  
|-----------|-----------------|  
|**名称**|*必填*。 这是此 Web 资源的唯一名称。 保存 Web 资源后，便无法更改此设置。<br />&bull; 此名称只能包含字母、数字、句点和非连续正斜杠（“/”）字符。<br /> &bull; 解决方案发布者自定义前缀将添加到 Web 资源名称的前面。|  
|**显示名称**|查看 Web 资源列表时所显示的名称。|  
|**Description**|对 Web 资源的说明。|  
|**类型**|*必填*。 这是 Web 资源的类型。 保存 Web 资源后，便无法更改此设置。|  
|**文本编辑器**|当 Web 资源的类型表示一种文本文件时，选择此按钮可打开页面以使用文本编辑器编辑内容。<br />详细信息：[适当使用文本编辑器](#use-the-text-editor-appropriately)| 
|**语言**|允许选择语言。 此选项仅标记存储 Web 资源数据的记录。 它不会更改 Web 资源的行为。|  
|**上载文件**|选择“浏览...” 按钮以选择要作为 Web 资源上载的文件。<br />&bull; 可以在创建新的 Web 资源时上载文件或覆盖现有 Web 资源。<br />&bull; 文件的文件扩展名必须与允许的扩展名匹配。<br />&bull; 默认情况下，可以作为 Web 资源上载的最大大小文件为 5MB。 可以使用“系统设置” > “电子邮件”选项卡 >“设置附件的文件大小限制”设置，在 Dynamics 365 Customer Engagement 中修改此值。 详细信息：[系统设置对话框 - 电子邮件选项卡](https://docs.microsoft.com/dynamics365/customer-engagement/admin/system-settings-dialog-box-email-tab) |  
|**URL**|保存 Web 资源后，将在此处显示 Web 资源的 URL。 选择此链接可在浏览器中查看 Web 资源。|  
  
添加更改后，选择“保存”，然后选择“发布”。  

> [!NOTE]
> 在发布之前，应用程序中不会显示对 Web 资源的更改。
  
<a name="BKMK_UsingTextEditor"></a>
   
### <a name="use-the-text-editor-appropriately"></a>适当使用文本编辑器

应用程序中针对 Web 资源提供的文本编辑器只能用于文本文件的简单编辑。 它可以用来创建和编辑 HTML Web 资源，但只能编辑使用文本编辑器创建的 HTML Web 资源。 文本编辑器专为非常简单的 HTML 内容而设计。 

> [!IMPORTANT]
> 如果 HTML Web 资源的内容不是使用文本编辑器创建的，请不要使用文本编辑器对其进行编辑。  
> 文本编辑器使用一种控件，该控件通过编辑 HTML 源来对其进行修改。 这些更改可能会使页面在浏览器中的行为方式不同，导致更复杂的代码停止工作。 如果使用文本编辑器打开 HTML Web 资源并保存它而不进行任何更改，可能会中断一些 HTML Web 资源。  详细信息：[开发人员文档：对 HTML Web 资源使用文本编辑器](/dynamics365/customer-engagement/developer/webpage-html-web-resources#use-the-text-editor-for-html-web-resources)
  
我们建议使用外部编辑器来编辑文本文件并将其保存在本地，然后再使用“上载文件”按钮进行上载。 这样可以保留 Web 资源的副本，以应对需要恢复到较早版本的情况。 可以使用记事本之类的简单编辑器，但强烈建议使用具有更高级的功能的文本编辑器。 [Visual Studio 社区](https://www.visualstudio.com/vs/community/)和 [Visual Studio Code](https://code.visualstudio.com/) 都是免费的编辑器，可提供强大的功能来编辑 Web 资源所用的基于文本的文件。  

<a name="BKMK_CreateAndEditFormWebResources"></a>
 
## <a name="create-and-edit-a-web-resource-on-a-form"></a>在窗体上创建和编辑 Web 资源

可以在窗体上添加或编辑 Web 资源，使其对用户更具吸引力或更有用。 

> [!NOTE]
> 不能在窗体页眉或页脚中包含 Web 资源。  

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

### <a name="navigate-to-a-form"></a>导航到窗体
打开解决方案资源管理器后，在“组件”下展开“实体”，然后展开要处理的实体。

选择“窗体”，在列表中找到 Main 类型的窗体，然后双击或点击该条目以打开并编辑窗体。

### <a name="add-or-edit-web-resource-in-a-form"></a>在窗体中添加或编辑 Web 资源

有关可以为窗体中的 Web 资源设置的属性的信息，请参阅 [Web 资源属性](web-resource-properties-legacy.md)。

### <a name="preview"></a>预览

若要预览主窗体的显示方式以及事件的运行方式，请执行以下操作：
- 在“主页”选项卡上，选择“预览”，然后选择“创建窗体”、“更新窗体”或“只读窗体”。
- 若要关闭“预览”窗体，请在“文件”菜单上选择“关闭”。

### <a name="save"></a>保存

完成窗体编辑后，在“主页”选项卡上选择“保存并关闭”以关闭窗体。 

### <a name="publish"></a>发布

完成自定义项后进行发布：
- 若要仅为当前正在编辑的组件发布自定义项，请在导航窗格中选择正在处理的实体，然后选择“发布”。
- 若要一次性发布所有未发布组件的自定义项，请在导航窗格中选择“实体”，然后在“操作”工具栏上选择“发布所有自定义项”。
   
  
### <a name="see-also"></a>另请参阅  

[Web 资源属性](web-resource-properties-legacy.md) <br /> 
[创建并设计窗体](create-design-forms.md) <br />
[自定义入门](getting-started-customization.md) <br /> 
[开发人员文档：用于 Customer Engagement 的 Web 资源](/dynamics365/customer-engagement/developer/web-resources)
