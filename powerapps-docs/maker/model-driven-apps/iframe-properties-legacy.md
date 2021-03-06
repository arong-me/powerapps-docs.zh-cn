---
title: Power Apps 中模型驱动应用主窗体的 iFrame 属性 | MicrosoftDocs
description: 了解主窗体的 iFrame 属性
Keywords: 主窗体; iFrame 属性; Dynamics 365
author: Mattp123
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.author: matp
manager: kvivek
ms.date: 03/18/2020
ms.service: powerapps
ms.topic: article
ms.assetid: 1b7e6a0c-18a9-47e2-aa7d-0cffb8c93b19
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 0775689b2edab8cdbee1b9a595ff73e56ee9af9b
ms.sourcegitcommit: 9f2694bd14d70798310b89a4673672c1bfad989d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/26/2020
ms.locfileid: "3166723"
---
# <a name="iframe-properties-for-model-driven-app-main-forms"></a>模型驱动应用程序主窗体的 iFrame 属性

可以向窗体添加 iFrame 以便在一个窗体中集成另一网站的内容。 

若要查看 IFrame 属性，请执行以下步骤。

1.  登录到 [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。

2.  展开**数据**，选择**实体**，选择所需实体，然后选择**窗体**选项卡。 

3. 在窗体列表中，打开**主**类型的窗体。

4.  选择**切换到经典**在经典窗体设计器中编辑窗体。

4.  在**插入**选项卡上，选择 IFRAME 查看 IFRAME 属性。

      > [!div class="mx-imgBorder"] 
      > ![iframe 属性](media/iframe-properties.png)


> [!NOTE]
> 窗体的设计并不适合在 iFrame 中显示。  
  
|Tab|属性|说明|  
|---------|--------------|-----------------|  
|**常规**|**名称**|**必需**：iFrame 的唯一名称。 该名称只能包含字母数字字符和下划线。|  
||**URL**|**必需**：要在 iFrame 中显示的页面的 URL。|  
||**以参数形式传递记录对象类型代码和唯一标识符**|可以将有关组织、用户和记录的数据传递到 iFrame。 详细信息：[将参数传递给 iFrame](#pass-parameters-to-iframes) |  
||**标签**|**必需**：要为 iFrame 显示的标签。|  
||**在窗体上显示标签**|是否应显示标签。|  
||**限制交叉框架脚本（若支持）**|允许来自其他网站的页面与使用脚本的 Dynamics 365 应用程序交互，被视为一种安全风险。 使用此选项可以限制您无法控制的页面的交叉框架脚本。<br /><br />|  
||**默认情况下可见**|是否显示 iFrame 是可选的，并可使用脚本来控制。 详细信息：[可见性选项](visibility-options-legacy.md)|
||**为移动设备启用**|选择此复选框启用适用于移动设备的 iFrame。|  
|**格式设置**|**选择控件所占据的栏数**|当包含 iFrame 的分区有多栏时，可以将字段设置为最多占据分区具有的栏数。|  
||**选择控件所占据的行数**|通过指定控件占据的行数，可以控制 iFrame 的高度。|  
||**自动扩展以利用可用空间**|除了按行数设置高度以外，还可以允许 iFrame 高度扩展到可用空间。|  
||**选择 iFrame 的滚动类型**|有三个选项：<br /><br /> - **视需要而定**：当 iFrame 大小大于可用空间时，显示滚动条。<br />- **始终**：始终显示滚动条。<br />- **从不**：从不显示滚动条。|  
||**显示边框**|在 iFrame 周围显示边框。|  
|**依赖项**|**从属字段**|iFrame 可以使用脚本与窗体中的字段交互。 如果从窗体中删除了某个字段，iFrame 中的脚本可能会中断。 将 iFrame 中的脚本引用的任何字段添加到**从属字段**，可防止其被意外删除。|  
  
## <a name="pass-parameters-to-iframes"></a> 向 iFrame 传递参数  
 通过启用**传递记录对象类型代码和唯一标识符作为参数** 选项，可以传递有关记录的信息。 传递的值包括：  
  
|参数|说明|  
|---------------|-----------------|  
|`orglcid`|组织默认语言 LCID。|  
|`orgname`|组织的名称。|  
|`userlcid`|用户的首选语言 LCID|  
|`type`|实体类型代码。 对于不同组织中的自定义实体，此值可能会有所不同。 改用 `typename`。|  
|`typename`|实体类型名称。|  
|`id`|记录的 ID 值。 在保存实体记录之前，此参数没有价值。|  

## <a name="next-steps"></a>后续步骤

[使用“主”窗体及其组件](use-main-form-and-components.md)
