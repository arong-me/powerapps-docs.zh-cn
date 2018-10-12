---
title: 使用 Common Data Service for Apps 创建和编辑虚拟实体 | Microsoft Docs
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
ms.openlocfilehash: 675c0ac5763698c82a7d13bfc75f8b7357d6cf0b
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39667874"
---
# <a name="create-and-edit-virtual-entities-that-contain-data-from-an-external-data-source"></a>创建和编辑包含外部数据源数据的虚拟实体

虚拟实体是 Common Data Service for Apps 中的自定义实体，具有含外部数据源数据的字段。 虚拟实体在应用中作为常规实体记录显示给用户，但包含来自外部数据库（如 Azure SQL 数据库）的数据。 基于虚拟实体的记录可用于所有客户端中，包括使用 CDS for Apps Web 服务开发的自定义客户端。  
  
过去，若要集成不同的数据源，需创建一个连接器来移动数据或开发自定义插件（无论是客户端还是服务器端）。 但是，使用虚拟实体，可在运行时直接与外部数据源连接，以便外部数据源中的特定数据在环境中可用，而无需复制数据。  

虚拟实体由三个主要部分组成：“数据提供程序”、“数据源”记录和“虚拟实体”。 数据提供程序由插件和数据源实体组成。 数据源是 CDS for Apps 中的实体记录，包括表示连接参数架构的元数据。 每个虚拟实体都引用实体定义中的数据源。  
  
CDS for Apps 包含一个 OData 数据提供程序，可使用该提供程序连接访问外部数据的 OData v4 Web 服务。 
  
或者，开发人员可构建自己的数据提供程序。 数据提供程序作为解决方案安装在环境中。 详细信息：[开发人员文档：虚拟实体入门](/dynamics365/customer-engagement/developer/virtual-entities/get-started-ve)
  
 ![虚拟实体关系图](media/virtual-entity-diagram.png "Virtual entity diagram")  
  
<a name="benefits"></a> 
  
## <a name="virtual-entity-benefits"></a>虚拟实体优势  
  
- 开发人员可使用 CDS for Apps Web 服务和插件注册工具实现插件，以读取外部数据。  
- 系统定制员使用 PowerApps 解决方案资源管理器来配置数据源记录，并在无需编写任何代码的情况下创建用于访问外部数据的虚拟实体。  
- 最终用户使用虚拟实体创建的记录查看字段、网格、搜索结果及基于 Fetch XML 的报表和仪表板中的数据。  
  
<a name="AddDataSource"></a> 
  
## <a name="add-a-data-source-to-use-for-virtual-entities"></a>添加用于虚拟实体的数据源 
 
 开发人员创建了自定义插件，以用作虚拟实体的数据提供程序。 或者，可使用提供的 OData v4 数据提供程序。 详细信息：[OData v4 数据提供程序配置、要求和最佳做法](virtual-entity-odata-provider-requirements.md)  
  
