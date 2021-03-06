---
title: 在 Power Apps 中使用解决方案 | MicrosoftDocs
description: 了解如何分发解决方案
ms.custom: ''
ms.date: 01/21/2020
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
ms.assetid: ece68f5f-ad40-4bfa-975a-3e5bafb854aa
caps.latest.revision: 55
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 309b6721d60d06e81926bfc0f97ff192f936686a
ms.sourcegitcommit: a1b54333338abbb0bc3ca0d7443a5a06b8945228
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/13/2020
ms.locfileid: "3125429"
---
# <a name="solutions-overview"></a>解决方案概述  

  在 Power Apps 中，解决方案被用来将应用和组件从一个环境传输到另一个环境，或将一组自定义项应用到现有应用。 一个解决方案中可以包含一个或多个应用程序，以及其他组件，如站点地图、实体、流程、Web 资源、选项集等。  可从 [AppSource](https://appsource.microsoft.com/) 或独立软件供应商 (ISV) 获取解决方案。
  
详细信息：[白皮书：解决方案生命周期管理](https://www.microsoft.com/download/details.aspx?id=57777)  
  
> [!NOTE]
>  如果您是创建要分发的应用的 ISV，则需要使用解决方案。 有关使用解决方案的详细信息，请参阅[开发人员指南：解决方案简介](/powerapps/developer/common-data-service/introduction-solutions)。  
  

<a name="BKMK_SolutionComponents"></a>   
## <a name="components"></a>组件  
 组件代表您有可能自定义的某些事项。 可以包括在解决方案中的任何项目是组件。 若要查看解决方案中包含的组件，请在解决方案资源管理器中转到**设置** > **解决方案**，然后打开所需解决方案。 这些组件包含在**组件**列表中。 请注意，不能编辑托管解决方案中包含的组件。 

> [!div class="mx-imgBorder"] 
> ![解决方案中的组件](media/components-in-solution.png "解决方案中的组件") 

若要查看可添加到解决方案的组件类型的列表，请参阅 [ComponentType 选项](../../developer/common-data-service/reference/entities/solutioncomponent.md#componenttype-options)。

<!-- The following is a list of components that you can view in a solution:  
  
-   AI Model

-   Application Ribbon  
  
-   Article Template  
  
-   Business Rule  

-   Canvas App 
  
-   Chart  
  
-   Connection Role  
  
-   Contract Template  

-   Custom Connector
 
-   Custom Control
  
-   Dashboard  
  
-   Email Template  
  
-   Entity  
  
-   Entity Relationship  

-   Environment variable
  
-   Field  
  
-   Field Security Profile  

-   Flow
  
-   Form  
  
-   Mail Merge Template  
  
-   Message  

-   Model-driven app
  
-   Option Set  
  
-   Plug-in Assembly  
  
-   Process  

-   Report  

-   Sdk Message Processing Step  
  
-   Security Role  
  
-   Service Endpoint  
  
-   Site Map  

-   Virtual Entity Data Provider

-   Virtual Entity Data Source
  
-   Web Resource  -->
  
 某些组件嵌套在其他组件内。 例如，实体包含窗体、视图、图表、字段、实体关系、消息和业务规则。 其中的每个组件都需要存在一个实体。 字段不能存在于实体之外。 我们称之为字段依赖于实体。 实际的组件类型的数量是之前列表中所示的两倍，但其中大多数不嵌套在其他组件内且不在应用程序中显示。  
  
 拥有组件的目的是跟踪对我们可以使用托管属性以及所有依赖项自定义的内容的所有限制，从而可以将其导出、导入和（在托管解决方案中）删除，而不会有任何遗漏。  
  
<a name="BKMK_ManagedAndUnmanagedSolutions"></a>   
## <a name="managed-and-unmanaged-solutions"></a>托管和非托管解决方案  
 存在**托管**和**非托管**解决方案。 在将**托管**解决方案导入后，无法进行修改，但可以将其卸载。 可以通过卸载解决方案来删除该解决方案的所有组件。  
  
 在导入**非托管**解决方案时，可以将该解决方案的所有组件添加到您的环境中。 无法通过卸载解决方案删除组件。  
  
 在导入包含您已经自定义的组件的**非托管**解决方案时，您的自定义项将被导入的非托管解决方案中的自定义项覆盖。 此操作无法撤消。  
  
> [!IMPORTANT]
>  请仅在需要将所有组件添加到您的环境并覆盖所有现有的自定义项时，安装非托管解决方案。  
  
 即使您不打算分发您的应用或自定义项，也可能需要创建并使用非托管解决方案，以便拥有一个仅包含您已经自定义的那部分应用程序的单独视图。 只要进行了自定义，就要将其添加到所创建的非托管解决方案。  
  
 在创建**托管**解决方案时，要在导出解决时选择**托管**选项。 如果您创建托管解决方案，则无法将其重新导入到用于创建该解决方案的同一个环境。 您只能将其导入到其他环境中。  
  
<a name="BKMK_HowSolutionsAreApplied"></a>   
### <a name="how-solutions-are-applied"></a>如何应用解决方案  
 所有解决方案都作为层进行评估，以确定您的应用实际要执行的内容。 下图展示了托管和非托管解决方案的评估方式，以及其中的更改在环境中的显示方式。  
  
 ![解决方案层](media/solution-layering.png "解决方案层")  
  
 从底部开始向上  
  
 **系统解决方案**  
 系统解决方案就像每个环境都有的托管解决方案。 系统解决方案是系统中所有现成的组件的定义。  
  
 **托管解决方案**  
 托管解决方案可以修改系统解决方案组件，并可添加新组件。 如果安装了多个托管解决方案，则安装的第一个托管解决方案在后安装的托管解决方案下面。 也就是说，安装的第二个解决方案可以自定义之前安装的那个解决方案。 当两托管解决方案的定义有冲突时，一般规则是“后来者赢”。 如果卸载托管解决方案，则其下方的托管解决方案后生效。 如果卸载所有托管解决方案，则应用系统解决方案中定义的默认行为。  
  
 **非托管自定义项**  
 非托管自定义项是通过非托管解决方案对环境所做的任何更改。 系统解决方案定义您能或不能使用托管属性自定义的内容。 托管解决方案的发布商具有相同的能力，可以限制您对他们在其解决方案中添加的解决方案组件的自定义能力。 您可以自定义没有阻止您自定义它们的托管属性的任何解决方案组件。  
  
 **应用程序行为**  
 这是您可在环境中实际看到的内容。 默认系统解决方案以及托管解决方案，加上已经应用的任何非托管自定义项。  
  
<a name="BKMK_ManagedProperties"></a>   
## <a name="managed-properties"></a>托管属性  
 有些组件不能自定义。 系统解决方案中的这些组件具有阻止您自定义它们的元数据。 这此元数据称为**托管属性**。 托管解决方案的发布商还可以设置托管属性，从而阻止您通过他们不希望您采用的方式来自定义其解决方案。  
  
<a name="BKMK_Dependencies"></a>   
## <a name="solution-dependencies"></a>解决方案依赖项  
 由于托管解决方案分层方式的原因，有些托管解决方案可能会依赖其他托管解决方案中的解决方案组件。 有些解决方案发布商会利用这一点来构建模块化的解决方案。 您可能需要先安装“基本”托管解决方案，然后再安装一个托管解决方案以进一步自定义基本托管解决方案中的组件。 第二个托管解决方案依赖于第一解决方案中的解决方案组件。  
  
 系统会跟踪解决方案之间的这些依赖关系。 如果您尝试安装的解决方案需要未安装的某个基本解决方案，则将无法安装该解决方案。 您将收到一条消息，指示该解决方案需要先安装另一个解决方案。 同样，由于依赖关系，当仍然安装了依赖于基本解决方案的解决方案时，将无法卸载基本解决方案。 您必须先卸载依赖的解决方案，然后才能卸载基本解决方案。  
 
## <a name="solution-publisher-prefix"></a>解决方案发布商前缀 

默认情况下，您在 Power Apps 内使用的解决方案将是与 **Common Data Service 默认发布商**关联的 **Common Data Services 默认解决方案**。 将为发布商随机分配默认自定义项前缀，例如，可能是 `cr8a3`。 这意味着为您的组织创建的元数据的每个新项目的名称都会将此前缀附加到用于唯一标识项目的名称前面。 

建议更改解决方案发布商前缀，使其更有意义。 详细信息：[更改解决方案发布商前缀](change-solution-publisher-prefix.md)
  
### <a name="next-steps"></a>后续步骤  
[导入、更新和导出解决方案](import-update-export-solutions.md) <br/>
[导航到特定解决方案](navigate-specific-solution.md)
 
