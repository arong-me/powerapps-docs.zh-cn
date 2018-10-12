---
title: 在 PowerApps 中为模型驱动的统一接口应用指定属性 | MicrosoftDocs
description: 了解如何配置应用的网格控件
keywords: ''
ms.date: 06/06/2018
ms.service: crm-online
ms.custom: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: 3ecea4a7-0d18-4ccd-9609-3a62179e9e1b
ms.author: matp
manager: kvivek
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
caps.latest.revision: 0
topic-status: Drafting
ms.openlocfilehash: 007ac566e317ee99bd85ab0675e5a53839800bb4
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39668011"
---
# <a name="specify-properties-for-model-driven-unified-interface-apps"></a>为模型驱动的统一接口应用指定属性

统一接口框架使用响应式设计原则，为任何大小或方向的屏幕提供最佳的查看和交互体验。 对于使用统一接口框架的模型驱动应用，网格（视图）控件是响应式的。 容器大小减小（例如，使用手机和视窗区较小）时，网格将转换为列表。 

“只读网格”控件指定网格应如何针对不同的屏幕大小进行重排。 作为应用开发者，如果使用统一接口应用，则可以为自定义网格和列表配置“只读网格”控件及其属性。
- “卡窗体”属性：使用列表的卡窗体而非默认列表模板。 相较于默认列表模板，卡窗体可提供列表项的更多信息。
- “重排行为”属性：使用此参数指定网格是否要重排为列表。

## <a name="allow-grid-to-reflow-into-list"></a>允许网格重排为列表

通过将“只读网格”控件添加到控件列表，可以配置以下功能： 
- 允许网格在小型显示器（如手机）上重排为列表。
- 将呈现模式指定为“仅限网格”或“仅限列表”。  

1. 打开[解决方案资源管理器](advanced-navigation.md#solution-explorer)。
2. 在导航窗格中，展开“实体”，选择相应实体（如“帐户”或“联系人”），然后在“控件”选项卡上，选择“添加控件”。

    ![打开“添加控”件](media/UnifiedInterface_ReadOnlyGrid_AddControl.png "打开“添加控件”")

3. 从控件列表中选择“只读网格”，然后选择“添加”。

    该控件将添加到可用控件列表中。
   
    ![选择控件](media/UnifiedInterface_ReadOnlyGrid_SelectControl.png "选择控件")
    
4. 选择要将网格设置为只读的设备（Web、手机或平板电脑）。

    ![选择设备类型](media/UnifiedInterface_ReadOnlyGrid_SelectDevice.png "选择设备")

5. 配置“卡窗体”属性。

    可以使用“卡窗体”属性显示列表项而非默认列表模板。 相较于默认列表模板，卡窗体可提供列表项的更多信息。    

    a. 选择“卡窗体”旁边的铅笔图标。

    ![编辑卡窗体](media/UnifiedInterface_ReadOnlyGrid_CardForm.png "编辑卡窗体")

    b.  选择“实体”和“卡窗体”类型。

    ![卡窗体属性](media/UnifiedInterface_ReadOnlyGrid_CardFormProperties.png "卡窗体属性")

    c. 选择“确定”。
6. 配置“重排行为”属性。 
    
    a. 选择“重排行为”旁边的铅笔图标。

    ![编辑重排行为](media/UnifiedInterface_ReadOnlyGrid_EditReflow.png "编辑重排行为")

    b. 从“绑定到静态选项”下拉列表中选择网格流类型。
    |流类型|描述|
    |--------------|--------------------|
    |**重排**|在没有足够的显示空间时，允许网格呈现为列表模式。|
    |**仅限网格**|即使没有足够的显示空间，也限制网格重排为列表。|
    |**仅限列表**|即使有足够的空间显示为网格，也仅显示为列表。|
    
     ![重排行为属性](media/UnifiedInterface_ReadOnlyGrid_ReflowProperties.png "重排行为属性")

    c. 选择“确定”。


7.  保存并发布更改。 


## <a name="conditional-image"></a>条件图像
可以在列表中显示自定义图标而不是值，并使用 JavaScript 根据列值建立用于选择它们的逻辑。 有关条件图像的详细信息，请参阅[在列表视图中显示自定义图标而不是值](../common-data-service/display-custom-icons-instead.md)。

## <a name="next-steps"></a>后续步骤
[创建或编辑视图](create-edit-views.md)