---
title: 将虚拟实体 OData v4 数据提供程序与 Common Data Service for Apps 结合使用 | MicrosoftDocs
ms.custom: ''
ms.date: 06/04/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
ms.assetid: ''
caps.latest.revision: ''
author: Mattp123
ms.author: matp
manager: brycho
ms.openlocfilehash: 0bd2aed852b5d7eb9b354f30978725b1386a89aa
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39668959"
---
# <a name="odata-v4-data-provider-configuration-requirements-and-best-practices"></a>OData v4 数据提供程序配置、要求和最佳做法

本主题介绍如何配置 OData v4 数据提供程序，以及使用 OData v4 数据提供程序与 OData v4 Web 服务进行连接的要求和建议的最佳做法。 

## <a name="odata-v4-data-provider-best-practices"></a>OData v4 数据提供程序最佳做法

- Common Data Service for Apps 需要所有实体都具有 ID 属性，此 ID 称为唯一标识符，并且值必须是 guid。  仅可以使用 `Edm.Guid` 数据类型将 ID 字段映射到外部字段。  无法将 `Edm.Int32` 数据类型映射到适用于应用的 CDS 中的唯一标识符数据类型字段。
-  具有可为 null 的属性的 OData 实体的设置须与虚拟实体中映射的字段相匹配。 例如，对于 Nullable=False 的 OData 实体属性，必须将适用于应用的 CDS “字段要求”特性中的映射字段设置为“业务必需”。 
- 如果要检索多个查询，例如向网格加载数据时，请使用 select 和 filter 查询参数控制从外部数据源返回的数据集的大小。
- 如果尚未启用插件跟踪，系统管理员应启用此功能。 启用后，插件跟踪日志中会捕获 OData 终结点的所有错误。 详细信息：[管理员指南：“系统设置”对话框 -“自定义”选项卡](/dynamics365/customer-engagement/admin/system-settings-dialog-box-customization-tab) 

## <a name="data-type-mapping"></a>数据类型映射

下表列出了 OData 实体数据模型 (EDM) 数据类型与适用于应用的 CDS 数据类型的映射。 

|OData 数据类型|适用于应用的 CDS 的数据类型  |
|---------|---------|
|`Edm.Boolean`|两个选项|
|`Edm.DateTime`|日期和时间|
|`Edm.DateTimeOffset`|日期和时间|
|`Edm.Decimal`|小数或货币|
|`Edm.Double`|浮点数|
|`Edm.Guid`|唯一标识符|
|`Edm.Int32`|整数|
|`Edm.Int64`|整数|
|`Edm.String`|单行文本或多行文本|


### <a name="odata-edm-data-types-that-are-not-supported-for-mapping-with-virtual-entities"></a>不支持虚拟实体映射的 OData EDM 数据类型 

- `Edm.Binary `
- `Edm.Time` 
- `Edm.Float `
- `Edm.Single` 
- `Edm.Int16` 
- `Edm.Byte` 
- `Edm.SByte`

 
## <a name="add-a-data-source-using-the-odata-v4-data-provider"></a>使用 OData v4 数据提供程序添加数据源

此过程演示如何将现成的 OData 数据提供程序用作虚拟实体数据源。   
  
1. 转到“[设置](../model-driven-apps/advanced-navigation.md#settings)” > “管理” > “虚拟实体数据源”。  
1. 在“操作”工具栏上，单击“新建”。  
1. 在“选择数据提供程序”对话框中，从以下数据源进行选择，然后单击“确定”。  
  
    - OData v4 数据提供程序。 适用于应用的 CDS 包含一个 Odata v4 数据提供程序，可用于连接到支持 OData v4 开放标准的数据源。  
    - 自定义数据提供程序。 如果已导入数据提供程序插件，数据提供程序将在此处显示。 详细信息：[开发人员文档：虚拟实体入门](/dynamics365/customer-engagement/developer/virtual-entities/get-started-ve)  
    
1. 在“新数据源”属性页上，完成以下字段，然后保存记录。  
  
    - 名称。 键入描述数据源的名称。  
    - URI。 如果使用的是 OData 数据提供程序，请输入 OData Web 服务的 URI。 例如，如果使用 OData 提供程序连接到 Azure 中托管的 Web 服务，则 URI 看起来类似于 `http://contosodataservice.azurewebsites.net/odata/`。  
    - 超时(以秒为单位)。 输入在数据请求超时前等待 Web 服务响应的秒数。例如，输入 30 秒，则最长等待 30 秒后便发生超时。  
    - 分页模式。 选择使用客户端或服务器端分页来控制查询结果分页方式。 默认值为客户端分页。 对于服务器端分页，服务器使用 $skiptoken 参数来控制结果的分页方式，该参数会添加到查询字符串中。 详细信息：[Skip Token System Query Option ($skiptoken)](https://msdn.microsoft.com/library/dd942121.aspx)（跳过标记系统查询选项 ($skiptoken)）  
        -  返回内联计数。 在结果集中返回记录总数。 将数据返回网格时，此设置可用于启用下一页功能。 如果 OData 终结点不支持 OData $inclinecount 参数，请使用 false 值。 默认值为 false。
    - 请求参数。 （可选）可以添加用于连接到 OData Web 服务的自定义标头或查询字符串参数，如连接到外部服务的身份验证参数。 单击“查询字符串”，在标头和查询字符串参数及值之间进行切换。 最多可添加 10 个标头或查询字符串。 
        ![虚拟实体数据源记录](media/virtual-entity-data-source.png) 


## <a name="see-also"></a>另请参阅  

[创建和编辑包含外部数据源数据的虚拟实体](create-edit-virtual-entities.md) <br/>
[TechNet 博客：使用新虚拟实体与外部系统中的数据进行交互](https://blogs.technet.microsoft.com/lystavlen/2017/09/08/virtual-entities/)
