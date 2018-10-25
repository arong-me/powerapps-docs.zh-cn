---
title: Common Data Service for Apps 应用构建做法 | MicrosoftDocs
ms.custom: ''
ms.date: 06/18/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.assetid: e9810433-224b-4bde-851a-e581cf5fb8a4
caps.latest.revision: 21
author: Mattp123
ms.author: matp
manager: kvivek
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 1eda4b591a3296001ffa62b16e185b421a197e75
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/24/2018
ms.locfileid: "42865032"
---
# <a name="common-data-service-for-apps-supported-and-unsupported-app-building-practices"></a>Common Data Service for Apps 支持和不支持的应用构建做法

<!--
The way your organization works is unique. Some organizations have well-defined business processes that they apply using PowerApps apps. Others aren’t happy with their current business processes and use PowerApps to apply new data and processes to their business. Whatever situation you find yourself in, you’ll find a lot of customization capabilities in PowerApps so that it can work for your organization.  
  
 Of course you’re eager to get started, but please take a few minutes to read the content in this section. This will introduce you to important terms, give you some background about why things are done a certain way, and help you avoid potential problems in the future.  

## What is metadata and why should you care?  
 In the past, you may have customized business applications by editing the source code. This created complications because each organization had unique changes and it was very difficult, or extremely expensive, to upgrade. Then application developers started exposing application programming interfaces (APIs) so that other developers could interact with the application and add their own logic without touching the source code. This was moderately better because it means developers can extend the application without changing it. But it still requires a developer to write code.  -->
  
 新式业务应用程序使用元数据驱动的体系结构，以便人们无需编写代码即可创建应用。 元数据是“描述数据的数据”，它定义了 Common Data Service for Apps 中存储的数据的结构。 通过此元数据，应用程序可了解对数据结构的任何更改，这使应用程序可随着数据结构的更改进行调整。 由于元数据是已知的，因此可以包含与元数据相关的其他功能。  

更改 Common Data Service for Apps 组件（如实体、视图、字段、图表和仪表板）以生成按所需方式工作的应用，这一过程称为“自定义”。  
 
使用 PowerApps 中的工具构建和自定义应用时，会添加或更新依赖于元数据的功能所使用的元数据或数据。 由于我们了解用于创建应用的数据类型，因此可将这些数据考虑在内，并在不中断应用的情况下为 Common Data Service for Apps 环境添加新功能。 <!-- This way you should always be able to apply an update rollup or upgrade to the latest version and enjoy the best new features.  -->

<!--  
> **Customize or Configure?**   
> Most people say they want to customize the application, so we use the word “customize” to describe changing the system to make it work the way you want. Some people prefer to use the word “configure” because it suggests that no code was required to make changes. Call it whatever you like, we just want to make it clear that you don’t need to be a developer to customize or create PowerApps apps.  -->
  
无需成为开发人员即可构建和自定义 PowerApps 应用。 但是，PowerApps 提供了一组 Web 服务和 API，可让开发人员编写代码。 使用支持的方法编写代码时，在 Common Data Service for Apps 环境更新后，代码会继续正常工作。  
  
