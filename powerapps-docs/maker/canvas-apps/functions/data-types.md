---
title: 数据类型 |Microsoft Docs
description: 画布应用中的数据类型
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 05/19/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 85567e120754d4f82e13bd7d7dac9fa0f7c80cbd
ms.sourcegitcommit: 982cab99d84663656a8f73d48c6fae03e7517321
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/28/2019
ms.locfileid: "67456770"
---
# <a name="data-types-in-canvas-apps"></a>画布应用中的数据类型

通过应用程序中的较小的离散值的信息流与电子表格的单元格非常非常相似。 例如中的数据**生日**字段和一个**周年**字段会同时流经作为**日期**包括年、 月和日的值。 应用已知道如何设置这些值的格式、 约束输入到什么是适用于每个，和与数据库共享的值。 生日与周年纪念日不同给人，但系统完全相同的方式处理它们。 在这种情况下，**日期**举例说明[数据类型](https://en.wikipedia.org/wiki/Data_type)。

本文提供有关画布应用支持的数据类型的详细信息。 当应用连接到外部数据源时，该源中的每种数据类型映射到画布应用的数据类型。

| 数据类型 | 描述 | 示例 |
|-----------|-------------|---------|
| **Boolean** | 一个 *，则返回 true*或*false*值。  可以直接在使用**如果**，**筛选器**和其他功能而无需进行比较。  | *true* |
|  颜色 | 一种颜色规范，包括 alpha 通道。 | **Color.Red**<br>**ColorValue ("#102030")**<br>**RGBA( 255, 128, 0, 0.5 )** |
| **货币** | 一个货币值，该值存储在一个浮点数。 货币值将与货币格式设置选项的 number 值相同。  | **123**<br>**4.56** |
| **日期** | 而无需对应用的用户的时区中的某个时间日期。 | **Date( 2019, 5, 16 )** |
| **DateTime** | 与应用程序的用户的时区中的某个时间日期。 | **DateTimeValue （"16，2019 年 5 1:23:09 PM"）** |
| **GUID** | 一个[全局唯一标识符](https://en.wikipedia.org/wiki/Universally_unique_identifier)。 | **GUID()**<br>**GUID( "123e4567-e89b-12d3-a456-426655440000" )** |
| **Hyperlink** | 一个文本字符串，包含超链接。 | **"http://powerapps.microsoft.com"** |
| **图像** | 一个[通用资源标识符 (URI)](https://en.wikipedia.org/wiki/Uniform_Resource_Identifier) .jpeg、.png、.svg、.gif 或其他常见 web 图像格式中的图像的文本字符串。 | **MyImage**添加为应用程序资源<br>**"https://northwindtraders.com/logo.jpg"**<br>**"appres://blobmanager/7b12ffa2..."** |
| **媒体** | URI 文本字符串与视频或音频录制。 | **MyVideo**添加为应用程序资源<br>**"https://northwindtraders.com/intro.mp4"**<br>**"appres://blobmanager/3ba411c..."** |
| **数量** | 一个浮点数。 | **123**<br>**-4.567**<br>**8.903e121** |
| **选项集** | 一组选项，由数字之间进行选择。 此数据类型与数字值进行组合的可本地化的文本标签。 在应用中，将显示该标签和存储和用于比较数字值。 | **ThisItem.OrderStatus** |
| **记录** | 数据值的记录。 此复合数据类型包含本主题中列出的其他数据类型的实例。 详细信息：[使用表](../working-with-tables.md)。 | **{公司："Northwind Traders"<br>人员：35，<br>非营利组织： false}** |
| **记录的引用** | 对实体中记录的引用。 此类引用通常用于多态查找。 详细信息：[使用引用](../working-with-references.md)。| **First(Accounts).Owner** |
| **Table** | 记录的表。  所有记录必须具有相同的数据类型，其字段相同的名称和忽略的字段将被视为*空白*。 此复合数据类型包含本主题中列出的其他数据类型的实例。 详细信息：[使用表](../working-with-tables.md)。 | **表 ({FirstName:"Sidney"<br>姓氏:"Higa"}， <br>{FirstName:"Nancy"<br>姓氏:"Anderson" } )**
| **文本** | Unicode 文本字符串。 | **"Hello，World"** |
| **时间** | 而无需对应用的用户的时区的日期时间。 | **Time( 11, 23, 45 )** |
| **两个选项** | 一组由一个布尔值的两个选项之间进行选择。 此数据类型与布尔值进行组合的可本地化的文本标签。 在应用中，将显示该标签和存储和用于比较的布尔值。 | **ThisItem.Taxable** |

许多这些数据类型类似，并且具有相同的底层表示形式，例如**超链接**字段被视为**文本**。  其他数据类型提供更好的默认体验在窗体和其他控件。

## <a name="blank"></a>Blank

所有数据类型的值都可以*空白*（换而言之，没有值）。 术语"null"通常在数据库中用于这一概念。  

使用**空白**起作用**设置**或**Patch**函数来设置变量或字段*空白*。 例如，**集 (x，blank （))** 全局变量中删除的任何值**x**。  

用于测试*空白*通过使用值[ **IsBlank** ](function-isblank-isempty.md)函数。 替换可能*空白*值与非*空白*使用值[ **Coalesce** ](function-isblank-isempty.md)函数。

因为所有数据类型都支持*空白*，则**布尔**并**两个选项**数据类型实际上都有三个可能的值。

## <a name="text-hyperlink-image-and-media"></a>文本、 超链接、 图像和媒体

这些数据类型的所有四个基于[Unicode](https://en.wikipedia.org/wiki/Unicode)文本字符串。

### <a name="image-and-media-resources"></a>图像和媒体资源

通过**文件**菜单中，可以为应用程序的资源添加图像、 视频和音频文件。 导入的文件的名称将成为应用程序中的资源名称。 在此图中，名为 Northwind Traders 徽标**nwindlogo**，已添加到应用程序：

![](media/data-types/nwind-resource.png)

若要在应用中使用此资源，指定在**图像**的属性[**图像**](../controls/control-image.md)控件：

![](media/data-types/nwind-image.png)

### <a name="uris-for-images-and-other-media"></a>图像和其他媒体的 Uri

您可以深入到最后一个示例通过设置**文本**的属性[**标签**](../controls/control-text-box.md)控制对**nwindlogo**。 标签显示的文本字符串：

![](media/data-types/nwind-text.png)

画布应用引用的每个图像或其他媒体文件是在云中还是由 URI 文本字符串添加为应用资源。

例如，**图像**图像控件的属性可接受应用资源不仅还指向图像在 web 上，如"https://northwindtraders.com/logo.jpg"。 属性也接受使用的内联图像[数据的 URI 方案](https://en.wikipedia.org/wiki/Data_URI_scheme)，如下例所示：

```powerapps-dot
"data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAkAAAAFAQMAAACtnVQoAAAABlBMVEUAAAB0J3UMNU6VAAAAAXRSTlMAQObYZgAAABRJREFUCNdjUGJgCGVg6GgAkkA2AA8/AffqCEBsAAAAAElFTkSuQmCC"
```

该 URI 显示两个紫色方块的扩展型版本：

![](media/data-types/double-diamonds.png)

可以显示最新的映像中捕获[**照相机**](../controls/control-camera.md)如果你设置控制**图像**到图像控件的属性**照片**照相机控件的属性。 应用映像保存在内存中，并**照片**的照相机控件的属性将返回图像的 URI 引用。 例如，可能需要一张图片和摄像机**照片**属性可能返回 **"appres://blobmanager/7b12ffa2ea4547e5b3812cb1c7b0a2a0/1"** 。

使用的 URI 来引用图像或存储在数据库中的另一个媒体文件。 这样一来，直到实际需要时，应用程序不会检索实际数据。 例如，Common Data Service 实体中的附件可能会返回 **"appres://datasources/Contacts/table/..."** 在照相机示例中，可以通过设置显示此图像**图像**图像控件引用，它检索的二进制数据的属性。

当媒体数据类型，如的图像保存到数据库时，该应用将发送的实际图像或媒体数据，不的 URI 引用。

### <a name="size-limits"></a>大小限制

作为文本字符串和 Uri，这些数据类型没有预设的限制对它们的长度。

这些数据类型还引用的二进制数据大小已没有预设的限制。 例如，现在作为引用的照相机控件通过捕获的映像 **"appres: /..."** 如设备的照相机可以 muster 可以是作为大型和高分辨率。 分辨率、 帧速率和媒体文件的其他属性不局限于数据类型，但用于播放和捕获媒体的特定控件可能有其自己的限制。

但是，所有数据大小都受到应用程序中的可用内存量。 通常在桌面计算机上运行的浏览器支持超过 100 兆字节的数据。 但是，如电话的设备上的可用内存量可能低得多，通常在范围内 30-70 兆字节为单位。 若要确定您的应用程序将运行这些限制范围内，测试应运行的所有设备上的常见方案。

最佳做法是，在长达必要的内存中保存数据。 将图像上载到数据库，就立即可以;仅当应用程序的用户请求它们时，请下载映像。

## <a name="number-and-currency"></a>数字和货币

**数字**并**货币**数据类型使用[IEEE 754 双精度浮点标准](https://en.wikipedia.org/wiki/IEEE_754)。 此标准提供了非常大范围中要使用从 –1.79769 x 10 的数字<sup>308</sup>到 1.79769 x 10<sup>308</sup>。 可表示的最小值为 5 x 10<sup>–324</sup>。

画布应用程序可以完全代表全部为数字 （或整数） 之间 –9,007,199,254,740,991 (– (2<sup>53</sup> – 1)) 和 9,007,199,254,740,991 (2<sup>53</sup> – 1) (含） 之间。 此范围大于数据库通常使用的 32 位 （或 4 字节） 整数数据类型。 但是，画布应用不能表示 64 位 （或 8 字节） 整数数据类型。 你可能想要在文本字段中存储的数字或使用计算的列来在文本字段中，制作一份数，以便映射到**文本**画布应用中的数据类型。 以这种方式，可以保存、 显示和输入这些值，以及将其以确定它们是否相等，则进行比较但是，不能在此窗体中对其执行数字计算。

浮点运算是一个近似值，因此它有时会产生意外的结果与许多有案可稽的示例。 您所料公式**55 / 100 * 100**返回完全 55 和 **(55 / 100 * 100)-55**以返回精确的零。 但是后, 一种公式将返回 7.1054 x 10<sup>–15</sup>，这是非常小，但不是为零。 该微小差异通常不会导致问题，并应用将舍入它立即显示结果时。 但是，细微的差异可以在随后的计算，复合，并提供错误答案看起来。

通常，数据库系统存储货币，并使用十进制数学，它提供了更小的范围，但更好地精度控制执行计算。 默认情况下，画布应用映射货币入和移出浮点值;因此，结果可能不同于在本机 decimal 数据类型中进行计算。 如果这种差异会导致问题，您可能想要使用这些值作为**文本**，就像您可能会在本部分中前面所述的大整数。

## <a name="date-time-and-datetime"></a>日期、 时间和日期时间

### <a name="time-zones"></a>时区

日期/时间值 fall 这些类别中：

- **用户本地**:这些值存储在[UTC （协调世界时）](https://en.wikipedia.org/wiki/Coordinated_Universal_Time)，但应用用户的时区影响该应用程序如何显示这些值和应用程序用户是如何指定它们。 例如，同一时刻以不同的方式的用户显示的加拿大日本国内的用户相比。
- **时区无关**:应用将显示这些值相同的方式和应用程序用户为它们指定相同的方式，而不考虑时区。 是同一时刻方式与其在日本的用户出现在加拿大的用户相同的方式。 应用程序创建者不期望在不同时区中运行其应用程序使用这些值，因为它们总体更简单。

此表显示了一些示例：

| 日期/时间类型 | 存储在数据库中的值 | 值显示，并且输入 7 小时在 UTC 以西 | 值显示，并且输入偏 UTC 东 4 小时 |
|--------------------------|------------------------------|------------------------------|
| **本地用户** | 星期日、&nbsp;可能&nbsp;19，&nbsp;2019年<br>4:00 AM | 星期六&nbsp;可能&nbsp;18，&nbsp;2019年<br>9:00 PM | 星期日、&nbsp;可能&nbsp;19，&nbsp;2019年<br>上午 8:00 |
| **时区无关** | 星期日、&nbsp;可能&nbsp;19，&nbsp;2019年<br>4:00 AM | 星期日、&nbsp;可能&nbsp;19，&nbsp;2019年<br>4:00 AM | 星期日、&nbsp;可能&nbsp;19，&nbsp;2019年<br>4:00 AM | 

有关**用户本地**日期/时间、 画布应用使用的浏览器或设备，时区，但模型驱动应用程序使用用户的通用设置数据服务。 这些设置通常与相匹配，但如果这些设置不同时将相同的结果。

### <a name="numeric-equivalents"></a>数字的等效项

画布应用，保存并计算所有日期/时间值，是否**用户本地**或**时区无关**utc 格式。 应用转换基于应用程序用户的时区显示它们时，当应用程序用户指定它们的值。

当画布应用中读取**时区无关**从数据源或写入到数据源，该应用程序这样的值自动调整要补偿的应用程序的用户的时区的值的值。 应用程序会将值视为 UTC 值，与应用程序中的所有其他日期/时间值一致。 由于此补偿，原始**时区无关**值显示时应用程序调整应用程序用户的时区 UTC 值。

您可以通过使用更紧密地观察此行为[**值**](function-value.md)函数来访问日期/时间值的基础数字值。 此函数返回的日期/时间值的毫秒数为自 1970 年 1 月 1 日起 00:00:00.000 UTC。

因为每个日期/时间值保存在 UTC，该公式**值 (日期 (自 1970 年 1，1))** 不会返回零个中的大多数在世界各地，因为**日期**函数返回以 UTC 日期。 例如，公式将返回 28,800,000 偏移的时区中与 UTC 八个小时。 该数字反映在八个小时内的毫秒数。

返回到我们从上面的示例：

| 日期/时间类型 | 存储在数据库中的值 | 值显示，并且输入 7 小时在 UTC 以西 | **值**函数返回 |
|--------------------------|------------------------------|------------------------------|
| **本地用户** | 星期日、&nbsp;可能&nbsp;19，&nbsp;2019年<br>4:00 AM | 星期六&nbsp;可能&nbsp;18，&nbsp;2019年<br>9:00 PM | 1,558,238,400,000<br> (星期日&nbsp;可能&nbsp;19，&nbsp;2019年<br>4:00 AM UTC) |
| **时区无关** | 星期日、&nbsp;可能&nbsp;19，&nbsp;2019年<br>4:00 AM | 星期日、&nbsp;可能&nbsp;19，&nbsp;2019年<br>4:00 AM |1,558,263,600,000<br> (星期日&nbsp;可能&nbsp;19，&nbsp;2019年<br>UTC 时间上午 11:00) |

### <a name="converting-unix-times"></a>将 Unix 时间转换

Unix 时间反映自 1970 年 1 月 1 日以来的秒数 00:00:00 UTC。 由于画布应用使用而不是秒毫秒，你可以转换相乘或除以 1000 两者之间。

例如，Unix 时间显示 2001 年 9 月 9 日，01:46:40 1,000,000,000 为 UTC。 向显示的日期/时间值中的画布应用，该数字乘以 1,000 以将其转换为毫秒，并使用它在[**文本**](function-text.md)函数。 该公式**文本 (1000000000 * 1000，DateTimeFormat.UTC)** 返回的字符串**2001年-09-09T01:46:40.000Z**。

但是，该函数返回**2001 年 9 月 8 日，星期六 18:46:40**如果你使用**DateTimeFormat.LongDateTime24**从 UTC （7 小时延伸 UTC） 偏移-7 小时的时区中的格式。 此结果显示**DateTime**正确值根据本地时区。

要将转换为 Unix 时间，除的结果**值**1,000 通过：
<br>**RoundDown( Value( UnixTime ) / 1000, 0 )**

如果你需要在 Unix 时间**日期**进行进一步的计算值或在 PowerApps 中显示，请使用以下公式：
<br>**DateAdd( Date( 1970,1,1 ), UnixTime, Seconds )**

### <a name="sql-server"></a>SQL Server

SQL Server 具有[ **Datetime**， **Datetime2**，和其他日期/时间数据类型](https://docs.microsoft.com/sql/t-sql/functions/date-and-time-data-types-and-functions-transact-sql?view=sql-server-2017)，不包含时区偏移量并不指示的时区中。 画布应用假定这些值存储在 UTC，并将它们视为**用户本地**。 如果值应是时区不依赖于，更正 UTC 转换通过使用[ **TimeZoneOffset** ](function-dateadd-datediff.md#converting-to-utc)函数。

画布应用使用中的包含的时区信息**Datetimeoffset**字段时将值转换为应用程序的内部 UTC 表示形式。 应用程序始终使用 UTC 与时区 （零个时区偏移量） 时写入的数据。

画布应用读取和写入的值[**时间**](https://docs.microsoft.com/sql/t-sql/data-types/time-transact-sql)中的文本字符串作为 SQL Server 中的数据类型[ISO 8601 持续时间格式](https://en.wikipedia.org/wiki/ISO_8601#Durations)。 例如，您必须分析此字符串格式，并使用[**时间**](function-date-time.md)函数将转换的文本字符串 **"PT2H1M39S"** 到**时间**值：

```powerapps-dot
First(
    ForAll(
        MatchAll( "PT2H1M39S", "PT(?:(?<hours>\d+)H)?(?:(?<minutes>\d+)M)?(?:(?<seconds>\d+)S)?" ),
        Time( Value( hours ), Value( minutes ), Value( seconds ) )
    )
).Value
```

### <a name="mixing-date-and-time-information"></a>混合使用日期和时间信息

**日期**，**时间**，和**DateTime**具有不同的名称，但它们都保留有关日期和时间相同的信息。 

一个**日期**值可以包括时间信息，通常是午夜。 一个**时间**值可以包含日期信息，这通常是自 1970 年 1 月 1 日。 Common Data Service 还存储与时间信息**仅限日期**字段但默认情况下显示仅将日期信息。 同样，画布应用有时区分这些数据类型来确定默认的格式和控件。

添加和直接减去的日期和时间值不被建议，因为此时区和其他转换可能会导致令人困惑的结果。 请使用**值**函数首先将日期/时间值转换为毫秒，并考虑到应用程序用户的时区，或使用[ **DateAdd** ](function-dateadd-datediff.md)和[ **DateDiff** ](function-dateadd-datediff.md)函数来添加或减去这些值之一。

## <a name="option-sets-and-two-options"></a>选项集和两个选项

选项集和两个选项的数据类型提供了应用程序用户无法选择两个或多个选择。 例如，**订单状态**选项集可能会提供选择**新建**， **Shipped**，**已开发票**，和**已关闭**. 两个选项的数据类型提供了只有两个选项。

这两种数据类型的文本字符串上下文中显示其标签。 例如，标签控件显示了一个订单状态选项如果控件的**文本**属性设置为一个公式来引用该选项集。 选项标签可能会本地化应用用户位于不同的位置。

当应用程序用户选择一个选项，并保存所做的更改时，应用将数据传输到数据库，将该数据存储在与语言无关的表示形式。 传输中的选项集的一个选项，并存储为一个数字，并传输中的两个选项的数据类型的一个选项，并存储为一个布尔值。

标签是仅出于显示目的。 无法执行带标签的直接比较，因为它们是特定于语言。 相反，每个选项集具有一个适用于基础数字或布尔值的枚举。 例如，不能使用此公式：

`If( ThisItem.OrderStatus = "Active", ...`

但您可以使用以下公式：

`If( ThisItem.OrderStatus = OrderStatus.Active, ...`

有关全局选项集 （哪个实体共享），选项集枚举的名称匹配全局选项集的名称。 对于本地选项集 （其范围限定到的实体），该名称可能包含的实体的名称。 如果多个实体有具有相同名称的选项集，此行为可避免冲突。 例如，**帐户**实体可能具有**OrderStatus**选项设置，并且其名称可能**OrderStatus （帐户）** 。 该名称包含一个或多个空格和括号，因此如果在公式中引用必须包围它用单引号。

此外，两个选项值还可充当布尔值。 例如，一个名为的两个选项值**TaxStatus**可能具有标签**应纳税**并**不应纳税**，对应于*true*并*false*分别。 为了演示，可以使用以下公式：

`If( ThisItem.Taxable = TaxStatus.Taxable, ...`

此外可以使用下面的等效公式：

`If( ThisItem.Taxable, ...`