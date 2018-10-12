---
title: PowerApps 中视图的模型驱动应用托管属性 | MicrosoftDocs
description: 了解如何设置视图的托管属性
ms.custom: ''
ms.date: 06/12/2018
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
ms.assetid: a9014576-8fb2-4f28-b8bb-5d2d49d76e12
caps.latest.revision: 25
ms.author: matp
manager: kvivek
ms.openlocfilehash: 9f33212ae81de0418dfc3695d5ae3c8e5acf36da
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39668454"
---
# <a name="model-driven-app-managed-properties-for-views"></a>视图的模型驱动应用托管属性

<a name="BKMK_ManagedProperties"></a>   
 
 如果在 PowerApps 中创建自定义公共视图，并希望将其包含在要分发的托管解决方案中，则可以选择限制安装解决方案的任何人对视图进行自定义。  
  
 默认情况下，大多数视图将其“可自定义”托管属性设置为“true”，以便用户可对其进行自定义。 除非有充分理由要更改此设置，否则建议允许用户自定义应用中的视图。  
  
## <a name="set-managed-properties-for-a-view"></a>设置视图的托管属性  
  
1.  打开[解决方案资源管理器](advanced-navigation.md#solution-explorer)，展开“实体”，选择所需实体，然后选择“视图”。  
  
2.  选择一个自定义公共视图。  
  
3.  在菜单栏上，选择“更多操作” > “托管属性”。  

    ![托管​​属性菜单](media/managed-properties.png)
  
4.  将“可自定义”或“可删除”选项设置为“True”或“False”。  

    ![设置托管​​属性](media/set-managed-properties.png)
  
> [!NOTE]
> 只有将包含视图的解决方案导出为托管解决方案并将其安装在其他环境中，该设置才会生效。  

## <a name="next-steps"></a>后续步骤
[了解视图](create-edit-views.md)
