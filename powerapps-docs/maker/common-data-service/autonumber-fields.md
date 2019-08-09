---
title: Common Data Service 中的自动编号字段 | MicrosoftDocs
description: 了解如何创建、管理和使用自动编号字段
keywords: ''
ms.date: 02/26/2019
ms.service: powerapps
ms.custom: null
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
author: daemelia
ms.assetid: null
ms.author: daemelia
manager: kvivek
ms.reviewer: Mattp123
ms.suite: null
ms.tgt_pltfrm: null
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="autonumber-fields"></a>自动编号字段

自动编号字段是在创建时即自动生成字母数字字符串的字段。 制造商可以按其偏好自定义这些字段的格式，然后依靠系统在运行时生成自动填充它们的匹配值。

虽然自动编号字段形式上只是文本字段，具有在其基础上构建的额外功能，而 [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) 通过在**文本**类别下将**自动编号**呈现为不同的数据类型来简化了这个概念。 务必注意，[经典解决方案资源管理器](use-solution-explorer.md#classic-solution-explorer)不支持创建或管理自动编号字段。

若要创建自动编号字段，请遵循用于[创建字段](create-edit-field-portal.md#create-a-field)的相同步骤，只需从**数据类型**下拉列表框中选择**自动编号**。 

您还可以激活现有文本字段的自动编号功能，方法是打开字段并从**数据类型**下拉列表框中选择**自动编号**。 同样，自动编号功能也可以随时禁用，方法是打开字段并在**数据类型**下拉列表框中选择其他选项。

## <a name="autonumber-types"></a>自动编号类型

为了使自动编号字段的创建更简单，有一些预定义的默认自动编号类型，其可以覆盖最常见的场景。 

### <a name="string-prefixed-number"></a>字符串前缀编号

最常见的自动编号格式是简单的字符串前缀编号。 如果选择此类型，自动编号将包含自动递增的数字，具有可选的字符串常量前缀。 例如，带有前缀 *Contoso* 的字符串前缀编号会生成诸如 *Contoso-1000*、*Contoso-1001*、*Contoso-1002* 等记录。

### <a name="date-prefixed-number"></a>日期前缀编号

另一个常见的自动编号格式为日期前缀编号。 如果选择此类型，自动编号将包含自动递增的数字，具有确定格式的日期前缀。 记录的日期部分将反映以 UTC 时间创建记录的当前日期和时间。 我们提供了很多可供选择的不同日期格式。
例如，根据当前的日期和选定的日期格式，日期前缀编号会生成诸如 *2019-26-02-1000*、*2019-27-02-1000*、*2019-28-02-1000* 等记录。

### <a name="custom"></a>自定义

对于具有特定使用案例的更高级的制造商，我们提供了可完全自定义所需的自动编号字段格式的选项。 格式可能包括字符串常量、自动递增数字、确定格式的日期格或随机的字母数字序列。
有关如何定义自定义格式的详细信息，请参阅 [AutoNumberFormat 选项](https://docs.microsoft.com/dynamics365/customer-engagement/developer/create-auto-number-attributes#autonumberformat-options)。

## <a name="seed-values"></a>种子值

自动编号字段的种子值是用于格式的数字部分的起始数字。 例如，如果您希望自动编号字段生成 *Contoso-1000*、*Contoso-1001*、*Contoso-1002* 等记录，那么所需的种子值为 1000，因为这是数字序列的起始值。 自动编号字段具有默认的种子值 1000，不过如果需要，您可以设置自定义种子值。 


> [!IMPORTANT]
> 设置种子仅更改当前环境中指定属性的当前数字值。 在导入不同环境时，种子值不包含在解决方案中。 

## <a name="create-an-autonumber-field"></a>创建自动编号字段
  
1.  登录 [PowerApps 门户](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。
  
2.  在左侧窗格上，展开**数据**，然后选择**实体**。
  
3.  选择要向其添加自动编号字段的实体，然后选择**字段**选项卡。
  
4.  在工具栏上，选择**添加**字段。  
  
5.  在右侧窗格中，输入**显示名称**并为**数据类型**选择**自动编号**。

    > [!div class="mx-imgBorder"] 
    > ![](media/create-autonumber-field.png "创建自动编号字段")
  
6. 根据需要设置可选字段。 更多信息：[创建和编辑字段](create-edit-field-portal.md#create-a-field)

7. 选择自动编号类型或保留默认的**字符串前缀编号**选项。

8. 自定义种子值或保留默认值 **1000**。

9. 选择**无**。

## <a name="see-also"></a>另请参阅
 [使用 PowerApps 门户创建和编辑 Common Data Service 的字段](create-edit-field-portal.md)
