---
title: 通过 PowerApps 设计模型驱动应用主窗体时的注意事项 | MicrosoftDocs
description: 了解如何设计主窗体
ms.custom: ''
ms.date: 06/27/2018
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
ms.assetid: a83872f4-9e36-413b-8561-41a1e5ffe5dd
caps.latest.revision: 17
ms.author: matp
manager: kvivek
ms.openlocfilehash: 68915af214b86511f7fba4bbb05ee59f598340b0
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39669616"
---
# <a name="design-considerations-for-model-driven-app-main-forms"></a>模型驱动应用主窗体的设计注意事项

主窗体是人员查看数据并与其交互的主要用户界面。 主窗体提供最广泛的选项，可用于模型驱动应用，适用于手机的 Dynamics 365 除外。  
  
 主窗体的主要设计目标之一是只需设计一次就可在任何位置进行部署。 为模型驱动应用或 Dynamics 365 Customer Engagement Web 应用程序设计的同一主窗体也可用于 Dynamics 365 for Outlook 和适用于平板电脑的 Dynamics 365。 这种方法的优点是不必将更改集成到多个窗体中。 但是，在设计这些窗体时需要考虑几个重要因素。  
  
<a name="BKMK_CustomFormsForGroups"></a>   

## <a name="custom-forms-for-different-groups"></a>不同组的自定义窗体  
 因为可以创建多个主窗体并为每个窗体分配不同的安全角色，所以可在组织中显示不同的组，并使用针对它们使用应用程序的方式进行优化的窗体。 甚至可以为每个组提供不同的选项，以便选择不同的窗体。 详细信息：[控制对窗体的访问](control-access-forms.md)  
  
 可以预料到的是，管理人员和决策者想使用经过优化的窗体，以便快速引用关键数据点。 他们希望看到图表而不是列表，并且可能不想执行大量数据输入。  
  
 与客户直接互动的人员可能需要根据他们最常执行的任务定制的窗体。 他们可能想使用能够高效输入数据的窗体。  
  
 因此需要了解组织中的人员想要和需要的内容。 这通常是一个迭代过程，在这个过程中需要收集输入，尝试不同的事物并构建人员可使用的窗体。 请记住，可使用各种工具，而且并非所有内容都必须在窗体中完成。 将业务规则、工作流程、对话框和业务流程与窗体结合使用，以提供适用于组织的解决方案。  
  
 必须将此与希望用于管理窗体的时间进行平衡。 创建和编辑窗体相对容易，但是创建更多窗体的同时，必须管理更多窗体。  
  
<a name="BKMK_PresentationDifferences"></a>   
## <a name="presentation-differences"></a>演示的差异  
 虽然不必为每个演示管理多个窗体，但必须考虑如何在主窗体中展现演示中的差异。 [主窗体演示](main-form-presentations.md)描述了可以呈现主窗体的不同方式。 要考虑的主要事项是：  
  
- 适用于平板电脑的 Dynamics 365 不支持将图像、HTML 或 Silverlight Web 资源添加到窗体中。  
  
-   适用于平板电脑的 Dynamics 365 窗体的布局是基于主窗体自动生成的。 适用于平板电脑的 Dynamics 365 窗体没有特殊的窗体编辑器。 需要验证窗体演示是否适用于两个客户端。  
  
-   如果在 Web 应用中发现与 DOM 元素交互的不受支持的脚本，则这些脚本将无法在适用于平板电脑的 Dynamics 365 窗体中使用，因为相同的 DOM 元素不可用。  
  
- Dynamics 365 for Outlook 阅读窗格窗体不允许编写脚本。 窗体元素的可见性取决于默认设置，并且无法在运行时使用脚本进行更改。  
  
<a name="BKMK_FormPerformance"></a>   
## <a name="form-performance"></a>窗体性能  
 加载缓慢或未快速响应的窗体肯定会影响应用的工作效率和用户采用率。 [优化窗体性能](optimize-form-performance.md)提供了在设计窗体时应考虑的一些建议，以便自定义项不会对窗体性能产生负面影响。  
  
### <a name="next-steps"></a>后续步骤 
 [创建并设计窗体](create-design-forms.md)    
 [创建和编辑快速创建窗体](create-edit-quick-create-forms.md)   

 
