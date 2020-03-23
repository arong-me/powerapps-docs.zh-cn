---
title: 配置连接角色 | MicrosoftDocs
ms.custom: ''
ms.date: 02/11/2020
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- PowerApps
ms.author: matp
manager: kvivek
author: Mattp123
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 0827acf9d7699e6bf88374d57a6e5218e3000ef5
ms.sourcegitcommit: 2b34de88c977c149e4c632b23d8e816901c15949
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/12/2020
ms.locfileid: "3040472"
---
# <a name="configure-connection-roles"></a>配置连接角色

使用 Common Data Service，您可以定义实体记录之间的**连接**，而无需创建实体关系。 在模型驱动应用程序中，用户可以在记录之间建立命名的链接，从而建立不创建实际实体关系的不太正式的关系。 部分示例包括*朋友*、*兄弟姊妹*、*配偶*、*与会者*和*利益干系人*。 有些连接还可以是相互的，如*孩子*和*父亲*、*丈夫*和*妻子*或*医生*和*患者*。

当用户在两个记录之间设置连接时，还可以添加描述和其他信息，如关系的开始日期和结束日期。 详细信息：[创建连接以定义和查看记录之间的关系](/dynamics365/customer-engagement/basics/create-connections-view-relationships-between-records)

具有**连接角色**实体写入访问权限的任何人都可以建立可供用户使用的连接。

> [!IMPORTANT]
> 要使某个实体可以用作新的或现有的连接角色的记录类型，必须为该实体启用**启用连接**属性。 

