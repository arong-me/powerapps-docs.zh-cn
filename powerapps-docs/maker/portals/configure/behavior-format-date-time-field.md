---
title: Common Data Service 中的日期和时间字段的行为和格式 | MicrosoftDocs
description: 门户中使用的日期和时间字段的行为和格式。
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: fe9a2e6e8cef5f2199eb4bd5aa98aacea8d14e67
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2020
ms.locfileid: "2979241"
---
# <a name="behavior-and-format-of-the-date-and-time-field"></a>行为和日期及时间字段的格式

在 Common Data Service 中，日期和时间数据类型在许多系统实体字段中使用。 例如，您可以显示客户市场营销活动中最后使用是什么时候，或显示案例升级的日期和时间。 您还可以创建包括日期和时间字段的自定义实体。 根据字段所表示的含义，您可以为门户窗体和网格选择以下其中一个字段行为： 
- **用户当地时间**：根据用户的当前门户语言/区域设置以用户的当地时间和格式显示的字段值。 该值以 UTC 时区格式存储在 Common Data Service 中。 当位于不同时区的 Common Data Service 中的用户（或其他门户用户）查看该值时，他们看到的是转换为自己所在时区的值。
- **仅限日期**：这些字段值仅包含日期且不转换时区进行显示。 该值的时间部分始终为 12:00 AM。 用户输入的值与不同时区的其他用户看到的值相同（例如，生日）。
  
  > [!Note]
  > 此字段行为在保存后不能更改。
  
- **时区无关**：这些字段值包含日期和时间，且不转换时区进行显示。 用户输入的值与不同时区的其他用户看到的值相同。
  
  > [!Note]
  > 此字段行为在保存后不能更改。

您还可以通过创建以下站点设置来覆盖要在门户上使用的默认日期/时间格式：
- DateTime/DateFormat：在门户上使用的日期格式。 
- DateTime/TimeFormat：在门户上使用的时间格式。 
- DateTime/DateTimeFormat：在门户上使用的完整日期和时间的格式。

默认情况下，门户使用网站语言设置指定的标准日期/时间格式。
已接受的日期/时间格式在[此处](https://docs.microsoft.com/dotnet/standard/base-types/custom-date-and-time-format-strings) 指定。
