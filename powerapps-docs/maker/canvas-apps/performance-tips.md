---
title: 优化画布应用性能 | Microsoft Docs
description: 按照本主题中的最佳做法提高你在 PowerApps 中创建的画布应用的性能。
author: yingchin
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 08/31/2018
ms.author: yingchin
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 6406afad9079895a0da38c7f1f6e3961f2e37fa1
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61536339"
---
# <a name="optimize-canvas-app-performance-in-powerapps"></a>在 PowerApps 中优化画布应用性能
Microsoft 正致力于完善在 PowerApps 平台上运行的所有应用的性能。 但你可以按照本主题中的最佳做法提高你所创建的应用的性能。

当用户打开一个应用时，在显示任何用户界面之前都会执行以下操作： 
1. 对用户进行身份验证 - 如果用户之前从未打开过该应用，则会提示用户使用应用所需的任何连接的凭据进行登录。 如果同一用户再次打开该应用，则系统可能会再次提示该用户，具体要取决于组织的安全策略。 
2. 获取元数据 - 检索元数据，如运行应用的 PowerApps 平台的版本以及必须从中检索数据的源。 
3. 初始化应用 - 执行 OnStart 属性中指定的任何任务。 
4. 呈现屏幕 - 使用应用已填充数据的控件呈现第一个屏幕。 如果用户打开其他屏幕，则应用会使用相同过程呈现这些屏幕。  

## <a name="limit-data-connections"></a>限制数据连接 
不要从同一应用连接到 30 个以上的数据源。 应用会提示新用户登录到每个连接器，因此，每个附加连接器会增加启动应用所需的时间。 运行应用且应用请求来自该源的数据时，每个连接器都会需要 CPU 资源、内存和网络带宽。 

在运行应用的同时打开 [Microsoft Edge](https://docs.microsoft.com/microsoft-edge/devtools-guide/network) 或 [Google Chrome](https://developers.google.com/web/tools/chrome-devtools/network-performance/) 中的开发人员工具可以快速度量应用的性能。 您的应用程序很有可能要花费的时间超过 15 秒，如果它经常请求从 30 多个数据源，如 Common Data Service、 Azure SQL、 SharePoint 和 OneDrive 上的 Excel 的数据返回数据。  

## <a name="limit-the-number-of-controls"></a>限制控件数 
不要向同一应用添加 500 个以上的控件。 PowerApps 会生成 HTML DOM 以呈现每个控件。 添加的控件越多，PowerApps 所需的生成时间就越多。 

在某些情况下，改用库而非单个控件，可以获得相同结果并更快地启动应用。 此外，你可能需要在同一屏幕上减少控件类型数。 某些控件（如 PDF 查看器、数据表和组合框）会拉入大型执行脚本，并需要较长时间才能呈现。 

## <a name="optimize-the-onstart-function"></a>优化 OnStart 函数
使用 [**ClearCollect**](functions/function-clear-collect-clearcollect.md) 函数可本地缓存数据（如果在用户会话期间未更改）。 此外，使用 [**Concurrent**](functions/function-concurrent.md) 函数可同时加载数据源。

如[本参考主题](functions/function-concurrent.md)中所示，你可以使用 Concurrent 将应用加载数据所需的时间减少一半。

如果没有 Concurrent 函数，此公式会逐个加载四个表：

    ClearCollect( Product, '[SalesLT].[Product]' );
    ClearCollect( Customer, '[SalesLT].[Customer]' );
    ClearCollect( SalesOrderDetail, '[SalesLT].[SalesOrderDetail]' );
    ClearCollect( SalesOrderHeader, '[SalesLT].[SalesOrderHeader]' )

你可以在浏览器的开发人员工具中确认以下行为：

![串行 ClearCollect](./media/performance-tips/perfconcurrent1.png)
    
在 Concurrent 函数中，你可以用双引号将同一公式引住，以减少该操作所需的总时间：

    Concurrent( 
        ClearCollect( Product, '[SalesLT].[Product]' ),
        ClearCollect( Customer, '[SalesLT].[Customer]' ),
        ClearCollect( SalesOrderDetail, '[SalesLT].[SalesOrderDetail]' ),
        ClearCollect( SalesOrderHeader, '[SalesLT].[SalesOrderHeader]' ))
        
进行以下更改后，应用会并行提取表： 

![并行 ClearCollect](./media/performance-tips/perfconcurrent2.png)  

## <a name="cache-lookup-data"></a>缓存查找数据
使用 Set 函数可本地缓存来自查找表的数据，以避免重复从源中检索数据。 当数据在会话期间可能不更改的情况下，该技术就可用来优化性能。 如本示例中所示，从源中检索数据，然后本地引用该数据，直到用户关闭应用。 

    Set(CustomerOrder, Lookup(Order, id = “123-45-6789”));
    Set(CustomerName, CustomerOrder.Name);
    Set(CustomerAddress, CustomerOrder.Address);
    Set(CustomerEmail, CustomerOrder.Email);
    Set(CustomerPhone, CustomerOrder.Phone);

通常情况下，联系人信息不会频繁更改，也不会更改默认值和用户信息。 因此，通常可以将此技术与 Defaults 和 User 函数结合使用。 

## <a name="avoid-controls-dependency-between-screens"></a>避免屏幕之间的控件依赖项
如果控件的值取决于不同屏幕上的控件值，请使用变量、集合或数据源引用来管理数据。

## <a name="use-global-variables"></a>使用全局变量
若要将应用的状态从一个屏幕传递到另一个屏幕，请使用 [**Set**](functions/function-set.md) 函数（而不是使用 Navigate 和 UpdateContext) 函数）创建或修改全局变量值。