## <a name="enable-connection-roles-for-an-entity"></a>为实体启用连接角色
1. 登录到 [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。 
2. 展开**数据**，然后选择**实体**。 
3. 选择要为连接角色启用的实体，然后在命令栏上选择**设置**。 
4. 在**设置**窗格中，展开**协作**区域，然后选择**启用连接**。
    > [!div class="mx-imgBorder"] 
    > ![启用连接设置](media/enable-connections.png "启用连接设置")

6. 选择**完成**。 

## <a name="view-connection-roles"></a>查看连接角色

Common Data Service 中已存在一些已经配置的标准连接角色。  

1. 登录到 [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)，然后在左窗格中选择**解决方案**。 
2. 打开所需的非托管解决方案。 
3. 在命令栏上，选择**添加现有**，然后选择**连接角色**。 
   将显示可用连接角色的列表。 
4. 选择**取消**可关闭**添加现有连接角色**对话框，而不向解决方案添加连接角色。

> [!NOTE]
> - 如果想要使用解决方案分发连接角色，请确保它们包含在您要分发的解决方案中。 详细信息：[向解决方案添加连接角色](#add-connection-roles-to-a-solution)

### <a name="view-and-edit-connection-roles-using-the-classic-experience"></a>使用经典体验查看和编辑连接角色

您可以在**设置**区域中查看的多数连接角色在*内部*的**默认解决方案中定义**（不要与 **Common Data Services 默认解决方案**混淆）。 此内部**默认解决方案**包含系统中的所有自定义项。 若要查看**默认解决方案**，选择**所有解决方案 - 内部**视图。 

1. 登录到 [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)，在命令栏上选择**设置** ![设置](media/powerapps-gear.png)，然后选择**高级设置**。
2. 导航到**设置** > **业务** > **业务管理**，然后选择**连接角色**。

   > [!div class="mx-imgBorder"] 
   > ![“业务管理”设置中的连接角色](media/navigate-settings-connection-roles.png "“业务管理”设置中的连接角色")

在该视图中，您可以查看该环境可用的所有连接角色，并且可以在此处编辑它们。

## <a name="add-connection-roles-to-a-solution"></a>向解决方案添加连接角色
由于连接角色*可识别解决方案*，这意味着它们可以包括在解决方案中，您也可以将连接角色添加到要分发的解决方案中。

通常不建议在内部**默认解决方案**中编辑组件。 在您创建的要使用的解决方案中，您可以使用**解决方案**区域的**添加现有**命令将任何可用连接角色加入您的解决方案。

> [!div class="mx-imgBorder"] 
> ![添加现有连接角色](media/add-existing-connection-role.png)

在您将连接角色添加到解决方案中后，您可以在其可见的位置进行编辑。

> [!NOTE]
> 在从解决方案导出连接角色时，不会将连接角色状态包含在连接角色中。 因此，在将解决方案导入目标环境时，默认情况下状态将设置为可用。 


## <a name="create-a-connection-role"></a>创建连接角色

> [!IMPORTANT]
> 如果您想要分发包括新连接角色或对现有连接角色的更改的解决方案，您必须将其添加到你将分发的解决方案中。 使用**设置**区域编辑或添加新连接角色会将这些连接角色添加到内部**默认解决方案**，且不会在您将分发的解决方案中包含这些连接角色，除非您首先将其添加到解决方案中。 详细信息[向解决方案添加连接角色](#add-connection-roles-to-a-solution)

1. 登录到 [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)，然后在左窗格中选择**解决方案**。 
2. 打开所需的非托管解决方案，然后在命令栏上选择**新建** > **其他** > **连接角色**。 
3. 完成窗体上的三个步骤来[描述连接角色](#describe-the-connection-role)。

   > [!div class="mx-imgBorder"] 
   > ![创建“连接角色”窗体](media/create-connection-role-form.png)

### <a name="describe-the-connection-role"></a>描述连接角色

设置以下字段：

|字段|说明|
|--|--|
|**名称**|（必填）描述连接的文本。|
|**连接角色类别**|描述连接类别的组。 详细信息：[连接角色类别值](#connection-role-category-values)|
|**说明**|为角色提供定义。|

#### <a name="connection-role-category-values"></a>连接角色类别值

**连接角色类别**的默认值为：
- 企业
- 家庭
- 社交
- Sales
- 其他
- 利益干系人
- 销售团队
- 服务

您可以通过编辑**类别**全局选项集添加新类别或修改现有类别。 详细信息：[为 Common Data Service 创建和编辑全局选项集（选择列表）](create-edit-global-option-sets.md)

#### <a name="select-record-types"></a>选择记录类型

选择哪些记录类型应用于连接。

> [!NOTE]
> 默认情况下选择**所有**，不过请确保您考虑了哪些类型适合您在添加的连接角色。

#### <a name="matching-connection-roles"></a>匹配的连接角色

在该可选步骤中，您可以定义以对应方式应用的所有角色。 这不是必要的，但是如果加以定义，连接会更有意义。

例如，用户可以设置 Glen 是 Mary 的*朋友*，但这意味着 Mary 是 Glen 的*朋友*吗？ 我们希望如此。 但是，如果 Glen 是 Mary 的*父亲*，这并不意味着 Mary 是 Glen 的*父亲*。 建立正确的相互角色需要此额外步骤。

在用户设置没有匹配的连接角色的连接角色时，仅在查看连接所应用的记录的连接时角色才会显示。 当从连接的记录查看时，角色将为空，除非设置了匹配的角色。

对于*朋友*、*配偶*、*同事*或*兄弟姐妹*这样的角色定义，最好向其分配匹配的角色。 如果配置了单个匹配的连接角色，这个单个匹配的连接角色将双向应用。

> [!IMPORTANT]
> 您需要保存没有此匹配的连接角色的新连接角色，然后才能够设置它自己的匹配的连接角色。

您会发现有些连接角色已经使用匹配的连接角色配置。 *以前的员工*与*以前的雇主*匹配，反之亦然。 此类一对一匹配的连接角色是最常见的。

您可以配置多个匹配的连接角色来描述复杂的关系。 如果您创建连接角色（如*父亲*），您可以再配置两个角色（如*女儿*和*儿子*），并将这两个角色作为匹配的连接角色应用到*父亲*。 反之，*女儿*和*儿子*连接角色均应与*父亲*匹配。 当然，随后您应为与*女儿*和*儿子*类似匹配的*母亲*设置同等角色。

> [!TIP]
> 在创建复杂的连接角色集前，请考虑更简单的角色集是否已经够用。 例如，先不要创建复杂的连接角色集，如*父亲*、*母亲*、*儿子*和*女儿* - 考虑只使用*父亲*和*孩子*能否满足您的需要。

如果配置了多个匹配的连接角色，这些连接角色仅表示有效的相互角色。 第一个角色将自动应用为默认值。 如果默认值不正确，用户需要手动编辑连接并在配置中定义的有效选项之间选择。

### <a name="see-also"></a>另请参阅
<!-- This is in the basics guide. It needs to be migrated -->
[创建连接以定义和查看记录之间的关系](/dynamics365/customer-engagement/basics/create-connections-view-relationships-between-records)<br />
[创建和编辑 Common Data Service 的全局选项集（选择列表）](create-edit-global-option-sets.md)<br />
[创建和编辑实体之间的关系](create-edit-entity-relationships.md)


