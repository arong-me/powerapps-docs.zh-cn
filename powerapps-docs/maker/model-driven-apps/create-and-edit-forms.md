---
title: 使用模型驱动的窗体设计器创建和编辑窗体 | MicrosoftDocs
ms.custom: ''
ms.date: 12/13/2018
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
  - PowerApps maker portal impact
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="create-and-edit-forms-using-the-form-designer"></a>使用窗体设计器创建和编辑窗体 
[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

使用新的窗体设计器为模型驱动的应用创建和设计窗体。

> [!IMPORTANT]
> 新的模型驱动的窗体设计器目前仅支持创建和编辑主窗体。 详细信息：[窗体类型](types-forms.md)

## <a name="create-a-form"></a>创建窗体 
1. 登录到 [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。 
2. 在左侧导航窗格上，展开**数据**，然后选择**实体**。 
3. 选择实体（如客户实体），然后选择**窗体**选项卡。 
4. 选择**添加窗体**，然后选择**主窗体(预览)**。     
    将使用现有主窗体定义填充新窗体的内容。 如果有多个主窗体，则使用窗体顺序中列表顶部的窗体填充新窗体。 
5. 选择**保存**保存窗体，或在要保存更改并向应用用户显示时选择**发布**。  

## <a name="edit-a-form"></a>编辑窗体 
1. 登录到 [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。 
2. 在左侧导航窗格上，选择**数据**，然后选择**实体**。 
3. 选择实体（如客户实体），然后选择**窗体**选项卡。
4. 选择要编辑的窗体，然后选择**编辑窗体(预览)**。  
   或者，选择要编辑的窗体旁边的 **...**，然后选择**编辑窗体(预览)**。 
5. 选择**保存**保存窗体，或在要保存更改并向应用用户显示时选择**发布**。 

## <a name="add-and-remove-fields"></a>添加和删除字段 
若要在窗体中添加字段或删除字段，请使用字段窗格。 可通过字段窗格搜索和筛选来帮助快速找到字段。 还包括用于仅显示未使用的字段的选项。 

### <a name="add-a-field"></a>添加字段
1. 打开窗体设计器创建或编辑窗体。 更多信息：[创建窗体](#create-a-form)和[编辑窗体](#edit-a-form)
2. 在窗体预览中，选择另一个现有字段或部分。 
    - 如果选择现有字段，将把新字段添加到现有字段下方。 
    - 如果选择部分，将把新字段添加到可用空间中，以便让字段在列之间平均分布。 
3. 选择**添加字段**，或在左侧窗格中选择**字段**。  
   打开窗体设计器时，默认打开字段窗格。 
4. 在**字段**窗格中，搜索、筛选或滚动以查找要添加的字段。 
   如果找不到字段，可能是因为该字段已在窗体上。 清除**显示未使用的字段**显示所有字段，包括已添加到窗体的字段。 
5. 在**字段**窗格中，选择字段将其添加到窗体。 <br />
   或者选择所需字段旁边的 **...**，然后选择**添加到所选部分**。 
6. 选择**保存**保存窗体，或在要保存更改并向最终用户显示时选择**发布**。 

### <a name="remove-a-field"></a>移除字段
1. 打开窗体设计器创建或编辑窗体。 更多信息：[创建窗体](#create-a-form)和[编辑窗体](#edit-a-form)
2. 在窗体预览中，选择要从窗体中删除的字段。 
3. 选择**删除**。 <br />
4. 选择**保存**。 

    > [!NOTE]
    >   -  如果误删了字段，请选择**撤销**以逆转操作。 
    >   -  不能删除必需字段或已锁定字段。 

## <a name="add-and-remove-tabs-and-sections"></a>添加和删除选项卡和部分 
若要在窗体中添加或删除窗体或部分，请使用布局窗格。 

### <a name="add-a-tab"></a>添加选项卡
1. 打开窗体设计器创建或编辑窗体。 更多信息：[创建窗体](#create-a-form)和[编辑窗体](#edit-a-form) 
2. 在窗体预览中，选择另一个现有选项卡或窗体。 
    - 如果选择现有选项卡，将把新选项卡添加到现有选项卡右侧。 
    - 如果选择窗体，将把新选项卡添加为窗体最右侧的选项卡。 
3. 选择**添加控件**，或在左侧窗格中选择**布局**。  
4. 在**布局**窗格中，选择一个选项卡控件（如 **2 列选项卡**），将其添加到窗体。 <br />
   或者选择所需选项卡空间旁边的 **...**，然后选择**添加到窗体**。  
5. 选择**保存**。 


### <a name="remove-a-tab"></a>移除选项卡
1. 打开窗体设计器创建或编辑窗体。 更多信息：[创建窗体](#create-a-form)和[编辑窗体](#edit-a-form)
2. 在窗体预览中，选择要删除的选项卡，然后选择**删除**。 
3. 选择**保存**。 
    > [!NOTE]
    >    - 如果误删了选项卡，请选择**撤销**以撤消删除操作。 
    >     - 一个窗体必须有至少一个选项卡。不能删除窗体上的唯一选项卡。 
    >    - 不能删除具有已锁定部分的选项卡。 
    >    - 不能删除具有包含必需字段或已锁定字段的部分的选项卡。 

### <a name="add-a-section"></a>添加部分 
1. 打开窗体设计器创建或编辑窗体。 更多信息：[创建窗体](#create-a-form)和[编辑窗体](#edit-a-form)
2. 在窗体预览中，选择另一个现有部分或选项卡。 
    - 如果选择现有部分，将把新部分添加到现有部分下方。 
    - 如果选择选项卡，将把新部分添加到选项卡第一列中的底部。 
3. 选择**添加控件**，或在左侧窗格中选择**布局**。
4. 在**布局**窗格中，选择部分控件将其添加到窗体。 <br />
   或者选择所需部分控件旁边的 **...**，然后选择**添加到所选选项卡**。      
5. 选择**保存**。 
 

### <a name="delete-a-section"></a>删除部分 
1. 打开窗体设计器创建或编辑窗体。 更多信息：[创建窗体](#create-a-form)和[编辑窗体](#edit-a-form) 
2. 在窗体预览中，选择要删除的部分，然后选择**删除**。  
3. 选择**保存**。 
    > [!NOTE]
    >    - 如果误删了部分，请选择**撤销**以撤消删除操作。 
    >    - 一个选项卡的每个列需要至少一个部分。  
    >    - 不能删除选项卡列中的唯一部分。 
    >    - 不能删除已锁定部分。 
    >    - 不能删除具有必需字段或已锁定字段的部分。 
 
## <a name="use-the-tree-view"></a>使用树视图 
树视图窗格显示控件和字段在窗体中的图形层次结构。 树视图中的图标可帮助您快速识别字段或控件的类型。 

也可以使用树视图选择窗体中的字段和控件。 如果要选择窗体预览中隐藏，因此未显示的元素，树视图非常有用。 

可展开或折叠树视图中的节点查看或隐藏节点内的元素。 如果选择树视图中的元素，该元素将在窗体预览中突出显示，而属性窗格则显示该元素的属性。 

   ![树视图](media/tree-view.png)

### <a name="open-the-tree-view"></a>打开树视图 
1. 打开窗体设计器创建或编辑窗体。 更多信息：[创建窗体](#create-a-form)和[编辑窗体](#edit-a-form)  
2. 在左侧窗格中，选择**树视图**。

## <a name="see-also"></a>另请参阅
[模型驱动的窗体设计器概述](form-designer-overview.md) <br />
[创建和编辑字段](../common-data-service/create-edit-field-portal.md)