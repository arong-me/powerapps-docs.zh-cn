---
title: 通过面向应用程序的 Common Data Service 使用虚拟实体 OData v4 数据提供程序 | MicrosoftDocs
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
ms.assetid: null
caps.latest.revision: null
author: Mattp123
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="odata-v4-data-provider-configuration-requirements-and-best-practices"></a>OData v4 数据提供程序配置，要求和最佳实践

本主题介绍如何配置 OData v4 数据提供程序，以及将 OData v4 数据提供程序用于连接 OData v4 Web 服务的要求和建议的最佳实践。 

## <a name="odata-v4-data-provider-best-practices"></a>OData v4 数据提供程序最佳实践

- 面向应用程序的 Common Data Service 要求所有实体都有一个 ID 属性，该 ID 称为唯一标识符，而值必须为 guid。  只能将 ID 字段映射到数据类型为 `Edm.Guid` 的外部字段。  不能将 `Edm.Int32` 数据类型映射到面向应用程序的 CDS 中的“唯一标识符”数据类型字段。
-  必须设置具有可空属性的 OData 实体，以便匹配虚拟实体中映射的字段。 例如，Nullable=False 的 OData 实体属性必须将面向应用程序的 CDS **字段要求**属性中映射的字段设置为**业务必需的**。 
- 要检索多个查询，如在将数据加载到网格中时，请通过使用选择参数和筛选器查询参数控制外部数据源返回的数据集的大小。
- 如果尚未启用插件跟踪，系统管理员应启用。 启用后，将把来自 OData 终结点的所有错误捕获到插件跟踪日志中。 详细信息：[管理员指南：“系统设置”对话框 -“自定义”选项卡](/dynamics365/customer-engagement/admin/system-settings-dialog-box-customization-tab) 

## <a name="data-type-mapping"></a>数据类型映射

下表列出了 OData 实体数据模型 (EDM) 数据类型与面向应用程序的 CDS 数据类型之间的映射。 

|OData 数据类型|面向应用程序的 CDS 的数据类型  |
|---------|---------|
|`Edm.Boolean`|两个选项|
|`Edm.DateTime`|日期和时间|
|`Edm.DateTimeOffset`|日期和时间|
|`Edm.Decimal`|十进制数字或货币|
|`Edm.Double`|浮点数|
|`Edm.Guid`|唯一标识符|
|`Edm.Int32`|整数|
|`Edm.Int64`|整数|
|`Edm.String`|一行文本或多行文本|


### <a name="odata-edm-data-types-that-are-not-supported-for-mapping-with-virtual-entities"></a>不支持与虚拟实体映射的 OData EDM 数据类型 

- `Edm.Binary `
- `Edm.Time` 
- `Edm.Float `
- `Edm.Single` 
- `Edm.Int16` 
- `Edm.Byte` 
- `Edm.SByte`

 
## <a name="add-a-data-source-using-the-odata-v4-data-provider"></a>使用 OData v4 数据提供程序添加数据源

此过程显示如何将自带的 OData 数据提供程序用作虚拟实体数据源。   
  
1. 转至**[设置](../model-driven-apps/advanced-navigation.md#settings)** > **管理** > **虚拟实体数据源**。  
1. 在操作工具栏上单击**新建**。  
1. 在**选择数据提供程序**对话框中，从以下数据源中进行选择，然后单击**确定**。  
  
    - **OData v4 数据提供程序**。 面向应用程序的 CDS 中包含 Odata v4 数据提供程序，可用于连接到支持 OData v4 开放标准的数据源。  
    - *自定义数据提供程序*。 如果已导入数据提供程序插件，将在此处显示该数据提供程序。 详细信息：[开发人员文档：虚拟实体入门](/dynamics365/customer-engagement/developer/virtual-entities/get-started-ve)  
    
1. 在**新数据源**属性页面中，填写以下字段，然后保存记录。  
  
    - **名称**。 键入用于描述数据源的名称。  
    - **Uri**。 如果在使用 OData 数据提供程序，请输入 OData Web 服务的 uri。 例如，如果在使用 OData 提供程序连接到 Azure 中托管的 Web 服务，URI 可能类似 *`http://contosodataservice.azurewebsites.net/odata/`*。  
    - **超时(以秒为单位)**。 输入数据请求超时前等待 Web 服务响应的秒数。例如，输入 30 将最多等待 30 秒才超时。  
    - **分页模式**。 选择使用客户端还是服务器端分页控制查询结果的分页方式。 默认值为客户端分页。 如果使用服务器端分页，服务器通过使用 $skiptoken 参数（将把该参数添加到查询字符串）控制结果的分页方式。 详细信息：[跳过标记系统查询选项 ($skiptoken)](https://msdn.microsoft.com/library/dd942121.aspx)  
        -  **返回内联计数**。 返回结果集中的总数记录。 此设置用于在将数据返回到网格时启用下一页功能。 如果 OData 终结点不支持 OData $inclinecount 参数，请使用值 false。 默认值为 false。
    - **请求参数**。 可以选择自定义用于连接到 OData Web 服务的标头或查询字符串参数，如外部服务的身份验证参数。 单击**查询字符串**可在标头和查询字符串参数与值之间切换。 最多可以添加 10 个标头或查询字符串。 
        > [!div class="mx-imgBorder"] 
        > ![虚拟实体数据源记录](media/virtual-entity-data-source.png) 


## <a name="see-also"></a>另请参阅  

[创建和编辑包含来自外部数据源的数据的虚拟实体](create-edit-virtual-entities.md) <br/>
[TechNet 博客：使用新的虚拟实体与来自外部系统中的数据进行交互](https://blogs.technet.microsoft.com/lystavlen/2017/09/08/virtual-entities/)
