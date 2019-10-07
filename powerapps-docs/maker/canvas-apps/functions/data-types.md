---
title: 数据类型 |Microsoft Docs
description: 画布应用中的数据类型
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 05/19/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 592399e6b5a95d27e5c0afe48541d04d444528bb
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/07/2019
ms.locfileid: "71985567"
---
# <a name="data-types-in-canvas-apps"></a>画布应用中的数据类型

信息通过小型离散值中的应用进行流动，与电子表格的单元格非常类似。 例如，"**生日**" 字段和 "**周年纪念日**" 字段中的数据都将流动为包含年、月和日的**日期**值。 应用知道如何设置这些值的格式，如何将输入限制为适用于每个值的内容，并与数据库共享值。 生日与周年纪念的不同之处在于，系统以完全相同的方式处理生日。 在这种情况下， **Date**是[数据类型](https://en.wikipedia.org/wiki/Data_type)的示例。

本文提供了有关画布应用支持的数据类型的详细信息。 当应用连接到外部数据源时，该源中的每个数据类型都将映射到画布应用的数据类型。

| 数据类型 | 描述 | 示例 |
|-----------|-------------|---------|
| **变量** | *True*或*false*值。  如果没有比较，则可以直接在**If**、 **Filter**和其他函数中使用。  | *true* |
| 颜色 | 颜色规范，包括 alpha 通道。 | **Color.Red**<br>**ColorValue （"#102030"）**<br>**RGBA （255，128，0，0.5）** |
| **货币** | 存储在浮点数中的货币值。 货币值与带有货币格式选项的数字值相同。  | **123**<br>**4.56** |
| **日期** | 不带时间的日期，采用应用用户的时区。 | **Date （2019，5，16）** |
| **型** | 日期，时间为应用程序用户的时区。 | **DateTimeValue （"5 月16日 2019 1:23:09 PM"）** |
| **GUID.EMPTY** | [全局唯一标识符](https://en.wikipedia.org/wiki/Universally_unique_identifier)。 | **GUID （）**<br>**GUID （"123e4567-e89b-12d3-a456-426655440000"）** |
| **Hyperlink** | 包含超链接的文本字符串。 | **"http://powerapps.microsoft.com"** |
| **图像** | 图像的[通用资源标识符（URI）](https://en.wikipedia.org/wiki/Uniform_Resource_Identifier)文本字符串，格式为 jpeg、.png、svg、.gif 或其他常见的 web 图像格式。 | 添加为应用资源的**MyImage**<br>**"https://northwindtraders.com/logo.jpg"**<br>**"appres://blobmanager/7b12ffa2 ..."** |
| **媒体** | 视频或音频录制的 URI 文本字符串。 | 添加为应用资源的**MyVideo**<br>**"https://northwindtraders.com/intro.mp4"**<br>**"appres://blobmanager/3ba411c ..."** |
| **多种** | 浮点数。 | **123**<br>**-4.567**<br>**8.903e121** |
| **选项集** | 从一组选项中选择，由数字支持。 此数据类型将可本地化的文本标签与数值组合在一起。 标签将出现在应用中，并存储数值并用于比较。 | **ThisItem. 对 orderstatus** |
| **记录** | 数据值的记录。 此复合数据类型包含本主题中列出的其他数据类型的实例。 详细信息：[处理表](../working-with-tables.md)。 | **{Company："Northwind 商贸" <br>Staff：35，<br>NonProfit： false}** |
| **记录引用** | 对实体中的记录的引用。 此类引用通常与多态查找一起使用。 详细信息：使用[引用](../working-with-references.md)。| **第一个（帐户）。Owner** |
| **数据表** | 记录的表。  对于具有相同数据类型的字段，所有记录必须具有相同的名称，并且省略的字段将被视为*空白*。 此复合数据类型包含本主题中列出的其他数据类型的实例。 详细信息：[处理表](../working-with-tables.md)。 | @no__t 0Table （{FirstName："Sidney"，<br>LastName："Higa"} <br> {FirstName："南希" <br>LastName："Anderson"}） **
| **文本** | Unicode 文本字符串。 | **"Hello，World"** |
| **阶段** | 不带日期的时间，采用应用用户的时区。 | **时间（11，23，45）** |
| **两个选项** | 从一组由布尔值支持的两个选项中进行选择。 此数据类型将可本地化的文本标签与布尔值组合在一起。 此标签将出现在应用中，并存储布尔值并用于比较。 | **ThisItem** |

其中的许多数据类型都是类似的，并且具有相同的基础表示形式，如作为**文本**处理的**超链接**字段。  其他数据类型在窗体和其他控件中提供了更好的默认体验。

## <a name="blank"></a>Blank

所有数据类型的值都为*空*（即，没有值）。 术语 "null" 通常用于此概念中的数据库。  

使用带有**set**或**Patch**函数的**空白**函数将变量或字段设置为*空白*。 例如， **Set （x，空白（））将**删除全局变量**x**中的任何值。  

使用[**IsBlank**](function-isblank-isempty.md)函数测试是否*有空*值。 使用[**合并**](function-isblank-isempty.md)函数将可能的*空*值替换为非*空*值。

由于所有数据类型都支持*空白*，因此**布尔**值和**两个选项**数据类型实际上具有三个可能的值。

## <a name="text-hyperlink-image-and-media"></a>文本、超链接、图像和媒体

这四种数据类型都基于[Unicode](https://en.wikipedia.org/wiki/Unicode)文本字符串。

### <a name="image-and-media-resources"></a>图像和媒体资源

通过 "**文件**" 菜单，可以将图像、视频和音频文件作为应用资源添加。 导入的文件的名称将成为应用中的资源名称。 在此图中，已将名为**nwindlogo**的 Northwind 商贸徽标添加到应用：

![](media/data-types/nwind-resource.png)

若要在应用中使用此资源，请在[**图像**](../controls/control-image.md)控件的**image**属性中指定它：

![](media/data-types/nwind-image.png)

### <a name="uris-for-images-and-other-media"></a>图像和其他媒体的 Uri

您可以通过将 "[**标签**](../controls/control-text-box.md)" 控件的 " **Text** " 属性设置为 " **nwindlogo**"，深入了解上一个示例。 标签显示文本字符串：

![](media/data-types/nwind-text.png)

画布应用引用每个映像或其他媒体文件，无论是在云中还是作为应用资源添加，都由 URI 文本字符串。

例如，图像控件的**image**属性不仅接受应用资源，还接受链接到 web 上的图像，如 "https://northwindtraders.com/logo.jpg"。 属性还接受使用[数据 URI 方案](https://en.wikipedia.org/wiki/Data_URI_scheme)的内联图像，如以下示例中所示：

```powerapps-dot
"data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAkAAAAFAQMAAACtnVQoAAAABlBMVEUAAAB0J3UMNU6VAAAAAXRSTlMAQObYZgAAABRJREFUCNdjUGJgCGVg6GgAkkA2AA8/AffqCEBsAAAAAElFTkSuQmCC"
```

该 URI 显示两个紫色菱形的向上缩放版本：

![](media/data-types/double-diamonds.png)

如果将 image 控件的**image**属性设置为相机控件的**Photo**属性，则可以在[**相机**](../controls/control-camera.md)控件中显示最近捕获的图像。 应用程序将图像保存在内存中，并且相机控件的**Photo**属性返回图像的 URI 引用。 例如，您可以拍摄一张照片，照相机的**照片**属性可能会返回 **"appres://blobmanager/7b12ffa2ea4547e5b3812cb1c7b0a2a0/1"** 。

使用 URI 可以引用存储在数据库中的图像或其他媒体文件。 这样一来，应用就不会检索实际数据，直到实际需要。 例如，Common Data Service 实体中的附件可能返回 **"appres://datasources/Contacts/table/..."** 如相机示例中所示，可以通过将图像控件的**image**属性设置为此引用来显示此图像，这将检索二进制数据。

将媒体数据类型（如图像）保存到数据库时，应用程序将发送实际的图像或媒体数据，而不是 URI 引用。

### <a name="size-limits"></a>大小限制

作为文本字符串和 Uri，这些数据类型的长度没有预设限制。

这些数据类型引用的二进制数据也没有预设的大小限制。 例如，通过相机控件捕获的图像现在被称为 **"appres://"** ，它可以像设备的照相机可以 muster 一样大且高的分辨率。 媒体文件的分辨率、帧速率和其他属性不受数据类型的限制，但用于播放和捕获媒体的特定控件可能有自己的限制。

但是，所有数据大小都受应用中的可用内存量的限制。 在台式计算机上运行的浏览器通常支持超过 100 mb 的数据。 不过，设备上的可用内存量可能会很低，通常在 30-70 mb 范围内。 若要确定应用程序是否将在这些限制内运行，请在运行该应用程序的所有设备上测试常见方案。

最佳做法是，仅在必要时才将数据保存在内存中。 尽快将图像上传到数据库;仅在应用程序的用户请求图像时下载映像。

## <a name="number-and-currency"></a>数字和货币

**数字**和**货币**数据类型使用[IEEE 754 双精度浮点标准](https://en.wikipedia.org/wiki/IEEE_754)。 此标准提供一个非常大的数字范围，从– 1.79769 x 10<sup>308</sup>到 1.79769 x 10<sup>308</sup>。 可表示的最小值为 5 x 10<sup>– 324</sup>。

画布应用可以完全表示–9007199254740991（–（2<sup>53</sup> –1））和9007199254740991（2<sup>53</sup> –1）（含）之间的整数（或整数）。 此范围大于数据库通常使用的32位（或4字节）整数数据类型。 但是，画布应用无法表示64位（或8字节）的整数数据类型。 您可能想要在文本字段中存储数字，或者使用计算列在文本字段中创建数字的副本，使其在画布应用中映射为**文本**数据类型。 通过这种方式，您可以保存、显示和输入这些值，并对它们进行比较以确定它们是否相等;但是，不能在此窗体中对其执行数字计算。

浮点运算是近似的，因此，有时它可能会产生意外的结果，并提供许多示例。 你可能希望公式**55/100 * 100**返回准确的55和 **（55/100 * 100）-55**返回精确的零。 但后一个公式返回 7.1054 x 10<sup>-15</sup>，这非常小但不是零。 这种微小差异通常不会导致问题，应用会在显示结果时将其舍入。 但是，在后续计算中可能会有细微的差别，并显示错误答案。

数据库系统通常使用十进制数学来存储货币并执行计算，这会提供较小的范围，但可以更好地控制精度。 默认情况下，画布应用将货币映射到浮点值并将其移出。因此，结果可能与在本机 decimal 数据类型中完成的计算有所不同。 如果这种类型的差异会导致问题，您可能希望将这些值作为**文本**处理，就像您在本部分前面所述的大整数。

## <a name="date-time-and-datetime"></a>日期、时间和日期时间

### <a name="time-zones"></a>时区

日期/时间值属于以下类别：

- **用户本地**：这些值以[UTC （协调世界时）](https://en.wikipedia.org/wiki/Coordinated_Universal_Time)存储，但是应用用户的时区会影响应用显示这些值的方式，以及应用用户如何指定这些值。 例如，与日本的用户相比，加拿大用户的显示时间也不同。
- **独立**时区：应用以相同的方式显示这些值，应用用户以相同方式指定这些值，而不考虑时区。 与日本的用户一样，同一时刻与加拿大用户的显示方式相同。 不希望应用程序在不同时区中运行的应用程序作者使用这些值，因为它们的整体更简单。

下表显示了一些示例：

| 日期/时间类型 | 存储在数据库中的值 | 显示和输入的值7小时的 UTC | 显示的值和输入的时间为4小时东部 |
|--------------------------|------------------------------|------------------------------|
| **用户本地** | 星期日、&nbsp;May @ no__t-119、&nbsp;2019<br>上午4:00 | 周六，&nbsp;May @ no__t-118，&nbsp;2019<br>9:00 PM | 星期日、&nbsp;May @ no__t-119、&nbsp;2019<br>上午8:00 |
| **独立时区** | 星期日、&nbsp;May @ no__t-119、&nbsp;2019<br>上午4:00 | 星期日、&nbsp;May @ no__t-119、&nbsp;2019<br>上午4:00 | 星期日、&nbsp;May @ no__t-119、&nbsp;2019<br>上午4:00 | 

对于**用户本地**日期/时间，画布应用使用浏览器或设备的时区，但模型驱动应用使用用户在 Common Data Service 中的设置。 这些设置通常匹配，但如果这些设置不同，结果会有所不同。

使用[**DateAdd**](function-dateadd-datediff.md)和[**TimeZoneInformation**](function-dateadd-datediff.md)函数将本地时间转换为 UTC，并再次返回回来。  请参阅文档末尾的示例以了解这些函数。

### <a name="numeric-equivalents"></a>等效数值

画布应用保留并计算所有日期/时间值，无论是独立于 UTC 的**用户本地** **时区**还是时区。 应用程序在显示值时，根据应用程序用户的时区转换值。

当画布应用从数据源读取时区**独立**值或将此类值写入数据源时，应用会自动调整值以补偿应用用户的时区。 然后，应用将值视为 UTC 值，与应用中的所有其他日期/时间值一致。 由于此补偿，当应用调整应用用户时区的 UTC 值时，将显示原始**时区独立**值。

您可以通过使用[**Value**](function-value.md)函数访问日期/时间值的基础数值来更密切地观察此行为。 此函数将日期/时间值返回为自 1970 00：00： 00.000 UTC 以来的毫秒数。

由于每个日期/时间值均以 UTC 格式保存，因此公式**值（date （1970，1，1））** 不会在世界大多数部分返回零，因为**date**函数返回 UTC 格式的日期。 例如，公式会在与 UTC 之间偏移量8小时的时区中返回28800000。 该数字反映了8小时内的毫秒数。

返回到上面的示例：

| 日期/时间类型 | 存储在数据库中的值 | 显示和输入的值7小时的 UTC | **值**函数返回 |
|--------------------------|------------------------------|------------------------------|
| **用户本地** | 星期日、&nbsp;May @ no__t-119、&nbsp;2019<br>上午4:00 | 周六，&nbsp;May @ no__t-118，&nbsp;2019<br>9:00 PM | 1558238400000<br> （星期日、&nbsp;May @ no__t-119、&nbsp;2019<br>4:00 AM UTC） |
| **独立时区** | 星期日、&nbsp;May @ no__t-119、&nbsp;2019<br>上午4:00 | 星期日、&nbsp;May @ no__t-119、&nbsp;2019<br>上午4:00 |1558263600000<br> （星期日、&nbsp;May @ no__t-119、&nbsp;2019<br>11:00 AM UTC） |

### <a name="converting-unix-times"></a>转换 Unix 时间

Unix 时间反映自1970年1月1日起自 00:00:00 UTC 以来的秒数。 由于画布应用使用的是毫秒，而不是秒，因此你可以在两者之间进行转换，方法是将两者相乘或除以1000。

例如，Unix 时间显示2001年9月9日，01:46:40 UTC 作为1000000000。 若要在画布应用中显示日期/时间值，请将该数字乘以1000将其转换为毫秒，然后在[**文本**](function-text.md)函数中使用它。 公式**文本（1000000000 * 1000，DateTimeFormat）** 返回字符串**2001-09-09T01：46： 40.000 z**。

但是，如果您在与 UTC 的7小时偏移量（UTC 的7小时西部）之间使用**DateTimeFormat**格式的时区，则该函数将返回**星期六、9月8日 2001 18:46:40** 。 此结果根据本地时区正确显示**DateTime**值。

若要转换为 Unix 时间，请将**值**除以1000：
<br>**RoundDown （Value （UnixTime）/1000，0）**

如果需要在**日期**值中输入 Unix 时间以便进一步计算或在 PowerApps 中显示，请使用以下公式：
<br>**DateAdd （Date （1970，1，1），UnixTime，秒）**

### <a name="sql-server"></a>SQL Server

SQL Server 具有[ **Datetime**、 **Datetime2**和其他](https://docs.microsoft.com/sql/t-sql/functions/date-and-time-data-types-and-functions-transact-sql?view=sql-server-2017)不包含时区偏移量的日期/时间数据类型，并且不指示它们所在的时区。 画布应用假设这些值以 UTC 存储，并将其视为**本地用户**。 如果值要独立于时区，请使用[**TimeZoneOffset**](function-dateadd-datediff.md#converting-to-utc)函数更正 UTC 翻译。

在将值转换为应用的内部 UTC 表示形式时，画布应用使用**Datetimeoffset**字段中包含的时区信息。 应用程序在写入数据时始终使用 UTC 作为时区（零时区偏移量）。

画布应用以[ISO 8601 持续时间格式](https://en.wikipedia.org/wiki/ISO_8601#Durations)将 SQL Server 中的[**Time**](https://docs.microsoft.com/sql/t-sql/data-types/time-transact-sql)数据类型的值作为文本字符串进行读取和写入。 例如，必须分析此字符串格式，并使用[**time**](function-date-time.md)函数将文本字符串 **"PT2H1M39S"** 转换为**时间**值：

```powerapps-dot
First(
    ForAll(
        MatchAll( "PT2H1M39S", "PT(?:(?<hours>\d+)H)?(?:(?<minutes>\d+)M)?(?:(?<seconds>\d+)S)?" ),
        Time( Value( hours ), Value( minutes ), Value( seconds ) )
    )
).Value
```

### <a name="mixing-date-and-time-information"></a>混合日期和时间信息

**日期**、**时间**和日期**时间**具有不同的名称，但它们都包含与日期和时间相同的信息。 

**日期**值可以包含它的时间信息，通常为午夜。 **时间**值可以携带日期信息，通常为1970年1月1日。 Common Data Service 还将时间信息存储为 "**仅日期**" 字段，但默认情况下仅显示日期信息。 同样，画布应用有时可以区分这些数据类型以确定默认格式和控件。

不建议直接添加和减去日期和时间值，因为时区和其他转换可能会导致混乱的结果。 使用**Value**函数将日期/时间值先转换为毫秒，并考虑应用程序用户的时区，或使用[**DateAdd**](function-dateadd-datediff.md)和[**DateDiff**](function-dateadd-datediff.md)函数来添加或减少其中一个值。

## <a name="option-sets-and-two-options"></a>选项集和两个选项

选项集和双选项数据类型为应用程序用户提供了两个或更多选项以供选择。 例如，"**订单状态**" 选项可能会提供 "**新**"、"已**发布**"、"已**开发**" 和 "**已关闭**" 选项。 双选项数据类型只提供两种选择。

这两种数据类型都在文本字符串上下文中显示其标签。 例如，如果控件的**Text**属性设置为引用该选项集的公式，则标签控件将显示一个顺序状态选项。 选项标签可能针对不同位置中的应用用户进行了本地化。

当应用程序用户选择一个选项并保存该更改时，应用程序将数据传输到数据库，该数据库将该数据存储在与语言无关的表示形式中。 选项集中的选项被传输并存储为数字，而双选项数据类型中的选项则作为布尔值进行传输和存储。

标签仅用于显示目的。 不能对标签执行直接比较，因为它们是特定于语言的。 相反，每个选项集都有一个使用基础数字或布尔值的枚举。 例如，不能使用以下公式：

`If( ThisItem.OrderStatus = "Active", ...`

但你可以使用以下公式：

`If( ThisItem.OrderStatus = OrderStatus.Active, ...`

对于全局选项集（实体共享），选项集枚举的名称与全局选项集的名称相匹配。 对于本地选项集（作用域为某一实体），该名称可能包含实体的名称。 如果多个实体包含具有相同名称的选项集，此行为将避免冲突。 例如，"**帐户**" 实体可能具有**对 orderstatus**选项集，其名称可能为 "**对 orderstatus （帐户）** "。 该名称包含一个或多个空格和括号，因此，如果在公式中引用它，则必须用单引号将它括起来。

此外，两个选项的值还可以作为布尔值。 例如，名为**TaxStatus**的双选项值可能具有可**纳税**和**不应缴税**的标签，分别对应于*true*和*false* 。 为了说明这一点，可以使用以下公式：

`If( ThisItem.Taxable = TaxStatus.Taxable, ...`

你还可以使用此等效公式：

`If( ThisItem.Taxable, ...`