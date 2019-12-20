---
title: 在 Power Apps 中定义计算字段 | MicrosoftDocs
description: 了解如何定义计算字段
ms.custom: ''
ms.date: 05/25/2018
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
ms.assetid: 6d58a297-2ddf-4236-be3a-47249b49d5fa
caps.latest.revision: 67
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 82bf8cad9b64f9866cb1cc856eff94eacf1f23a2
ms.sourcegitcommit: 861ba8e719fa16899d14e4a628f9087b47206993
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "2873890"
---
# <a name="define-calculated-fields-to-automate-manual-calculations"></a>定义计算字段以自动化手动计算

使用计算字段将您业务流程中使用的手动计算自动化。 

例如，推销员可能想知道商机的加权收入，这基于商机与概率乘积得到的预计收入。 或者，如果订单大于 500 美元，他们想要自动使用一个折扣。 计算字段可以包含简单数学运算或条件运算（如大于或 if - else 等）产生的值。 您可以使用 Power Apps 完成这些操作，并且不需要编写代码。  
  
## <a name="capabilities"></a>功能
  
- 计算字段使用来自于当前实体或相关父实体的字段。  
- 在**条件**部分和**操作**部分的当前实体和相关父实体字段上表达式支持可用。 内置函数包括：  
 **ADDHOURS**、**ADDDAYS**、**ADDWEEKS**、**ADDMONTHS**、**ADDYEARS**、**SUBTRACTHOURS**、 **SUBTRACTDAYS**、**SUBTRACTWEEKS**、**SUBTRACTMONTHS**、**SUBTRACTYEARS**、**DIFFINDAYS**、 **DIFFINHOURS**、**DIFFINMINUTES**、**DIFFINMONTHS**、**DIFFINWEEKS**、**DIFFINYEARS**、**CONCAT**、**TRIMLEFT** 和 **TRIMRIGHT**。  
- 丰富的条件支持提供分支和多个条件。 逻辑操作包括 **AND** 和 **OR** 运算符。  
- 在**操作**部分，可视编辑功能包括现代 UI 和 intellisense。 
- 计算字段与窗体、视图、图表和报表的无缝集成是实时的。  
- 您可以配置计算字段来使用自定义控件。  
  
  
## <a name="scenarios"></a>情形
  
- **加权收入**：预计收入乘以概率  
- **净值**：资产减去给定客户的负债  
- **劳动力成本**：保证工资达 40 个小时，加上额外的加班  
- **联系电话**：基于客户或联系人的商机电话号码  
- **潜在顾客评分**：提供对给定潜在顾客质量见解的单一字段  
- **跟进**：通过基于优先级的指定天数跟进活动  
  
> [!IMPORTANT]
>  若要创建一个计算字段，必须对[字段安全配置文件实体](/powerapps/developer/common-data-service/reference/entities/fieldsecurityprofile)有写入特权。 如果计算字段在计算中使用安全字段，应该考虑保护计算字段，以防止没有足够权限的用户访问数据。 如果正在创建在计算中使用安全字段的计算字段，计算字段编辑器将给您一个警告并建议您保护计算字段。 详细信息：[用于控制访问的字段级安全性](/dynamics365/customer-engagement/admin/field-level-security)  

## <a name="create-a-calculated-field"></a>创建计算字段

使用字段编辑器指定计算字段。 在此示例中，我们将使用 [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)，不过步骤类似于使用解决方案资源管理器。 详细信息：[创建和编辑字段](create-edit-fields.md)
  
1. 打开 [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)
1. 展开**数据** > **实体**。  
1. 选择所需实体并选择**字段**。 选择**添加字段**。  
1. 为字段提供所需的信息，包括**显示名称**、**名称**和**数据类型**。 
1. 如果数据类型是支持计算字段的类型之一，您可以通过选择**添加** > **计算**来将字段设置为计算字段。

    ![将字段设置为计算字段](media/make-field-calculated-maker.png)

    以下是支持计算的字段类型：
    - 文本
    - 选项集  
    - 两个选项  
    - 整数  
    - 十进制数  
    - 货币  
    - 日期时间

