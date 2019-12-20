---
title: 使用模型驱动的窗体设计器创建、编辑或配置窗体 | MicrosoftDocs
ms.custom: ''
ms.date: 08/26/2019
ms.reviewer: ''
ms.service: powerapps
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
ms.openlocfilehash: 3d35a73f02a1df1e3d5fd51f422b2b24263f53b5
ms.sourcegitcommit: 861ba8e719fa16899d14e4a628f9087b47206993
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "2875606"
---
# <a name="create-edit-or-configure-forms-using-the-form-designer"></a>使用窗体设计器创建、编辑或配置窗体 
使用新的窗体设计器为模型驱动的应用创建、编辑或配置窗体。 

> [!IMPORTANT]
> 新的模型驱动的窗体设计器目前不支持编辑卡窗体。 详细信息：[窗体类型](types-forms.md)

## <a name="create-a-form"></a>创建窗体 
1. 登录到 [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。 
2. 在左侧导航窗格上，展开**数据**，然后选择**实体**。 
3. 选择实体（如客户实体），然后选择**窗体**选项卡。 
4. 选择**添加窗体**，然后选择下列选项之一
    - **主窗体**  
    将使用现有主窗体定义填充新窗体的内容。 如果有多个主窗体，则使用窗体顺序中列表顶部的窗体填充新窗体。 
    - **快速创建窗体**
    - **快速视图窗体**
5. 在完成对窗体的更改时，选择**保存**保存窗体，或在要保存更改并向应用用户显示时选择**发布**。  

## <a name="edit-a-form"></a>编辑窗体 
1. 登录到 [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。 
2. 在左侧导航窗格上，展开**数据**，然后选择**实体**。 
3. 选择实体（如客户实体），然后选择**窗体**选项卡。
4. 选择要编辑的窗体名称。  
    - 您还可以选择窗体的这一行，然后在命令栏中，选择**编辑窗体**
    - 另一个替代方法是选择窗体名称旁边的 **...**，然后在菜单中，选择**编辑窗体**。 
5. 在完成对窗体的更改时，选择**保存**保存窗体，或在要保存更改并向应用用户显示时选择**发布**。 

## <a name="configure-a-form"></a>配置窗体
当您使用窗体设计器创建或编辑窗体时，以下属性可用于配置窗体。

|姓名  |说明  |
|---------|---------|
|**标题**  | 输入对其他开发者和应用用户有意义的名称。 此名称显示给应用用户。 如果用户可以访问实体的多个窗体，则他们将使用此名称来区分可用的窗体。 <br /><br />该属性是必需的。 |
|**说明** |  输入描述，说明此窗体与其他主窗体的不同之处。 此描述仅在解决方案资源管理器中某个实体的窗体列表中向开发者显示。 |
|**最大宽度** | 设置最大宽度（像素）可限制窗体的宽度。 默认值为 1900。 <br /><br />该属性是必需的。 |
|**显示图像** | 显示实体的**主要图像**（如果已经设置）。 此设置允许在此窗体的标题中显示图像字段。 <br /><br /> 有关实体选项的详细信息，请参阅启用或禁用实体选项。 |

## <a name="see-also"></a>另请参阅
[模型驱动的窗体设计器概述](form-designer-overview.md)  
[添加、配置、移动或删除窗体中的字段](add-move-or-delete-fields-on-form.md)  
[添加、配置、移动或删除窗体中的组件](add-move-configure-or-delete-components-on-form.md)  
[添加、配置、移动或删除窗体中的分区](add-move-or-delete-sections-on-form.md)  
[添加、配置、移动或删除窗体中的选项卡](add-move-or-delete-tabs-on-form.md)  
[在窗体设计器中配置页眉属性](form-designer-header-properties.md)  
[在窗体中添加和配置子网格组件](form-designer-add-configure-subgrid.md)  
[在窗体中添加和配置快速视图组件](form-designer-add-configure-quickview.md)  
[在窗体中配置查找组件](form-designer-add-configure-lookup.md)  
[在窗体设计器中使用树视图](using-tree-view-on-form.md)  
[创建和编辑字段](../common-data-service/create-edit-field-portal.md)  
