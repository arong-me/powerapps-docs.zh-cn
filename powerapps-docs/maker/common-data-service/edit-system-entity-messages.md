---
title: 使用 PowerApps 编辑系统实体消息 | MicrosoftDocs
description: 了解如何编辑系统实体消息
ms.custom: ''
ms.date: 05/15/2018
ms.reviewer: ''
ms.service: crm-online
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
ms.openlocfilehash: 797d6855bea421abd90752dd9ae0ad73a9d92f38
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39668809"
---
# <a name="edit-system-entity-messages"></a>编辑系统实体消息

某些系统实体的默认显示名称用于 Common Data Service for Apps 中的界面文本和错误消息。 如果更改显示名称，也应该更新使用默认显示名称的所有消息。 例如，如果将显示名称从“帐户”更改为“公司”，仍然可能会看到使用旧名称的错误消息。  

不能使用 PowerApps 门户编辑系统消息，必须使用解决方案资源管理器。

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

在解决方案资源管理器中的实体下方，如果看到“消息”节点，则可以编辑包含引用原始实体显示名称的某些文本。 

![实体消息](../model-driven-apps/media/entity-messages.png)

编辑此文本非常简单。 双击消息以查看包含三个字段的窗体：  
  
|字段|描述|  
|-----------|-----------------|  
|**默认显示字符串**|显示原始文本。|  
|**自定义显示字符串**|编辑此文本以更改显示字符串。|  
|**注释**|可选。 包括有关更改内容和原因的注释。|  
  
某些消息文本中可能包含占位符。 这些占位符是两侧带括号的数字。 例如：`{0}`。 这些占位符允许在消息中插入文本。 如果要编辑消息，请确保保留这些占位符。 

选择![保存](media/save-entity-icon-solution-explorer.png)以保存更改。 保存时，请选择“保存并关闭”以关闭窗体。

> [!NOTE]
> 虽然为编辑系统实体消息而公开的 UI 包括许多对实体名称的引用，但是它并不包括所有内容。 有关更全面的方法，请参阅[更新采用基本语言的可本地化文本](../model-driven-apps/translate-localizable-text.md#updating-localizable-text-in-the-base-language)

## <a name="programmatically-update-entity-display-strings"></a>以编程方式更新实体显示字符串

对于寻求在代码中使用这些字符串的方法的开发人员，显示字符串存储在 [DisplayString](../../developer/common-data-service/reference/entities/displaystring.md) 实体中。 

`DisplayString` 实体不包含默认显示字符串。 此包含文本的实体的两个属性是 [CustomDisplayString](../../developer/common-data-service/reference/entities/displaystring.md#BKMK_CustomDisplayString) 和 [PublishedDisplayString](../../developer/common-data-service/reference/entities/displaystring.md#BKMK_PublishedDisplayString)。 默认情况下，除非已自定义和发布了显示字符串，否则这些属性值为 Null。 `PublishedDisplayString` 值为只读，反映出当前发布的 `CustomDisplayString`。
 
## <a name="see-also"></a>另请参阅
[编辑实体](edit-entities.md)<br />
[为模型驱动应用翻译可本地化文本](../model-driven-apps/translate-localizable-text.md)
