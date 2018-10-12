---
title: 使用 Common Data Service for Apps 中的 OData 数据提供程序进行虚拟实体演练 | MicrosoftDocs
description: 了解如何将 OData v4 数据提供程序与虚拟实体结合使用
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
- powerapps
ms.assetid: ''
caps.latest.revision: 11
author: Mattp123
ms.author: matp
manager: kvivek
ms.openlocfilehash: ebdd8f80aad2d353d017626b7c403da93803c19b
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39668009"
---
# <a name="virtual-entity-walkthrough-using-the-odata-v4-data-provider"></a>使用 OData v4 数据提供程序进行虚拟实体演练

假设你希望从模型驱动应用中的外部数据源或 Dynamics 365 for Customer Engagement 的服务区域访问票证信息。 在此简单演练中，将使用映射到外部架构的字段为虚拟实体建模，该外部架构会在运行时从 OData Web 服务检索票证数据。

## <a name="data-source-details"></a>数据源详细信息

由于本演练中使用的数据源具有 OData v4 Web 服务，因此我们可以使用环境附带的 OData v4 数据提供程序。

Web 服务 URL：`http://contosowebservice.azurewebsites.net/odata/` 

> [!IMPORTANT]
> 用于本演练的 Web 服务 URL 不是正常运行的 Web 服务。

对于本演练，需要包含以下三个字段的单个虚拟实体。

|外部字段名称 |外部数据类型 |虚拟实体数据类型 |用途 |
|---------|---------|---------|---------|
|TicketID |`Edm.Guid` |主键 |实体的主键 |
|标题  |`Edm.String` |单行文本 |票证的标题 |
|严重性 |`Edm.Int32`| 整数 |数值 0-4，用于表示票证的严重级别 |

外部数据源“票证”实体的 OData 元数据：

```xml
<EntityType Name="Ticket">
  <Key>
    <PropertyRef Name="TicketID" />
  </Key>
  <Property Name="TicketID" Nullable="false" Type="Edm.Guid" />
  <Property Name="Title" Type="Edm.String" />
  <Property Name="Severity" Nullable="false" Type="Edm.Int32" />
</EntityType>
```

## <a name="create-the-data-source"></a>创建数据源

为使用 OASIS Open Data Protocol (OData) 示例 Web 服务的 OData v4 数据提供程序创建数据源。

1. 转到“设置” > “管理” > “虚拟实体数据源”。
1. 依次选择“新建”、“OData v4 数据提供程序”，然后选择“确定”。
1. 输入或选择以下信息。

    |字段|值|
    |--|--|
    |**名称**|Contoso 示例数据源|
    |**URL**|`http://contosowebservice.azurewebsites.net/odata` |
    |**超时**|30|
    |**返回内联计数**|True|

其他字段保持不变，然后选择“保存并关闭”。

> [!TIP]
> 如果使用自己的 Web 服务，请将 URL 粘贴到 Web 浏览器以验证该 URL 是否有效。 

## <a name="open-solution-explorer"></a>打开解决方案资源管理器

所创建的任何自定义实体的部分名称都是自定义前缀。 这是根据所用解决方案的解决方案发布者设置的。 如果很在意自定义前缀，请确保使用的是非托管解决方案，其中自定义前缀是你希望此实体使用的前缀。 详细信息：[更改解决方案发布者前缀](change-solution-publisher-prefix.md) 

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]


## <a name="create-the-virtual-entity"></a>创建虚拟实体

1. 在解决方案资源管理器的左侧导航窗格中，选择“实体”，然后在主窗格中选择“新建”。
2. 在“实体: 新建”窗体上，选择“虚拟实体”选项，然后输入以下信息： 

    |字段|值|
    |--|--|
    |**数据源**|Contoso 示例数据源|
    |**显示名称**|票证|
    |**复数名称**|票证|
    |**名称**|new_ticket|
    |**外部名称**|票证|
    |**外部集合名称**|票证|
    |**说明（包括附件）**|选中|
    |**活动**|选中|

1. 选择“显示此实体的区域”旁的“服务”，然后选择“保存”（但不要关闭实体窗体）。
    ![票证实体定义](media/ticket-entity.png)

## <a name="create-the-fields-for-the-virtual-entity"></a>为虚拟实体创建字段

在“实体: 票证”页面的左侧导航窗格中，选择“字段”。 在本演练中，将编辑两个现有字段并添加第三个字段。

> [!IMPORTANT]
> 外部名称需区分大小写。 请参阅 Web 服务元数据，确保使用正确的名称。
> 可以为 Null 的值若为 false，则表示其为必需属性。 请注意，主键字段始终是系统必需的。

1. 打开“new_ticketid”字段，并使用此处指示的值更改以下属性：“外部名称”：TicketID ![TicketID 字段](media/ticketid-field.png)
1. 选择“保存并关闭”。
1. 打开“new_name”字段，并将以下属性更改为此处指示的值：
    - “显示名称”：标题
    - “外部名称”：标题![标题字段](media/title-field.png)
1. 选择“保存并关闭”。
1. 选择“新建”，然后在“字段: 新建票证”页面上输入以下信息：

    |字段|值|
    |--|--|
    |**显示名称**|严重性|
    |**名称**|new_severity|
    |**外部名称**|严重性|
    |**字段要求**|业务必需|
    |**数据类型**|整数|
    |**最小值**|0|
    |**最大值**|4|

  ![严重级别字段](media/severity-field.png)
1. 选择“保存并关闭”。

## <a name="add-the-fields-to-the-main-form"></a>将字段添加到主窗体

1. 在“票证”实体窗口中，选择“窗体”。
1. 打开主窗体，将“严重级别”字段从右窗格拖放到“标题”字段下“常规”部分的窗体中。 
    ![已添加到主窗体的“严重级别”字段](media/drop-severity-field.png)
1. 在“票证”实体窗口中，选择“保存并关闭”。

## <a name="configure-the-default-view"></a>配置默认视图

1. 在解决方案资源管理器左侧窗格的“票证实体”下，选择“视图”。
1. 打开“所有票证”视图。
1. 在“常规任务”窗格中，选择“添加列”。
    ![为视图添加列](media/addcolumns.png)
1. 选择“严重级别”，然后选择“确定”。
1. 在“视图: 所有票证”窗口中，选择“保存并关闭”。
1. 在“解决方案资源管理器”窗口中，选择“发布所有自定义项”。
    ![发布所有自定义项](media/publishall.png)
1. 发布所有自定义项后，关闭“解决方案资源管理器”窗口。

## <a name="view-the-virtual-entity-in-action-with-dynamics-365-customer-engagement"></a>使用 Dynamics 365 客户参与查看实际运行的虚拟实体

1. 转到“服务” > “扩展” > “票证”。
    
    ![票证区域](media/ticket-area.png)

    随即显示“所有票证”视图。 请注意，可能需要刷新浏览器才能从“服务”区域查看实体。

    ![“所有票证”视图](media/all-tickets-view.png)
1. 打开“票证”记录以查看窗体，该窗体包含使用给定记录的“标题”和“严重级别”字段。
    ![票证记录](media/ticket-record.png)

### <a name="see-also"></a>另请参阅

[OData v4 数据提供程序配置、要求和最佳做法](virtual-entity-odata-provider-requirements.md)<br />
[创建和编辑包含外部数据源数据的虚拟实体](create-edit-virtual-entities.md)
