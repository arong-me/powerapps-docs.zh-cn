---
title: 使用面向应用程序的 Common Data Service 创建和编辑虚拟实体 | MicrosoftDocs
description: 了解如何创建虚拟实体
ms.custom: ''
ms.date: 06/27/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
ms.assetid: 44834893-0bf6-4a64-8f06-7583fe08330d
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
# <a name="create-and-edit-virtual-entities-that-contain-data-from-an-external-data-source"></a>创建和编辑包含来自外部数据源的数据的虚拟实体

虚拟实体是面向应用程序的 Common Data Service 中的自定义实体，这种实体有字段包含来自外部数据源的数据。 虚拟实体在您的应用程序中作为定期实体记录显示给用户，但包含源自外部数据库（如 Azure SQL 数据库）的数据。 所有客户端（包括使用面向应用程序的 CDS Web 服务开发的自定义客户端）中均提供基于虚拟实体的记录。  
  
以前，要集成分散的数据源，需要创建连接器来移动数据，或开发自定义插件（客户端或服务器端）。 但是，通过虚拟实体可以在运行时直接连接外部数据源，这样无需复制数据即可在环境中使用外部数据源。  

虚拟实体包含三个主要组成部分：*数据提供程序*、*数据源*记录和*虚拟实体*。 数据提供程序由插件和数据源实体组成。 数据源是面向应用程序的 CDS 中的实体记录，其中包含表示连接参数的架构的元数据。 每个虚拟实体都引用实体定义中的一个数据源。  
  
面向应用程序的 CDS 中包含 OData 数据提供程序，可用于连接 OData v4 Web 服务来访问外部数据。 
  
开发人员也可以构建自己的数据提供程序。 数据提供程序作为解决方案安装在环境中。 详细信息：[开发人员文档：虚拟实体入门](/dynamics365/customer-engagement/developer/virtual-entities/get-started-ve)
  
 ![虚拟实体图](media/virtual-entity-diagram.png "虚拟实体图")  
  
<a name="benefits"></a> 
  
## <a name="virtual-entity-benefits"></a>虚拟实体的优点  
  
- 开发人员可以实施插件以使用面向应用程序的 CDS Web 服务和插件注册工具读取外部数据。  
- 系统定制员可使用 PowerApps 解决方案资源管理器配置数据源记录和创建虚拟实体，用于在不编写任何代码的情况下访问外部数据。  
- 最终用户使用虚拟实体创建的记录来查看字段、网格、搜索结果以及基于 Fetch XML 的报告和仪表板中的数据。  
  
<a name="AddDataSource"></a> 
  
## <a name="add-a-data-source-to-use-for-virtual-entities"></a>添加用于虚拟实体的数据源 
 
 开发人员可以创建自定义插件来用作虚拟实体的数据提供程序。  您也可以使用提供的 OData v4 数据提供程序。 详细信息：[OData v4 数据提供程序配置，要求和最佳实践](virtual-entity-odata-provider-requirements.md)  
  
