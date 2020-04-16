---
title: 在 Power Apps 中将字段添加到模型驱动应用窗体 | MicrosoftDocs
ms.custom: ''
ms.date: 03/18/2020
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- PowerApps
author: Mattp123
ms.assetid: 29499887-6e7b-44a1-86a7-eaad33f3075d
caps.latest.revision: 30
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: f3b24d42fa8a9c800bf16eab51f39bb741c3d3bc
ms.sourcegitcommit: 9f2694bd14d70798310b89a4673672c1bfad989d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/26/2020
ms.locfileid: "3166870"
---
# <a name="add-a-field-to-a-model-driven-app-form"></a>将字段添加到模型驱动的应用程序窗体 

如果标准实体的 Power Apps 窗体不能满足贵组织业务需求，您可以通过更改现有字段或将添加新字段自定义窗体。 虽然编辑窗体中的现有字段可能更简单，但有时最好添加字段以处理特定业务情况。

在本主题中，您将字段添加到窗体。   
  
1.  登录到 [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。  

2.  展开**数据**，选择**实体**，选择所需实体，然后选择**窗体**选项卡。  

3.  在列表中，打开**主**类型的窗体进行编辑。  
  
4.  在窗体中，单击要向其中添加字段的部分，然后在**字段**窗格中，单击要添加到窗体的字段。  
  
    > [!TIP]
    >  在窗体上添加选项集字段时，包含选项集值的下拉列表只能显示两个值。 用户必须滚动查看详细列表中的值。 如果希望查看多个值，而用户无需滚动，单击窗体的选项集字段下方添加一个或多个**空格**控件。 每个**空格**控件为另外一个选项集值提供一个空格。 例如，如果您要在不滚动的情况下显示下拉列表中的四个值，单击窗体的选项集字段下方添加两个**空格**控件。  
  
5.  要为您编辑的窗体发布自定义项，在窗体打开状态下，单击**发布**。 
  
6.  编辑完窗体后，单击**保存并关闭**。  
  
> [!NOTE]
>  发布自定义项会干扰常规系统运行。 我们建议您以对用户造成的干扰最少为宗旨，合理安排发布。  
  
## <a name="next-steps"></a>后续步骤  
 
 [创建和设计窗体](create-design-forms.md)
