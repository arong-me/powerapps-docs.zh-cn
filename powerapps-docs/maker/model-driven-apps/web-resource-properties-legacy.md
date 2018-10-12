---
title: PowerApps 中模型驱动应用主窗体的 Web 资源属性 | MicrosoftDocs
description: 了解主窗体的 Web 资源属性
Keywords: Main form; Web resource properties; Dynamics 365
author: Mattp123
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.author: matp
manager: kvivek
ms.date: 06/27/2018
ms.service: crm-online
ms.topic: article
ms.assetid: 82cd41ea-95b0-4606-9e7d-43eb5ce9ecd6
ms.openlocfilehash: a08ca32b1d300d4302064940e65fd1d067c3ade6
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39669004"
---
# <a name="web-resource-properties-for-model-driven-app-forms"></a>模型驱动应用窗体的 Web 资源属性

可以在窗体上添加或编辑 Web 资源，使其对应用用户更具吸引力或更有用。 支持窗体的 Web 资源是图像或 HTML 文件控件。

> [!NOTE]
> Silverlight Web 资源已弃用，在统一界面客户端中无效。

## <a name="access-web-resource-properties"></a>访问 Web 资源属性

在查看窗体时：
- **添加 Web 资源时**：选择要将其插入的选项卡（例如，“常规”或“备注”），然后在“插入”选项卡上，选择“Web 资源”。<br />![插入 Web 资源](media/insert-web-resource.png)
- **编辑 Web 资源时**：选择窗体选项卡和要编辑的 Web 资源，然后在“主页”选项卡上，选择“更改属性”。 <br />![更改 Web 资源属性](media/web-resource-change-properties.png)

这将打开“添加 Web 资源”或“Web 资源属性”对话框。

![“添加 Web 资源”对话框](media/add-web-resource-dialog.png)


## <a name="web-resource-properties"></a>Web 资源属性

 “添加 Web 资源”或“Web 资源属性”对话框将具有两个（有时为三个）选项卡，具体取决于 Web 资源的类型。

### <a name="general-tab"></a>“常规”选项卡

这些属性定义要使用的 Web 资源及其行为。

|字段|描述|
|--|--|
|**Web 资源**|必填。 查找现有 Web 资源，或新建一个。 使用“启用窗体的 Web 资源”视图，以仅包括可添加为窗体中可视元素的 HTML 和图像 Web 资源。|
|**名称**|必填。 指定要添加到窗体的 Web 资源控件的名称。 此值唯一地标识窗体中的控件。|
|**Label**|必填。 基于“名称”字段值自动生成。 为要添加到窗体的 Web 资源控件指定可本地化的文本。 如果想要使其可见，请选择“在窗体上显示标签”。|
|**默认情况下可见**|如果启用此字段，加载窗体时 Web 资源将是可见的。 如果业务规则或窗体脚本需按需显示 Web 资源，请取消选中此字段。 详细信息：[显示或隐藏窗体元素](visibility-options-legacy.md)|
|**为移动应用启用**|选择此选项可允许此 Web 资源在移动应用中可见。|

根据所选择的 Web 资源类型，设置其他属性。

对于 HTML Web 资源，将显示以下内容：

![HTML Web 资源属性](media/web-resource-general-html-properties.png)

|字段|描述|
|--|--|
|**自定义参数(数据)**|通常是作为 `data` 查询字符串参数传递到 HTML Web 资源的配置数据。 与 HTML 页面关联的脚本可访问此数据，并使用该数据来更改页面的行为。|
|**限制交叉框架脚本(若支持)**|如果不完全信任 HTML Web 资源中的内容，请使用此选项。 详细信息：[开发人员文档：选择是否限制交叉框架脚本](/dynamics365/customer-engagement/developer/use-iframe-and-web-resource-controls-on-a-form#select-whether-to-restrict-cross-frame-scripting)|
|**将记录对象类型代码和唯一标识符作为参数传递**|有关窗体中可见的当前记录的数据可以传递到 HTML Web 资源页，以便在该页中运行的脚本可访问有关记录的数据。 详细信息： <br />[将参数传递给 Web 资源](#pass-parameters-to-web-resources)<br />[开发人员文档：传递有关记录的上下文信息](/dynamics365/customer-engagement/developer/use-iframe-and-web-resource-controls-on-a-form#pass-contextual-information-about-the-record)|

对于图像 Web 资源，可选择指定“替代文本”，这对于用于使每个人都能访问此页的辅助技术而言非常重要。

<!-- TODO: Why are Custom Parameters available to pass to image web resources? -->

### <a name="formatting-tab"></a>“格式设置”选项卡

在“格式设置”选项卡上，显示的选项因插入 Web 资源的类型及其插入位置的上下文而异。 这些选项包括指定显示的列数和行数、是否显示边框和滚动行为。

![Web 资源格式设置属性](media/web-resource-formatting-properties.png)

|属性|描述|  
|--------------|-----------------|
|**选择控件占用的列数**|如果包含 Web 资源的部分具有多个列，则可以将该字段的占用列数上限设置为该部分所具有的列数。|  
|**选择控件占用的行数**|可以通过指定行数来控制 Web 资源的高度，或选择“自动扩展以使用可用空间”，来允许 Web 资源高度扩展到可用空间。|  
|**选择 IFRAME 的滚动类型**|需使用 IFRAME 将 HTML Web 资源添加到窗体。<br /><br /> - **根据需要**：在 Web 资源的大小超过可用空间时显示滚动条。<br />- **始终**：始终显示滚动条。<br />- **从不**：从不显示滚动条。|  
|**显示边框**|在 Web 资源周围显示边框。|  


### <a name="dependencies-tab"></a>“依赖项”选项卡

Web 资源可使用脚本与窗体中的字段进行交互。 如果从窗体中删除字段，则 Web 资源的脚本可能中断。 将 Web 资源中脚本引用的任何字段添加到“从属字段”，以免意外将其删除。

![Web 资源依赖项属性](media/web-resource-dependency-properties.png)
  
<a name="BKMK_PassingParametersToWebResource"></a> 
 
## <a name="pass-parameters-to-web-resources"></a>将参数传递给 Web 资源 

HTML Web 资源可接受作为查询字符串参数传递的参数。  
  
可以通过启用“将记录对象类型代码和唯一标识符作为参数传递”选项来传递有关记录的信息。 如果在“自定义参数(数据)”字段中键入信息，则将使用 data 参数传递信息。 传递的值为：  
  
|参数|描述|  
|---------------|-----------------|  
|`data`|仅当为“自定义参数(数据)”提供文本时，才会传递此参数。|  
|`orglcid`|组织默认语言 LCID。|  
|`orgname`|组织名称。|  
|`userlcid`|用户首选语言 LCID|  
|`type`|不要使用此参数。 实体类型代码。 对于不同组织中的自定义实体，此数值可能不同。 改用实体类型名称。|  
|`typename`|实体类型名称。|  
|`id`|记录的 ID 值。 保存实体记录前，此参数没有值。|  
  
不允许使用任何其他参数，如果使用其他参数，则不会打开 Web 资源。 如果需要传递多个值，可以重载 data 参数，以在其中包括多个参数。

详细信息：[开发人员文档：传递有关记录的上下文信息](/dynamics365/customer-engagement/developer/use-iframe-and-web-resource-controls-on-a-form#pass-contextual-information-about-the-record)

### <a name="see-also"></a>另请参阅

[创建或编辑 Web 资源以扩展应用](create-edit-web-resources.md)<br />
[使用主窗体及其组件](use-main-form-and-components.md)
