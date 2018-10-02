---
title: 使用 PowerApps 在模型驱动应用程序中配置 Bing 地图 | MicrosoftDocs
ms.custom: ''
ms.date: 06/18/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
ms.assetid: f9729664-561c-4758-86ce-7216d68075d9
caps.latest.revision: 63
ms.author: matp
author: Mattp123
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="configure-bing-maps-in-a-model-driven-app"></a>在模型驱动应用程序中配置 Bing 地图

 必应地图可以在帐户、联系人、潜在顾客、报价、订单、发票、对手和系统用户实体的窗体中显示。 可以在窗体编辑器中删除 Bing 地图区，也可以使用窗体编辑器**插入** 选项卡上的**Bing 地图** 按钮重新添加 Bing 地图区。  
  
 若要启用 Bing 地图，必须启用系统设置**在窗体上显示 Bing 地图**。  
  
|Tab|属性|说明|  
|---------|--------------|-----------------|  
|**常规**|**标签**|**必需**：要为 Bing 地图显示的标签。|  
||**在表单上显示标签**|是否应显示标签。|  
||**选择要用于 Bing 地图控件的地址**|选择应使用哪个地址来提供地图数据。|  
||**默认情况下可见**|是否显示 Bing 地图是可选的，并可使用脚本来控制。 详细信息：[可见性选项](visibility-options-legacy.md)|  
|**格式设置**|**选择控件所占据的栏数**|当包含 Bing 地图的分区有多栏时，可以将字段设置为最多占据分区具有的栏数。|  
||**选择控件所占据的行数**|通过指定行数，可以控制 Bing 地图的高度。|  
||**自动扩展以利用可用空间**|您可以允许 Bing 地图高度扩展到可用空间。|  

## <a name="next-steps"></a>后续步骤

[使用“主”窗体及其组件](use-main-form-and-components.md)
