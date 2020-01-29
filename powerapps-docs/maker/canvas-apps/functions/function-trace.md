---
title: Trace 函数 | Microsoft Docs
description: 提供 Power Apps Test Studio 中 Trace 函数的参考信息（包括语法）
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 12/19/2018
ms.author: aheneay
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 86d28400e0eaea89b59286df173d0e67655bb7a5
ms.sourcegitcommit: 6b2961308c41867756ecdd55f55eccbebf70f7f0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2020
ms.locfileid: "76541235"
---
# <a name="trace-function"></a>Trace 函数 

与 Test Studio 一起使用时，Trace 是一个可选表达式，可用于在来自 OnTestCaseComplete 事件的测试结果中提供其他信息  。 Trace 事件消息以及通过和失败断言的所有消息都包含在 TestCaseResult 记录的 Traces 表中。 Traces 表有两个属性：Message 和 Timestamp。 

如果已允许应用将遥测数据发送到 Azure Application Insights，则还可以使用 Trace 函数将自定义事件或诊断信息发送到 Application Insights 资源。 可以在 Application Insights 中检查此数据，以帮助诊断问题或了解应用和功能的使用情况。 测试中使用的 Trace 信息也将记录在 Application Insights 中。 还可以在 Power Apps Monitor 工具中查看所有 Trace 消息，这将有助于调试或识别应用中实时诊断会话的问题。   

## <a name="syntax"></a>语法

Trace(message, severity, custom_record) 

- *Message* - 必需。 要跟踪的信息。 在测试中，这会在 TestCaseResult 记录的 Traces 表中创建一条记录。 
- Severity - 可选  。 Application Insights 中记录的 Trace 的严重性级别。 选项包括 Information、Warning 或 Error。 
- custom_record - 可选  。 包含将记录到 Application Insights 中的自定义数据的记录。 
  

### <a name="see-also"></a>另请参阅

[Test Studio 概述](../test-studio.md) <br>
[使用 Test Studio](../working-with-test-studio.md)
