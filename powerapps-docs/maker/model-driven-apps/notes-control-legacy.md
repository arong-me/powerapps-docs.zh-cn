---
title: 在 PowerApps 中设置模型驱动应用注释控件以访问公告信息 | Microsoft Docs
ms.custom: ''
ms.date: 05/06/2018
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
ms.assetid: f10cdf1c-3540-439c-a171-27a10e72da45
caps.latest.revision: 63
ms.author: matp
manager: kvivek
ms.openlocfilehash: 014f0c2516813b7cbcaa8e44a188455b07056c71
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39669470"
---
# <a name="set-up-the-model-driven-app-notes-control-to-access-information-about-posts"></a>设置模型驱动应用注释控件以访问公告信息

 在使用[更新后的表单](main-form-presentations.md#updated-forms)的某些系统实体的 PowerApps 表单中，可使用“注释”控件访问公告、活动和注释的相关信息。 对于已启用注释和活动的自定义实体，只会看到“注释”和“活动”。 要将“公告”包含在内，必须为自定义实体启用它们。  
  
## <a name="enable-posts-for-a-custom-entity"></a>为自定义实体启用“公告”  
  
1.  转到[设置](advanced-navigation.md#settings) > “活动源配置”。 
  
2.  打开自定义实体的记录。  
  
3.  确保选中“为此类记录表单启用留言板”并保存记录。  
  
4.  选择命令栏中的“激活”。  
  
5.  如需启用留言板，需要发布该实体。  
  
 对系统实体而言，“注释”控件默认位于表单顶部的三栏选项卡中心的“社交”窗格分区中。 它只能在表单中出现一次。 可移动或删除“注释”控件。 要重新添加该控件，可使用“插入”选项卡的“控件”组中的“注释”按钮。  
  
 下表介绍了“注释”控件的属性。  
  
|选项卡|属性|说明|  
|---------|--------------|-----------------|  
|**显示**|**标签**|**必需**：默认不显示标签，但必须具有它。|  
||**在窗体上显示标签**|可选择显示标签。|  
||**在表单上锁定字段**|这将防止从表单中意外删除注释。|  
||**默认选项卡**|选择应默认显示的选项卡。 选项包括：<br /><br /> - 活动<br />- 公告<br />- 注释|  
|**格式设置**|**选择控件占用的列数**|如果包含“注释”控件的分区具有多个列，可将该字段的占用列数上限设置为该分区的列数。|  
||**行数**|通过选择控件占用的行数，控制“注释”控件的高度。|  
||**自动扩展以利用可用空间**|除了按行数设置高度以外，还可允许“注释”控件上下扩展，填充可用空间。|  
  
## <a name="next-steps"></a>后续步骤
[打开表单编辑器](open-form-editor.md)
