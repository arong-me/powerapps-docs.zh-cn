---
title: Concurrent 函数 | Microsoft 文档
description: PowerApps 中 Concurrent 函数的参考信息（包括语法）
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 06/26/2018
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: a0fdddcf906a04914ea9ba9a8572798ea5d55378
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/24/2018
ms.locfileid: "42834810"
---
# <a name="concurrent-function-in-powerapps"></a>PowerApps 中的 Concurrent 函数
并发计算多个公式。

## <a name="description"></a>描述
Concurrent 函数同时计算多个公式。 通常情况下，多个公式由 [**;**](operators.md)（或 [**;;**](operators.md)）运算符串联计算，此运算符按顺序计算每个公式。 当应用并发执行操作时，用户等待较短时间即可获得相同结果。

在应用的 [**OnStart**](../controls/control-screen.md) 属性中，使用 **Concurrent** 在应用程序加载数据时提高性能。 如果必须等到前一个调用完成才能启动数据调用，则应用必须等待所有请求时间之和。 如果数据调用都同时启动，应用只需等待最长请求的时间。 Web 浏览器通常通过同时执行数据操作提高性能。

不能预测 Concurrent 函数中的公式开始和结束求值的顺序。 Concurrent 函数中的公式不应包含对同一 Concurrent 函数中其他公式的依赖项，如果尝试这么做，PowerApps 会显示错误。 在其中，可以安全接受对 Concurrent 函数之外公式的依赖项，因为它们会在 Concurrent 函数开始之前完成。 Concurrent 函数后的公式可以安全接受对其中公式的依赖项：它们都会在 Concurrent 函数完成并转到链中下一个公式（如果使用 ; 或 ; 运算符）前完成。 如果要调用有副作用的函数或服务方法，请注意细微的顺序依赖关系。

可在 Concurrent 的参数内使用 ;（或 ;;）操作符串联公式。 例如 Concurrent( Set( a, 1 ); Set( b, a+1 ), Set( x, 2 ); Set( y, x+2 ) ) 将同时计算 Set( a, 1 ); Set( b, a+1 ) 和 Set( x, 2 ); Set( y, x+2 ) 在本例中，公式内的依赖项可正常运行：a 将在 b 前设置，x 将在 y 前设置。

根据应用运行于的设备或浏览器，实际可能只有少量的公式会同时求值。 Concurrent 使用提供的功能，并在所有公式计算完成后完成。

如果（在高级设置中）启用公式级错误管理，Concurrent 将返回参数命令中遇到的第一个错误；否则返回空白。 如果所有公式都成功，则返回 true。 如果一个公式失败，则该公式的其余部分将会停止，但其他公式将继续计算。

只能在[行为公式](../working-with-formulas-in-depth.md)中使用 Concurrent。

## <a name="syntax"></a>语法
**Concurrent**( *Formula1*, *Formula2* [, ...] )

* *Formula(s)* - 必需。 要同时计算的公式。 必须提供至少两个公式。

## <a name="examples"></a>示例

#### <a name="loading-data-faster"></a>更快地加载数据

