---
title: 使用 PowerApps 在模型驱动应用中配置 Bing 地图 | MicrosoftDocs
ms.custom: ''
ms.date: 10/18/2019
ms.reviewer: ''
ms.service: powerapps
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
ms.openlocfilehash: ff7f5c01e913da60409bb60c637b37ebd4bfa096
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2019
ms.locfileid: "2756464"
---
# <a name="configure-a-map-on-a-form"></a>配置窗体上的地图
默认情况下，在主窗体上为客户和联系人实体都配置了 Bing 地图控件，该控件提供在实体记录上显示地图的功能。 尽管默认情况下未配置，但可以将 Bing 地图控件添加到系统用户实体。 Bing 地图控件也可以与 Dynamics 365 中模型驱动应用附带的某些实体一起使用，例如 Dynamics 365 Sales 和 Dynamics 365 Customer Service。 例如，潜在顾客、报价单、订单、发票和竞争对手实体。 Bing 地图控件不能与自定义实体一起使用。  

启用后，地图将显示在给定记录的地址复合字段中的指定位置。 

> [!div class="mx-imgBorder"] 
> ![应用中的 Bing 地图控件](media/bing-map-example.png "应用中的 Bing 地图控件")

> [!IMPORTANT]
> 若要使用地图，必须启用系统设置“在窗体上显示 Bing 地图”。 详细信息：[为您的环境启用地图](#enable-maps-for-your-environment)

可以在窗体编辑器中删除地图区，也可以使用经典窗体编辑器**插入**选项卡上的 **Bing 地图**按钮重新添加地图区。

## <a name="enable-maps-for-your-environment"></a>为您的环境启用地图
1. 打开模型驱动应用，然后选择**设置** > **高级设置**。 
2. 选择**设置** > **管理** > **系统设置**。 
3. 在**常规**选项卡上，选择**在窗体上显示 Bing 地图**，然后选择**确定**。 
 
    ![在窗体上启用地图](media/enable-maps.png)

## <a name="configure-a-map"></a>配置地图 
1. 登录到 [PowerApps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。 
2. 转到**数据** > **实体**，然后选择要在主窗体上配置地图的实体。 
3. 选择**窗体**选项卡，然后选择主窗体，然后在命令栏上选择**切换到经典**。 
4. 在经典窗体设计器上，双击**地图视图**控件以查看和编辑属性。 详细信息：[查看和编辑地图属性](#view-and-edit-map-properties)

    ![地图视图控件](media/map-view-control.png)

要从窗体中删除地图控件，请选择**地图视图**控件，然后按 Delete 键。

## <a name="view-and-edit-map-properties"></a>查看和编辑地图属性

|      选项卡       |                        属性                         |                                                                                                  说明                                                                                                   |
|----------------|---------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  **常规**   |                        **标签**                        |                                                                              **必需**：要为 Bing 地图显示的标签。                                                                               |
|                |              **在表单上显示标签**              |                                                                                     是否应显示标签。                                                                                     |
|                | **选择要用于 Bing 地图控件的地址** |                                                                        选择应使用哪个地址来提供地图数据。                                                                        |
|                |                 **默认情况下可见**                  | 是否显示 Bing 地图是可选的，并可使用业务规则或脚本来控制。 详细信息：[可见性选项](visibility-options-legacy.md) |
| **格式设置** |  **选择控件所占据的栏数**  |                              当包含 Bing 地图的部分有多栏时，可以将字段设置为最多占据部分具有的栏数。                              |
|                |   **选择控件所占据的行数**    |                                                                  通过指定行数，可以控制 Bing 地图的高度。                                                                   |
|                |     **自动扩展以利用可用空间**     |                                                                        您可以允许 Bing 地图高度扩展到可用空间。                                                                        |

### <a name="see-also"></a>另请参阅
[创建和设计模型驱动应用程序窗体](create-design-forms.md) 
