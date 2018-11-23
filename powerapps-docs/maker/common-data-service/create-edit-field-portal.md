---
title: 使用 PowerApps 门户创建和编辑面向应用程序的 Common Data Service 的字段 | MicrosoftDocs
ms.custom: ''
ms.date: 05/18/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - PowerApps
ms.author: matp
manager: brycho
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="create-and-edit-fields-for-common-data-service-for-apps-using-powerapps-portal"></a>使用 PowerApps 门户创建和编辑面向应用程序的 Common Data Service 的字段

[PowerApps 门户](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)提供通过面向应用程序的 Common Data Service 创建和编辑实体字段的简单方法。

此门户支持配置最常见的选项，但是某些选项只能使用解决方案资源管理器设置。 <br />详细信息： 
- [创建和编辑面向应用程序的 Common Data Service 的字段](create-edit-fields.md)
- [使用 PowerApps 解决方案资源管理器创建和编辑面向应用程序的 Common Data Service 的字段](create-edit-field-solution-explorer.md)

## <a name="view-fields"></a>视图字段

1. 从 [PowerApps 门户](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)，选择**模型驱动**或**画布**设计模式。
2. 选择**数据** > **实体**，然后选择具有您要查看的字段的实体。
3. 选择**字段**选项卡后，您可以选择以下视图： 

 |视图|说明|
 |--|--|
 |**所有**| 显示实体的所有字段|
 |**自定义**|仅显示实体的自定义字段|
 |**默认**|仅显示实体的标准字段|
<!-- TODO: What is the actual difference between All and Default? -->

## <a name="create-a-field"></a>创建字段

当查看字段时，在命令栏中，单击将显示**字段属性**的**添加字段**。

![字段属性](media/field-properties.png)


最初，只有三个字段可用：

 |属性|说明|
 |--|--|
 |**显示名称**|用户界面中要为字段显示的文本。|
 |**名称**|在整个环境中的唯一名称。 名称将根据您输入的显示名称为您生成，不过您可以在保存之前进行编辑。 在创建字段后，不能更改名称，因为它将在您的应用程序或代码中引用。 名称会将 **CDS 默认发布商**的自定义项前缀附加到字段的前面。|
 |**数据类型**|控制值如何在某些应用程序中存储以及如何确定格式。 一旦保存字段，您无法更改数据类型，因为这可能影响实体中的数据。|

您可以根据所选择的**数据类型**设置其他选项。

## <a name="field-data-types"></a>字段数据类型

有许多不同类型的字段，但是，您只能创建其中一部分。 有关所有字段类型的详细信息，请参阅[字段类型和字段数据类型](types-of-fields.md)。

在创建字段时，**数据类型**提供以下选择：

### <a name="text"></a>文本 