## <a name="use-delegation"></a>使用委派
如果可能，请尽量使用将数据处理委派给数据源的函数，而不是将数据检索到本地设备进行处理的函数。 如果应用必须本地处理数据，则该操作将需要更多的处理能力、内存和网络带宽，尤其是在数据集较大时。

如[本列表](delegation-list.md)中所示，不同数据源支持来自不同函数的委派：

![使用委派](./media/performance-tips/perfdelegation1.png)

例如，SharePoint 列表支持来自 [**Filter**](functions/function-filter-lookup.md) 函数（而不是 [**Search**](functions/function-filter-lookup.md) 函数）的委派。 因此，如果 SharePoint 列表包含 500 个以上的项，则应使用 Filter（而不是 Search）来查找库中的项。 有关更多提示，请参阅[在 PowerApps 中使用大型 SharePoint 列表](https://powerapps.microsoft.com/blog/powerapps-now-supports-working-with-more-than-256-items-in-sharepoint-lists/)（博客文章）。 

## <a name="use-delayed-load"></a>使用延迟加载
如果应用有 10 个以上的屏幕，无规则以及位于多个屏幕上且直接绑定到数据源的多个控件，请启用用于延迟加载的[实验性功能](working-with-experimental.md)。 如果你构建此类型的应用但不启用此功能的话，应用性能可能会受到影响，因为必须填充所有屏幕中的控件，即使在未打开的屏幕上也是如此。 此外，每当数据源发生更改时（诸如当用户添加记录时），都必须更新应用的所有屏幕。

## <a name="working-with-large-data-sets"></a>使用大型数据集
使用可以委派的数据源和公式来保持应用正常运行，让用户可以访问他们所需全部信息的同时，还能够避免超过不可委派查询的 2000 数据行限制。 对于用户可在其上搜索、筛选或排序数据的数据记录列，这些列的索引如 [SQL Server](https://docs.microsoft.com/sql/relational-databases/sql-server-index-design-guide?view=sql-server-2017) 和 [SharePoint](https://support.office.com/article/Add-an-index-to-a-SharePoint-column-f3f00554-b7dc-44d1-a2ed-d477eac463b0) 文档中所述设计得当。  

## <a name="republish-apps-regularly"></a>定期重新发布应用
[重新发布应用](https://powerapps.microsoft.com/blog/republish-your-apps-to-get-performance-improvements-and-additional-features/)（博客文章），以从 PowerApps 平台中获取性能改进和其他功能。

## <a name="avoid-repeating-the-same-formula-in-multiple-places"></a>避免重复多个位置中的相同公式
如果多个属性运行同一个公式 （尤其是如果它是复杂），请考虑将其设置一次，然后引用后续条件中的第一个属性的输出。 例如，未设置**DisplayMode**为相同的复杂公式 A、 B、 C、 D 和 E 控件的属性。 与此相反，设置 A 的**DisplayMode**属性设为复杂的公式中，设置 B 的**DisplayMode**属性设置为 A 的结果**DisplayMode**属性等的 C、 D 和 e。

## <a name="enable-delayoutput-on-all-text-input-controls"></a>所有文本输入控件上启用 DelayOutput
如果你有多个公式或引用的值的规则**文本输入**控件，将设置**DelayedOutput**为 true 的控件的属性。 **文本**只有在输入中快速连续的击键记录有时间后将更新该控件的属性。 公式或规则不会运行多次，以及如何改善应用性能。

## <a name="avoid-using-formupdates-in-rules-and-formulas"></a>避免在规则和公式中使用 Form.Updates
如果使用引用规则或公式中的用户输入值**Form.Updates**变量时，它循环访问窗体的所有数据卡，并创建一条记录每次。 若要使应用能够更高效，引用直接从数据卡或控件值的值。

## <a name="next-steps"></a>后续步骤
审阅[编码标准](https://aka.ms/powerappscanvasguidelines)最大化应用程序性能和使应用程序更易于维护。
