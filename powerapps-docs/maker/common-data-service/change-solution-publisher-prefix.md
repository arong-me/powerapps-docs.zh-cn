---
title: 更改解决方案发布者前缀 | MicrosoftDocs
ms.custom: ''
ms.date: 05/11/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
author: Mattp123
ms.assetid: ece684h8-ad40-4bfa-975a-3e5bafb854aa
caps.latest.revision: 55
ms.author: matp
manager: kvivek
ms.openlocfilehash: 5881dd6742dd441d135768d3a96fd36dbef9e700
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39668570"
---
# <a name="change-the-solution-publisher-prefix"></a>更改解决方案发布者前缀

每个自定义项均是解决方案的一部分。 每个解决方案都具有发布者。 默认情况下，要在 PowerApps 中使用的解决方案是“Common Data Services 默认解决方案”，该解决方案与 CDS 默认发布者相关联。

将为该发布者随机分配默认自定义前缀，例如这可以是 `cr8a3`。 这意味着，为组织创建的每个新元数据的名称都会以此为前缀，置于用于唯一标识项目的名称前。 如果创建名为“Animal”的新实体，则适用于应用的 CDS 使用的唯一名称为 `cr8a3_animal`。 这同样适用于任何新字段（属性）、关系或选项集选项。

除非要分发解决方案，以便将其与为其他解决方案发布者创建的元数据项一起安装，否则自定义前缀内容并不重要。 这对大多数使用应用的用户并不可见。 但会向负责生成报告等事项的开发人员和其他技术人员公开。 这提供了一种了解哪种解决方案添加了项目的快速方法。

出于这一原因，许多人希望更改解决方案发布者前缀，使其更有意义，尤其是在查看包含从其他解决方案导入的各项的元数据项时。 

> [!NOTE]
> 如果更改解决方案发布者前缀，应在创建新元数据项前完成。 无法更改元数据项名称。
> 更改自定义前缀值时，请务必点击到下一个字段。 “选项值前缀”将基于自定义前缀自动生成数字。 此数字在向选项集添加选项时会用到，并提供用于添加选项的解决方案的指示符。 

## <a name="change-the-solution-publisher-prefix-for-the-cds-default-publisher"></a>更改 CDS 默认发布者的解决方案发布者前缀  

 1. 在 PowerApps 门户中，选择左下角的“模型驱动”。
 2. 在左侧导航栏中单击“高级”，打开“Common Data Services 默认解决方案”
 3. 在解决方案资源管理器，选择左侧导航中的“信息”区域。
 4. 单击“发布者”链接，打开“CDS 默认发布者”窗体。
 5. 将“前缀”字段值编辑为所需的自定义前缀。
 6. 单击“保存并关闭”。
  
## <a name="change-the-solution-publisher-prefix-for-any-publisher"></a>更改任何发布者的解决方案发布者前缀

分发其解决方案的人员通常在自己创建的解决方案中工作，而不是在“Common Data Services 默认解决方案”中工作。 他们在创建解决方案时，通常已设置自定义前缀。 可以按照以下步骤操作，更改所使用的其他非托管解决方案的自定义前缀： 

 1. 在 PowerApps 门户中，选择左下角的“模型驱动”。
 2. 在左侧导航栏中单击“高级”，打开“Common Data Services 默认解决方案”
 3. 编辑页面的 URL，删除 `dynamics.com` 之后的所有内容并重新加载页面。
 4. 导航到“设置” > “自定义” > “自定义项”。 
 5. 单击“发布者”。 现在，可以看到可用发布者列表。
 6. 单击想要编辑的发布者，打开发布者窗体。
 7. 将“前缀”字段值编辑为所需的自定义前缀。
 6. 单击“保存并关闭”。
  