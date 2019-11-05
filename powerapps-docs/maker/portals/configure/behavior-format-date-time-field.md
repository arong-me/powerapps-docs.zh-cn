---
title: Common Data Service 中的日期和时间字段的行为和格式 |MicrosoftDocs
description: 门户中使用的日期和时间字段的行为和格式。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 785b5fa7def4a5b8e4964e888567d64643405708
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2019
ms.locfileid: "73553316"
---
# <a name="behavior-and-format-of-the-date-and-time-field"></a>日期和时间字段的行为和格式

在 Common Data Service 中，在许多系统实体字段中使用日期和时间数据类型。 例如，您可以显示某个帐户在市场营销活动中的最后使用时间，或显示升级案例的日期和时间。 你还可以创建包含日期和时间字段的自定义实体。 根据字段表示的内容，可以为门户窗体和网格选择以下字段行为之一： 
- **用户本地**：字段值以用户的本地时间显示，并根据其当前门户语言/区域设置进行格式化。 值以 UTC 时区格式存储在 Common Data Service 中。 当位于不同时区的 Common Data Service 中的用户（或另一个门户用户）查看该值时，他们将看到它转换为自己的时区。
- **仅限日期**：字段值仅包含日期，显示时不带时区转换。 值的时间部分始终为 12:00 AM。 一个用户输入的值在不同时区中的其他用户看来相同（例如，出生日期）。
  
  > [!Note]
  > 此字段的行为在保存后将无法更改。
  
- **独立于**时区：字段值包含日期和时间，并显示，无时区转换。 一个用户输入的值在不同时区中被其他用户看见。
  
  > [!Note]
  > 此字段的行为在保存后将无法更改。

还可以通过创建以下站点设置来覆盖门户上使用的默认日期/时间格式：
- DateTime/DateFormat：门户上使用的日期格式。 
- DateTime/TimeFormat：门户上使用的时间格式。 
- DateTime/DateTimeFormat：门户上使用的完整日期和时间的格式。

默认情况下，门户使用由网站语言设置指定的标准日期/时间格式。
[此处](https://docs.microsoft.com/dotnet/standard/base-types/custom-date-and-time-format-strings)指定了接受的日期/时间格式。
