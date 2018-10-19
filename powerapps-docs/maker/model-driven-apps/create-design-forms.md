---
title: 创建和设计模型驱动应用程序窗体 | MicrosoftDocs
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
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="create-and-design-model-driven-app-forms"></a>创建和设计模型驱动应用程序窗体 

通过 PowerApps，窗体提供用户用于与其工作所需的数据交互的用户界面。 用户所用的窗体要设计成允许他们高效地查找或输入所需的信息，这很重要。 

在默认解决方案或非托管解决方案中，您可以为允许窗体自定义的所有实体创建新窗体或编辑现有窗体。 在非托管解决方案中，可以编辑为该解决方案创建的非托管自定义实体的托管属性。
如果您正在查看托管解决方案，则无法为实体创建新窗体或编辑现有窗体。 但是，如果托管解决方案中某个实体的托管属性设置为允许自定义，则可以为此实体添加或编辑窗体。 
  

<a name="BKMK_TypesOfForms"></a> 
## <a name="type-of-forms"></a>窗体类型
有不同类型的窗体，每个类型具有特定功能或用途。 详细信息：[PowerApps 中的窗体类型](types-forms.md)。  

  
<a name="BKMK_FormDifferencesByEntity"></a>   
## <a name="updated-versus-classic-entities"></a>更新后的实体与经典实体  
PowerApps 提供了许多窗体设计选项。 借助统一接口，更新了大多数实体以更契合响应式接口。 更新后的实体和您自己的自定义实体中包含对 Dynamics 365 for tablets 客户端、业务流程和业务规则的支持。 使用这些实体时，设计一次即可部署到所有客户端。  
  
仍然有一些实体（此处称为经典实体）保留了来自早期版本的外观和功能。 这些实体使用频率不高。 在下面列出来了：  
  
||||||  
|-|-|-|-|-|  
|地址|文章|文章注释|批量删除操作|连接|  
|折扣|折扣表|文档位置|电子邮件附件|追随|  
|目标|目标度量|导入的源文件|发票产品|订单产品|  
|价目表|队列项|报价单产品|汇总字段|汇总查询|  
|已保存的视图|服务|服务活动|SharePoint 网站|场所|  
|区域|单位|计价单位组|||  
  
### <a name="related-topics"></a>相关主题  
    
[指定窗体顺序](assign-form-order.md) <br />
[控制对窗体的访问](control-access-forms.md) <br />
[主窗体在不同客户端的显示方式](main-form-presentations.md) <br />
