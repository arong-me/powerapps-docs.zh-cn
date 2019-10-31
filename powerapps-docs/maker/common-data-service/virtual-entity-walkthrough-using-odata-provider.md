---
title: 在 Common Data Service 中使用 OData 数据提供程序演练虚拟实体 | MicrosoftDocs
description: 了解如何在虚拟实体中使用 OData v4 数据提供程序
ms.custom: ''
ms.date: 06/04/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
ms.assetid: null
caps.latest.revision: 11
author: Mattp123
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="virtual-entity-walkthrough-using-the-odata-v4-data-provider"></a>使用 OData v4 数据提供程序演练虚拟实体

假设要从模型驱动应用内访问外部数据源中的票据信息。 在此演练中，您将使用映射到外部架构的字段对虚拟实体建模，该架构在运行时从 OData Web 服务检索票据数据。

## <a name="data-source-details"></a>数据源详细信息

因为用于此演练的数据源拥有 OData v4 Web 服务，所以可使用您的环境随附的 OData v4 数据提供程序。

Web 服务 URL：`http://contosowebservice.azurewebsites.net/odata/` 

> [!IMPORTANT]
> 用于本演练的 Web 服务 url 不是可工作的 Web 服务。

本演练需要一个包含下面三个字段的虚拟实体。

|外部字段名称 |外部数据类型 |虚拟实体数据类型 |用途 |
|---------|---------|---------|---------|
|TicketID |`Edm.Guid` |主键 |实体的主键 |
|标题  |`Edm.String` |单行文本 |票据的标题 |
|严重性 |`Edm.Int32`| 整数 |数值 0-4，用于指示票据的严重性 |

外部数据源票据实体的 OData 元数据：

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

为使用 OASIS 开放数据协议 (OData) 示例 Web 服务的 OData v4 数据提供程序创建数据源。

1. 转至**设置** > **管理** > **虚拟实体数据源**。
1. 依次选择**新建**、**OData v4 数据提供程序**和**确定**。
1. 输入或选择以下信息。

    |字段|值|
    |--|--|
    |**名称**|Contoso Sample Data Source|
    |**URL**|`http://contosowebservice.azurewebsites.net/odata` |
    |**超时**|30|
    |**返回内联计数**|True|

让其他字段保留原样，然后选择**保存并关闭**。

> [!TIP]
> 使用自己的 Web 服务时，请验证 URL 是否有效，方法是将其粘贴到 Web 浏览器中。 

## <a name="open-solution-explorer"></a>打开解决方案资源管理器

您创建的任何自定义实体的名称中都包含自定义前缀。 这是根据您在其中工作的解决方案的解决方案发布商设置的。 如果您关心自定义前缀，请确保在非托管解决方案中工作，其中的自定义前缀是您需要的此实体的前缀。 详细信息：[更改解决方案发布商前缀](change-solution-publisher-prefix.md) 

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]


## <a name="create-the-virtual-entity"></a>创建虚拟实体

1. 在解决方案资源管理器的左侧导航窗格中，选择**实体**，然后从主窗格选择**新建**。
2. 在**实体：新建**窗体中，选择**虚拟实体**选项，然后输入以下信息： 

    |字段|值|
    |--|--|
    |**数据源**|Contoso Sample Data Source|
    |**显示名称**|票据|
    |**复数名称**|票据|
    |**名称**|new_ticket|
    |**外部名称**|票据|
    |**外部集合名称**|票据|
    |**注释(包括附件)**|已选择|
    |**活动**|已选择|

1. 在**显示此实体的区域**旁边，选择**服务**，然后选择**保存**（但不关闭实体窗体）。
    ![票据实体定义](media/ticket-entity.png)

## <a name="create-the-fields-for-the-virtual-entity"></a>创建虚拟实体的字段

在**实体：票据**页面的左侧导航窗格中，选择**字段**。 本演练过程中将编辑两个现有字段，再添加一个字段。

> [!IMPORTANT]
> 外部名称区分大小写。 请参阅 Web 服务元数据以确保使用正确名称。
> 可空值 false 表示属性为必需属性。 请注意，系统始终需要主键字段。

1. 打开 **new_ticketid** 字段，然后使用此处指示的值更改以下属性：**外部名称**：TicketID ![TicketID 字段](media/ticketid-field.png)
1. 选择**保存并关闭**。
1. 打开 **new_name** 字段，然后将以下属性更改为此处指示的值：
    - **显示名称**：标题
    - **外部名称**：标题 ![标题字段](media/title-field.png)
1. 选择**保存并关闭**。
1. 选择**新建**，然后在**票据的字段：新建**页面中输入以下信息：

    |字段|值|
    |--|--|
    |**显示名称**|严重性|
    |**名称**|new_severity|
    |**外部名称**|严重性|
    |**字段要求**|业务必需的|
    |**数据类型**|整数|
    |**最小值**|0|
    |**最大值**|4|

  ![“严重性”字段](media/severity-field.png)
1. 选择**保存并关闭**。

## <a name="add-the-fields-to-the-main-form"></a>将字段添加到主窗体

1. 在“票据实体”窗口中，选择**窗体**。
1. 打开主窗体，将**严重性**字段从右窗格拖放到**常规**部分**标题**字段下的窗体中。 
    ![添加到主窗体的“严重性”字段](media/drop-severity-field.png)
1. 在“票据实体”窗口中，选择**保存并关闭**。

## <a name="configure-the-default-view"></a>配置默认视图

1. 在解决方案资源管理器的左窗格中**票据实体**下，选择**视图**。
1. 打开**所有票据**视图。
1. 在**常规任务**窗格中，选择**添加列**。
    ![为视图添加列](media/addcolumns.png)
1. 选择**严重性**，然后选择**确定**。
1. 在**视图：所有票据**窗口中，选择**保存并关闭**。
1. 在解决方案资源管理器窗口中，单击**发布所有自定义项**。
    ![发布所有自定义项](media/publishall.png)
1. 发布了所有自定义项之后，关闭解决方案资源管理器窗口。

## <a name="view-the-virtual-entity-in-action-with-dynamics-365"></a>通过 Dynamics 365 查看使用中的虚拟实体

1. 转至**服务** > **扩展** > **票据**。
    
    ![“票据”区域](media/ticket-area.png)

    将显示**所有票据**视图。 请注意，可能需要刷新浏览器，才能从**服务**区域查看实体。

    ![“所有票据”视图](media/all-tickets-view.png)
1. 打开**票据**记录查看其中包含给定记录的**标题**和**严重性**字段的窗体。
    ![票据记录](media/ticket-record.png)

### <a name="see-also"></a>另请参阅

[OData v4 数据提供程序配置，要求和最佳实践](virtual-entity-odata-provider-requirements.md)<br />
[创建和编辑包含来自外部数据源的数据的虚拟实体](create-edit-virtual-entities.md)
