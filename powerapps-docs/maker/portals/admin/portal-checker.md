---
title: 使用门户标识并解决客户问题 |MicrosoftDocs
description: 了解如何识别和解决门户的客户问题。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: b361efd6a1f44485e9b7337e3e5b3a29c1a826d4
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/11/2019
ms.locfileid: "72976176"
---
# <a name="portal-checker"></a>门户检查器

门户网站检查器是一种自助服务诊断工具，可供门户管理员用来识别其门户中的常见问题。 门户检查器通过查看不同的配置参数并提供有关如何修复这些参数的建议，帮助确定你的门户的问题。

运行门户检查器时，结果将以网格格式显示在 "**诊断结果**" 部分中。 "结果" 网格具有以下列：

- **问题**：显示客户面临的顶级问题;例如，性能问题。
- **类别**：显示可以分类的问题的顶级区域;例如，设置、解决方案升级等。
- **Result**：显示问题的状态;例如，错误、警告等。

默认情况下，网格中的信息按 "**结果**" 列按以下顺序排序： "错误"、"警告" 和 "通过"。

> [!div class=mx-imgBorder]
> ![诊断]结果(../media/diagnostic-results.png "诊断结果")

你可以展开问题以查看详细信息和缓解措施。 如果缓解操作需要执行任何操作，则会看到一个用于执行该操作的按钮。 你还可以提供有关缓解是否有用的反馈。

> [!div class=mx-imgBorder]
> ![展开诊断结果中的问题](../media/diagnostic-results-issue-expand.png "展开诊断结果中的问题")

如果需要，您可以重新运行诊断检查，这会刷新包含更新数据的结果。

> [!NOTE]
> 如果关闭了门户或启用了 IP 地址筛选，则无法在门户上运行某些诊断检查。

有关门户检查器工具所诊断的常见问题的列表，请参阅[门户网站检查程序诊断的常见门户问题及其最佳实践](https://docs.microsoft.com/dynamics365/customer-engagement/portals/portal-faq)。

运行门户网站检查程序：

1.  打开[PowerApps 门户管理中心](admin-overview.md)。

2.  请参阅**运行门户网站检查**程序。

    > [!div class=mx-imgBorder]
    > ![运行门户检查]程序(../media/run-diagnostics.png "运行门户检查")程序

3.  选择 "**运行门户网站检查器**"。 诊断会话将启动并收集有关客户问题的数据。 结果将显示在 "**诊断结果**" 部分中。

    > [!div class=mx-imgBorder]
    > ![诊断]结果(../media/diagnostic-results.png "诊断结果")

4.  若要重新运行诊断检查，请选择 "**刷新结果**"。

    > [!div class=mx-imgBorder]
    > ![刷新诊断结果](../media/diagnostic-results-refresh.png "刷新诊断结果")
