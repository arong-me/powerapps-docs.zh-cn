---
title: 创建和设计模型驱动应用程序窗体 | MicrosoftDocs
ms.custom: ''
ms.date: 12/06/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- PowerApps
ms.assetid: 99c795e0-9165-4112-85b1-6b5e1a4aa5ec
caps.latest.revision: 33
ms.author: matp
manager: kvivek
author: Mattp123
tags:
- Links to topic not migrated
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: d052e981d80578a2db844f3e8ff3f70ff0c07c2c
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "2884901"
---
# <a name="create-and-design-model-driven-app-forms"></a>创建和设计模型驱动应用程序窗体 

通过 Power Apps，窗体提供用户用于与其工作所需的数据交互的用户界面。 用户所用的窗体要设计成允许他们高效地查找或输入所需的信息，这很重要。 

在默认解决方案或非托管解决方案中，您可以为允许窗体自定义的所有实体创建新窗体或编辑现有窗体。 在非托管解决方案中，可以编辑为该解决方案创建的非托管自定义实体的托管属性。
如果您正在查看托管解决方案，则无法为实体创建新窗体或编辑现有窗体。 但是，如果托管解决方案中某个实体的托管属性设置为允许自定义，则可以为此实体添加或编辑窗体。 
  

<a name="BKMK_TypesOfForms"></a> 
## <a name="type-of-forms"></a>窗体类型
有不同类型的窗体，每个类型具有特定功能或用途。 详细信息：[Power Apps 中的窗体类型](types-forms.md)。  

  
<a name="BKMK_FormDifferencesByEntity"></a>   
## <a name="updated-versus-classic-entities"></a>更新后的实体与经典实体  
Power Apps 提供了许多窗体设计选项。 借助统一接口，更新了大多数实体以更契合响应式接口。 更新后的实体和您自己的自定义实体中包含对 Dynamics 365 for tablets 客户端、业务流程和业务规则的支持。 使用这些实体时，设计一次即可部署到所有客户端。  
  
仍然有一些实体（此处称为经典实体）保留了来自早期版本的外观和功能。 这些实体使用频率不高。 在下面列出来了：  
  
||||||  
|-|-|-|-|-|  
|地址|文章|文章注释|批量删除操作|连接|  
|折扣|折扣表|文档位置|电子邮件附件|追随|  
|目标|目标度量|导入的源文件|发票产品|订单产品|  
|价目表|队列项|报价单产品|汇总字段|汇总查询|  
|已保存视图|服务|服务活动|SharePoint 站点|场所|  
|区域|单位|计价单位组|||  
  
## <a name="form-display-faq"></a>窗体显示常见问题

### <a name="why-is-my-form-not-visible-in-the-form-selector-drop-down-in-my-app"></a>我的应用中窗体选择器下拉列表内为什么不显示我的窗体？
不显示窗体的原因可能是因为尚未将其添加到应用中。
1. 在应用程序设计器中打开该窗体。
2. 在**实体视图**区域中选择实体旁边的**窗体**。
3. 在**组件**选项卡上演着应用中是否包含主窗体。 验证是否已选中了要显示的窗体。 如果未选中，请选中，保存，然后发布应用。

   > [!div class="mx-imgBorder"] 
   > ![](media/forms-included-in-app.png "Forms included with app")
   
### <a name="why-isnt-my-form-displayed-as-the-default-form-in-the-app"></a>为什么我的窗体在应用中不显示为默认窗体？
可通过配置窗体顺序或在用户将默认窗体设置为个性化设置时间窗体设置为默认窗体。
1. 打开解决方案资源管理器。 展开包含要排序的窗体的实体，然后选择**窗体**。
2. 在工具栏上，选择**窗体顺序** > **主窗体集**。 

   > [!div class="mx-imgBorder"] 
   > ![](media/form-order-toolbar.png "Form Order toolbar command")
   
3. 将显示窗体顺序。 选择窗体并使用向上箭头和向下箭头在窗体顺序内移动窗体。 列表顶部的窗体为默认窗体。 

   > [!div class="mx-imgBorder"] 
   > ![](media/form-order-dialog.png "Form order dialog")
   
4. 选择**确定**保存窗体顺序更改。
5. 在窗体设计器工具栏上，选择**发布**以便在应用中应用窗体顺序。
 
#### <a name="form-order-user-personalization-setting"></a>窗体顺序用户个性化设置
请注意，如果应用用户在应用的窗体选择器下拉列表中更改窗体的选择，该窗体将变为用户的默认窗体。 此项个性化设置将覆盖在应用中为实体指定的默认窗体。

   > [!div class="mx-imgBorder"] 
   > ![](media/change-form-user-setting.png "User setting to change default form")
   
### <a name="related-topics"></a>相关主题  
    
[指定窗体顺序](assign-form-order.md) <br />
[控制对窗体的访问](control-access-forms.md) <br />
[主窗体在不同客户端的显示方式](main-form-presentations.md) <br />
