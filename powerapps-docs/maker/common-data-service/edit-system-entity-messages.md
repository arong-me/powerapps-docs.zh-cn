---
title: 使用 PowerApps 编辑系统实体消息 | MicrosoftDocs
description: 了解如何编辑系统实体消息
ms.custom: ''
ms.date: 05/15/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
author: Mattp123
ms.assetid: 3ccbd8de-8d6f-4058-87f7-15463667cfc6
caps.latest.revision: 41
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="edit-system-entity-messages"></a>编辑系统实体消息

有些系统实体的默认显示名称会用在 Common Data Service 中的用户界面文本和错误消息中。 如果更改显示名称，则还应更新使用默认显示名称的所有消息。 例如，如果将显示名称从*客户*更改为*公司*，则仍可能看到使用旧名称的错误消息。  

无法使用 PowerApps 门户编辑系统消息，必须使用解决方案资源管理器。

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

在解决方案资源管理器中的实体下，如果看到**消息**节点，就可以编辑包含对原实体显示名称的引用的特定文本。 

![实体消息](../model-driven-apps/media/entity-messages.png)

编辑此文本很简单。 双击消息可看到一个包含三个字段的窗体：  
  
|字段|说明|  
|-----------|-----------------|  
|**默认的显示字符串**|显示原始文本。|  
|**自定义显示字符串**|编辑此文本以更改显示字符串。|  
|**注释**|可选。 包括有关更改内容及更改原因的注释。|  
  
有些消息文本中可以会有占位符。 这些占位符是在任何一侧有括号的数字。 例如：`{0}`。 这些占位符可用于在消息中插入文本。 如果编辑消息，请确保保留这些占位符。 

选择![保存](media/save-entity-icon-solution-explorer.png)以保存您所做的更改。 选择**保存并关闭**以在保存后关闭窗体。

> [!NOTE]
> 虽然显示的用于编辑系统实体消息的 UI 包括很多对实体名称的引用，但不包括所有引用。 有关更全面的方式，请参阅[使用基本语言更新可本地化文本](../model-driven-apps/translate-localizable-text.md#updating-localizable-text-in-the-base-language)

## <a name="programmatically-update-entity-display-strings"></a>以编程方式更新实体显示字符串

对于查找在代码中使用这些字符串的方法的开发人员，这些显示字符串存储在 [DisplayString](../../developer/common-data-service/reference/entities/displaystring.md) 实体中。 

`DisplayString` 实体不包含默认显示字符串。 对于这个包含文本的实体，它的两个属性是 [CustomDisplayString](../../developer/common-data-service/reference/entities/displaystring.md#BKMK_CustomDisplayString) 和 [PublishedDisplayString](../../developer/common-data-service/reference/entities/displaystring.md#BKMK_PublishedDisplayString)。 除非显示字符串是自定义的并且已经发布，否则这些属性值在默认情况下为空值。 `PublishedDisplayString` 值是只读的，反映当前发布的 `CustomDisplayString`。
 
## <a name="see-also"></a>另请参阅
[编辑实体](edit-entities.md)<br />
[翻译模型驱动应用程序的可本地化文本](../model-driven-apps/translate-localizable-text.md)
