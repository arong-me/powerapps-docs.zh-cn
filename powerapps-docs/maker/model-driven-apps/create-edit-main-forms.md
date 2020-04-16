---
title: 在 Power Apps 中创建或编辑模型驱动应用主窗体 | MicrosoftDocs
description: 了解如何创建或编辑主窗体
ms.custom: ''
ms.date: 05/23/2018
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
ms.assetid: <needs new guid>
caps.latest.revision: 18
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 1f2faa63b75a6842ee73f74ac1ebabd36b24d383
ms.sourcegitcommit: 551af7e0273862b28d9b2387671a4eeaf719eb37
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/11/2020
ms.locfileid: "3116666"
---
# <a name="create-or-edit-a-model-driven-app-main-form-for-an-entity"></a>创建或编辑实体的模型驱动应用程序主窗体 

在本主题中，您可以了解如何创建或编辑实体的主窗体。

为实体创建新窗体时，其窗体类型为主要。 打开新窗体时，它等同于名为“信息”的窗体。 可以添加或编辑字段、节、选项卡、导航，以及与窗体关联的属性，然后保存该窗体。

每个主窗体由一个或多个选项卡组成。 每个选项卡可包含一个或多个节。 每个节可包含一个或多个字段。 如果要基于现有窗体创建新窗体，则可以克隆一个窗体。 

请确保您具有系统管理员或系统定制员安全角色或等效权限以执行此任务。

## <a name="how-to-create-or-edit-a-main-form"></a>如何创建或编辑主窗体
  
1.   登录到 [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。

2.  展开**数据**，选择**实体**，选择所需实体，然后选择**窗体**选项卡。 

3. 若要创建新的主窗体，在工具栏上选择**添加窗体** > **主窗体**。  
    \-或者- 若要编辑现有的主窗体，请选择**类型**为**主**的任何窗体。
  
3.  根据需要按照以下方式更改窗体设计：
    - 向窗体中添加选项卡
    - 向窗体中添加节
    - 向窗体中添加字段
    - 在窗体上添加或编辑子网格
    - 编辑表单页眉和页脚
    - 删除选项卡部分字段
    
4.  根据需要编辑窗体某些部分的属性：
    - 编辑窗体属性
    - 编辑窗体字段属性
    - 编辑选项卡属性
    - 编辑节属性

5.    编辑完窗体后，选择**保存** > **另存为**，输入窗体名称，然后选择**确定**。

6.    完成自定义后，您可以发布它们：选择**发布**。
 
### <a name="next-steps"></a>后续步骤  
[模型驱动的窗体设计器概述](form-designer-overview.md)

[窗体编辑器用户界面概述](form-editor-user-interface-legacy.md)
 
