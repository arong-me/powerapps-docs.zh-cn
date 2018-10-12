---
title: 在 PowerApps 中分配模型驱动应用窗体顺序 | MicrosoftDocs
description: 了解如何分配应用中的默认窗体
ms.custom: ''
ms.date: 06/22/2018
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
ms.assetid: 914c5694-9c80-4424-be89-9f63256b4811
caps.latest.revision: 33
ms.author: matp
manager: kvivek
tags: ''
ms.openlocfilehash: 22ed9c144c90c5393b6d9e76692172f0dd067225
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39668429"
---
# <a name="assign-model-driven-app-form-order"></a>分配模型驱动应用窗体顺序

 如果一个实体有多个主窗体、快速创建窗体或移动窗体，则可以分配窗体顺序。 窗体顺序决定了默认显示哪些可用窗体。 通过向窗体分配安全角色，可进一步控制可用的主窗体或移动窗体。 请参阅[控制对窗体的访问](control-access-forms.md)，获取详细信息。  
  
 不能将安全角色分派给快速创建窗体，每个人都将使用的唯一窗体是窗体顺序最上面的那个窗体。  
  
## <a name="to-assign-a-form-order"></a>如何分配窗体顺序  
  
1.  打开[解决方案资源管理器](advanced-navigation.md#solution-explorer)，展开所需实体，然后选择“窗体”。  
  
2.  在窗体列表工具栏中，选择“窗体顺序”。  

    ![窗体顺序工具栏命令](media/form-order.png)
  
3.  根据需要使用的窗体类型，选择“主窗体集”、“快速创建窗体集”、“快速视图窗体集”或“移动窗体集”。 详细信息：[窗体类型](types-forms.md)。 
  
4.  “窗体顺序”对话框是一个简单列表，从中可按窗体顺序将所选窗体向上或向下移动。  
  
5.  设置所需顺序后，单击“确定”，关闭对话框。  

## <a name="next-steps"></a>后续步骤

[更改窗体中的导航](use-the-form-editor-legacy.md)