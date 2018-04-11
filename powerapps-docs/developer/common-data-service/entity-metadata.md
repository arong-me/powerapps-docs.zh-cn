---
title: 实体元数据 | Microsoft Docs
description: 了解在 Common Data Service for Apps 中使用的实体元数据。
services: ''
suite: powerapps
documentationcenter: na
author: JimDaly
manager: faisalmo
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 03/19/2018
ms.author: jdaly
ms.openlocfilehash: eb908978eee8d6473a46ca3894cee55ce4b036df
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2018
---
# <a name="entity-metadata"></a>实体元数据

每个实体都提供了存储结构化数据的功能。 对于开发人员，实体对应于在 Common Data Service 中处理数据时使用的类。

## <a name="entity-names"></a>实体名称
每个实体在创建时都有定义的唯一名称。 此名称以多种方式表示：

|名称属性 |说明|
|---------|---------|
|`SchemaName`|通常情况下，是逻辑名称的帕斯卡拼写版本。 例如，“Account”|
|`CollectionSchemaName`|架构名称的复数形式。 例如，“Accounts”|
|`LogicalName`|架构名称的全部小写版本。 例如，“account”|
|`LogicalCollectionName`|集合架构名称的全部小写版本。 例如，“accounts”|
|`EntitySetName`|用于通过 Web API 标识集合。 默认情况下，它与逻辑集合名称相同。<br />可通过以编程方式更新元数据来更改实体集名称。 但仅可在为实体编写任何 Web API 代码前完成。 详细信息：[Dynamics 365 客户参与开发人员指南：Web API 类型和操作 > 更改实体集的名称](/dynamics365/customer-engagement/developer/webapi/web-api-types-operations#change-the-name-of-an-entity-set)|

> [!NOTE]
> 创建自定义实体时，所选名称前将添加与创建该实体的解决方案关联的解决方案发布者的自定义前缀值。 除了实体集名称外，无法在创建实体后更改其名称。 如果希望解决方案中的元数据项的名称一致，则应在创建的解决方案的上下文中创建它们，该解决方案与包含要使用的自定义前缀的解决方案发布商相关联。 详细信息：[创建解决方案发布商和解决方案](introduction-solutions.md#create-a-solution-publisher-and-solution)

每个实体还包含可以显示已本地化值的三个属性：


|名称  |说明  |
|---------|---------|
|`DisplayName`|通常与架构名称相同，但可以包含空格。 例如，“Account”|
|`DisplayCollectionName`|显示名称的复数形式。 例如，“Accounts”|
|`Description`|描述实体的短句，例如，代表客户或潜在客户的企业。也是在商业交易中向其收取费用的公司。|

这些是用于引用应用中实体的可本地化的值。 可随时更改这些值。 要添加或编辑本地化值，请参阅 [Dynamics 365 自定义指南：将自定义实体和字段文本翻译成其他语言](/dynamics365/customer-engagement/customize/export-customized-entity-field-text-translation)。


## <a name="primary-key"></a>主键

`PrimaryIdAttribute` 属性值是实体主键的属性的逻辑名称。

默认情况下，所有实体都有一个 GUID 唯一标识符属性。 通常命名为&lt;实体逻辑名称&gt;+ `Id`。

## <a name="primary-name"></a>主要名称

`PrimaryNameAttribute` 属性值是属性的逻辑名称，该属性用于存储标识实体记录的字符串值。 这是将在用于打开 UI 中的记录的链接中显示的值。

**示例**：联系人实体使用 `fullname` 属性作为主要名称属性。

> [!NOTE]
> 并非每个实体都有主要名称。 某些实体不应在 UI 中显示。

## <a name="entity-images"></a>实体图像

`PrimaryImageAttribute` 属性值是属性的逻辑名称，该属性用于存储实体记录的图像数据。 每个实体仅可有一个图像属性，并且该属性的逻辑名称始终为 `entityimage`。

**示例**：[联系人实体](reference/entities/contact.md) [EntityImage](reference/entities/contact.md#BKMK_EntityImage) 属性可存储联系人的照片。

出于性能原因，除非明确请求，否则实体图像不包括在检索操作中。

支持实体图像的每个实体都有三个支持的属性。

|SchemaName|类型|说明|
|--|--|--|
|`EntityImage_Timestamp` |`BigIntType`|该值表示上次更新图像的时间，用于帮助确保最新版本图像已下载并缓存在客户端上。|
|`EntityImage_URL`|`StringType`|用于在客户端显示实体图像的绝对 URL。|
|`EntityImageId`|`UniqueIdentifierType`|图像的唯一标识符|

详细信息： 
- [Dynamics 365 客户参与开发人员指南图像属性](/dynamics365/customer-engagement/developer/image-attributes)
- [Dynamics 365 客户参与开发人员指南示例：设置并检索实体图像](/dynamics365/customer-engagement/developer/sample-set-retrieve-entity-images)

> [!NOTE]
> 这与模型驱动应用中显示的实体图标不同。 `IconVectorName` 属性包含设置此属性的 SVG Web 资源的名称。

## <a name="types-of-entities"></a>实体类型

实体的功能和行为取决于多个实体属性。 大多数属性都相对简单且具有描述性名称。 需要某些附加说明的四个属性是：所有权、Activity 实体、Activityparty 实体和子实体。

### <a name="entity-ownership"></a>实体所有权

可按实体内部数据的拥有方式对实体进行分类。 这是与如何将安全性应用于实体相关的重要概念。 此信息位于 `OwnershipType` 属性中。 下表描述了不同的所有权类型：

|所有权类型  |说明  |
|---------|---------|
|业务|数据属于业务部门。 可在业务部门级别控制对数据的访问。|
|无|不属于其他实体的数据。|
|组织|数据属于组织。 在组织级别控制对数据的访问。|
|用户或团队|数据属于用户或团队。 可在用户级别控制对这些记录执行的操作。|

创建新实体时，唯一的所有权选项为：“组织”或“用户或团队”。 选择此选项后，无法更改。 选择“用户或团队”，可精确控制可查看或执行记录操作的人员。 如果不需要此级别的控制，请选择“组织”。 

### <a name="activity-entities"></a>Activity 实体

活动是由用户执行或将要执行的任务。 活动是可在日历上进行录入的任何操作。 

活动的建模方式不同于存储业务数据的其他类型的实体。 有关活动的数据经常一起显示在列表中，但每种活动都需要唯一属性。 与具有每个可能属性的单个活动实体不同，存在不同类型的活动实体，并且每个活动实体都从基础 [ActivityPointer 实体](reference/entities/activitypointer.md)继承属性。 这些实体将 `IsActivity` 属性设置为 true。


|实体 |说明  |
|---------|---------|
|[Appointment](reference/entities/appointment.md)|代表时间间隔的承诺，包括开始/结束时间和持续时间。|
|[Email](reference/entities/email.md)|使用电子邮件协议传送的活动。|
|[Fax](reference/entities/fax.md)|跟踪传真呼叫结果和页数并可选择存储文档电子副本的活动。|
|[Letter](reference/entities/letter.md)|跟踪信件发送的活动。 该活动可包含该信件的电子副本。|
|[PhoneCall](reference/entities/phonecall.md)|跟踪电话呼叫的活动。|
|[RecurringAppointmentMaster](reference/entities/recurringappointmentmaster.md)|定期约会系列的主约会。|
|[SocialActivity](reference/entities/socialactivity.md)|仅供内部使用。|
|[Task](reference/entities/task.md)|通用活动，代表必须完成的工作。|

每当有人创建其中一种活动实体记录时，将以相同的 `ActivityId` 唯一标识符属性值创建相应的 `ActivityPointer` 实体记录。 无法创建、更新或删除 `ActivityPointer` 实体的实例，但可以检索它们。 该操作允许所有类型的活动一起呈现在列表中。

可创建行为相同的自定义活动实体。
<!-- TODO: Add link to topic about creating an activity entity -->

### <a name="activityparty-entity"></a>ActivityParty 实体

该实体用于将结构添加到包含对其他实体的引用的活动实体 `PartyListType` 属性。 为活动实体属性（如 `Email.to` 或 `PhoneCall.from`）设置值时，将使用此实体。 在 [ActivityParty 实体](reference/entities/activityparty.md)中，可设置 [ParticipationTypeMask](reference/entities/activityparty.md#BKMK_ParticipationTypeMask) 属性来定义引用所扮演的角色。 角色包括`Sender``ToRecipient``Organizer`等等。

可查询 `ActivityParty` 实体，但不能在与其相关的活动外创建、检索、更新或删除活动方。
详细信息： 
- [Dynamics 365 客户参与开发人员：ActivityParty 实体](/dynamics365/customer-engagement/developer/activityparty-entity)。


### <a name="child-entities"></a>子实体

`IsChildEntity` 属性为 true 的实体永远不会定义任何特权，并且永远不会属于“用户或团队”。 将可在子实体上执行的操作通过多对一关系绑定到与其关联的实体。 在对相关实体执行相同操作的情况下，用户方可对子实体执行操作。 删除子实体所依赖的实体记录时，会自动删除子实体。

例如，`PostComment``PostLike` 和 `PostRole` 都是 `Post` 实体的子实体。

## <a name="entity-keys"></a>实体键

每个备用键定义描述一个或多个属性组合，这些属性将唯一识别实体实例。 备用键通常仅用于与外部系统集成。 可定义备用键来唯一识别记录。 如果要将数据与不支持 GUID 唯一标识符键的系统集成，这将意义非凡。 可定义单个字段值或字段值组合来唯一识别实体。 添加备用键将对这些属性强制执行唯一性约束。 无法创建或更新其他实体记录以获取相同值。

详细信息： 
 - [Dynamics 365 客户参与自定义指南：定义备用键，引用 Dynamics 365 记录](/dynamics365/customer-engagement/customize/define-alternate-keys-reference-records)
 - [Dynamics 365 客户参与开发人员指南：定义实体和开发人员的备用键指南：将 Dynamics 365 数据与外部系统同步](/dynamics365/customer-engagement/developer/synchronize-dynamics-365-data-with-external-systems)

## <a name="entity-states"></a>实体状态

大多数实体具有两个属性，用于跟踪记录的状态。 分别为 `StateCode` 和 `StatusCode`，前者在模型驱动应用中称为“状态”，后者在模型驱动应用中称为“状态描述”。 

这两个属性都包含一组显示有效值的选项。 `StateCode` 和 `StatusCode` 属性值已链接，因此只有某些 `StatusCode` 选项对给定的 `StateCode` 有效。

这可能因实体而有所不同，但与许多实体的常见模式无关，自定义实体的默认值如下：

|StateCode 选项  |StatusCode 选项  |
|---------|---------|
|0 : Active|1 : Active|
|1: Inactive|2: Inactive|

某些实体将含有不同选项集。 

**示例**：`PhoneCall` 实体的 `StateCode` 和 `StatusCode` 选项


|Column1  |Column2  |
|---------|---------|
|0 : Open|1: Open|
|1 : Completed|2: Made <br />4: Received|
|2: Cancelled|3: Cancelled|

不可自定义实体的有效状态代码集，但可自定义状态代码。 可为相应的 `StateCode` 添加其他 `StatusCode` 选项。

对于自定义实体，可为状态间的有效转换定义其他条件。 详细信息： 
- [Dynamics 365 客户参与开发人员指南：自定义实体属性元数据](/dynamics365/customer-engagement/developer/customize-entity-attribute-metadata)
- [Dynamics 365 客户参与开发人员指南：定义自定义状态模型转换](/dynamics365/customer-engagement/developer/define-custom-state-model-transitions)。

### <a name="see-also"></a>另请参阅

[Common Data Service for Apps 实体](entities.md)