1. 选择**计算**需要将所做的更改保存到实体。 单击**待定更改**对话框中的**保存**以继续。
1. 这将打开计算字段定义编辑器，在这里新的计算字段已创建，但未设置公式。 计算字段定义包括两个部分:**条件**和**操作**。  
  ![新建字段计算窗体](media/empty-field-calculation.png)
- 在**条件**部分中，您可以指定一个实体、字段、运算符、类型和值。 在**实体**的下拉框中，您可以选择当前实体或相关实体。 在**字段**下拉框中，您可以选择实体所有可用字段。 根据所选运算符，您可能需要提供类型和值。 您可以使用 `AND` 或 `OR` 运算符指定多个条件。  
- 在**操作**部分中,您可以提供计算字段的公式。  
  
> [!NOTE]
>  在您的“操作”内，您可以使用查找记录中的数据。 您必须首先选择“查找”字段，然后输入一个期间。 之后，您可以选择可用于相关实体中的相应字段。 例如，如果是 *`<LookupFieldName>.<RelatedFieldName>`*，可以选择：`ParentAccountId.AccountNumber`。  
>   
>  注意，如果已访问字段中包含敏感数据，字段级别的安全性将会在相关实体中被忽略，因此，我们还建议您保护计算字段。  


<a name="BusinessScenarios"></a> 
  
## <a name="examples"></a>示例  

我们更详细地看一下计算字段示例。 
  
### <a name="weighted-revenue-of-opportunity"></a>商机的加权收入

在此示例中，我们使用商机实体的字段根据商机概率来计算加权收益。 在商机实体的字段编辑器中，我们创建一个名为**加权收入**的字段并指定字段类型为**计算**和数据类型为**货币**。

在计算字段定义编辑器中的**条件**部分，我们指定商机状态 = 打开。 在**操作**中，根据商机预计收入与商机概率乘积公式来计算加权收入。  以下屏幕截图显示如何分步定义**加权收益**计算字段。  
  
#### <a name="set-the-condition-on-the-opportunities"></a>设置商机条件：
  
![在 Dynamics 365 中设置加权收入](media/calc-field-open-opportunity.png)  
  
#### <a name="provide-the-formula-for-the-weighted-revenue"></a>提供加权收入公式： 
  
![在 Dynamics 365 中设置加权收入预计值](media/calc-field-open-opportunities-3.png)  
  
#### <a name="altogether"></a>总共：
  
![Dynamics CRM 中的 Dynamics 365 中的收入](media/calculated-field-open-opportunity.png)  
  
### <a name="follow-up-date-of-opportunity"></a>跟进商机日期 
 
在此示例中，当跟进商机时，我们使用商机最初潜在顾客字段来计算合适的日期。 

在商机实体字段编辑器中，我们创建一个名为**跟进日期**的字段并指定类型为**计算**和数据类型为**日期和时间**。  

在计算字段定义编辑器的**条件**部分，我们指定两个条件：潜在顾客的购买期限和估计值。 

在**操作**中，我们提供两个公式：
 - 对眼前的商机跟进一周
 - 对不可能立刻出现的商机跟进一个月。 

以下屏幕截图显示如何分步定义**跟进日期**计算字段。  
  
#### <a name="set-the-two-conditions-on-the-originating-lead"></a>设置最初潜在顾客的两个条件：
  
![在 Dynamics 365 中跟进商机的日期](media/calc-field-follow-update-2.PNG)  
  
![在 Dynamics 365 中跟进商机的日期](media/calc-field-follow-update-3.PNG)  
  
#### <a name="provide-the-formula-to-follow-up-in-one-week"></a>提供跟进一周的公式：
  
![在 Dynamics 365 中跟进商机的日期](media/calc-field-follow-update-4.PNG)  
  
#### <a name="provide-the-formula-to-follow-up-in-one-month"></a>提供跟进一月的公式：
  
