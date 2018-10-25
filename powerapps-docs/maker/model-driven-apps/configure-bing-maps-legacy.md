---
title: 通过 PowerApps 在模型驱动的应用中配置必应地图 | MicrosoftDocs
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
ms.openlocfilehash: 44977925bfa92647ddbc29b7a82028f55b146921
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39668548"
---
# <a name="configure-bing-maps-in-a-model-driven-app"></a>在模型驱动的应用中配置必应地图

 必应地图可以在帐户、联系人、潜在顾客、报价、订单、发票、竞争对手和系统用户实体的窗体中显示。 你可以在窗体编辑器中删除必应地图区，也可以使用窗体编辑器“插入”选项卡上的“必应地图”按钮重新添加必应地图区。  
  
 若要启用必应地图，必须启用系统设置“在窗体上显示必应地图”。  
  
|选项卡|属性|描述|  
|---------|--------------|-----------------|  
|常规|标签|必需：要为必应地图显示的标签。|  
||**在窗体上显示标签**|是否应显示标签。|  
||选择要用于必应地图控件的地址|选择应使用哪个地址来提供地图数据。|  
||默认情况下可见|显示必应地图是可选的，并可使用脚本控制。 详细信息：[可见性选项](visibility-options-legacy.md)|  
|格式设置|**选择控件占用的列数**|如果包含必应地图的分区具有多列，可将该字段的占用列数上限设置为该分区所具有的列数。|  
||**选择控件占用的行数**|通过指定行数，可以控制必应地图的高度。|  
||自动扩展以利用可用空间|可以允许必应地图高度扩展到可用空间。|  

## <a name="next-steps"></a>后续步骤

[使用主窗体及其组件](use-main-form-and-components.md)