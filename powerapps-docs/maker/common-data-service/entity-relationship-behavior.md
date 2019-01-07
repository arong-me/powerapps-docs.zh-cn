---
title: 实体关系行为（面向应用程序的 Common Data Service）| Microsoft Docs
description: <Description>
ms.custom: ''
ms.date: 08/01/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: Mattp123
ms.author: matp
manager: kvivek
---
# <a name="entity-relationship-behavior"></a>实体关系行为

相关实体的行为非常重要，因为它有助于确保数据完整性，并可以让您公司的业务流程实现自动化。

## <a name="preserve-data-integrity"></a>保持数据完整性

某些实体的用途是为其他实体提供支持。 这些实体对自身无用。 它们通常有一个链接到所支持主实体的必需的查找字段。 当删除主记录时，会发生什么情况？

可使用关系行为根据业务的规则对此进行定义。 两个选项如下：

- 阻止删除主实体，以便可以协调相关实体记录，方法可以是将其与其他主实体关联。
- 允许在删除主实体记录时自动删除相关实体。

如果相关实体不支持主实体，可允许删除主实体，这样将清除查找值。

## <a name="automate-business-processes"></a>自动化业务流程
  
假定您有一位新销售员，您希望向其分派一些当前分派给另一位销售员的现有客户。 每个客户记录可能有一些与其关联的任务活动。 您可以轻松地找到要重新分派的可用客户，并将其分派给新销售员。 但是，对于与这些客户关联的任何任务活动，会发生什么情况？ 您是否打开每项任务，并决定是否也应将其分派给新销售员？ 可能不需要。 您可以让关系自动应用一些标准规则。 这些规则只适用于与您要重新分派的客户关联的任务记录。 您的选择是：  
  
- 重新分派所有可用任务。  
- 重新分派所有任务。 
- 不重新分派任务。  
- 重新分派当前分派给前一个客户负责人的所有任务。  
  
关系可以控制对主要实体记录的记录执行的操作如何向下级联到所有相关实体记录。  

## <a name="behaviors"></a>行为

在进行某些操作时，有多个行为类型可以应用。

|行为|说明|
|--|--|
|**可用项的级联**|对所有可用的相关实体记录执行操作。|
|**全部级联**|对所有相关实体记录执行操作。|
|**无级联**|不执行任何操作。|
|**移除链接**|删除所有相关记录的查找值。|
|**限制**|当存在相关实体记录时，阻止删除主要实体记录。|
|**用户负责项的级联**|对被主要实体记录的用户所负责的所有相关实体记录执行操作。|

## <a name="actions"></a>操作

下面是可以触发特定行为的操作：

|字段|说明|Options|
|--|--|--|
|**分派**|当主要实体记录分配给其他人时，会发生什么情况？|全部级联<br />可用项的级联<br />用户负责项的级联<br />无级联|
|**重定父级**|在父关系中的相关实体的查找值发生更改时，会发生什么情况？<br />详细信息：[父实体关系](#parental-entity-relationships)|全部级联<br />可用项的级联<br />用户负责项的级联<br />无级联|
|**共享**|当主要实体记录共享时，会发生什么情况？|全部级联<br />可用项的级联<br />用户负责项的级联<br />无级联|
|**删除**|当删除主要实体记录时，会发生什么情况？|全部级联<br />移除链接<br />限制|
|**取消共享**|当主要实体记录不共享时，会发生什么情况？|全部级联<br />可用项的级联<br />用户负责项的级联<br />无级联|
|**合并**|当主要实体记录合并时，会发生什么情况？|全部级联<br />无级联|
|**汇总视图**|与此关系关联的汇总视图的预期行为是什么？ |全部级联<br />可用项的级联<br />用户负责项的级联<br />无级联|


## <a name="parental-entity-relationships"></a>父级实体关系

可以具有 1:N 关系的每对实体之间可以具有多个 1:N 关系。 但通常只能将其中一个关系视为父实体关系。

父实体关系是下表的**父**列中的级联选项之一为 true 的任何 1:N 实体关系。

|目的|父|非父|  
|------------|--------------|------------------|  
|**分派**|全部级联<br />用户负责项的级联<br />可用项的级联|无级联|  
|**删除**|全部级联|移除链接<br />限制|  
|**重定父级**|全部级联<br />用户负责项的级联<br />可用项的级联|无级联|  
|**共享**|全部级联<br />用户负责项的级联<br />可用项的级联|无级联|  
|**取消共享**|全部级联<br />用户负责项的级联<br />可用项的级联|无级联|  

例如，如果您新建一个自定义实体并添加与客户实体的 1:N 实体关系（其中自定义实体是相关实体），则可以将该实体关系的操作配置为使用**父**列中的选项。 如果您后来添加了自定义实体作为引用实体的另一个 1:N 实体关系，则只能将操作配置为使用**非父**列中的选项。

通常这意味着，对于每个实体对，只有一个父关系。 有些情况下，相关实体上的查找可能允许与多种类型的实体之间的关系。

例如，如果实体具有可以引用联系人或客户实体的“客户”查找。 有两个单独的父 1:N 实体关系。

对于可使用相关项查找字段进行关联的实体，任何活动实体都具有一组类似的父实体关系。

<a name="BKMK_RelationshipBehaviorLimitations"></a>   

## <a name="limitations-on-behaviors-you-can-set"></a>对可以设置的行为的限制
  
由于存在父关系，在定义实体关系时，应当记住一些限制。  
  
- 在有级联的相关系统实体的关系中，自定义实体不能为主要实体。 这表示在主要自定义实体和相关系统实体间不能与设置为**全部级联**、**可用项的级联**或**用户负责项的级联**的任何操作具有关系。  
- 如果新关系中的相关实体已作为其他关系（该其他关系具有设置为**全部级联**、**可用项的级联**或**用户负责项的级联**的任意操作）中的相关实体而存在，则任何新关系都不能具有设置为**全部级联**、**可用项的级联**或**用户负责项的级联**的任意操作。 这将防止创建具有多个父级的关系。  