<a name="BKMK_SupportedCust"></a>   
## <a name="what-kinds-of-customizations-are-supported"></a>支持哪些类型的自定义？  
 应可使用 PowerApps 工具完成大多数应用构建和自定义。 如果自定义工具无法满足需求，可以安装第三方提供的解决方案，或雇用开发人员编写应用代码。 如果需要投资一种需要代码的解决方案，请务必使用支持的 API 编写代码。 这有助于保护在应用和所获取的任何解决方案上的投资。  
  
 扩展 PowerApps 应用的开发人员有责任遵循规则和 SDK 中所述的最佳做法：[使用 Dynamics 365 客户参与进行开发的最佳做法](https://docs.microsoft.com/dynamics365/customer-engagement/developer/best-practices-sdk)。 SDK 记录了可供开发人员使用的 API，并提供了有关如何最佳利用这些 API 的指南。 Microsoft 仅支持 SDK 中记录的 API 和做法。 或许 Internet 上可找到介绍如何解决问题的内容，但如果未利用 SDK 中记录的 API，则 Microsoft 不支持该内容。 在让开发人员应用更改之前，应验证更改是否使用了支持的方法。  
  
 如果开发人员使用 SDK 中所述的 API 和最佳做法，我们便确定能够测试出对 Common Data Service for Apps 所做的任何更改是否可能中断现有自定义内容。 我们的目标是，在 Common Data Service for Apps 的新版本或更新发布时，使用受支持的方法所编写的代码自定义内容将继续有效。 你将因此受益：无需每次都让开发人员更改其代码，即可升级到改进了功能的新版本。  
  
 如果我们检测到新版本 Common Data Service for Apps 中的更改将导致支持的自定义内容中断，我们将记录受影响的内容以及人们可如何更改其代码来进行修复。  
  
<a name="BKMK_Unsupported"></a>   
## <a name="what-kinds-of-customizations-arent-supported"></a>不支持哪些类型的自定义？  
 虽然某些 API 和编程做法不受 Microsoft 支持，但并不意味着它们不起作用。 <!--  “Unsupported by Microsoft” means exactly what it says: you can’t get support about these APIs or programming practices from Microsoft. We don’t test them and we don’t know if something we change will break them. We can’t predict what will happen if someone changes code in our application.  --> 使用不受支持的 API 和编程做法的开发人员有义务为其代码提供相应支持。 他们需要测试自己的代码，以确保该代码可正常工作。  
  
 如果选择在 Common Data Service for Apps 环境中使用不受支持的自定义内容，则在联系 Microsoft 技术支持前，应确保已记录下完成的操作并具有删除这些自定义的策略。 如果需要有关不受支持的自定义的帮助，请联系准备自定义的开发人员或组织。  
  
<a name="BKMK_CommonUnsupportedCustomizations"></a>   
### <a name="common-unsupported-customization-practices"></a>常见的不受支持的自定义做法  
 下面是不受支持的常见自定义做法的列表。 这并非完整列表。 详细信息：[Dynamics 365 支持的扩展：不支持的自定义](https://docs.microsoft.com/dynamics365/customer-engagement/developer/supported-extensions#Unsupported)。 
 
**使用 JavaScript 与 Web 应用程序文档对象模型 (DOM) 元素进行交互**  
 应用程序中任何位置使用的任何 JavaScript 库必须仅与记录的 API 进行交互。 JavaScript 开发人员在使用应用程序时，经常使用特定名称访问 DOM 元素。 由于 PowerApps 应用是 Web 应用程序，因此能够使用这种技巧，但应用可能会在更新期间中断，因为它们所引用元素的名称随时都可能发生变化。 我们保留在应用程序中进行任何必要更改的权利，这通常指的是更改页面的构造方式。 添加依赖于页面当前结构的任何更改意味着，每次向应用程序应用更新时，都需要为测试投入费用或有可能为更改这些脚本中的自定义代码投入费用。  
  
 jQuery 是 JavaScript 开发人员常用的库。 使用 jQuery 的主要优势是，它简化了开发人员访问和创建 DOM 元素的过程，而这恰恰是 Common Data Service for Apps 应用程序页面中所不支持的。 如果开发人员使用 HTML Web 资源创建自定义用户界面，建议其使用 jQuery，但在 PowerApps 应用程序页面中，支持的 API 并不需要使用 jQuery。  
  
 **使用任何未记录的、运用 JavaScript 的内部对象或方法**  
Common Data Service for Apps 使用页面中的许多 JavaScript 对象。 JavaScript 开发人员可以通过调试页面来发现这些对象，然后访问并重复使用这些对象。 我们保留对这些对象进行必要更改的权利，包括删除对象或更改方法的名称。 如果脚本引用了这些对象，找不到对象时，脚本将会中断。  <a name="BKMK_Metadata"></a>   
 
<a name="BKMK_CombineCustomizations"></a>   
## <a name="combine-customization-capabilities"></a>组合自定义功能  
 这些部分中的主题相当深入地介绍了各种自定义功能。 但请务必记住，满足业务需求的解决方案通常会将其中一种功能与其他一种或多种功能结合使用。  
  
<a name="BKMK_ChooseTheRightCustomization"></a>   
### <a name="choose-the-right-customization-capability-for-the-job"></a>为作业选择合适的自定义功能  
 用户能够轻松掌握 PowerApps 中提供的各种不同自定义功能，并可尝试使用它们解决任何问题。 在评估想要解决的业务问题时，请考虑一下想要实现的最终结果，然后再考虑如何实现该目标。  
 
<a name="BKMK_changesinperformance"></a>   
## <a name="changes-that-affect-common-data-service-for-apps-environment-performance"></a>影响 Common Data Service for Apps 环境性能的更改  
 导入解决方案和应用可更改元数据的自定义项可能会影响 Common Data Service for Apps 环境性能。 可能会干扰正常系统操作的操作包括：  
  
-   添加、删除或更改实体、备用键、属性或关系。   
-   导入解决方案
  
-   发布自定义项 
  
如果要将这些更改应用到生产系统，建议计划这些操作时将对用户的不良影响降至最低。   
  
  
## <a name="next-steps"></a>后续步骤  
[PowerApps 中的模型驱动应用有哪些？](../../maker/model-driven-apps/model-driven-app-overview.md)