标准字段文本最多可以存储 4,000 个字符。 默认[最大长度](#max-length)选项设置为较低值，您可以调整。

|数据类型|说明|
|--|--|
|**文本**|要在单行文本框中显示的文本值。|
|**文本区域**|要在多行文本框中显示的文本值。 如果需要多于 4,000 个字符，请使用[多行文本](#multi-line-field)数据类型。|
|**Email**|在字段中作为电子邮件地址验证并作为 mailto 链接呈现的文本值。 |
|**URL**|作为 URL 验证并作为链接呈现以打开 URL 的文本值。|
|**股票代号**|将显示一个将打开以显示股票代号的报价单的股票代号的文本值。 |
|**电话**|作为电话号码验证并作为链接呈现以使用 Skype 进行电话联络的文本值。 |

#### <a name="max-length"></a>最大长度

用于存储文本的字段根据类型有最大绝对值。 **最大长度**选项设置低于特定于您的环境的最大值的值。 如果您在系统中的数据超过此较低值，可以增加该最大长度，但不能低于此值。

### <a name="whole-number"></a>整数

这些字段将数据存储为数字，但包含不同的显示和验证选项。

|数据类型|说明|
|--|--|
|**整数**|在文本框中的显示的数字值。|
|**持续时间**|显示为包含时间间隔的下拉列表的数字值。 用户可从列表中选择值，或键入表示分钟数的整数值。|
|**时区**|显示为包含时区列表的下拉列表的数字值。|
|**语言**|显示为包含已为环境启用的语言列表的下拉列表的数字值。 如果没有启用其他语言，则基本语言将是唯一选项。 保存的值是该语言的区域设置标识符 (LCID) 值。|


### <a name="date-time"></a>日期时间

使用这些字段来存储时间值。 您可以存储的值早达 1/1/1753 12:00 AM。

|数据类型|说明|
|--|--|
|**日期和时间**|日期和时间值。|
|**仅限日期**|仅日期显示的日期和时间值。 时间值在系统中存储为 12:00 AM (00:00:00)。|

您还可以在**高级选项**中为“日期时间”字段设置特定**行为**。

- **用户当地时间**：显示转换为当前用户当地时区的值。 这是新字段的默认值。
- **仅限日期**：此行为可用于**仅限日期**类型。 显示不进行时区转换的值。 将此设置用于生日和纪念日等数据。
- **时区无关**：显示无时区转换的值。

详细信息：[日期及时间字段的行为和格式](behavior-format-date-time-field.md)

### <a name="other-data-types"></a>其他数据类型

|数据类型|说明|
|--|--|
|**货币**|为环境配置的任何货币的货币值。 您可以设置一个精度，或者选择根据特定货币来设置精度，设置组织使用的单个标准精度。详细信息：[使用货币字段](types-of-fields.md#using-currency-fields)|
|**十进制数**| 最多 10 位精确的十进制值。 详细信息：[使用恰当的数值类型](types-of-fields.md#using-the-right-type-of-number)|
|**浮点数**|最多 5 位精确的浮点数。 详细信息：[使用恰当的数值类型](types-of-fields.md#using-the-right-type-of-number)|
|**图像**|在应用程序中显示每个记录的单个图像。 每个实体可以有一个图像字段。 在创建图像字段时输入的**名称**将被忽略。 图像字段始终名为 'EntityImage'。|
|**多选选项集**|显示可以多选的选项列表。|
|<a name="multi-line-field"></a> **多行文本**|要在多行文本框中显示的文本值。 限制为最多 1,048,576 个字符。 您也可以设置更低的[最大长度](#max-length)。 |
|**选项集**|显示只能单选的选项列表。|
|**两个选项**|显示只能单选的两个选项。 选择为每个选项显示的标签。 默认值为**是**和**否**。|

## <a name="save-new-field"></a>保存新字段

一旦您设置了**显示名称**、**名称**和**数据类型**属性，您可以单击**完成**关闭**字段属性**面板。 

您可以继续编辑实体并添加其他字段，或返回继续编辑该字段。 在单击**保存实体**将所做的全部更改保存到实体前，字段不会创建。

![保存实体按钮](media/save-entity-button.png)

您还可以单击**放弃**放弃所做的更改。
 
## <a name="edit-a-field"></a>编辑字段

在查看字段时，选择要编辑的字段。 您可以修改**显示名称**，但如果已保存了对实体的更改以添加字段，则无法更改**名称**和**数据类型**。

### <a name="general-properties"></a>常规属性
每个字段都具有可以更改的以下属性：

|属性|说明|
|--|--|
|**必填**|如果选择此项，当字段中无数据时将无法保存记录。|
|**可搜索**|取消选择您不使用的实体的字段的此项。  可搜索的字段会出现在**高级查找**中，并且可在自定义视图时使用该字段。 取消选择此设置将减少向使用高级查找的用户显示的选项数量。|
|**说明**|在**高级选项**中找到。 为用户输入有关字段用途的说明。 当用户将鼠标悬停在字段的标签上时，这些描述在模型驱动应用程序中显示为用户的工具提示。|

> [!NOTE]
> **将字段设置为必填字段**：在将字段设置为必填字段时应谨慎小心。 如果用户由于缺乏要输入到必需字段中的正确信息而无法保存记录，将抗拒使用应用程序。 用户可能会简单地输入不正确的数据以保存记录，然后继续其工作。
>
>**动态设置要求**：在模型驱动应用程序中，当记录中的数据由于用户处理而发生变化时，您可以使用业务规则或窗体脚本来更改要求级别。 详细信息：[创建业务规则和建议以在窗体中应用逻辑](../model-driven-apps/create-business-rules-recommendations-apply-logic-form.md)
>
>**高级查找的可用性**：“高级查找”当前仅可用于使用 Web 客户端的模型驱动应用程序。 “高级查找”当前不可用于统一接口客户端。

## <a name="calculated-or-rollup"></a>“计算”或“汇总”

您可以将自定义字段设置为**计算**或**汇总**字段。 不是计算字段或汇总字段的字段有时称为*简单*字段。

### <a name="calculated"></a>计算

使用计算字段，您可以输入公式来向字段分配值。 这些数据类型可以设置为计算字段：**货币**、**日期和时间**、**仅限日期**、**十进制数**、**持续时间**、**电子邮件**、**语言**、**多选选项集**、**选项集**、**文本**、**文本区域**、**股票代号**、**时区**、**两个选项**、**URL** 和**整数**。

详细信息：[定义计算字段以自动化手动计算](define-calculated-fields.md)

### <a name="rollup"></a>Rollup

使用汇总字段，您可以设置将定期运行的聚合函数来为字段设置数字值。 这些数据类型可以设置为计算字段：**货币**、**日期和时间**、**仅限日期**、**十进制数**、**持续时间**、**语言**、**时区**和**整数**。

详细信息：[定义用于聚合值的汇总字段](define-rollup-fields.md)

## <a name="number-field-options"></a>数值字段选项

每个数字字段类型都有最小和最大绝对值。 您可以在这些绝对值中设置合适的**最大值**和**最小值**。 执行此操作使用面向应用程序的 CDS 验证要存储在字段中的数据的值。

对于**浮点数**和**十进制数**数据类型，您可以指定多个**小数位数**。


## <a name="option-set-field-options"></a>选项集字段选项

提供一组选项的字段可以包含其自己的一组*本地*选项，或引用一组可由多个字段使用的通用*全局*选项。

当您发现自己在为多个字段创建一组相同的选项时，使用全局选项集非常重要。 通过全局选项集，您只需要在一个位置维护一组选项。 

如果选择**多选选项集**或**选项集**数据类型，设计器将列出可供您从中选择的一组可用全局选项集，并提供创建**新选项集**的选项。

![选择选项集类型](media/option-set-options.png)

如果选择**新建选项集**，默认行为是创建新的全局选项集。

> [!NOTE]
> 在您编辑新全局选项集的选项时，**显示名称**和**名称**值针对全局选项集而不是字段。 默认值与字段值匹配，但您可以在编辑全局选项集以使其不同于当前创建的字段时对它们进行编辑。

如果要创建本地选项集，您必须单击**查看更多**并选择**本地选项集**。

![本地选项集](media/local-option-set.png)

> [!NOTE]
> 如果您将每个选项集定义为全局选项集，您的全局选项集列表将增大并可能很难管理。 如果您知道这组选项只会在一个位置使用，请使用本地选项集。

[!INCLUDE [cc_remove-option-warning](../../includes/cc_remove-option-warning.md)]

## <a name="delete-a-field"></a>删除字段

具有系统管理员安全角色，您可以删除不属于托管解决方案的任何自定义字段。 删除字段时，字段中存储的所有数据都将丢失。 从删除的字段中恢复数据的唯一方式是从删除字段前的某个点恢复数据库。

> [!NOTE]
> 在删除自定义字段之前，必须删除其他解决方案组件中可能存在的所有依赖项。 

在[查看字段](#view-fields)时，如果您选择可以从列表中删除的自定义字段，**删除字段**命令将显示并启用。

![使用门户删除字段](media/delete-field-portal.png)

使用**删除字段**命令删除字段。 在删除字段后，必须保存对实体所做的更改。

![在删除字段后保存实体](media/delete-field-portal-save-entity.png)

> [!NOTE]
> 如果您收到与依赖项相关的错误，则必须使用解决方案资源管理器检测依赖项。 详细信息：[检查字段依赖性](create-edit-field-solution-explorer.md#check-field-dependencies)

## <a name="ime-mode"></a>IME 模式

提供直接文本输入的任何字段都有一个 IME 模式。 输入法编辑器 (IME) 用于东亚语言（如日语）。 用户可以使用 IME，通过标准的 101 键键盘输入东亚书面语中使用的数千个不同字符。



### <a name="see-also"></a>另请参阅  
[创建和编辑面向应用程序的 Common Data Service 的字段](create-edit-fields.md)<br />
[使用 PowerApps 解决方案资源管理器创建和编辑面向应用程序的 Common Data Service 的字段](create-edit-field-solution-explorer.md)<br />
[字段类型和字段数据类型](types-of-fields.md)<br />
[定义计算字段以自动化手动计算](define-calculated-fields.md)<br />
[定义用于聚合值的汇总字段](define-rollup-fields.md)<br />
[行为和日期及时间字段的格式](behavior-format-date-time-field.md)