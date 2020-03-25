---
title: Common Data Service 中的字段数据类型 | MicrosoftDocs
description: 了解可用于您的应用的不同字段数据类型
keywords: ''
ms.date: 09/30/2019
ms.service: powerapps
ms.custom: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: 734b4ffa-5543-4f88-8517-299589f433f7
ms.author: matp
manager: kvivek
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 2b54cad59b1f5a6cc4199675308f5cd48d05240d
ms.sourcegitcommit: 629e47c769172e312ae07cb29e66fba8b4f03efc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "3108045"
---
# <a name="types-of-fields"></a>字段类型

用于类型的名称取决于所使用的设计器。 [Power Apps 门户](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)使用包括数据格式确定方式的约定。 解决方案资源管理器类型使用与具有格式修饰符的数据库数据类型一致的名称。 下表包含对应的 `AttributeTypeDisplayName` API 类型。

|门户数据类型 |解决方案资源管理器类型| API 类型|
|--|--|--|
|**大整数**|**时间戳**|`BigIntType`|
|**货币**|**货币**|`MoneyType`|
|**客户**|**客户**|`CustomerType`|
|**日期和时间**|**日期和时间**<br />*日期和时间*格式|`DateTimeType`|
|**仅限日期**|**日期和时间**<br />*仅限日期*格式|`DateTimeType`|
|**十进制数**|**十进制数**|`DecimalType`|
|**持续时间**|**整数**<br />*持续时间*格式|`IntegerType`|
|**Email**|**单行文本**<br />*电子邮件*格式|`StringType`|
|**文件** | **文件**   | `FileType`  |
|**浮点数**|**浮点数**|`DoubleType`|
|**图像**|**图像**|`ImageType`|
|**语言**|**整数**<br />*语言*格式|`IntegerType`|
|**查找**|**查找**|`LookupType`|
|**多选选项集**|**多选选项集**|`MultiSelectPicklistType`|
|**多行文本**|**多行文本**|`MemoType`|
|**选项集**|**选项集**|`PicklistType`|
|**负责人**|**负责人**|`OwnerType`|
|**电话**|**单行文本**<br />*电话*格式|`StringType`|
|**状态描述**|**状态描述**|`StatusType`|
|**状态**|**状态**|`StateType`|
|**文本区域**|**单行文本**<br />*文本区域*格式|`StringType`|
|**文本**|**单行文本**<br />*文本*格式|`StringType`|
|**股票代号**|**单行文本**<br />股票代号格式|`StringType`|
|**时区**|**整数**<br />*时区*格式|`IntegerType`|
|**两个选项**|**两个选项**|`BooleanType`|
|**唯一标识符**|**唯一标识符**或**主键**|`UniqueidentifierType`|
|**URL**|**单行文本**<br />*URL* 格式|`StringType`|
|**整数**|**整数**<br />*无*格式|`IntegerType`|

