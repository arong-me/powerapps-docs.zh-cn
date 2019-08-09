---
title: 在 PowerApps 中指定模型驱动统一接口应用程序的属性 | MicrosoftDocs
description: 了解如何配置您的应用的网格控件
keywords: ''
ms.date: 06/03/2019
ms.service: powerapps
ms.custom: null
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
author: Mattp123
ms.assetid: 3ecea4a7-0d18-4ccd-9609-3a62179e9e1b
ms.author: matp
manager: kvivek
ms.reviewer: null
ms.suite: null
ms.tgt_pltfrm: null
caps.latest.revision: 0
topic-status: Drafting
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="specify-properties-for-model-driven-unified-interface-apps"></a>指定模型驱动统一接口应用程序的属性

此统一接口框架使用响应式设计原则，为任何屏幕尺寸或方向提供最佳的查看和交互体验。 通过使用统一接口框架的模型驱动应用，网格（视图）控件可以响应。 如果容器尺寸减小（如在手机和较小视区上），将把网格转换为列表。 

只读网格控件指定网格应如何根据不同屏幕大小重排。 作为应用制造者，如果您使用统一接口应用，则可为自定义网格和列表配置只读网格控件及其属性。
- **卡窗体**属性：为列表使用卡窗体而不是默认列表模板。 卡窗体提供的列表项信息比默认列表模板提供的多。
- **重排行为**属性：使用此参数指定是否将网格重排为列表。

## <a name="allow-grid-to-reflow-into-list"></a>允许网格重排为列表

可通过向控件添加只读网格控件配置以下功能： 
- 允许网格在手机之类小型显示屏上重排为列表。
- 指定呈现模式为仅网格还是仅列表。  

1. 打开[解决方案资源管理器](advanced-navigation.md#solution-explorer)。
2. 在导航窗格中展开**实体**，选择相应实体（如**客户**或**联系人**），然后在**控件**选项卡上，选择**添加控件**。

    ![打开“添加控件”](media/UnifiedInterface_ReadOnlyGrid_AddControl.png "打开“添加控件”")

3. 从控件列表选择**只读网格**，然后选择**添加**。

    将把控件添加到可用控件列表。
   
    ![选择控件](media/UnifiedInterface_ReadOnlyGrid_SelectControl.png "选择控件")
    
4. 选择要为其把网格设置为只读的设备（**Web**、**手机**或**平板电脑**）。

    ![选择设备类型](media/UnifiedInterface_ReadOnlyGrid_SelectDevice.png "选择设备")

5. 配置**卡窗体**属性。

    可使用卡窗体属性显示列表项，而不是显示默认列表模板。 卡窗体提供的列表项信息比默认列表模板提供的多。    

    a. 选择**卡窗体**旁边的铅笔图标。

    ![编辑卡窗体](media/UnifiedInterface_ReadOnlyGrid_CardForm.png "编辑卡窗体")

    b.  选择**实体**和**卡窗体**类型。

    ![卡窗体属性](media/UnifiedInterface_ReadOnlyGrid_CardFormProperties.png "卡窗体属性")

    c. 选择**确定**。
6. 配置**重排行为**属性。 
    
    a. 选择**重排行为**旁边的铅笔图标。

    ![编辑重排行为](media/UnifiedInterface_ReadOnlyGrid_EditReflow.png "编辑重排行为")

    b. 从**绑定到静态选项**下拉列表选择网格流类型。 

    |流类型|说明|
    |--------------|--------------------|
    |**回流**|允许网格在显示空间不足时视情况显示为列表模式。|
    |**仅网格**|即使显示空间不足也限制网格重排为列表。|
    |**仅列表**|即使空间足以显示为网格也仅显示为列表。|
    
     ![重排行为属性](media/UnifiedInterface_ReadOnlyGrid_ReflowProperties.png "重排行为属性")

    c. 选择**确定**。


7.  保存并发布更改。 


## <a name="conditional-image"></a>条件图像
可在列表中显示自定义图标而不是值，并使用 JavaScript 建立用于根据列的值选择图标的逻辑。 有关条件图像的详细信息，请参阅[在列表视图中显示自定义图标而不是值](../common-data-service/display-custom-icons-instead.md)。

## <a name="next-steps"></a>后续步骤
[ 创建或编辑视图 ](create-edit-views.md)
