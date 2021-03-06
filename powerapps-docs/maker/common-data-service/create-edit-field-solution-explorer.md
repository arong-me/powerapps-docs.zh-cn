---
title: 使用 Power Apps 解决方案资源管理器创建和编辑 Common Data Service 的字段 | MicrosoftDocs
ms.custom: ''
ms.date: 05/18/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- PowerApps
ms.author: matp
manager: kvivek
author: Mattp123
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 8eee62b8190c2422e2e910fd28306a0d56da85ec
ms.sourcegitcommit: a1b54333338abbb0bc3ca0d7443a5a06b8945228
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/13/2020
ms.locfileid: "3125341"
---
# <a name="create-and-edit-fields-for-common-data-service-using-power-apps-solution-explorer"></a>使用 Power Apps 解决方案资源管理器创建和编辑 Common Data Service 的字段

解决方案资源管理器为创建和编辑 Common Data Service 的字段提供一种方法。

[Power Apps 门户](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)支持配置最常见的选项，但是某些选项只能使用解决方案资源管理器设置。 <br />详细信息： 
- [创建和编辑 Common Data Service 的字段](create-edit-fields.md)
- [使用 Power Apps 门户创建和编辑 Common Data Service 的字段](create-edit-field-portal.md)
  
## <a name="open-solution-explorer"></a>打开解决方案资源管理器

您创建的任何自定义字段的名称中包含自定义前缀。 这是根据您在其中工作的解决方案的解决方案发布商设置的。 如果您关心自定义前缀，请确保在非托管解决方案中工作，其中的自定义前缀是您需要的此实体的前缀。 详细信息：[更改解决方案发布商前缀](change-solution-publisher-prefix.md) 

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]


## <a name="view-fields"></a>视图字段

解决方案资源管理器打开后，在**组件**下展开**实体**，然后选择您要创建或编辑字段的实体。

![解决方案资源管理器字段视图](media/solution-explorer-fields-view.png)

可以选择下列视图： 

 |视图|说明|
 |--|--|
 |**所有**| 显示实体的所有字段|
 |**自定义**|仅显示实体的自定义字段|
 |**可自定义**|只显示可编辑的字段|

## <a name="create-a-field"></a>创建字段

当查看字段时，在命令栏中，单击将打开新字段窗体的**新建**。  托管解决方案中包含的某些标准实体或自定义实体可能不允许您添加新字段。

> [!NOTE]
> 对于模型驱动应用程序，您还可以从窗体编辑器创建新字段。 在窗体编辑器中，在**字段资源管理器**下单击**新建字段**以创建新字段。 详细信息：[将字段添加到窗体](../model-driven-apps/add-field-form.md)

![解决方案资源管理器新字段窗体](media/solution-explorer-new-field-form.png)

您必须输入数据并在保存前确认为以下属性设置的默认值。

