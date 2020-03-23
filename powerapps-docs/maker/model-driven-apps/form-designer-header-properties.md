---
title: 在窗体设计器中配置页眉属性 | MicrosoftDocs
ms.custom: ''
ms.date: 09/30/2019
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- PowerApps
author: Aneesmsft
ms.author: matp
manager: kvivek
tags:
- Power Apps maker portal impact
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 67173c01bc6a96f0ada55c62688db76ca0af0596
ms.sourcegitcommit: 6cffa70358fd2e388d64a01f906c8c196fbbdefb
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/17/2020
ms.locfileid: "3069659"
---
# <a name="configure-header-properties-in-the-form-designer"></a>在窗体设计器中配置页眉属性

开发者可以控制模型驱动应用程序窗体页眉的密度，以便满足任何用户的需要。

## <a name="high-density-header"></a>高密度页眉

高密度窗体页眉可以确保始终向用户显示关键信息。 如果使用高密度页眉，则始终不会截断记录标题。 将多行显示极长的记录标题。 同样，高密度页眉还可以确保在页眉中直接显示最多四个字段值，并且始终不会截断或隐藏这些字段值。  

为了确保始终显示关键信息，此框架显示只读字段值，而用户则不能直接编辑页眉中的字段值。 也不允许使用自定义组件或 Web 资源之类可视化效果。

如果不为窗体指定页眉密度或在创建新窗体时，此框架默认使用高密度页眉。

> [!div class="mx-imgBorder"] 
> ![高密度窗体页眉](media/form-header-high-density.png "高密度窗体页眉")
    
## <a name="low-density-header"></a>低密度页眉
低密度窗体页眉允许用户直接编辑页眉中的字段值。 还允许使用自定义组件和 Web 资源之类可视化效果。  
  
但是，这通常会带来关键信息截断或无法轻松显示之类牺牲。 低密度页眉会截断记录标题和页眉中显示的字段值。 页眉中通常仅直接显示一个或两个字段，其余字段会溢出，需要额外单击才会弹出显示。

> [!div class="mx-imgBorder"] 
> ![低密度窗体页眉](media/form-header-low-density.png "低密度窗体页眉")

### <a name="configuring-header-density"></a>配置页眉密度

若要配置模型驱动窗体的页眉密度，请执行以下步骤：
1.  打开窗体设计器[创建或编辑窗体](create-and-edit-forms.md)。
2.  选择窗体页眉，方法是在窗体预览中选择，或使用[树视图](using-tree-view-on-form.md)。
3.  在属性窗格中，选中**高密度**以使用高密度窗体页眉，或清除以使用低密度窗体页眉。
4.  在命令栏中，选择**保存**保存窗体，或选择**发布**以保存更改并向用户显示。

> [!NOTE]
> 使用新窗体设计器。 经典窗体设计器不能配置页眉密度。

## <a name="header-flyout"></a>页眉弹出项目
用户在窗体页眉中选择 V 形控件时，将显示页眉弹出项目。 供用户编辑字段值，并显示窗体页眉中的可视化效果，如自定义组件或 Web 资源。

页眉弹出项目的行为根据页眉密度配置改变。

### <a name="high-density-header-flyout"></a>高密度页眉弹出项目
如果使用高密度窗体页眉，则页眉弹出项目将显示所有页眉字段，包括页眉中直接显示的四个字段。 如果使用高密度页眉，此框架默认显示页眉弹出项目。 开发者可以控制高密度页眉的页眉弹出项目的显示。

> [!div class="mx-imgBorder"] 
> ![具有高密度页眉的页眉弹出项目](media/form-header-flyout-high-density.png "具有高密度页眉的页眉弹出项目")

### <a name="low-density-header-flyout"></a>低密度页眉弹出项目
如果使用低密度窗体页眉，页眉弹出项目将仅显示溢出字段，如窗体根据窗体宽度无法在页眉中直接显示的字段。 还将根据页眉中的字段数量和窗体宽度自动显示或隐藏页眉弹出项目。 如果使用低密度页眉，则开发者不能控制页眉弹出项目的显示。

> [!div class="mx-imgBorder"] 
> ![具有低密度页眉的页眉弹出项目](media/form-header-flyout-low-density.png "具有低密度页眉的页眉弹出项目")

### <a name="show-or-hide-the-header-flyout"></a>显示或隐藏页眉弹出项目
若要显示或隐藏模型驱动窗体的页眉弹出项目，请执行以下步骤：