1. 创建应用，并从 Common Data Service for Apps、SQL Server 或 SharePoint 添加四个数据源。 

    此示例使用来自 [SQL Azure 上的示例 Adventure Works 数据库](https://docs.microsoft.com/azure/sql-database/sql-database-get-started-portal)的四个表。 创建数据库后，请使用完全限定的服务器名称（例如 srvname.database.windows.net）从 PowerApps 连接到它：

    ![连接到 Azure 中的 Adventure Works 数据库](media/function-concurrent/connect-database.png)

2. 添加 **[按钮](../controls/control-button.md)** 控件，并将其 OnSelect 属性设置为以下公式：

    **ClearCollect( Product, '[SalesLT].[Product]' );<br> ClearCollect( Customer, '[SalesLT].[Customer]' );<br> ClearCollect( SalesOrderDetail, '[SalesLT].[SalesOrderDetail]' );<br> ClearCollect( SalesOrderHeader, '[SalesLT].[SalesOrderHeader]' )**

3. 在 [Microsoft Edge](https://docs.microsoft.com/microsoft-edge/devtools-guide/network) 或 [Google Chrome](https://developers.google.com/web/tools/chrome-devtools/network-performance/) 中，打开开发人员工具，以便在应用运行时监视网络流量。

1. （可选）打开网络限制，增强这一比较的效果。

4. 按住 Alt 键，选择按钮，然后观察网络流量。

    工具会显示按顺序执行的四个请求，与此示例类似。  示例中删除了实际时间，因为它们将有很大差异。  图标显示，每个调用都在上一个调用完成后启动：

    ![四个网络请求的时间图表，其中每个请求都在上一个完成后启动，从而占用整个时间跨度](media/function-concurrent/chained-network.png)

5. 保存、关闭并重新打开应用。

    PowerApps 会缓存数据，因此再次选择该按钮不一定会产生四个新请求。 每次要测试性能时，都要关闭并重新打开应用。 如果打开了网络限制，最好将其关闭，直到准备好进行另一个测试。

1. 添加第二个 **[按钮](../controls/control-button.md)** 控件，并将其 OnSelect 属性设置为以下公式：

    **Concurrent(<br> &nbsp;&nbsp;&nbsp;&nbsp;ClearCollect( Product, '[SalesLT].[Product]' ),<br> &nbsp;&nbsp;&nbsp;&nbsp;ClearCollect( Customer, '[SalesLT].[Customer]' ),<br> &nbsp;&nbsp;&nbsp;&nbsp;ClearCollect( SalesOrderDetail, '[SalesLT].[SalesOrderDetail]' ),<br> &nbsp;&nbsp;&nbsp;&nbsp;ClearCollect( SalesOrderHeader, '[SalesLT].[SalesOrderHeader]' )<br> )**

    请注意，对第一个按钮添加了相同 ClearCollect 调用，但这一次，它们封装在 Concurrent 函数中，由逗号分隔。

2. 清除浏览器中的网络监视器。

1. 如果在此前使用了网络限制，请将其重新打开。

3. 按住 Alt 键，选择第二个按钮，然后观察网络流量。

    工具会显示同时执行的四个请求，与此示例类似。  再一次，示例中删除了实际时间，因为它们将有很大差异。  图表显示，所有调用在大致相同的时间开始，并不等待上一个调用完成：

    ![四个网络请求的时间图表，四个请求占用约一半的时间跨度](media/function-concurrent/concurrent-network.png)

    这些图表基于相同的刻度。 通过使用 Concurrent，将完成这些操作所用的时间总量减少了一半。 

5. 保存、关闭并重新打开应用。

#### <a name="race-condition"></a>争用条件

1. 向应用添加到 [Microsoft Translator](../connections/connection-microsoft-translator.md) 服务的连接。

2. 添加一个[**Text input**](../controls/control-text-input.md)  控件，然后将其重命名为 TextInput1（如果它具有不同名称）。

3. 添加按钮控件，并将其 OnSelect 属性设置为以下公式：

    **Set( StartTime, Value(Now()) );<br> Concurrent(<br> &nbsp;&nbsp;&nbsp;&nbsp;Set(FRTrans, MicrosoftTranslator.Translate(TextInput1.Text,"fr")); Set(FRTransTime, Value(Now()) ),<br> &nbsp;&nbsp;&nbsp;&nbsp;Set(DETrans, MicrosoftTranslator.Translate(TextInput1.Text,"de")); Set(DETransTime, Value(Now()) )<br> ); <br> Collect( <br> &nbsp;&nbsp;&nbsp;&nbsp;Results, <br> &nbsp;&nbsp;&nbsp;&nbsp;{<br> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Input: TextInput1.Text, <br> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;French: FRTrans, FrenchTime: FRTransTime-StartTime,<br> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;German: DETrans, GermanTime: DETransTime-StartTime,<br> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;FrenchFaster: FRTransTime < DETransTime <br> &nbsp;&nbsp;&nbsp;&nbsp;}<br> )**

4. 添加[**数据表**](../controls/control-data-table.md)控件，然后将其 Items 属性设置为 Results。

1. 在右窗格的“属性”选项卡上，选择“结果”以打开“数据”窗格。

1. 在字段列表中，选中每个字段的复选框，以在数据表中显示它们。

1. （可选）将 Input 字段拖动到列表顶部，并将 FrenchFaster 字段拖动到列表底部。

    ![结果集合中字段的列表](media/function-concurrent/field-list.png) 

6. 在文本输入控件中，键入或粘贴要翻译的短语。

7. 按住 Alt 键，多次选择按钮以填充该表。

    时间以毫秒为单位显示。
  
    ![显示了数据表，其中包含字符串“Hello World”翻译为法语和德语的结果。 有时法语翻译比德语快，有时则相反。](media/function-concurrent/race-condition.png) 

    在某些情况下，法语翻译比德语翻译快，有时则相反。 二者同时开始，但由于各种原因（包括网络延迟和服务器端处理），二者相继返回。

    如果应用依赖于一种语言的翻译率先结束，将出现[争用条件](https://en.wikipedia.org/wiki/Race_condition)。 幸运的是，PowerApps 会标志它能检测到的大多数执行时间依赖项。