|属性|说明|
|--|--|
|**显示名称**|用户界面中要为字段显示的文本。 您可以在保存后更改此值，但是您输入的值将为**名称**字段生成值。|
|**字段要求**|字段中是否需要数据才能保存记录。 详细信息：[字段要求选项](#field-requirement-options)|
|**名称**|在整个环境中的唯一名称。 名称将根据您输入的显示名称为您生成，不过您可以在保存之前进行编辑。 在创建字段后，不能更改名称，因为它将在您的应用程序或代码中引用。 名称会将当前解决方案发布商的自定义项前缀附加到字段的前面。|
|**可搜索**|将您不使用的实体的字段的此项设置为**否**。  可搜索的字段会出现在模型驱动应用程序的**高级查找**中，并且可在自定义视图时使用该字段。 取消选择此设置将减少向使用高级查找的用户显示的选项数量。|
|**字段安全性**|字段中的数据是否在比实体更高的级别受到保护。 详细信息：[用于控制访问的字段级安全性](/dynamics365/customer-engagement/admin/field-level-security)|
|**审核**|此字段的数据是否在启用实体以进行审核时被审核。 详细信息：[审核数据和用户活动的安全性和合规性](/customer-engagement/admin/audit-data-user-activity)|
|**说明**|为用户输入有关字段用途的说明。 当用户将鼠标悬停在字段的标签上时，这些描述在模型驱动应用程序中显示为用户的工具提示。|
|**以交互式体验显示在全局筛选器中**|详细信息：[配置交互式体验仪表板](/dynamics365/customer-engagement/customize/configure-interactive-experience-dashboards) |
|**在交互式体验仪表板中可排序**|详细信息：[配置交互式体验仪表板](/dynamics365/customer-engagement/customize/configure-interactive-experience-dashboards)|
|**数据类型**|控制值如何在某些应用程序中存储以及如何确定格式。 一旦保存字段，您无法更改数据类型，因为这可能影响实体中的数据。 详细信息：[字段数据类型](#field-data-types)|
|**字段类型**|字段是否是**简单**、**计算**或**汇总**。 详细信息：[字段类型](#field-type)|
|**格式**|如何确定字段的格式。 可用的格式选项取决于**数据类型**。|

您可以根据所选择的**数据类型**设置其他选项。 详细信息：[字段数据类型](#field-data-types)

## <a name="field-requirement-options"></a>字段需求选项

有三个字段需求选项：
- **可选**：即使此字段中无数据，也可以保存记录。
- **业务建议**：即使此字段中无数据，也可以保存记录。 但是，字段旁边将出现一个蓝色符号以指示这是一个重要字段。
- **业务必需**：如果此字段中无数据，无法保存记录。
> [!NOTE]
> 让字段成为业务必需字段时，要谨慎。 如果用户由于缺乏要输入到必需字段中的正确信息而无法保存记录，将抗拒使用应用程序。 用户可能会简单地输入不正确的数据以保存记录，然后继续其工作。 当记录中的数据由于用户处理而发生变化时，您可以使用业务规则或窗体脚本来更改要求级别。 详细信息[创建业务规则和建议以在窗体中应用逻辑](../model-driven-apps/create-business-rules-recommendations-apply-logic-form.md)

## <a name="field-data-types"></a>字段数据类型

有许多不同类型的字段，但是，您只能创建其中一部分。 有关所有字段类型的详细信息，请参阅[字段类型和字段数据类型](types-of-fields.md)。

在创建字段时，**数据类型**提供以下选择：

|选项|说明|
|--|--|
|**单行文本**|此字段中最多可以包含 4,000 个文本字符。 可以设置一个小于此数的最大长度。 此字段有多个格式选项，可以更改文本的表示形式。  详细信息：[单行文本选项](#single-line-of-text-options)|
|**选项集**|显示可以单选的选项列表。 详细信息：[选项集字段选项](#option-set-field-options)|
|**多选选项集**|显示可以多选的选项列表。 详细信息：[选项集字段选项](#option-set-field-options)|
|**两个选项**|显示可以选择两项之一的选项列表。<br /><br /> 两个选项字段不提供字段级的格式选项。 但是，当向窗体添加一个选项字段时，可以选择将其显示为单选按钮、复选框或选择列表。|
|**图像**|在应用程序中显示每个记录的单个图像。 每个实体可以有一个图像字段。 图像字段始终名为 `EntityImage`。|
|**整数**|此字段可以有值介于 -2,147,483,648 和 2,147,483,647 之间的整数。  此字段具有根据如何显示字段更改的选项。 详细信息：[整数选项](#whole-number-options)|
|**浮点数**|此字段中可以有 5 位小数精度的介于 -100,000,000,000 与 100,000,000,000 之间的值。 您可以指定精度以及最小值和最大值。 详细信息：[使用恰当的数值类型](types-of-fields.md#using-the-right-type-of-number)|
|**十进制数**|此字段中可以有 10 位小数精度的介于 -100,000,000,000 与 100,000,000,000 之间的值。 您可以指定精度以及最小值和最大值。 详细信息：[使用恰当的数值类型](types-of-fields.md#using-the-right-type-of-number)|
|**货币**|此字段中可以有介于 -922,337,203,685,477 和 922,337,203,685,477 之间的货币值。 您可以设置一个精度，或者选择根据特定货币来设置精度，设置组织使用的单个标准精度。 详细信息：[使用货币字段](types-of-fields.md#using-currency-fields)|
|**多行文本**|此字段中最多可以包含 1,048,576 个文本字符。 可将最大长度设置为低于此值。 在将该字段添加到模型驱动应用程序窗体时，可以指定字段的维度。|
|**日期和时间**|使用这些字段来存储时间值。 您可以存储的值早达 1/1/1753 12:00 AM。 详细信息：[日期和时间选项](#date-and-time-options)|
|**查找**|允许设置对一实体类型的单个记录的引用的字段。 有些系统查找字段有不同的行为。 详细信息：[不同的查找类型](types-of-fields.md#different-types-of-lookups)|
|**客户**|您可以使用查找字段指定客户，可以是客户或联系人。  详细信息：[不同的查找类型](types-of-fields.md#different-types-of-lookups)|

### <a name="single-line-of-text-options"></a>单行文本选项

单行文本数据类型具有以下格式选项：

|格式|说明|
|--|--|
|**文本**|要在单行文本框中显示的文本值。|
|**文本区域**|要在多行文本框中显示的文本值。 如果需要多于 4,000 个字符，请使用**多行文本**数据类型。|
|**Email**|在字段中作为电子邮件地址验证并作为 mailto 链接呈现的文本值。 |
|**URL**|作为 URL 验证并作为链接呈现以打开 URL 的文本值。|
|**股票代号**|将显示一个将打开以显示股票代号的报价单的股票代号的文本值。 |
|**电话**|作为电话号码验证并作为链接呈现以使用 Skype 进行电话联络的文本值。 |

您还可以设置**最大长度**，以使系统不允许超过您指定长度的文本值。

### <a name="option-set-field-options"></a>选项集字段选项

提供一组选项的字段可以包含其自己的一组*本地*选项，或引用一组可由多个字段使用的通用*全局*选项。

当您发现自己在为多个字段创建一组相同的选项时，使用全局选项集非常重要。 通过全局选项集，您只需要在一个位置维护一组选项。 

如果选择**多选选项集**或**选项集**数据类型，解决方案资源管理器设计器将默认提供本地选项集的选项。

![配置本地选项集](media/local-option-set-solution-explorer.png)

#### <a name="configure-local-options"></a>配置本地选项

[!INCLUDE [cc_configure-option-set-options-solution-explorer](../../includes/cc_configure-option-set-options-solution-explorer.md)]

#### <a name="use-existing-option-set"></a>使用现有选项集

如果您选择**使用现有选项集**，设计器将显示现有*全局选项集*的列表，并包含**编辑**和**新建**按钮来配置此字段应使用的全局选项。

![配置全局选项集](media/global-option-set-solution-explorer.png)

您还可以单独配置全局选项集。 详细信息：[为 Common Data Service 创建和编辑全局选项集（选择列表）](create-edit-global-option-sets.md)

> [!NOTE]
> 如果您将每个选项集定义为全局选项集，您的全局选项集列表将增大并可能很难管理。 如果您知道这组选项只会在一个位置使用，请使用本地选项集。


### <a name="whole-number-options"></a>整数选项

整数字段具有以下格式选项：

|格式|说明|
|--|--|
|**无**|在文本框中的显示的数字值。|
|**持续时间**|显示为包含时间间隔的下拉列表的数字值。 用户可从列表中选择值，或键入表示分钟数的整数值。|
|**时区**|显示为包含时区列表的下拉列表的数字值。|
|**语言**|显示为包含已为环境启用的语言列表的下拉列表的数字值。 如果没有启用其他语言，则基本语言将是唯一选项。 保存的值是该语言的区域设置标识符 (LCID) 值。|

您还可以限制允许的最大值和最小值。

### <a name="date-and-time-options"></a>日期和时间选项

日期和时间字段具有以下选项：

|格式 |说明|
|--|--|
|**日期和时间**|日期和时间值。|
|**仅限日期**|仅日期显示的日期和时间值。 时间值在系统中存储为 12:00 AM (00:00:00)。|

您还可以在**高级选项**中为“日期时间”字段设置特定**行为**。

- **用户当地时间**：显示转换为当前用户当地时区的值。 这是新字段的默认值。
- **仅限日期**：此行为可用于**仅限日期**类型。 显示不进行时区转换的值。 将此设置用于生日和纪念日等数据。
- **时区无关**：显示无时区转换的值。

详细信息：[日期及时间字段的行为和格式](behavior-format-date-time-field.md)

## <a name="field-type"></a>字段类型

您可以将自定义字段的**字段类型**设置为**简单**、**计算**或**汇总**字段。 

### <a name="simple"></a>简单

简单表示字段不是计算字段或汇总字段。

### <a name="calculated"></a>计算

使用计算字段，您可以输入公式来向字段分配值。 这些数据类型可以设置为计算字段：**货币**、**日期和时间**、**十进制数**、**多选选项集**、**选项集**、**单行文本**、**两个选项**和**整数**。

详细信息：[定义计算字段以自动化手动计算](define-calculated-fields.md)

### <a name="rollup"></a>Rollup

使用汇总字段，您可以设置将定期运行的聚合函数来为字段设置数字值。 这些数据类型可以设置为计算字段：**货币**、**日期和时间**、**十进制数**和**整数**。

详细信息：[定义用于聚合值的汇总字段](define-rollup-fields.md)

## <a name="save-new-field"></a>保存新字段

在您配置字段后，请使用命令栏中的三个命令之一：

|Command|说明|
|--|--|
|**保存**|保存字段定义并保持窗体窗口打开。|
|**保存并关闭**|保存字段定义并关闭窗口。|
|**保存并新建**|保存字段定义并打开新窗体以创建新字段。|


## <a name="edit-a-field"></a>编辑字段 

在[查看字段](#view-fields)时，单击要编辑的字段。 托管解决方案中包含的某些标准字段或自定义字段可能不允许您编辑新字段。

> [!NOTE]
> 在编辑窗体时，对于任何已添加到窗体中的字段，可以双击字段以显示**字段属性** 。 在**详细信息**选项卡上，单击**编辑**。 详细信息：[将字段添加到窗体](../model-driven-apps/add-field-form.md)

在对字段进行更改后，必须发布自定义项。 

- 要发布您对实体的更改，请在**组件**中选择**实体**，然后选择您已更改的实体。 在**操作**工具栏上选择**发布**。  
  
- 若要发布对多个实体或组件进行的所有更改，请在**操作**工具栏上选择**发布所有自定义项**。  
  
> [!NOTE]
>  安装解决方案或发布自定义项会干扰常规的系统操作。 我们建议您以对用户造成的干扰最少为宗旨，合理安排解决方案的发布时间。  

### <a name="edit-multiple-fields"></a>编辑多个字段

若要编辑一个或多个字段，请选择您希望修改的字段（使用 Shift 键），然后在**操作**工具栏上，选择**编辑**。 
  
如果选择编辑多个字段时，显示**编辑多个字段**对话框。 您可以编辑**字段要求**、**可搜索**和**审核**。 

## <a name="delete-a-field"></a>删除字段

具有系统管理员安全角色，您可以删除不属于托管解决方案的任何自定义字段。 删除字段时，字段中存储的所有数据都将丢失。 从删除的字段中恢复数据的唯一方式是从删除字段前的某个点恢复数据库。

> [!NOTE]
> 在删除自定义字段之前，必须删除其他解决方案组件中可能存在的所有依赖项。 

1. 在[查看字段](#view-fields)时，选择可以从列表中删除的自定义字段并单击命令栏中的![删除命令](../model-driven-apps/media/delete.gif)按钮。
2. 在**确认删除**对话框中，选择**删除**。

> [!TIP]
> 您可以在一项操作中选择要删除的多个自定义字段。

### <a name="check-field-dependencies"></a>检查字段依赖项 

在列表中选择字段。 在**更多操作**菜单中，选择**显示依赖项**。

![显示字段的依赖项](media/check-field-dependencies.png)

依赖项是与字段相关的将会阻止其被删除的任何使用。 例如，如果在窗体或视图中使用了字段，则必须先取消在这些解决方案组件中对字段的引用。  
  
如果删除查找字段，则将自动删除它的 1:N 实体关系。  

## <a name="ime-mode"></a>IME 模式

提供直接文本输入的任何字段都有一个 IME 模式。 输入法编辑器 (IME) 用于东亚语言（如日语）。 用户可以使用 IME，通过标准的 101 键键盘输入东亚书面语中使用的数千个不同字符。


### <a name="see-also"></a>另请参阅  
[创建和编辑 Common Data Service 的字段](create-edit-fields.md)<br />
[使用 Power Apps 门户创建和编辑 Common Data Service 的字段](create-edit-field-portal.md)<br />
[字段类型和字段数据类型](types-of-fields.md)<br />
[定义计算字段以自动化手动计算](define-calculated-fields.md)<br />
[定义用于聚合值的汇总字段](define-rollup-fields.md)<br />
[行为和日期及时间字段的格式](behavior-format-date-time-field.md)
