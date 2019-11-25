---
title: PowerApps 中模型驱动应用主窗体的特殊字段属性 | MicrosoftDocs
description: 了解主窗体的特殊字段属性
Keywords: 主窗体; 特殊字段属性; Dynamics 365
author: Mattp123
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.author: matp
manager: kvivek
ms.date: 06/06/2018
ms.service: powerapps
ms.topic: article
ms.assetid: 6ad7e43c-b6a1-48c4-9dfb-ed830142a841
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: ad0fbb1208e612ba43d0a8c074ac62fab0000c2f
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "2711023"
---
# <a name="overview-of-model-driven-app-special-field-properties"></a>模型驱动应用程序特殊字段属性概述

 所有字段都具有[常见字段属性](common-field-properties-legacy.md)中列出的属性，但是，某些字段具有其他属性，如可以从案例实体的主窗体打开的此权利字段。  

![特殊属性对话框](media/special-properties.png)
  
<a name="BKMK_LookupFieldProperties"></a>  
 
## <a name="lookup-field-properties"></a>查找字段属性  
  
> [!NOTE]
>  下表中描述的选项仅支持单实体查找字段。  
  
|节​​|属性|说明|  
|-------------|--------------|-----------------|  
|**相关记录筛选**|**仅在以下情况下显示记录**|如果启用此功能，用户搜索记录时显示的记录将应用额外的筛选。 这有助于在设置查找值时提供更具相关性的搜索。<br /><br /> 默认情况下，它处于关闭状态。<br /><br /> 此表后面的表中列出了筛选相关记录时可能存在的关系组合。*<br /><br /> 第一个列表使用可用于筛选此查找的所有潜在关系填充。 选择一个。<br /><br /> 第二个列表则使用将相关实体（在第一个列表中选择）连接到目标实体的所有关系填充。 选择一个。<br /><br /> 选中**允许用户关闭筛选器**复选框将允许用户选择禁用此处定义的筛选器。<br /><br /> 当用户选择**查找更多记录**选项时，在设置查找的值时，他们可以看到该对话框。<br /><br /> ![查找更多记录](media/crm-ua-v-8-1-look-up-more-records.png) <br /><br /> 如果选择**允许用户关闭筛选器**选项，在配置查找字段时，用户将看到用于关闭筛选器的复选框。  这样，用户可以查看范围更广的记录。 如果要确保用户只能看到此筛选器定义的有限范围的记录，请清除**允许用户关闭筛选器**复选框。|  
|**其他属性**|**在查找对话框中显示搜索框**|您可以选择不在查找对话框中显示搜索框。|  
||**默认视图**|此视图用于筛选内联搜索的结果，以及设置当用户选择**查找更多记录**选项时在查找对话框中显示的默认视图。<br /><br /> 默认视图还可控制包括在内联查找中的字段。<br /><br /> 对于仅允许选择一种实体类型的查找，内联查找中显示的字段被设置为包括在默认视图中的前两个字段。 在本例中，**主要电话** 和**电子邮件** 是为帐户查找配置的默认视图中的前两栏。<br /><br /> 对于允许多种实体类型的系统查找，将显示实体查找视图的前两栏。|  
||**视图选择器**|可供选择的选项有三个：<br /><br /> -   **关**：不允许用户选择其他视图。<br />-   **显示所有视图**：所有视图均可用。<br />-   **显示选定视图**：选择此选项时，可以使用 Ctrl 键和鼠标选择要显示的视图。 不能取消选择实体的查找视图。|  
  
 **\*可行关系组合**  
  
|第一个列表关系|第二个列表关系|是否存在？|  
|-----------------------------|------------------------------|----------------|  
|N:1|1:N|是|  
|N:1|N:1|是|  
|N:1|N:N|是|  
|1:N|1:N|是|  
|1:N|N:1|No|  
|1:N|N:N|No|  
|N:N|1:N|是|  
|N:N|N:1|No|  
|N:N|N:N|No|  
  
<a name="BKMK_TwoOptionProperties"></a>   

### <a name="two-option-field-properties"></a>两个选项字段属性  
 在“格式”选项卡上，两个选项字段具有以下格式设置选择：  
  
- **两个单选按钮**：两个带标签的标签控件 只能选择其中的一个。  
  
- **复选框**：单个复选框，可设置为 True 值或 False 值。  
  
- **列表**：包含两个值的下拉列表。  
  
<a name="BKMK_MultipleLinesOfTextProperties"></a>   

### <a name="multiple-lines-of-text-field-properties"></a>多行文本字段属性  
 使用 `Text Area` 格式的多行文本字段和单行文本字段具有**行布局** 属性。 利用属性，可以指定**行数** 值，或选择**自动扩展以利用可用空间** 。  

## <a name="next-steps"></a>后续步骤

[使用“主”窗体及其组件](use-main-form-and-components.md)
