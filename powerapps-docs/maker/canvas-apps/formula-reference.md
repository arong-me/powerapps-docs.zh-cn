---
title: 函数、信号和枚举 |Microsoft 文档
description: 有关 PowerApps 中的函数、信号和枚举的参考信息。
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 06/05/2018
ms.author: gregli
ms.openlocfilehash: b36510dc7c7dce9a0f49e4c3ab5e2e12cd15fa62
ms.sourcegitcommit: 0f6d7bb9e524202c065b9a7ef92a7f54bdc4bc7c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2018
ms.locfileid: "39018022"
---
# <a name="formula-reference-for-powerapps"></a>PowerApps 的公式参考
公式组合了许多元素。  下面列出的包括：

* **函数**，它接受参数、执行操作并返回值。 例如，**Sqrt(25)** 返回 **5**。 函数模仿了 Microsoft Excel 函数。  某些函数具有副作用，例如 **SubmitForm**，该函数仅在诸如 **Button.OnSelect** 的[行为公式](working-with-formulas-in-depth.md)中适用。
* **信号**，它返回关于环境的信息。 例如，**[Location](functions/signals.md)** 返回设备的当前 GPS 坐标。 信号不接受参数，也没有副作用。
* **枚举**，它返回预定义的常量值。 例如，**[Color](functions/function-colors.md)** 是一个具有预定义值 **Color.Red**、**Color.Blue** 等等的枚举。  此处包括了通用枚举；函数特定的枚举随函数进行了介绍。
* **已命名运算符**，例如 **[ThisItem](functions/operators.md#thisitem-operator)** 和 **[Parent](functions/operators.md#parent-operator)**，用于从容器内访问信息。

其他元素包括：

* [所有运算符](functions/operators.md)
* [控件及其属性](reference-properties.md)

## <a name="a"></a>A
**[Abs](functions/function-numericals.md)** – 数字的绝对值。  

**[Acceleration](functions/signals.md)** – 读取你的设备中的加速度传感器。

**[Acos](functions/function-trig.md)** – 以弧度为单位返回某个数字的反余弦值。

**[Acot](functions/function-trig.md)** – 以弧度为单位返回某个数字的反余切值。

**[AddColumns](functions/function-table-shaping.md)** – 返回添加了[列](working-with-tables.md#columns)的表。 

**[And](functions/function-logicals.md)** – 布尔逻辑与。  如果所有参数都为 **true**，则返回 **true**。  还可以使用 [**&&** 运算符](functions/operators.md)。

**[App](functions/signals.md)** – 返回有关当前正在运行的应用的信息，例如当前显示了哪个屏幕。

**[Asin](functions/function-trig.md)** – 以弧度为单位返回某个数字的反正弦值。

**[Atan](functions/function-trig.md)** – 以弧度为单位返回某个数字的反正切值。

**[Atan2](functions/function-trig.md)** – 基于 (*x*,*y*) 坐标以弧度为单位返回反正切。

**[Average](functions/function-aggregates.md)** – 计算某个表表达式或一组参数的平均值。

## <a name="b"></a>B
**[Back](functions/function-navigate.md)** – 显示上一屏幕。  

**[Blank](functions/function-isblank-isempty.md)** - 返回可用于在数据源中插入 NULL 值的 *空白* 值。

## <a name="c"></a>C
**[Calendar](functions/function-clock-calendar.md)** – 检索有关当前区域设置的日历信息。

**[Char](functions/function-char.md)** – 将字符代码转换为字符串。

**[Choices](functions/function-choices.md)** - 返回查找列可能值的表。

**[Clear](functions/function-clear-collect-clearcollect.md)** – 删除某个[集合](working-with-data-sources.md#collections)中的所有数据。

**[ClearCollect](functions/function-clear-collect-clearcollect.md)** – 删除某个集合中的所有数据，然后添加一组[记录](working-with-tables.md#records)。

**[Clock](functions/function-clock-calendar.md)** – 检索有关当前区域设置的时钟信息。

**[Coalesce](functions/function-isblank-isempty.md)** – 替换空值并保留非空值不变。

**[Collect](functions/function-clear-collect-clearcollect.md)** – 创建一个集合或者向数据源添加数据。

**[Color](functions/function-colors.md)** – 将某个属性设置为内置的颜色值。

**[ColorFade](functions/function-colors.md)** – 使颜色值变淡。

**[ColorValue](functions/function-colors.md)** – 将 CSS 颜色名称或十六进制代码转换为颜色值。  

**[Compass](functions/signals.md)** – 返回你的罗盘航向。

**[Concat](functions/function-concatenate.md)** – 连接数据源中的字符串。  

**[Concatenate](functions/function-concatenate.md)** – 连接字符串。

**[Concurrent](functions/function-concurrent.md)** - 并发计算多个公式。 

**[Connection](functions/signals.md)** – 返回关于你的网络连接的信息。

**[Count](functions/function-table-counts.md)** – 对包含数字的表记录进行计数。

**[Cos](functions/function-trig.md)** – 返回以弧度为单位指定的角度的余弦值。

**[Cot](functions/function-trig.md)** – 返回以弧度为单位指定的角度的余切值。

**[CountA](functions/function-table-counts.md)** – 对不为[空](functions/function-isblank-isempty.md)的表记录进行计数。

**[CountIf](functions/function-table-counts.md)** – 对满足某个条件的表记录进行计数。  

**[CountRows](functions/function-table-counts.md)** – 对表记录进行计数。   

## <a name="d"></a>D
**[DataSourceInfo](functions/function-datasourceinfo.md)** – 提供数据源的相关信息。

**[Date](functions/function-date-time.md)** – 基于**年**、**月**和**日**的值返回日期/时间值。  

**[DateAdd](functions/function-dateadd-datediff.md)** – 将天数、月数、季度数或年数加到某个日期/时间值上。

**[DateDiff](functions/function-dateadd-datediff.md)** – 将两个日期值相减，并显示以天数、月数、季度数或年数表示的结果。

**[DateTimeValue](functions/function-datevalue-timevalue.md)** – 将日期和时间字符串转换为日期/时间值。

**[DateValue](functions/function-datevalue-timevalue.md)** – 将纯日期字符串转换为日期/时间值。

**[Day](functions/function-datetime-parts.md)** – 检索日期/时间值的日部分。  

**[Defaults](functions/function-defaults.md)** – 返回数据源的默认值。

**[Degrees](functions/function-trig.md)** - 将弧度转换为度。

**[Disable](functions/function-enable-disable.md)** – 禁用某个信号，例如用于读取 GPS 的 **[Location](functions/signals.md)**。

**[Distinct](functions/function-distinct.md)** – 对表的记录数进行汇总并删除重复项。  

**[Download](functions/function-param.md)** – 将文件从 web 下载到本地设备。

**[DropColumns](functions/function-table-shaping.md)** – 返回删除了一个或多个列后的表。

## <a name="e"></a>E
**[EditForm](functions/function-form.md)** – 重置用于编辑某个项的表单控件。

**[Enable](functions/function-enable-disable.md)** – 启用某个信号，例如用于读取 GPS 的 **[Location](functions/signals.md)**。

**[EndsWith](functions/function-startswith.md)** – 检查某个文本字符串是否以另一个文本字符串结尾。

**[Errors](functions/function-errors.md)** – 提供之前对数据源的更改的错误信息。

**[EncodeUrl](functions/function-encode-decode.md)** – 使用 URL 编码对特殊字符进行编码。

**[Exit](functions/function-exit.md)** – 退出当前正在运行的应用。

**[Exp](functions/function-numericals.md)** - 返回 *e* 的乘幂。

## <a name="f"></a>F
**[Filter](functions/function-filter-lookup.md)** – 返回基于一个或多个条件筛选后的表。

**[Find](functions/function-find.md)** – 检查一个字符串是否出现在另一个字符串内并返回位置。

**[First](functions/function-first-last.md)** – 返回表中的第一条记录。

**[FirstN](functions/function-first-last.md)** – 返回表中的第一组记录（N 条记录）。

**[ForAll](functions/function-forall.md)** – 针对表中的所有记录计算值和执行操作。

## <a name="g"></a>G
**[GroupBy](functions/function-groupby.md)** – 返回将记录分组在一起的表。

## <a name="h"></a>H
**[HashTags](functions/function-hashtags.md)** – 从字符串中提取井号标签 (#strings)。

**[Hour](functions/function-datetime-parts.md)** – 返回日期/时间值的小时部分。

## <a name="i"></a>I
**[If](functions/function-if.md)** – 如果条件为 true，返回一个值，否则返回另一个值。 

**[IfError](functions/function-iferror.md)**  - 检测错误并提供替代值或执行操作。 

**[IsBlank](functions/function-isblank-isempty.md)** – 检查是否为[空](functions/function-isblank-isempty.md)值。

**[IsEmpty](functions/function-isblank-isempty.md)** – 检查是否为空表。

**[IsMatch](functions/function-ismatch.md)** – 对照某个模式检查字符串。  可以使用正则表达式。

**[IsNumeric](functions/function-isnumeric.md)** – 检查是否为数字值。

**[IsToday](functions/function-now-today-istoday.md)** – 检查某个日期/时间值是否为今天的某个时间。

## <a name="l"></a>L
**[Language](functions/function-language.md)** – 返回当前用户的语言标记。

**[Last](functions/function-first-last.md)** – 返回表中的最后一条记录。

**[LastN](functions/function-first-last.md)** – 返回表中的最后一组记录（N 条记录）。

**[Launch](functions/function-param.md)** – 启动某个 web 地址或应用。

**[Left](functions/function-left-mid-right.md)** – 返回字符串最左侧的部分。

**[Len](functions/function-len.md)** – 返回字符串的长度。

**[Ln](functions/function-numericals.md)** – 返回自然对数。

**[LoadData](functions/function-savedata-loaddata.md)** – 从 PowerApps 专用存储中加载集合。

**[Location](functions/signals.md)** – 通过使用全球定位系统 (GPS) 和其他信息将你的位置返回为地图坐标。

**[LookUp](functions/function-filter-lookup.md)** – 基于一个或多个条件在表中查找单条记录。

**[Lower](functions/function-lower-upper-proper.md)** – 将文本字符串中的字母转换为全部小写。

## <a name="m"></a>M
**[Max](functions/function-aggregates.md)** – 某个表表达式或一组参数的最大值。

**[Mid](functions/function-left-mid-right.md)** – 返回字符串的中间部分。

**[Min](functions/function-aggregates.md)** – 某个表表达式或一组参数的最小值。

**[Minute](functions/function-datetime-parts.md)** – 检索日期/时间值的分钟部分。  

**[Mod](functions/function-mod.md)** – 返回被除数除以除数之后的余数。

**[Month](functions/function-datetime-parts.md)** – 检索日期/时间值的月份部分。

## <a name="n"></a>N
**[Navigate](functions/function-navigate.md)** – 更改要显示的屏幕。

**[NewForm](functions/function-form.md)** – 重置用于创建某个项的表单控件。

**[Not](functions/function-logicals.md)** – 布尔逻辑非。  如果其参数为 **false**，则返回 **true**；如果其参数为 **true**，则返回 **false**。  还可以使用 [**!** 运算符](functions/operators.md)。

**[Notify](functions/function-showerror.md)** - 向用户显示横幅消息。

**[Now](functions/function-now-today-istoday.md)** – 返回当前的日期/时间值。

## <a name="o"></a>O
**[Or](functions/function-logicals.md)** – 布尔逻辑或。  如果其任一参数为 **true**，则返回 **true**。  还可以使用 [**||** 运算符](functions/operators.md)。

## <a name="p"></a>P
**[Param](functions/function-param.md)** – 用于访问当用户打开应用时传递给它的参数。

**[Parent](functions/operators.md#parent-operator)** – 用于访问容器控件的属性。

**[Patch](functions/function-patch.md)** – 在数据源中修改或创建记录，或者在数据源外部合并记录。

**[Pi](functions/function-trig.md)** – 返回数字 &pi;。

**[PlainText](functions/function-encode-decode.md)** – 从字符串中删除 HTML 和 XML 标记。

**[Power](functions/function-numericals.md)** – 返回某个数字的乘幂。  还可以使用 [**^** 运算符](functions/operators.md)。

**[Proper](functions/function-lower-upper-proper.md)** – 将字符串中每个单词的首字母转换为大写，将其余字母转换为小写。

## <a name="r"></a>R
**[Radians](functions/function-trig.md)** - 将度转换为弧度。

**[Rand](functions/function-rand.md)** – 返回一个伪随机数。

**[Refresh](functions/function-refresh.md)** – 刷新数据源的记录。

**[Remove](functions/function-remove-removeif.md)** – 从数据源中删除一条或多条特定记录。

**[RemoveIf](functions/function-remove-removeif.md)** – 基于某个条件从数据源中删除记录。

**[RenameColumns](functions/function-table-shaping.md)** – 重命名表的列。

**[Replace](functions/function-replace-substitute.md)** – 从字符串的起始位置开始，将一个字符串的一部分替换为另一个字符串。

[Reset](functions/function-reset.md) - 将输入控件重置为默认值，放弃任何用户更改。

**[ResetForm](functions/function-form.md)** – 重置用于编辑某个现有项的表单控件。

**[Revert](functions/function-revert.md)** – 重新加载数据源的记录并清除错误。

**[RGBA](functions/function-colors.md)** – 返回一组红、绿、蓝和 alpha 组件的颜色值。

**[Right](functions/function-left-mid-right.md)** – 返回字符串最右侧的部分。

**[Round](functions/function-round.md)** – 舍入到最接近的数字。

**[RoundDown](functions/function-round.md)** – 向下舍入到最大的上一数字。

**[RoundUp](functions/function-round.md)** – 向上舍入到最小的下一数字。

## <a name="s"></a>S
**[SaveData](functions/function-savedata-loaddata.md)** – 将集合保存到 PowerApps 专用存储。

**[Search](functions/function-filter-lookup.md)** – 在表中查找其某个列中包含某个字符串的记录。  

**[Second](functions/function-datetime-parts.md)** – 检索日期/时间值的秒部分。

**[Select](functions/function-select.md)** - 在控件上模拟选择操作，导致对 **OnSelect** 公式进行求值。

**[Set](functions/function-set.md)** – 设置全局变量的值。

**[ShowColumns](functions/function-table-shaping.md)** – 返回仅包含所选列的表。

**[Shuffle](functions/function-shuffle.md)** – 随机重新排列表记录的顺序。

**[Sin](functions/function-trig.md)** – 返回以弧度为单位指定的角度的正弦值。

**[Sort](functions/function-sort.md)** – 返回基于某个公式排序后的表。

**[SortByColumns](functions/function-sort.md)** – 返回基于一个或多个列排序后的表。

**[Split](functions/function-split.md)** – 将文本字符串拆分成子字符串表。

**[Sqrt](functions/function-numericals.md)** – 返回数字的平方根。

**[StartsWith](functions/function-startswith.md)** – 检查某个文本字符串是否以另一个文本字符串开头。

**[StdevP](functions/function-aggregates.md)** – 返回其参数的标准偏差。  

**[Substitute](functions/function-replace-substitute.md)** – 通过对字符串进行匹配，将一个字符串的一部分替换为另一个字符串。

**[SubmitForm](functions/function-form.md)** – 将表单控件中的项保存到数据源。

**[Sum](functions/function-aggregates.md)** – 计算某个表表达式或一组参数的和。  

**[Switch](functions/function-if.md)** - 先与一组值匹配，再对相应公式求值。

## <a name="t"></a>T
**[Table](functions/function-table.md)** – 创建一个临时表。  

**[Tan](functions/function-trig.md)** - 返回以弧度为单位指定的角度的正切值。

**[Text](functions/function-text.md)** – 将数字设置为字符串格式进行显示。

**[ThisItem](functions/operators.md#thisitem-operator)** – 当在库或表单中时，返回容器中当前项的数据。

**[Time](functions/function-date-time.md)** – 基于**小时**、**分钟**和**秒**的值返回日期/时间值。  

**[TimeValue](functions/function-datevalue-timevalue.md)** – 将纯时间字符串转换为日期/时间值。

**[TimeZoneOffset](functions/function-dateadd-datediff.md)** - 返回 UTC 和用户本地时间的时间差（以分钟为单位）。

**[Today](functions/function-now-today-istoday.md)** – 返回当前的日期/时间值。

**[Trim](functions/function-trim.md)** – 从文本字符串的末尾和内部删除多余的空格。

**[TrimEnds](functions/function-trim.md)** – 仅从文本字符串的末尾删除多余的空格。

## <a name="u"></a>U
**[Ungroup](functions/function-groupby.md)** – 删除某个分组。

**[Update](functions/function-update-updateif.md)** – 替换数据源中的某条记录。

[UpdateContext](functions/function-updatecontext.md) – 设置当前屏幕的一个或多个[上下文变量](working-with-variables.md#create-a-context-variable)的值。

**[UpdateIf](functions/function-update-updateif.md)** – 基于某个条件修改数据源中的一组记录。

**[Upper](functions/function-lower-upper-proper.md)** – 将文本字符串中的字母转换为全部大写。

**[User](functions/function-user.md)** – 返回当前用户的相关信息。

## <a name="v"></a>V
**[Validate](functions/function-validate.md)** – 检查单个列或整条记录的值对数据源是否有效。

**[Value](functions/function-value.md)** – 将字符串转换为数字。

**[VarP](functions/function-aggregates.md)** – 返回其参数的方差。  

[ResetForm](functions/function-form.md) – 重置用于查看现有项的表单控件。

## <a name="w"></a>W
**[Weekday](functions/function-datetime-parts.md)** – 检索日期/时间值的星期几部分。

## <a name="y"></a>Y
**[Year](functions/function-datetime-parts.md)** – 检索日期/时间值的年份部分。  

