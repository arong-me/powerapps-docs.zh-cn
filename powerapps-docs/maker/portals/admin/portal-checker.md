---
title: 确定并修复门户的客户问题 | MicrosoftDocs
description: 了解如何确定并修复门户的客户问题。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: b361efd6a1f44485e9b7337e3e5b3a29c1a826d4
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "2709615"
---
# <a name="portal-checker"></a>门户检查器

门户检查器是一个自助服务诊断工具，可供门户管理员确定门户中的常见问题。 门户检查器通过查看各种配置参数帮助确定门户的问题，并提供有关解决方法的建议。

运行门户检查器时，结果在**诊断结果**部分中以网格格式显示。 结果网格中包含下面的列：

- **问题**：显示门户面临的最大问题；例如，性能问题。
- **类别**：显示问题可归类的最高区域；例如，设置、解决方案升级等。
- **结果**：显示问题的状态；例如，错误、警告等。

默认情况下，网格中的信息按**结果**列以下面的顺序排序：错误、警告、通过。

> [!div class=mx-imgBorder]
> ![诊断结果](../media/diagnostic-results.png "诊断结果")

可展开问题以查看详细信息和缓解步骤。 如果需要执行任何操作才能缓解，将显示用于执行此操作的按钮。 也可以提供有关缓解是否成功的反馈。

> [!div class=mx-imgBorder]
> ![在诊断结果中展开问题](../media/diagnostic-results-issue-expand.png "在诊断结果中展开问题")

如果需要，可以重新运行诊断检查，这将使用更新后的数据刷新结果。

> [!NOTE]
> 如果门户关闭或启用了 IP 地址筛选，将不会对门户运行某些诊断检查。

有关门户检查器可诊断的常见问题列表，请参阅[门户检查器可诊断的常见门户问题及其最佳实践](https://docs.microsoft.com/dynamics365/customer-engagement/portals/portal-faq)。

若要运行门户检查器：

1.  打开 [PowerApps 门户管理中心](admin-overview.md)。

2.  转到**运行门户检测器**。

    > [!div class=mx-imgBorder]
    > ![运行门户检测器](../media/run-diagnostics.png "运行门户检测器")

3.  选择**运行门户检测器**。 将启动诊断会话并收集有关客户问题的数据。 将在**诊断结果**部分中显示结果。

    > [!div class=mx-imgBorder]
    > ![诊断结果](../media/diagnostic-results.png "诊断结果")

4.  若要重新运行诊断检查，请选择**刷新结果**。

    > [!div class=mx-imgBorder]
    > ![刷新诊断结果](../media/diagnostic-results-refresh.png "刷新诊断结果")
