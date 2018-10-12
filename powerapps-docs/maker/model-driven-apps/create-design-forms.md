---
title: 创建和设计模型驱动的应用窗体 | MicrosoftDocs
ms.custom: ''
ms.date: 06/26/2018
ms.reviewer: ''
ms.service: crm-online
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
tags:
- Links to topic not migrated
ms.openlocfilehash: ed51d04919c6316c827b0286eefaaccdf539c6ef
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39669563"
---
# <a name="create-and-design-model-driven-app-forms"></a>创建和设计模型驱动的应用窗体 

在 PowerApps 中，窗体提供了用户界面，用户可以使用这些界面与他们完成工作所需的数据进行交互。 重要的是，用户使用的窗体旨在让他们能够高效地查找或输入所需信息。 

在默认解决方案或非托管解决方案中，可以为允许对窗体进行自定义的所有实体创建新窗体或编辑现有窗体。 在非托管解决方案中，可以编辑为解决方案创建的非托管自定义实体的托管属性。
如果正在查看托管解决方案，则无法为实体创建新窗体或编辑现有窗体。 但是，如果托管解决方案中实体的托管属性设置为允许自定义，则可以向该实体添加窗体或编辑窗体。 
  

<a name="BKMK_TypesOfForms"></a> 
## <a name="type-of-forms"></a>窗体类型
有不同类型的窗体，每种类型都有特定的功能或用途。 详细信息：[PowerApps 中的窗体类型](types-forms.md)。  

  
<a name="BKMK_FormDifferencesByEntity"></a>   
## <a name="updated-versus-classic-entities"></a>已更新的实体与经典实体  
PowerApps 为设计窗体提供了多种选项。 借助统一接口，大多数实体得到更新，能更好地适应响应式接口。 已更新的实体以及拥有的自定义实体包括对适用于平板电脑的 Dynamics 365 客户端、业务流程流和业务规则的支持。 使用这些实体时，只需要设计一次，就可以部署到所有客户端。  
  
仍有许多实体（此处称为经典实体）保留了早期版本的外观和功能。 这些实体的使用频率较低。 下面列出了这些实体：  
  
||||||  
|-|-|-|-|-|  
|地址|文章|文章注释|批量删除操作|连接|  
|折扣|折扣列表|文档位置|电子邮件附件|关注|  
|目标|目标指标|导入源文件|发票产品|订单产品|  
|价格列表|队列项|报价单产品|汇总字段|汇总查询|  
|已保存的视图|服务|服务活动|SharePoint 站点|站点|  
|Territory|单位|计价单位组|||  
  
### <a name="related-topics"></a>相关主题  
    
[分配窗体顺序](assign-form-order.md) <br />
[控制对窗体的访问](control-access-forms.md) <br />
[主窗体在不同客户端中的显示方式](main-form-presentations.md) <br />