1. 转到“[设置](../model-driven-apps/advanced-navigation.md#settings)” > “管理” > “虚拟实体数据源”。  
1. 在操作工具栏上，选择“新建”。  
1. 在“选择数据提供程序”对话框中，从以下数据源中进行选择，然后选择“确定”。
 
    |数据提供程序|描述|
    |--|--|
    |自定义数据提供程序|如果已导入数据提供程序插件，数据提供程序将在此处显示。 详细信息：[开发人员文档：虚拟实体入门](/dynamics365/customer-engagement/developer/virtual-entities/get-started-ve)|
    |OData v4 数据提供程序|CDS for Apps 包括可与 OData v4 Web 服务一起使用的 OData 数据提供程序。 详细信息：[OData v4 数据提供程序配置、要求和最佳做法](virtual-entity-odata-provider-requirements.md)|

  
### <a name="add-a-secured-field-to-a-data-source"></a>将受保护字段添加到数据源

可使用与任何其他实体相同的方式为数据源创建字段。 对于加密或敏感数据，请在数据源的自定义字段上启用数据源机密属性。 例如，保护包含数据库连接字符串的字段。 

> [!NOTE]
> 仅添加到数据源窗体的字段才提供数据源机密属性。

![数据源机密属性](media/datasourcesecret.png)
  
<a name="createVirtualEntity"></a> 
  
## <a name="create-a-virtual-entity"></a>创建虚拟实体
  
可通过添加一些此处所述的其他属性在 CDS for Apps 中创建像任何其他实体一样的虚拟实体。 必须使用解决方案资源管理器创建虚拟实体。

> [!NOTE]
>  虽然可通过选择 None 作为数据源来创建虚拟实体，但要获取数据，虚拟实体还需要数据源。 详细信息：[添加用于虚拟实体的数据源](#AddDataSource)

### <a name="open-solution-explorer"></a>打开解决方案资源管理器

所创建的任何虚拟实体的部分名称都是自定义前缀。 这是根据所用解决方案的解决方案发布者设置的。 如果很在意自定义前缀，请确保使用的是非托管解决方案，其中自定义前缀是你希望此虚拟实体使用的前缀。 详细信息：[更改解决方案发布者前缀](change-solution-publisher-prefix.md) 

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

### <a name="create-a-virtual-entity"></a>创建虚拟实体
  
1. 在解决方案资源管理器中，创建一个新实体。 若要执行此操作，在左侧导航窗格中选择“实体”，然后选择“新建”。  
2. 在“实体定义”的“常规”选项卡上，选择“虚拟实体”，然后在“数据源”下拉列表中选择所需数据源。  
  
    ![实体定义上的“虚拟实体”选项](media/virtual-entity-click-option.png)  
  
1. 在“实体定义”上，完成以下必填字段。
  
    |字段|描述|
    |--|--|
    |外部名称|在此实体映射到的外部数据源中输入表的名称。|
    |外部集合名称|在此实体映射到的外部数据源中输入表的复数名称。|
      
    以下是名为 Movie 的虚拟实体的示例，该实体使用 Azure Cosmos DB 数据提供程序来访问文档文件。  
      
    ![使用 Azure Cosmos DB 数据提供程序的虚拟实体定义](media/virtual-entity-definition.PNG)  
      
    > [!IMPORTANT]
    > 虚拟实体不提供“访问团队”、“队列”和“快速创建”等多种选项。 详细信息：[使用虚拟实体时的注意事项](#considerations)  
      
    根据需要完成其他必需和可选属性，例如显示名称和复数名称。 有关这些属性的详细信息，请参阅[创建和编辑实体](create-edit-entities.md)。  
  
1. 为虚拟实体创建和添加一个或多个字段。 除创建自定义字段所需的标准字段属性外，这些可选属性还可用于为虚拟实体创建的每个自定义字段。

    |字段|描述|
    |--|--|
    |外部名称|这通常是用于标识要在字段中显示的数据的唯一名称。|
    |外部类型名称|如果创建的字段类型是 OptionSet：此属性映射到选项集外部服务中的值集的外部名称。  通常，这可以是字符串值类的枚举或名称。 当需要完全限定名称时，可使用“外部类型名称”。  例如，作为含 OData 的“类型名称”，其中查询中的参数需要完全限定名称，例如 [类型名称].[值]。|
    |外部值|如果创建的字段类型是 OptionSet：此属性映射到选项集项的外部数据源中的相应值。  输入的此值用于确定要在应用中显示的选项集项。  |

    根据需要完成其他属性。 有关这些属性的详细信息，请参阅[创建和编辑字段](create-edit-fields.md)。  
  
1. 在“字段”属性页上选择“保存并关闭”。  
1. 在解决方案资源管理器工具栏上，选择“保存”。  
1. 在解决方案资源管理器工具栏上，选择“发布”。  
1. 关闭解决方案资源管理器。  

<a name="considerations"></a>
   
## <a name="considerations-when-you-use-virtual-entities"></a>使用虚拟实体时的注意事项  

虚拟实体具有以下限制。  
  
- 所有虚拟实体都是只读的。  
- 现有实体无法转换为虚拟实体。  
- 默认情况下，虚拟实体仅包含“名称”和“ID”字段。  不支持其他系统托管字段，例如“状态”或“创建时间”/“修改时间”。
- 虚拟实体不支持具有“货币”、“映像”或“客户”数据类型的自定义字段。
- 虚拟实体不支持审核。  
- 虚拟实体字段不能用于汇总或计算字段。
- 虚拟实体不能为实体的活动类型。  
- 无法通过虚拟实体启用影响实体表行的诸多功能。  其示例包括队列、知识管理、SLA、重复检测、更改跟踪、移动离线功能、字段安全性、相关性搜索、Dynamics 365 Web 门户解决方案的门户，以及虚拟实体之间的 N:N 关系。  
- 虚拟实体由组织所有，不支持行级别的 Common Data Service for Apps 安全概念。 建议你为外部数据源实现你自己的安全模型。  
- 建议在“高级查找”中使用虚拟实体时以单个数据源为目标。 例如，不支持创建最终会在 Common Data Service for Apps 本机数据和虚拟实体外部数据之间创建联接的“高级查找”。  
- 更新时确认的字段元数据属性不适用于虚拟实体。 例如，虚拟实体字段上的“整数”字段可设置为最小值为零。 但是，由于该值来自外部数据源，因此，从虚拟实体中检索时，查询将返回小于零的值。  查询中不隐含最小值属性。  如果需要，仍需筛选大于 0 的值。
- 虚拟实体不支持更改跟踪，并且无法使用 CDS for Apps 功能（例如数据导出服务）进行同步。
  
### <a name="see-also"></a>另请参阅  

[OData v4 数据提供程序要求和最佳做法](virtual-entity-odata-provider-requirements.md)</br> 
[创建并编辑实体](create-edit-entities.md)</br>
[创建并编辑字段](create-edit-fields.md)
