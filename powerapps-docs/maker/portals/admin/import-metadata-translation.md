---
title: 导入元数据翻译 | MicrosoftDocs
description: 导入元数据翻译的说明。
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/21/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: a648efdea5538dbedc431f0c3299b23948d39eb2
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2020
ms.locfileid: "2978005"
---
# <a name="import-metadata-translation"></a>导入元数据翻译

在设置门户时，将在组织上安装与门户有关的解决方案。 在安装解决方案期间，仅安装当前在组织中激活的语言的解决方案元数据翻译（例如：字段名称、表单名称和视图名称）。 如果您将来激活新的语言，将不自动为新激活的语言安装元数据。 若要获取新激活语言的元数据翻译，则必须从 Power Apps 门户管理中心导入元数据翻译。

## <a name="to-import-metadata-translation"></a>若要导入元数据转换

1.  打开 [Power Apps 门户管理中心](admin-overview.md)。

2.  转到**门户操作** > **获取最新的元数据翻译**。 此时将显示询问是否更新门户解决方案的确认窗口。

3.  选择**更新**。 门户解决方案将使用最新的元数据翻译进行更新。

> [!Note]
> - 如果提供了最新的门户包版本，则不会进行更新。 门户解决方案在相同版本中进行更新。 若要基于最新可用的包升级您的门户解决方案，需访问解决方案管理中心。
> - 如果用户已经修改 Common Data Service 中的任何数据，在更新期间，该现有数据不会被覆盖。
> - 如果正在安装门户解决方案，则不会触发解决方案更新。