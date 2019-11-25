---
title: 在 PowerApps 中分配模型驱动应用窗体顺序 | MicrosoftDocs
description: 了解如何在应用中分派默认表单
ms.custom: ''
ms.date: 03/07/2019
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
ms.assetid: 914c5694-9c80-4424-be89-9f63256b4811
caps.latest.revision: 33
ms.author: matp
manager: kvivek
tags: ''
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 90190dc9021d3852d123dd63e678c7924e164838
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "2700859"
---
# <a name="assign-model-driven-app-form-order"></a>分配模型驱动的应用程序窗体顺序

 当某个实体有多个主窗体、快速创建窗体、快速视图窗体或卡窗体时，您可以指定窗体顺序。 窗体顺序确定默认情况下将显示哪个可用窗体。 可以通过向窗体分配安全角色来进一步控制可用的主窗体。 有关详细信息，请参阅[控制对窗体的访问](control-access-forms.md)。  
  
 不能将安全角色分派给快速创建窗体、快速视图窗体或卡窗体，每个人都将使用的唯一窗体是窗体顺序最上面的那个窗体。  
  
## <a name="to-assign-a-form-order"></a>指定窗体顺序  
  
1.  打开[解决方案资源管理器](advanced-navigation.md#solution-explorer)，展开您需要的实体，然后选择**窗体**。  
  
2.  在窗体列表工作栏上，选择**窗体顺序**。  

     > [!div class="mx-imgBorder"] 
     > ![窗体顺序工具栏命令](media/form-order.png)
  
3.  根据您要使用的窗体类型，选择**主窗体集**、**快速创建窗体集**、**快速视图窗体**或**卡窗体集**。 详细信息：[窗体类型](types-forms.md)。 
  
4.  **窗体顺序**对话框是一个简单的列表，可在其中上下移动窗体顺序。  
  
5.  在设置了所需的顺序之后，单击**确定**关闭对话框。  

## <a name="next-steps"></a>后续步骤

[更改窗体内的导航](use-the-form-editor-legacy.md)