1. 转至**[设置](../model-driven-apps/advanced-navigation.md#settings)** > **管理** > **虚拟实体数据源**。  
1. 在“操作”工具栏上，选择**新建**。  
1. 在**选择数据提供程序**对话框中，从以下数据源中进行选择，然后选择**确定**。
 
    |数据提供程序|说明|
    |--|--|
    |*自定义数据提供程序*|如果已导入数据提供程序插件，将在此处显示该数据提供程序。 详细信息[开发人员文档：虚拟实体入门](/dynamics365/customer-engagement/developer/virtual-entities/get-started-ve)|
    |**OData v4 数据提供程序**|面向应用程序的 CDS 中包含可与 OData v4 Web 服务配合使用的 OData 数据提供程序。 详细信息 [OData v4 数据提供程序配置，要求和最佳实践](virtual-entity-odata-provider-requirements.md)|

  
### <a name="add-a-secured-field-to-a-data-source"></a>向数据源添加安全字段

按照与其他任何实体相同的方式为数据源创建字段。 对于加密数据或敏感数据，请对数据源的自定义字段启用“数据源密码”属性。 例如，若要保护包含数据库连接字符串的字段。 

> [!NOTE]
> 只有添加到“数据源”窗体的字段才有“数据源密码”属性。

> [!div class="mx-imgBorder"] 
> ![数据源密钥属性](media/datasourcesecret.png)
  
<a name="createVirtualEntity"></a> 
  
## <a name="create-a-virtual-entity"></a>创建虚拟实体
  
除了此处介绍的一些额外的属性，虚拟实体的创建方法和面向应用程序的 CDS 中的其他任何实体很像。 虚拟实体必须使用解决方案资源管理器创建。

> [!NOTE]
>  尽管可以通过选择**无**作为数据源来创建虚拟实体，但是为了获取数据，虚拟实体需要数据源。 详细信息[添加用于虚拟实体的数据源](#AddDataSource)

### <a name="open-solution-explorer"></a>打开解决方案资源管理器

您创建的任何虚拟实体的名称中都包含自定义前缀。 这是根据您在其中工作的解决方案的解决方案发布商设置的。 如果您关心自定义前缀，请确保在非托管解决方案中工作，其中的自定义前缀是您需要的此虚拟实体的前缀。 详细信息：[更改解决方案发布商前缀](change-solution-publisher-prefix.md) 

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

### <a name="create-a-virtual-entity"></a>创建虚拟实体
  
1. 在解决方案资源管理器中，创建一个新实体。 方法是，选择左导航窗格中的**实体**，然后选择**新建**。  
2. 在**实体定义**的**常规**选项卡上，选择**虚拟实体**，然后在**数据源**下拉列表中，选择所需数据源。  

    > [!div class="mx-imgBorder"] 
    > ![实体定义中的虚拟实体选项](media/virtual-entity-click-option.png)  
  
1. 在“实体定义”中，填写以下必填字段。
  
    |字段|说明|
    |--|--|
    |**外部名称**|在此实体映射到的外部数据源中输入表的名称。|
    |**外部集合名称**|在此实体映射到的外部数据源中输入表的复数名称。|
      
    下面是名称为 *Movie* 的虚拟实体的示例，该实体使用 Azure Cosmos 数据库数据提供程序访问文档文件。  
      
    > [!div class="mx-imgBorder"] 
    > ![使用 Azure Cosmos DB 数据提供程序的虚拟实体定义](media/virtual-entity-definition.PNG)  
      
    > [!IMPORTANT]
    > 虚拟实体支持多个选项，如“访问团队”、“队列”和“快速创建”。 详细信息：[使用虚拟实体时的注意事项](#considerations)  
      
    请根据需要完成更多必需属性和可选属性。 有关这些属性的详细信息，请参阅[创建和编辑实体](create-edit-entities.md)。  
  
1. 为虚拟实体创建和添加一个或多个字段。 除了创建自定义字段所需的标准字段属性，还可以为您为虚拟实体创建的各自定义字段使用以下可选属性。

    |字段|说明|
    |--|--|
    |**外部名称**|这通常是用于标识要在字段中显示的数据的唯一名称。|
    |**外部类型名称**|如果您创建的字段类型是 OptionSet：此属性映射到选项集的外部服务中的值集的外部名称。  通常可以是字符串值类的枚举或名称。 如果需要完全限定的名称，则可使用外部类型名称。  例如，因为在查询中的参数需要完全限定的名称的 OData 中的*类型名称*，如 [*类型名称*].[*值*]。|
    |**外部值**|如果您创建的字段类型是 OptionSet：此属性映射到选项集项目的外部数据源中的对应值。  输入的该值用于确定应用中显示哪个选项集。  |

    根据需要完成更多属性。 有关这些属性的详细信息，请参阅[创建和编辑字段](create-edit-fields.md)。  
  
1. 选择**字段**属性页中的**保存并关闭**。  
1. 在解决方案资源管理器工具栏中，选择**保存**。  
1. 在解决方案资源管理器工具栏中，选择**发布**。  
1. 关闭解决方案资源管理器。  

<a name="considerations"></a>
   
## <a name="considerations-when-you-use-virtual-entities"></a>使用虚拟实体时的注意事项  

虚拟实体有以下限制。  
  
- 所有虚拟实体均为只读。  
- 不能将现有实体转换为虚拟实体。  
- 默认情况下，虚拟实体只包含“名称”和“ID”字段。  其他系统管理字段（如“状态”或“创建日期/修改日期”）不受支持。
- 虚拟实体不支持数据类型为“货币”、“图像”或“客户”的自定义字段。
- 虚拟实体不支持审核。  
- 不能在汇总字段或计算字段中使用虚拟实体字段。
- 虚拟实体不能为实体的活动类型。  
- 不能为虚拟实体启用许多可影响实体表行的功能。  例如，队列、知识管理、SLA、重复项检测、更改跟踪、Mobile offline 功能、现场安全、相关性搜索、Dynamics 365 Web 门户解决方案的门户，以及虚拟实体之间的 N:N 关系。  
- 虚拟实体归组织所有，不支持行级别的适用于应用的 Commond Data Service 安全概念。 建议为外部数据源实施您自己的安全模型。  
- 建议在高级查找中使用虚拟实体时，针对单个数据源。 例如，不支持创建最终在适用于应用的 Commond Data Service 本机数据与虚拟实体外部数据之间创建联接的高级查找。  
- 更新时验证的字段元数据属性不应用于虚拟实体。 例如，可将虚拟实体字段中的整数字段设置为最小值为零。 但是，因为该值来自外部数据源，所以从虚拟实体检索时，查询将返回小于零的值。  查询中不表示最小值属性。  您仍需将该值筛选为大于 0（如果需要这样）。
- 虚拟实体不支持更改跟踪，因此不能使用面向应用程序的 CDS 功能（如数据导出服务）同步。
  
### <a name="see-also"></a>另请参阅  

[OData v4 数据提供程序要求和最佳实践](virtual-entity-odata-provider-requirements.md)</br> 
[创建和编辑实体](create-edit-entities.md)</br>
[创建和编辑字段](create-edit-fields.md)
