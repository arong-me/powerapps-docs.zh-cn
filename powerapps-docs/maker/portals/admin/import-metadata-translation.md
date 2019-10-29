---
title: 导入元数据转换 |MicrosoftDocs
description: 导入元数据转换的说明。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/21/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: f05a0dfb6424b11e71cf5bf4324d5e3db03a7897
ms.sourcegitcommit: 57b968b542fc43737330596d840d938f566e582a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/22/2019
ms.locfileid: "72977970"
---
# <a name="import-metadata-translation"></a>导入元数据转换

设置门户时，将在组织中安装与门户相关的解决方案。 在解决方案的安装过程中，解决方案元数据转换（例如，字段名称、窗体名称和视图名称）仅适用于组织中当前激活的语言。 如果以后激活一种新语言，则不会自动为新激活的语言安装元数据。 若要获取新激活语言的元数据转换，必须从 PowerApps 门户管理中心导入元数据翻译。

## <a name="to-import-metadata-translation"></a>导入元数据转换

1.  打开[PowerApps 门户管理中心](admin-overview.md)。

2.  转到**门户操作** > **获取最新的元数据翻译**。 将显示一个确认窗口，询问是否更新门户解决方案。

3.  选择 "**更新**"。 门户解决方案将更新为最新的元数据翻译。

> [!Note]
> - 如果最新版本的门户包可用，则它不会更新。 门户解决方案在同一版本中进行了更新。 若要根据最新的可用包升级门户解决方案，需要访问解决方案管理中心。
> - 如果用户已在 Common Data Service 中修改了任何数据，则在更新过程中不会覆盖现有数据。
> - 如果正在安装门户解决方案，则无法触发解决方案更新。