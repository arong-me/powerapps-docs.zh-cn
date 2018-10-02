---
title: PowerApps 中模型驱动应用程序主窗体的 Web 资源属性 | MicrosoftDocs
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
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="web-resource-properties-for-model-driven-app-forms"></a>模型驱动应用程序窗体的 Web 资源属性

您可以添加或编辑表单上的 web 资源，使其对应用用户而言更具吸引力或更有用。 窗体支持的 Web 资源有图像或 HTML 文件控件。

> [!NOTE]
> Silverlight Web 资源已弃用，不能在统一接口客户端使用。

## <a name="access-web-resource-properties"></a>访问 Web 资源属性

在查看窗体时：
- **添加 Web 资源时**：选择您要在其上进行插入的选项卡（例如**常规**或**注释**），然后在**插入**选项卡上，选择 **Web 资源**。<br />![插入 Web 资源](media/insert-web-resource.png)
- **在编辑 Web 资源时**：选择窗体选项卡和要编辑的 Web 资源，然后在**主页**选项卡上选择**更改属性**。 <br />![更改 Web 资源属性](media/web-resource-change-properties.png)

这将打开**添加 Web 资源**或 **Web 资源属性**对话框。

![添加 Web 资源对话框](media/add-web-resource-dialog.png)


## <a name="web-resource-properties"></a>Web 资源属性

 **添加 Web 资源**或 **Web 资源属性**对话框有两个选项卡，有时有三个选项卡，具体取决于 Web 资源的类型。

### <a name="general-tab"></a>“常规”选项卡

这些属性定义要使用的 Web 资源及其如何操作。

|字段|说明|
|--|--|
|**Web 资源**|*必需。* 查找现有的 Web 资源或创建新资源。 使用**启用窗体的 Web 资源**视图以仅包含可在窗体中添加为可视元素的 HTML 和图像 Web 资源。|
|**名称**|*必需。* 为要添加到窗体的 Web 资源控件指定名称。 此值唯一标识窗体中的控件。|
|**标签**|*必需。* 基于**名称**字段值自动生成。 为要添加到窗体的 Web 资源控件指定可本地化文本。 如果要使此内容可见，选择**在窗体上显示标签**。|
|**默认情况下可见**|在启用此设置时，Web 资源会在加载窗体时可见。 如果您具有将根据需要显示 Web 资源的业务规则或窗体脚本，请取消选中此字段。 详细信息：[显示或隐藏窗体元素](visibility-options-legacy.md)|
|**为移动设备启用**|选择此选项以使此 Web 资源在移动应用程序中可见。|

根据您选择的 Web 资源类型，设置其他属性。

对于 HTML Web 资源，您将看到这些内容：

![HTML Web 资源属性](media/web-resource-general-html-properties.png)

|字段|说明|
|--|--|
|**自定义参数(数据)**|通常是将作为 `data` 查询字符串参数传递到 HTML Web 资源的配置数据。 与 HTML 页面关联的脚本可以访问此数据，并使用它来更改页面的行为。|
|**限制交叉框架脚本（若支持）**|如果您对 HTML Web 资源中的内容不完全信任，请使用此选项。 详细信息：[开发人员文档：选择是否限制交叉框架脚本](/dynamics365/customer-engagement/developer/use-iframe-and-web-resource-controls-on-a-form#select-whether-to-restrict-cross-frame-scripting)|
|**以参数形式传递记录对象类型代码和唯一标识符**|有关窗体中显示的当前记录的数据可以传递到 HTML Web 资源页面，以便在页面中运行的这个脚本可以访问有关记录的数据。 详细信息： <br />[将参数传递到 Web 资源](#pass-parameters-to-web-resources)<br />[开发人员文档：传递有关记录的上下文信息](/dynamics365/customer-engagement/developer/use-iframe-and-web-resource-controls-on-a-form#pass-contextual-information-about-the-record)|

对于图像 Web 资源，您可以选择指定对于让页面可供每个人访问的辅助技术很重要的**替换文本**。

<!-- TODO: Why are Custom Parameters available to pass to image web resources? -->

### <a name="formatting-tab"></a>“格式设置”选项卡

在**格式设置**选项卡，显示的选项基于插入的 Web 资源类型以及所插入的上下文而不同。 这些选项包含指定列和行显示边框的数目，查看边框是否显示及其滚动行为。

![Web 资源格式属性](media/web-resource-formatting-properties.png)

|属性|说明|  
|--------------|-----------------|
|**选择控件所占据的栏数**|当包含 Web 资源的分区有多栏时，可以将字段设置为最多占据分区具有的栏数。|  
|**选择控件所占据的行数**|您可以通过指定行数来控制 Web 资源的高度，或选择**自动扩展以利用可用空间**来允许 Web 资源的高度扩展到可用空间。|  
|**选择 IFRAME 的滚动类型**|使用 IFRAME 将 HTML Web 资源添加到窗体。<br /><br /> - **视需要而定**：当 Web 资源大小大于空间时，显示滚动条。<br />- **始终**：始终显示滚动条。<br />- **从不**：从不显示滚动条。|  
|**显示边框**|在 Web 资源周围显示边框。|  


### <a name="dependencies-tab"></a>依赖项选项卡

Web 资源可以使用脚本与窗体中的字段交互。 如果从窗体中删除了某个字段，Web 资源中的脚本可能会中断。 将 Web 资源中的脚本引用的任何字段添加到**从属字段**，可防止其被意外删除。

![Web 资源依赖项属性](media/web-resource-dependency-properties.png)
  
<a name="BKMK_PassingParametersToWebResource"></a> 
 
## <a name="pass-parameters-to-web-resources"></a>将参数传递到 Web 资源 

HTML Web 资源可以接受作为查询字符串参数传递的参数。  
  
通过启用**传递记录对象类型代码和唯一标识符作为参数** 选项，可以传递有关记录的信息。 如果在**自定义参数（数据）** 字段中键入了信息，则将使用 data 参数传递该信息。 传递的值包括：  
  
|参数|说明|  
|---------------|-----------------|  
|`data`|仅当为**自定义参数（数据）** 提供文本时，才会传递此参数。|  
|`orglcid`|组织默认语言 LCID。|  
|`orgname`|组织的名称。|  
|`userlcid`|用户的首选语言 LCID|  
|`type`|**不使用此选项。** 实体类型代码。 对于不同组织中的自定义实体，此数值可能会有所不同。 请代之以使用实体类型名称。|  
|`typename`|实体类型名称。|  
|`id`|记录的 ID 值。 在保存实体记录之前，此参数没有价值。|  
  
不允许任何其他参数；如果使用其他参数，Web 资源将不会打开。 如果需要传递多个值，则 data 参数可能会因为要在其中包括更多参数而超载。

详细信息：[开发人员文档：传递有关记录的上下文信息](/dynamics365/customer-engagement/developer/use-iframe-and-web-resource-controls-on-a-form#pass-contextual-information-about-the-record)

### <a name="see-also"></a>另请参阅

[创建或编辑 Web 资源以扩展应用](create-edit-web-resources.md)<br />
[使用“主”窗体及其组件](use-main-form-and-components.md)
