---
title: PowerApps 中主窗体的模型驱动应用特殊字段属性 | MicrosoftDocs
description: 了解主窗体的特殊字段属性
Keywords: Main forms; Special field properties; Dynamics 365
author: Mattp123
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.author: matp
manager: kvivek
ms.date: 06/06/2018
ms.service: crm-online
ms.topic: article
ms.assetid: 6ad7e43c-b6a1-48c4-9dfb-ed830142a841
ms.openlocfilehash: 0c4e67b14816ae6eaf100221ac0ac29269000f9b
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39667671"
---
# <a name="overview-of-model-driven-app-special-field-properties"></a>模型驱动应用特殊字段属性概述

 所有字段都具有[常用字段属性](common-field-properties-legacy.md)中列出的属性，但某些字段具有其他属性，例如可以从案例实体的主窗体打开的此授权字段。  

![special-properties-dialog](media/special-properties.png)
  
<a name="BKMK_LookupFieldProperties"></a>  
 
## <a name="lookup-field-properties"></a>查找字段属性  
  
> [!NOTE]
>  下表中描述的选项仅适用于单一实体查找字段。  
  
|节|属性|描述|  
|-------------|--------------|-----------------|  
|**相关记录筛选**|**仅显示记录位置**|启用此选项后，用户搜索记录时显示的记录将应用其他筛选。 这有助于在设置查找值时提供相关度更高的搜索结果。<br /><br /> 默认情况下，此功能处于关闭状态。<br /><br /> 筛选相关记录时可能出现的关系组合列在此表后面的表中。*<br /><br /> 第一个列表填充了可用于筛选此查找的所有潜在关系。 选择其中一项。<br /><br /> 然后第二个列表填充将相关实体（第一个列表中所选）连接到目标实体的所有关系。 选择其中一项。<br /><br /> 选中“允许用户关闭筛选器”复选框，以便用户可以选择关闭此处定义的筛选器。<br /><br /> 如果用户在设置查找值时选择“查找更多记录”选项，会看到此对话框。<br /><br /> ![look-up-more-records](media/crm-ua-v-8-1-look-up-more-records.png) <br /><br /> 如果在配置查找字段时选择“允许用户关闭筛选器”选项，用户将看到复选框并可关闭筛选器。  这样他们就能看到范围更广的记录。 如果要确保用户只能看到此筛选器定义的范围有限的记录，请清除“允许用户关闭筛选器”复选框。|  
|**其他属性**|**在查找对话框中显示搜索框**|可选择不在查找对话框中显示搜索框。|  
||**默认视图**|此视图用于筛选内联搜索的结果，并在用户选择“查找更多记录”选项时设置查找对话框中显示的默认视图。<br /><br /> 默认视图还可控制内联查找中包含的字段。<br /><br /> 对于仅允许选择单个实体类型的查找，内联查找中显示的字段将设置为默认视图中包含的前两个字段。 在此示例中，主要电话号码和电子邮件是为帐户查找配置的默认视图中的前两列。<br /><br /> 对于允许多个实体类型的系统查找，将显示实体查找视图的前两列。|  
||**视图选择器**|可从三个选项中进行选择：<br /><br /> -   **关**：不允许用户选择其他视图。<br />-   **显示所有视图**：可使用所有视图。<br />-   **显示所选视图**：选择此选项时，可使用 Ctrl 键和光标选择要显示的视图。 无法取消选择实体的“查找”视图。|  
  
 \*可能的关系组合  
  
|第一个列表关系|第二个列表关系|是否可用？|  
|-----------------------------|------------------------------|----------------|  
|N:1|1:N|是|  
|N:1|N:1|是|  
|N:1|N:N|是|  
|1:N|1:N|是|  
|1:N|N:1|否|  
|1:N|N:N|否|  
|N:N|1:N|是|  
|N:N|N:1|否|  
|N:N|N:N|否|  
  
<a name="BKMK_TwoOptionProperties"></a>   

### <a name="two-option-field-properties"></a>两个选项字段属性  
 在“格式设置”选项卡上，两个选项字段具有以下格式设置选择：  
  
- **两个单选按钮**：两个带标签的标记控件。 只能选择一个。  
  
- **复选框**：单个复选框，用于设置 true 值，否则为 false。  
  
- **列表**：包含两个值的下拉列表。  
  
<a name="BKMK_MultipleLinesOfTextProperties"></a>   

### <a name="multiple-lines-of-text-field-properties"></a>多行文本字段属性  
 使用 `Text Area` 格式的多行文本和单行文本字段具有“行布局”属性。 使用此属性，可为“行数”指定值，或选择“自动展开以使用可用空间”。  

## <a name="next-steps"></a>后续步骤

[使用主窗体及其组件](use-main-form-and-components.md)
