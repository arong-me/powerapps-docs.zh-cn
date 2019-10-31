---
title: 使用 PowerApps 的模型驱动应用主窗体的设计注意事项 | MicrosoftDocs
description: 了解如何设计主窗体
ms.custom: ''
ms.date: 06/27/2018
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
ms.assetid: a83872f4-9e36-413b-8561-41a1e5ffe5dd
caps.latest.revision: 17
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="design-considerations-for-model-driven-app-main-forms"></a>模型驱动应用程序主窗体的设计注意事项

主窗体是用户查看及与其数据交互的主要用户界面。 主窗体提供了广泛的选项，可用于模型驱动应用（Dynamics 365 for phones 除外）。  
  
 主窗体的主要设计目标之一是一次设计，到处部署。 您为模型驱动应用设计的相同主窗体也用于 Dynamics 365 for Outlook 和适用于平板电脑的 Dynamics 365。 此方法的优势在于您无需将更改集成到多个窗体中。 但是，在设计这些窗体时，需要考虑几个具有要的因素。  
  
<a name="BKMK_CustomFormsForGroups"></a>   

## <a name="custom-forms-for-different-groups"></a>不同组的自定义窗体  
 由于可以创建多个主窗体并为每个窗体分派不同的安全角色，因此可以使用针对用户使用应用程序的方式优化的窗体来呈现组织中的不同组。 您甚至可以为每个组提供不同的选项，使其有不同的窗体可供选择。 详细信息：[控制对窗体的访问](control-access-forms.md)  
  
 您可能会期望经理和决策者需要优化的窗体来提供对关键数据点的快速引用。 他们将乐于看到图表而不是列表，他们可能不会执行许多数据录入操作。  
  
 直接与客户的交互的用户可能需要针对其最常执行的任务定制的窗体。 他们可能希望窗体能实现最高效的数据录入。  
  
 您将需要发现组织中的人希望和需要的东西。 这通常是一个迭代过程，可在其中收集输入信息，尝试不同的事情，以及构建用户可以使用的窗体。 请记住，您有各种工具可用，并非什么事情都要在窗体中完成。 业务规则、工作流、对话和业务流程和窗体配合使用，可以提供适合您的组织的解决方案。  
  
 您必须将此与您希望用于管理窗体的时间进行平衡。 创建和编辑窗体相对容易一些，但在创建更多窗体时，就必须管理更多窗体。  
  
<a name="BKMK_PresentationDifferences"></a>   
## <a name="presentation-differences"></a>表示形式差异  
 虽然不必为每种表示形式管理多个窗体，但必须考虑表示形式的差异对主窗体的影响。 [主窗体表示形式](main-form-presentations.md)介绍了可用于呈现主窗体的不同方式。 要考虑的主要事项包括：  
  
- Dynamics 365 for tablets 不支持将图像、HTML 或 Silverlight Web 资源添加到窗体中。  
  
-   Dynamics 365 for tablets 窗体的布局是根据主窗体自动生成的。 没有用于 Dynamics 365 for tablets 窗体的特殊窗体编辑器。 您需要验证窗体的表示形式对两种客户端都有效。  
  
-   如果您有与 Web 应用程序中的 DOM 元素交互的不支持的脚本，这些脚本在 Dynamics 365 for tablets 窗体中将无效，因为相同的 DOM 元素不可用。  
  
- Dynamics 365 for Outlook 阅读窗格窗体不允许脚本。 窗体元素的可见性取决于默认设置，不能在使用脚本运行时更改。  
  
<a name="BKMK_FormPerformance"></a>   
## <a name="form-performance"></a>窗体性能  
 加载速度慢或不能迅速响应的窗体必定影响生产力和用户对应用程序的采用。 [优化窗体性能](optimize-form-performance.md)提供了您在设计窗体时为了使自定义不影响窗体性能而应当考虑的大量建议。  
  
### <a name="next-steps"></a>后续步骤 
 [创建和设计窗体](create-design-forms.md)    
 [创建和编辑快速创建窗体](create-edit-quick-create-forms.md)   

 
