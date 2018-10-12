---
title: 配置连接角色 | Microsoft Docs
ms.custom: ''
ms.date: 05/27/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- PowerApps
ms.author: matp
manager: brycho
ms.openlocfilehash: 4faf195f1c751e3796267d52725c1cb753c4889d
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39669135"
---
# <a name="configure-connection-roles"></a>配置连接角色

使用 Common Data Service for Apps 可以在实体记录之间定义**连接**，而无需创建实体关系。 在模型驱动应用中，用户可以在记录之间建立命名链接，以建立不太正式的关系，而这并不表示创建实际的实体关系。 一些示例包括*朋友*、*兄弟姐妹*、*配偶*、*与会者*和*利益干系人*。 有些连接也可能是对等的，例如*孩子*和*父母*、*丈夫*和*妻子*或者*医生*和*病人*。

当用户在两个记录之间建立连接时，他们还可以添加描述和其他信息，例如关系的开始和结束日期。 详细信息：[创建连接以定义和查看记录之间的关系](/dynamics365/customer-engagement/basics/create-connections-view-relationships-between-records)

对**连接角色**实体拥有写访问权限的任何人都可以确定哪些连接可供人们使用。

## <a name="view-connection-roles"></a>查看连接角色

CDS for Apps 中已经配置了许多标准连接角色。 若要查看它们，需转到设置区域。 

### <a name="navigate-to-the-settings-area"></a>导航到设置区域

1. 查看模型驱动应用时，编辑 URL 以删除 `dynamics.com` 后面的所有内容并刷新页面。
1. 导航到“设置” > “业务” > “业务管理”，然后选择“连接角色”。

![“业务管理”设置中的连接角色](media/navigate-settings-connection-roles.png)

在此视图中，可以看到可用于此环境的所有连接角色，并且可以在此处对其进行编辑。

> [!NOTE]
> 如果要使用解决方案分发连接角色，请确保它们包含在要分发的解决方案中。 详细信息：[将连接角色添加到解决方案中](#add-connection-roles-to-a-solution)

## <a name="view-connection-roles-in-the-solution-explorer"></a>在解决方案资源管理器中查看连接角色。

由于连接角色*可识别解决方案*，这意味着它们可以包含在解决方案中，因此还可以将连接角色添加到分发的解决方案中。

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

可在“设置”区域中看到的大多数连接角色都在*内部***默认解决方案**中定义（不要与 **Common Data Services 默认解决方案**混淆）。 此内部**默认解决方案**包含系统中的所有自定义项。 若要查看**默认解决方案**，请选择“所有解决方案 - 内部”视图。

## <a name="add-connection-roles-to-a-solution"></a>将连接角色添加到解决方案中

通常建议不要编辑内部**默认解决方案**中的组件。 在 **Common Data Services 默认解决方案**或已经创建以供使用的任何解决方案中，可以使用“添加现有”命令将任何默认连接角色引入解决方案。

![添加现有连接角色](media/add-existing-connection-role.png)

将连接角色添加到解决方案后，无论它出现在哪个位置，都可以对它进行编辑。

## <a name="create-or-edit-connection-roles"></a>创建或编辑连接角色。

> [!IMPORTANT]
> 如果打算分发包含新连接角色或现有连接角色更改的解决方案，则必须将它们添加到要分发的解决方案中。 在使用“设置”区域编辑或添加新的连接角色时，会将这些连接角色添加到内部**默认解决方案**中，而不会将它们包含在你要分发的解决方案中，除非你先将其添加到你的解决方案中。 详细信息[将连接角色添加到解决方案中](#add-connection-roles-to-a-solution)

在“连接角色”列表中，选择一个连接角色进行编辑。
定义连接角色有三个步骤，这些步骤已在窗体中清楚地标注出来。

![“创建连接角色”窗体](media/create-connection-role-form.png)

### <a name="describe-the-connection-role"></a>描述连接角色

设置以下字段：

|字段|描述|
|--|--|
|**名称**|（必填）描述连接的文本。|
|**连接角色类别**|描述连接类别的组。 详细信息：[连接角色类别值](#connection-role-category-values)|
|**Description**|提供角色定义。|

#### <a name="connection-role-category-values"></a>连接角色类别值

默认的“连接角色类别”值为：
- 业务
- 家庭
- 社交
- 销售热线
- 其他
- 利益干系人
- 销售团队
- 服务

可以通过编辑“类别”全局选项集来添加新类别或修改现有类别。 详细信息：[为 Common Data Service for Apps 创建和编辑全局选项集（选择列表）](create-edit-global-option-sets.md)

### <a name="select-record-types"></a>选择记录类型

选择可供连接的记录类型。

> [!NOTE]
> 虽然默认选择“全部”，但请务必考虑哪些类型适用于要添加的连接角色。

### <a name="matching-connection-roles"></a>匹配连接角色

在此可选步骤中，可以定义以对等方式应用的任何角色。 此步骤不是必需的，但如果定义了连接，连接将更有意义。

例如，用户可以设定 Glen 是 Mary 的*朋友*，但这是否意味着 Mary 是 Glen 的*朋友*？ 我们希望如此。 但如果 Glen 是 Mary 的*父亲*，则不意味着 Mary 是 Glen 的*父亲*。 若要建立正确的对等关系，则需执行这个额外的步骤。

当用户设置一个没有匹配连接角色的连接角色时，只有在从应用了连接的记录中查看连接时才会显示该角色。 从连接的记录中查看时，除非设置了匹配角色，否则该角色将为空。

对于*朋友*、*配偶*、*同事*或*兄弟姐妹*等角色定义，最好将匹配角色分配给自身。 如果配置了单一匹配连接角色，则将双向应用单一匹配连接角色。

> [!IMPORTANT]
> 需保存没有此匹配连接角色的新连接角色，才能将匹配连接角色设置为自身。

你会发现某些连接角色已经配置了匹配连接角色。 *前雇员*与*前雇主*匹配，反之亦然。 这种一对一的匹配连接角色是最常见的。

可以配置多个匹配连接角色来描述复杂的关系。 如果创建诸如*父亲*之类的连接角色，则可以配置另外两个角色，例如*女儿*和*儿子*，并将它们作为匹配连接角色应用于*父亲*。 反过来，*女儿*和*儿子*连接角色都应与*父亲*匹配。 当然，接下来应该为*母亲*设置一个等效角色，该角色同样与*女儿*和*儿子*匹配。

> [!TIP]
> 在创建一组复杂的连接角色之前，请考虑是否创建一组较简单的角色便已足够。 例如，请考虑是否使用*父母*和*孩子*就能满足你的需求，而不是创建一组复杂的连接角色，例如*父亲*、*母亲*、*儿子*和*女儿*。

如果配置了多个匹配连接角色，则这些连接角色代表唯一有效的对等角色。 第一个将自动应用为默认值。 如果默认值不正确，则需要手动编辑连接并在配置中定义的有效选项之间进行选择。

### <a name="see-also"></a>另请参阅
<!-- This is in the basics guide. It needs to be migrated -->
[创建连接以定义和查看记录之间的关系](/dynamics365/customer-engagement/basics/create-connections-view-relationships-between-records)<br />
[为 Common Data Service for Apps 创建和编辑全局选项集（选择列表）](create-edit-global-option-sets.md)<br />
[创建和编辑实体之间的关系](create-edit-entity-relationships.md)


