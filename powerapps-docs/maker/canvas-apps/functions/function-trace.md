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
ms.openlocfilehash: 927b8dae59a4dc6fc55d74c1998b0d434eb8356c
ms.sourcegitcommit: d500f44e77747a3244b6691ad9b3528e131dbfa5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2020
ms.locfileid: "79133579"
---
# <a name="trace-function"></a>Trace 函数 

与 Test Studio 一起使用时，Trace 是一个可选表达式，可用于在来自 OnTestCaseComplete 事件的测试结果中提供其他信息。 Trace 事件消息以及通过和失败断言的所有消息都包含在 TestCaseResult 记录的 Traces 表中。 Traces 表有两个属性：Message 和 Timestamp。 

还可以在应用中定义跟踪消息。 可以在 Power Apps 监视工具中查看这些内容以及其他应用活动，以帮助调试或识别应用的实时诊断信息的问题。 如果已允许应用将遥测数据发送到 Azure Application Insights，则还可以使用 Trace 函数将自定义事件或诊断信息发送到 Application Insights 资源。 可以在 Application Insights 中检查此数据，以帮助诊断问题或了解应用和功能的使用情况。 测试中使用的 Trace 信息也将记录在 Application Insights 中。 当监视器从 Canvas studio 播放时，将无法在 "监视" 工具中使用测试跟踪信息。 

## <a name="syntax"></a>语法

*Trace （message，trace_severity，custom_record）*

- *Message* - 必需。 要跟踪的信息。 在测试中，这会在 TestCaseResult 记录的 Traces 表中创建一条记录。 
- *Trace_severity* -可选。 Application Insights 中记录的 Trace 的严重性级别。 选项包括 TraceSeverity、TraceSeverity 或 TraceSeverity。 
- custom_record - 可选。 包含将记录到 Application Insights 中的自定义数据的记录。 
  

### <a name="see-also"></a>另请参阅

[Test Studio 概述](../test-studio.md) <br>
[使用 Test Studio](../working-with-test-studio.md)