1.  打开窗体设计器[创建或编辑窗体](create-and-edit-forms.md)。
2.  在窗体预览中选择窗体页眉，或使用[树视图](using-tree-view-on-form.md)进行选择。
3.  在属性窗格中，选择**高密度**以使用高密度窗体页眉。 
4.  在属性窗格中，选中**显示页眉弹出项目**以显示页眉弹出项目，或清除以隐藏页眉弹出项目。
5.  在命令栏中，选择**保存**保存窗体，或选择**发布**以保存更改并向用户显示。

> [!NOTE]
> - 使用新窗体设计器。 经典窗体设计器不能显示或隐藏页眉弹出项目。   
> - 只有在使用高密度窗体页眉时，才能控制页眉弹出项目的显示。 使用低密度页眉时，将根据页眉中的字段数量和窗体宽度自动显示或隐藏页眉弹出项目。
> - 仅当为实体定义了**主要图像**属性，并且启用了**在窗体中显示图像**窗体属性，才将在页眉中显示实体的图像。 详细信息：[图像字段](../common-data-service/types-of-fields.md#image-fields)。 <br />
    开发人员可使用 [EntityMetadata.PrimaryImageAttribute](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.metadata.entitymetadata.primaryimageattribute?view=dynamics-general-ce-9) 属性为实体指定图像。 


## <a name="form-designer-messages-related-to-form-headers"></a>与窗体页眉有关的窗体设计器消息
使用新窗体设计器或经典窗体设计器编辑窗体时，可能会看到与窗体页眉有关的消息。 下面提供有关每条消息的详细信息和显示的原因。

### <a name="weve-upgraded-your-form-to-show-a-high-density-header-that-displays-more-data-you-can-edit-this-setting-in-the-properties-of-the-header"></a>我们已升级了您的窗体，以便显示高密度页眉，其中显示的数据更多。 可以在页眉的属性中编辑此设置。 
当开发者创建新的主窗体（包括通过“另存为”操作创建）或编辑以前尚未配置页眉密度的主窗体时，窗体设计器中将显示此消息。  
  
此框架默认使用高密度页眉，而此消息则可以帮助开发者注意该行为。 开发者随时可以按照前面的概述通过手动配置窗体页眉密度来覆盖框架默认设置。

### <a name="this-form-isnt-using-high-density-header-access-the-setting-in-the-header-properties-high-density-header-helps-display-more-data"></a>此窗体不使用高密度页眉，请在窗体属性中访问设置。 高密度窗体有助于显示更多数据。 
当开发者打开配置为使用低密度页眉的主窗体进行编辑时，将在窗体编辑器中显示此消息。 

此消息可帮助提高对高密度页眉及其优点的关注。

### <a name="field-moved-to-header-flyout-the-header-supports-displaying-up-to-four-read-only-field-values-the-field-field-display-name-will-now-only-be-available-from-the-flyout"></a>字段已移到页眉弹出项目：页眉支持显示最多四个只读字段值。 现在只有弹出项目中才显示字段 *[字段显示名称]*。
当窗体使用高密度页眉并显示页眉弹出项目时，窗体设计器中将显示此消息。  
  
高密度页眉显示页眉中前四个字段的只读值。 当开发者在页眉中前四个位置添加字段时，会导致页眉中直接显示的一个现有字段扩展并仅在页眉弹出项目中显示。      

此消息告知开发者更改，并确认是否继续执行操作。

### <a name="header-field-limit-exceeded-the-header-supports-displaying-up-to-four-read-only-field-values-remove-unused-fields-to-add-more"></a>超过了页眉字段限制：页眉支持显示最多四个只读字段值。 请移除未使用字段以添加更多字段。 
当窗体使用高密度页眉并隐藏页眉弹出项目时，窗体设计器中将显示此消息。  
  
高密度页眉显示页眉中最多四个字段的只读值。 由于隐藏了页眉弹出项目，所以用户不能查看更多字段。  

此消息告知开发者在页眉中已经有四个字段，并阻止在页眉中添加用户不能查看的更多字段。

### <a name="header-does-not-display-custom-components-the-header-supports-displaying-up-to-four-read-only-field-values-remove-the-custom-component-from-the-field-before-adding-it-to-the-header"></a>页眉不显示自定义组件：页眉支持显示最多四个只读字段值。 先从字段中移除自定义组件，再将该字段添加到页眉。  
当窗体使用高密度页眉并隐藏页眉弹出项目时，窗体设计器中将显示此消息。  
  
高密度页眉显示页眉中的字段的只读值。 由于隐藏了页眉弹出项目，所以用户不能查看与页眉中的字段关联的所有自定义组件。  

此消息告知开发者，说明他们正在尝试向页面添加具有关联的自定义组件的字段，并且必须先移除自定义组件，才能将字段添加到页眉。 这是因为用户不能查看页眉中的自定义组件。

### <a name="header-displays-read-only-field-values-the-header-supports-displaying-up-to-four-read-only-field-values-to-provide-editability-to-the-user-add-the-field-to-a-section-in-the-form"></a>页眉显示只读字段值：页眉支持显示最多四个只读字段值。 若要让用户可以编辑，请将字段添加到窗体中的某个部分中。  
当窗体使用高密度页眉并隐藏页眉弹出项目时，窗体设计器中将显示此消息。  
  
高密度页眉显示页眉中的字段的只读值。 由于隐藏了页眉弹出项目，所以用户不能编辑字段值。  
  
此消息告知开发者，说明所有添加到页眉的字段均为只读，并且也应该将所有希望用户编辑的字段添加到窗体中的某个部分中。

### <a name="header-field-values-are-not-editable-moving-a-field-from-the-body-to-the-header-will-display-as-a-read-only-value-to-maintain-editability-copy-the-field-to-the-header"></a>页眉字段值不可编辑：如果将字段从主体移到页眉，将显示为只读值。 若要保留可编辑性，请将字段复制到页眉。  
窗体设计器中仅对使用高密度页眉并隐藏页眉弹出项目的窗体显示此消息。  
  
高密度页眉显示页眉中的字段的只读值。 由于隐藏了页眉弹出项目，所以用户不能编辑字段值。  

此消息告知开发者，说明其正在尝试将字段从窗体主体移到窗体页眉。 这样做将使其成为只读字段。 所以开发者可以选择将字段移到页眉，还是向页眉添加字段的副本。 将字段移到页眉将让用户不能在窗体主体中的原始位置编辑该字段。 将字段副本添加到页眉则会让该字段留在原始位置，从而确保用户可以继续在窗体主体内编辑该字段。

### <a name="form-headers-now-default-to-high-density-to-display-more-data-use-the-new-form-designer-to-edit-header-density"></a>窗体页眉现在默认使用高密度以显示更多数据。 请使用新窗体设计器编辑页眉密度。  
当开发者打开配置为使用低密度页眉的主窗体进行编辑时，将在经典窗体编辑器中显示此消息。  
  
此消息可帮助提高对高密度页眉及其优点的关注，而开发者应该使用新的窗体编辑器来配置页眉密度。  

当开发者打开配置为使用低密度页眉的主窗体进行编辑时，将在经典窗体编辑器中显示此消息。 

此消息可帮助提高对高密度页眉及其优点的关注，而开发者应该使用新的窗体编辑器来配置页眉密度。  

### <a name="this-form-is-using-high-density-header-for-the-best-authoring-experience-with-this-form-use-the-new-form-designer"></a>此窗体正在使用高密度页眉。 若要在此窗体中获得最佳创作体验，请使用新窗体设计器。 
当开发者打开配置为使用高密度页眉的主窗体进行编辑时，将在经典窗体编辑器中显示此消息。  
  
经典窗体设计器不提供 WYSIWYG 创作体验。 也不检测和阻止或警告开发者有关对窗体页眉所作更改的影响。 例如，如果编辑的窗体在使用高密度页眉并隐藏了页眉弹出项目，则经典窗体设计器不会阻止开发者向窗体添加四个以上的字段，即使这些字段对用户不可用。  
  
此消息告知开发者，如果编辑的窗体在使用高密度页眉，则应使用新窗体设计器。 这有助于确保开发者注意到其对窗体页眉的更改的影响。

## <a name="see-also"></a>另请参阅
[模型驱动的窗体设计器概述](form-designer-overview.md)  
[使用窗体设计器创建、编辑或配置窗体](create-and-edit-forms.md)  
[添加、配置、移动或删除窗体中的字段](add-move-or-delete-fields-on-form.md)  
[添加、配置、移动或删除窗体中的组件](add-move-configure-or-delete-components-on-form.md)  
[添加、配置、移动或删除窗体中的分区](add-move-or-delete-sections-on-form.md)  
[添加、配置、移动或删除窗体中的选项卡](add-move-or-delete-tabs-on-form.md)  
[在窗体中添加和配置子网格组件](form-designer-add-configure-subgrid.md)  
[在窗体中添加和配置快速视图组件](form-designer-add-configure-quickview.md)  
[在窗体中配置查找组件](form-designer-add-configure-lookup.md)  
[在窗体设计器中使用树视图](using-tree-view-on-form.md)  
[创建和编辑字段](../common-data-service/create-edit-field-portal.md)  