要查看您可以添加或编辑的每个类型的更多描述，请参阅相应设计器的主题：
 - [使用 Power Apps 门户创建和编辑 Common Data Service 的字段：字段数据类型](create-edit-field-portal.md#field-data-types)
 - [使用 Power Apps 解决方案资源管理器创建和编辑 Common Data Service 的字段：字段数据类型](create-edit-field-solution-explorer.md#field-data-types)

有关如何在 API 中定义字段数据类型的详细信息，请参阅[属性元数据](/powerapps/developer/common-data-service/entity-attribute-metadata)

## <a name="field-types-used-by-the-system"></a>系统使用的字段类型

有些系统使用的字段无法使用设计器添加。

|类型 |说明|
|--|--|
|**大整数**或**时间戳**|系统用来获取版本号以管理实体的更新。|
|**客户**|您可以使用查找字段指定客户，可以是客户或联系人。<br />**注意**：可以使用解决方案资源管理器设计器添加此属性。|
|**负责人**|引用分派有用户或团队负责的实体记录的用户或团队折系统查找字段。|
|**状态描述**|具有可以提供有关状态字段的其他详细信息的选项的系统字段。 每个选项与其中一个可用的状态选项关联。 您可以添加和编辑选项。 <br /><br /> 您还可以包含自定义状态转换来控制哪些状态选项可用于某些实体。 详细信息：[为自定义实体定义状态原因转换](define-status-reason-transitions.md)|
|**状态**|具有通常对应于活动和非活动状态的选项的系统字段。 有些系统属性有其他选项，但所有自定义属性只有**活动**和**非活动**状态选项。  |
|**唯一标识符**|系统字段存储每个记录的全局唯一标识符 (GUID) 值。|

  
## <a name="multiselect-option-set"></a>多选选项集

可通过添加多选字段来自定义窗体（主、快速创建和快速查看）和电子邮件模板。 在添加“多选选项集”字段后，您可以指定多个可供用户选择的值。 用户填充窗体时，可选择下拉列表中显示的一个、多个或所有值。

例如，如果组织在多个区域或国家或地区运营，则可在“运营区域”字段中包括多个位置或国家或地区。 然后，用户可以从可用值列表中选择一个或多个位置。

多选选项集仅在只读网格、可编辑网格和窗体中才可用。 多选选项集在下面不受支持： 
- “工作流”、“操作”、“对话”、“汇总”、“图表”和“计算”字段。
- 报表、SLA 和传递规则。

多选字段在以下窗体类型中受支持：

|窗体类型|可用性|
|--|--|
|**Turbo 窗体**|是|
|**刷新窗体**|只读（窗体可用，但不可编辑）|
|**旧窗体**|No|
|**批量编辑窗体**|No|

可使用组织中定义的全局选项集为多选选项集配置值。


<a name="BKMK_UsingTheRightTypeOfNumber"></a>
  
## <a name="using-the-right-type-of-number"></a>使用恰当的数值类型

在选择要使用的正确数值字段类型时，选择使用**整数**或**货币**类型应该相当简单易懂。 选择**浮点**还是**小数**数值则要求更多思考。  
  
小数数值完全按指定样子存储在数据库中。 浮点数值存储极其接近值的近似值。 当可以准确的值时，为什么要选择极其接近的近似值？ 答案是可以获得不同的系统性能。  
  
如果需要提供的报告要求非常精确的计算结果时，或者只是使用查询来查找等于或不等于另一个值的值，可使用小数。  
  
如果存储代表分数的数据，或者只是使用查询来比较大于或小于另一个值的值，可使用浮点数值。 大多数情况下，小数与浮点之间的差异并不明显。 除非需要尽可能准确的计算结果，浮点数值应该就适合您。  
  
<a name="BKMK_UsingCurrencyFields"></a>
 
## <a name="using-currency-fields"></a>使用货币字段

货币字段允许组织配置可用于组织中记录的多种货币。 当组织有多种货币时，通常需要能够执行计算来提供采用其基础货币的值。 向没有其他货币字段的实体中添加货币字段时，会添加两个额外字段：  
  
- 一个称为**货币**的查找字段，可将其设置为为组织配置的任何活动货币。 可以在**设置** > **业务管理** > **货币**中为组织配置多个活动货币。 可在此处为组织指定货币以及与基础货币的汇率。 如果您有多个活动货币，则可将货币字段添加到窗体中，并允许用户指定仅将哪种货币应用于此字段的货币值。 这将更改为窗体中的货币字段显示的货币符号。  
  
  个人也可以更改其个人选项，为其创建的记录选择默认货币。
  
- 名为**汇率**的小数字段，提供选择的与实体关联的货币相对于基础货币的汇率。 如果将该字段添加到窗体，用户能看到值，但不能编辑值。 汇率与货币一起存储。  
  
对于添加的每个货币字段，会添加另一个名称带后缀 `_Base` 的货币字段。 此字段存储您添加的货币字段值的计算结果和基础货币。 同样，如果将该字段添加到窗体，将无法对其编辑。  
  
在配置货币字段时，可以选择精度值。 如下表所示，有三个选项。  
  
|选项|说明|  
|------------|-----------------|  
|定价小数精度|这是一个单组织精度，用于在**设置** > **管理** > **系统设置** > **常规**选项卡中的价格。|  
|货币精度|此选项应用为记录中的货币定义的精度。|  
|特定精度值|这些设置允许使用从 0 到 4 的值定义特定的设置精度。|  
  
<a name="BKMK_DifferentTypesOfLookups"></a> 
  
## <a name="different-types-of-lookups"></a>不同类型的查找  

在创建新的查找字段时，要在正在处理的实体与为查找定义的**目标记录类型**之间创建一个新的多对一 (N: 1) 实体关系。 此关系还有在[创建和编辑实体之间的关系](create-edit-entity-relationships.md)中介绍的其他配置选项。 但是，所有自定义查找仅可用于引用单个目标记录类型的单个记录。  
  
但是，您应该知道，并非每个查找的行为都采用这种方式。 有多种不同类型的系统查找，如下所示。  
  
|查找类型|说明|  
|-----------------|-----------------|  
|**简单**|允许对特定实体的单个引用。 所有自定义查找都是此类型。|  
|**客户**|允许对客户或联系人记录的单个引用。|  
|**负责人**|允许对团队或用户记录的单个引用。 所有团队或用户负责的实体具有其中之一。 详细信息：[添加团队实体充当应用程序中的查找选项](../model-driven-apps/team-entity-lookup.md)|  
|**PartyList**|允许对多个实体的多个引用。 这些查找在“电子邮件”实体**收件人**和**抄送**字段中。 在“电话”和“约会”实体中也使用它们。|  
|**相关**|允许对多个实体的单个引用。 这些查找在活动中使用的相关字段中。|  

<a name="BKMK_ImageFields"></a>

## <a name="image-fields"></a>图像字段  
使用图像字段可在应用程序中显示每个记录的单个图像。 每个实体可以有一个图像字段。 可以将图像字段添加到自定义实体，但不能添加到标准实体。 有些标准实体定义了图像字段。
  
即使实体有图像字段，在模型驱动应用程序中显示该图像还需要您启用两项设置。 
- 必须将标准实体定义**主要图像**属性设置为**默认图像**。 自定义实体需要自定义图像字段。 然后，可以在自定义实体定义中为**主要图像**值选择该图像字段。  
- 必须为要在其中显示该图像的实体窗体启用**在窗体中显示图像**属性。  
  
为实体启用图像显示时，没有图像的所有记录将显示占位符图像。 例如：

> [!div class="mx-imgBorder"] 
> ![默认实体图像](../common-data-service/media/account-record-default-image.png "默认客户实体图像")
  
用户可以选择默认图像从计算机上载图片。 图像必须小于 10 MB，并且必须采用以下格式之一：  
  
- jpg
- jpeg
- gif
- tif
- tiff
- bmp
- png
  
图像上载之后，将被转换为 .jpg 格式，并且所有下载的图像也将使用此格式。 如果上载了动画 .gif，则仅保存第一帧。  
  
图像上载后，将作为“缩略图”图像调整其大小，最大为 144 x 144 像素。 用户应在上载图像之前调整图像大小或裁剪图像，以便以此大小正确显示。 所有图像都裁剪成正方形。 如果图像的两边都小于 144 像素，则将使用较小边的尺寸裁剪成正方形。  

<!-- 
By default, when an app user adds an image to display to a form or canvas app, the image displayed is the thumbnail image. To display a full image for a canvas app, see [Display a full-sized image on a canvas app form](../canvas-apps/display-full-image-on-form.md).


### Add an image field to an entity using the Power Apps site

[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

1. Sign in to [Power Apps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).  
2.  Select **Data** > **Entities** and then select the entity where you want to add an image field. 
3. Select **Add field** on the command bar, enter the following properties, and then select **Done**: 
   - **Display name**. Enter a friendly name for the field. 
   - **Data type**. Select **Image**. 
   - **Primary image**. When selected, the primary image field becomes the image field for the entity. You can only have one primary image for each entity. 
   - **Maximum image size**. The maximum file size that an app user can upload to the record. 10,240 KB is the default maximum size and 10 MB is the maximum size limit. 
   - **Can store full images**. When selected, in addition to the rescaled thumbnail image described earlier, the full image is stored when uploaded by the user for each record. Full size images are limited to 30 MB.  -->

### <a name="add-image-support-for-a-form-in-a-custom-entity-using-solution-explorer"></a>使用解决方案资源管理器在自定义实体中为窗体添加图像支持
1. 打开[解决方案资源管理器](../model-driven-apps/advanced-navigation.md#solution-explorer)。 
2. 在左侧导航窗格中，展开**实体**，展开所需自定义实体，然后选择**字段**。 
3. 在工具栏上，选择**新建**。 
4. 在**类型**部分的**数据类型**下拉列表中选择**图像**。 
5. 输入**显示名称**，如*自定义实体名称*。 
6. 根据需要填写其余字段。 请注意，不能更改**名称**、**字段要求**和**可搜索**字段。 选择**保存并关闭**。 
7. 在**主要图像**属性旁边的视图定义中，确保值设置为您在上一步中创建的自定义图像。 如果未选择，请选择。  
    > [!div class="mx-imgBorder"] 
    > ![已选择主要图像属性](media/primary-image-property.png "已选择主要图像属性")

8.  打开需要图像支持的窗体，如实体主窗体。 
9.  在窗体编辑器功能区上，选择**窗体属性**。 
10. 在**窗体属性**页面中，选择**显示**选项卡，选择**在窗体中显示图像**，然后选择**确定**。 

    > [!div class="mx-imgBorder"] 
    > ![在窗体设置中显示图像](media/show-image-on-form.png "在窗体设置中显示图像")

11. 在窗体编辑器功能区上，选择**保存**，然后选择**发布**。 关闭窗体编辑器。 

应用程序用户现在可选择要在窗体中显示的图像。 当应用程序用户打开记录的窗体时，可以选择要在该窗体中显示的图像。 

> [!IMPORTANT]
> 如果记录是尚未保存的新记录，尝试更改图像时，将返回“参数无效”错误。 

### <a name="change-the-image-for-a-record"></a>更改记录的图像
在实体窗体具有图像字段后，应用用户可以更改给定记录的图像。 

1. 打开其中包含实体窗体的应用程序，然后在窗体中选择图像。 
   > [!div class="mx-imgBorder"] 
   > ![默认实体图像](../common-data-service/media/default-entity-image-on-form.png "默认实体图像")

2. 选择**上载图像**，浏览并选择要在实体窗体中显示的图像，然后选择**更改**。 将在记录中显示该图像。 
   > [!div class="mx-imgBorder"] 
   > ![更改后的图像已保存到记录](../common-data-service/media/custom-entity-icon-record.png "更改后的图像已保存到记录")


面向使用图像数据的开发人员的更多信息：
- [实体元数据 > 实体图像](/powerapps/developer/common-data-service/entity-metadata#entity-images)
- [图像属性](/powerapps/developer/common-data-service/image-attributes)


## <a name="file-fields"></a>文件字段
[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

当前，文件数据类型仅可用于画布应用和流。 

**文件**字段用于存储二进制数据。 此字段的主要用途是存储单个图像、注释或附件。 但是，也可以存储其他形式的二进制数据。 可以将此数据类型的一个或多个字段添加到现有的标准可自定义实体或自定义实体中。

默认**最大文件大小**为 32 MB，可以设置的最大大小为 128 MB。 可以为添加到实体的文件类型的每个字段分别设置文件大小限制。 

面向使用文件数据的开发人员的更多信息：[文件属性](/powerapps/developer/common-data-service/file-attributes)