![在 Dynamics 365 中设置跟进日期](media/calc-field-follow-update-5.PNG)  
  
#### <a name="altogether"></a>总共：
  
 ![在 Dynamics 365 中设置跟进日期 If-Then 和 Else](media/calc-field-follow-update-6.PNG)  
  
### <a name="days-from-a-record-creation"></a>记录创建的天数 
 
在此示例中，我们使用**DIFFINDAYS** 函数计算从记录创建到现在的天数差。 

创建名为**计算天数差**的新整数字段。
  
#### <a name="provide-the-formula-for-computing-the-difference-in-days"></a>提供计算天数差的公式
  
![计算字段，DIFFINDAYS 函数](media/custom-calc-field-diff-days.png)  
  
#### <a name="altogether"></a>总共：
  
![创建记录后相差的天数](media/calc-field-diff-days-complete.png)  
  
<a name="Syntax"></a> 
  
## <a name="functions-syntax"></a>函数语法  

以下表包含计算字段的**操作**部分所提供的函数的语法的信息。  
  
> [!TIP]
>  将函数名称指定为大写字母。  
  
|函数语法|说明|返回类型|  
|---------------------|-----------------|-----------------|  
|**ADDDAYS**（整数、日期和时间）|返回与给定日期和时间等同的新日期和时间，以及指定的天数。|日期和时间|  
|**ADDHOURS**（整数、日期和时间）|返回与给定日期和时间等同的新日期和时间，以及指定的小时数。|日期和时间|  
|**ADDMONTHS**（整数、日期和时间）|返回与给定日期和时间等同的新日期和时间，以及指定的月数。|日期和时间|  
|**ADDWEEKS**（整数、日期和时间）|返回与给定日期和时间等同的新日期和时间，以及指定的周数。|日期和时间|  
|**ADDYEARS**（整数、日期和时间）|返回与给定日期和时间等同的新日期和时间，以及指定的年数。|日期和时间|  
|**SUBTRACTDAYS**（整数、日期和时间）|返回与给定日期和时间等同的新日期和时间，减去指定的天数。|日期和时间|  
|**SUBTRACTHOURS**（整数、日期和时间）|返回与给定日期和时间等同的新日期和时间，减去指定的小时数。|日期和时间|  
|**SUBTRACTMONTHS**（整数、日期和时间）|返回与给定日期和时间等同的新日期和时间，减去指定的月数。|日期和时间|  
|**SUBTRACTWEEKS**（整数、日期和时间）|返回与给定日期和时间等同的新日期和时间，减去指定的周数。|日期和时间|  
|**SUBTRACTYEARS**（整数、日期和时间）|返回与给定日期和时间等同的新日期和时间，减去指定的年数。|日期和时间|  
|**DIFFINDAYS**（日期和时间，日期和时间）|返回两个**日期和时间**字段之间的天数差。 如果两个日期和时间为同一天，此差为零。|整数|  
|**DIFFINHOURS**（日期和时间，日期和时间）|返回两个**日期和时间**字段之间的小时差。|整数|  
|**DIFFINMINUTES**（日期和时间，日期和时间）|返回两个**日期和时间**字段之间的分钟差。|整数|  
|**DIFFINMONTHS**（日期和时间，日期和时间）|返回两个**日期和时间**字段之间的月数差。 如果两个日期和时间为同一个月，此差为零。|整数|  
|**DIFFINWEEKS**（日期和时间，日期和时间）|返回两个**日期和时间**字段之间的周数差。 如果两个日期和时间为同一周，此差为零。|整数|  
|**DIFFINYEARS**（日期和时间，日期和时间）|返回两个**日期和时间**字段之间的年数差。 如果两个日期和时间为同一年，此差为零。|整数|  
|**CONCAT**（单行文本，单行文本… 单行文本）|返回连接两个或多个字符串结果的字符串。|字符串|  
|**TRIMLEFT**（单行文本、整数）|返回包含一个含指定字符串，但第一字符不是 N 的字符串。|字符串|  
|**TRIMRIGHT**（单行文本、整数）|返回一个包含指定字符串，但最后一个字符不是 N 的字符串。|字符串|  
  
