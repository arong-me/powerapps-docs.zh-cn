---
title: 如何合并托管解决方案 (Common Data Service) | Microsoft Docs
description: 为了避免多个已安装的解决方案相互干扰，请在构造解决方案时遵循最佳实践
ms.custom: ''
ms.date: 02/27/2020
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: shmcarth
ms.author: jdaly
manager: ryjones
search.audienceType:
- maker
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 7b6a5d741179c26799badfd6c7427e06941f5851
ms.sourcegitcommit: 629e47c769172e312ae07cb29e66fba8b4f03efc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "3108049"
---
# <a name="understand-how-managed-solutions-are-merged"></a>了解如何合并托管的解决方案

准备要安装的托管解决方案时，请记住环境可能已安装了多个解决方案，或者将来可能要安装其他解决方案。 构造遵循最佳实践的解决方案，以便您的解决方案不会干扰其他解决方案。  
  
Common Data Service 用于合并自定义项的进程强调维护解决方案的功能。 尽管已竭尽全力保持外观，但是自定义项之间的不兼容性可能需要计算的解决方案更改某些外观细节来维护自定义项的功能。  
  
<a name="BKMK_MergingFormCustomizations"></a>   

## <a name="merge-form-customizations"></a>合并窗体自定义  
 必须要合并的窗体自定义项只有那些要对已存在于环境中的任何实体窗体执行的自定义项。 通常，这意味着对于安装 Common Data Service 时创建的实体，仅当您的解决方案自定义这些实体包括的窗体时，才需合并窗体自定义项。 避免窗体合并的一种方法是为任何 Common Data Service 实体提供新窗体。 自定义实体的窗体不需要合并，除非您创建更新或修改现有托管解决方案（创建了自定义实体及其窗体）的解决方案。  
  
 将解决方案打包成托管解决方案时，存储在 FormXML 中的窗体定义将与原始的 FormXML 进行比较，只有不同项才会包括在托管解决方案中。 在新环境中安装托管解决方案时，表单自定义的不同项则会与现有窗体的 FormXML 合并以创建新的窗体定义。 此新的窗体定义即为用户看到的定义，也是系统定制员可以修改的定义。 卸载托管解决方案时，仅移除托管解决方案中找到的那些窗体元素。  
  
 将新元素添加到要合并的窗体时，建议将新元素包括在新的容器元素（选项卡或区段）中。 向任何容器添加的内容会追加到容器的末端。 例如，添加到区段中的字段会放置在区段的末端。 建议安装解决方案的定制员在安装它后修改窗体以重新排列元素。  
  
 包含使用新安全角色的窗体的托管解决方案依赖于这些角色。 您应该将这些安全角色包括在托管解决方案中。 如果有与某个窗体关联的安全角色，而窗体不在托管解决方案安装在的环境中，则虽然安装不会失败，但是表单可能不会与任何安全角色关联。 卸载托管解决方案时，将移除它所包括的所有安全角色。 托管解决方案外部的所有窗体将不再与那些安全角色关联。  
  
> [!NOTE]
>  当托管解决方案实体包含多个窗体且环境实体窗体也包含多个窗体时，新的表单则不会追加至可用窗体列表的底部 – 它们会与原先的实体窗体进行交叉存取。  
  
<a name="BKMK_MergingNavigationCustomizations"></a>   
## <a name="merge-navigation-sitemap-customizations"></a>合并导航（网站地图）自定义  
 将解决方案打包为托管解决方案时，SiteMap XML 会与原始的 SiteMap XML 以及对 SiteMap 进行的任何其他自定义项进行比较。 只有不同项才会包括在托管解决方案中。 这些不同项包括更改、移动、添加或移除的项。 当托管解决方案安装在新的环境中时，SiteMap 更改会与安装托管解决方案所在的环境中发现的 SiteMap XML 进行合并。 新的 SiteMap 定义是用户所能看到的内容。  
  
 此时，定制员可以将 SiteMap 导出到非托管解决方案，该 SiteMap 定义将包括活动 SiteMap 的所有元素。 定制员然后可以修改 SiteMap 并将其重新导入为非托管自定义项。  稍后，如果卸载了托管解决方案，将引用随托管解决方案导入的 SiteMap XML 以移除该托管解决方案引入的更改。 然后计算新的活动 SiteMap。  
  
 向 SiteMap 添加新的可见元素时，它会显示在任何所属容器的底部。 例如，新区域显示在导航区域的底部。 若要放置已添加的元素，您必须导出 SiteMap，对其进行编辑以设置精确位置，然后将其重新导入为非托管解决方案。  
  
> [!NOTE]
>  发布之间只能应用一个 SiteMap 自定义项。 导入新的 SiteMap 定义时，任何未发布的 SiteMap 自定义项都将丢失。  
  
<a name="BKMK_MergingOptionSetOptions"></a>   
## <a name="merge-option-set-options"></a>合并选项集选项  
 每个新的选项集选项都将使用分配的整数值（包括选项值前缀）进行初始化。 选项值前缀是一组五位数，附加在选项值的前面。 选项值前缀根据解决方案发布商自定义前缀生成，但也可以设置为任何值。 选项值前缀可帮助区分在特定解决方案发布商上下文中创建的新选项集选项，并降低损坏选项值的可能性。 建议使用选项值前缀，但不要求使用。  
  
 托管解决方案通常会为已存在于环境中的选项集更新或添加选项，例如，帐户“类别”或“行业”选项集。 当托管解决方案修改选项集中可用的选项时，在托管解决方案中定义的所有选项都将在环境中可用。 卸载托管解决方案时，选项集选项将返回至它们的原始状态。  
  
### <a name="see-also"></a>另请参阅  

[解决方案概述](solutions-overview.md)  <br />
[导出解决方案](export-solutions.md) <br />
[使用站点地图设计器创建模型驱动应用站点地图](../model-driven-apps/create-site-map-app.md)