> [!NOTE]
>  所有 DIFF 都函数需要第一个**日期和时间**字段和第二个**日期和时间**字段具有相同的行为：**用户当地时间**、**仅限日期**或**时区无关时区独立**。 如果第二个字段的行为不与第一个字段的行为匹配，错误消息将显示，指示第二个字段不能在当前函数中使用。 详细信息：[日期及时间字段的行为和格式](behavior-format-date-time-field.md)。  
  
> [!NOTE]
>  不能输入日期作为计算字段的日期值，例如 01/01/2015。 只能使用其他“日期时间”字段设置或比较日期和日期时间值。  
  
在**CONCAT**函数中，可将文字字符串用作单行文本、包含单行文本的实体字段或者两者的组合。 例如：**CONCAT**（FirstName 或 LastName“是经理。”）。 如果文字字符串包含引号，请在前面每个引号前面加上反斜线 (\\) 转义字符，例如：`This string contains the \"quotation marks.\"` 这可以确保字符串中的引号不被看作分隔字符串的特殊字符。  
  
以下示例显示如何使用**TRIMLEFT**和**TRIMRIGHT**函数： 他们包含由**TRIMLEFT**和**TRIMRIGHT**函数返回的初始字符串和结果字符串：  
  
**TRIMLEFT**（"RXX10-3456789"，3），返回字符串 `10-3456789`    
**TRIMRIGHT**（"20-3456789RXX"，3），返回字符串 `20-3456789` 
  
<a name="Considerations"></a> 
  
## <a name="considerations"></a>注意事项 
 
在使用计算字段时，您应了解的某些条件和限制：  
  
- 保存的查询、图表和可视化最多可以有 10 个唯一的计算字段。  
- 在 Outlook 客户端脱机模式中，视图或实体主窗体中不显示计算字段的值。  
- 链接的计算字段的最大数量是 5。  
- 计算字段无法引用本身或具有循环链。  
- 如果您在多个条件条款中更改一个条件运算符，所有条件操作符将更新至该条件。 例如，在从句 `IF (x > 50) OR (y ==10) OR (z < 5)` 中,如果您将 `OR` 运算符更改为 `AND` 运算符，那么从句中的所有 `OR` 运算符将变为 `AND` 运算符。  
- 您可以通过查找父实体的字段来访问父级字段，如 *`<LookupFieldName>.<FieldName>`*。 多实体查找字段（如客户，可以是客户或联系人）无法执行此操作。 但是，一些实体有特定实体的单个查找字段，如`ParentAccountid.`*`<FieldName>`* 或`ParentContactid.`*`<FieldName>`*。  
- 以下情况禁用排序：  
  - 包含父记录字段的计算字段。  
  - 计算字段包含一个逻辑字段（如地址字段）
  - 计算字段包含其他计算字段。  
- 计算字段只可以跨两个实体。  
  - 计算字段可以包含其他实体的字段（跨两个实体 – 当前实体和父记录）。  
  - 计算字段不能包含其他实体（此实体还包含另一实体的其他字段）（跨三个实体）：   
    （当前实体）计算字段 &larr; （父记录）计算字段 1 &larr;（父记录）计算字段 2。  
- 您无法触发计算字段上的工作流或插件。  
- 您无法将现有简单字段更改为计算字段。 如果您的当前应用程序正在使用 JavaScript 或插件来计算字段，且未创建新字段，则您无法使用计算字段功能。  
- 未对计算字段触发重复检测规则。  
- 汇总无法引用使用其他计算字段的计算字段，即使其他计算字段的所有字段在当前实体中。  
  
### <a name="see-also"></a>另请参阅
 
[创建和编辑字段](create-edit-fields.md)<br />
[定义用于聚合值的汇总字段](define-rollup-fields.md)<br />
[视频：汇总字段和计算字段](https://go.microsoft.com/fwlink/p/?LinkId=517727)
