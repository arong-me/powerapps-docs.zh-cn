---
title: "导入或导出数据 | Microsoft 文档"
description: "导入或导出实体。"
services: powerapps
documentationcenter: na
author: kfend
manager: kfend
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 12/06/2016
ms.author: kfend
ms.openlocfilehash: 880881b31362d38ed0d44126245dd96d2a74150f
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2017
---
# <a name="import-or-export-data-from-the-common-data-service"></a>将数据导入或导出 Common Data Service
可以采用以下两种方式之一，将数据导入或导出 Common Data Service：

* 若要一次性批量导入或导出数据，可以对多个实体使用 Microsoft Excel。
* 若要将一个实体的数据持续导入或导出其他服务（如，Dynamics 365、Salesforce 或 Excel 文件）。 要设置正在进行的导入或导出，可以使用 [Microsoft Flow](https://flow.microsoft.com)。

## <a name="import-or-export-data-once"></a>一次导入或导出数据
### <a name="import-data-from-excel"></a>从 Excel 导入数据
1. 在 [powerapps.com](https://web.powerapps.com) 上，展开“Common Data Service”部分，然后单击或点击左侧导航窗格中的“实体”。
2. 在“**新建实体**”旁边，单击或点击省略号，然后单击或点击“**导入数据**”。
3. 选择要将数据导入其中的实体，然后单击或点击“**下一步**”。
4. 单击或点击“搜索”。 选择要导入其中数据的文件。
5. 如果“映射状态”不是带绿色复选标记的“匹配”，则需要在实体字段和 Excel 文件列之间指定映射。 要映射这些列，可执行以下操作：
   1. 单击或点击“**显示映射**”。
   2. 对于每个实体字段，选择 Excel 文件中的匹配列。
   3. 单击或点击“**保存更改**”。
6. 单击“**导入**”。

### <a name="export-data-to-excel"></a>将数据导出到 Excel
可以一次性导出标准实体或自定义实体的数据，并能一次导出多个实体的数据。 如果从多个实体导出数据，则每个实体的数据导出到各自的 Microsoft Excel 文件中。

1. 在 [powerapps.com](https://web.powerapps.com) 上，单击或点击左侧导航窗格中的“实体”。
2. 在“**新建实体**”旁边，单击或点击省略号，然后单击或点击“**导出数据**”。
3. 选择要从中导出数据的实体，然后单击或点击“**导出到 Excel**”。
4. 出现“**导出完成**”时，单击或点击“**下载导出的数据**”即可下载数据。

## <a name="use-microsoft-flow-to-set-up-ongoing-import-or-export"></a>使用 Microsoft Flow 设置正在进行的导入或导出
可以同时为单个标准实体或自定义实体设置正在进行的导入或导出。 可以连接的一些可能位置包括：

* Dynamics 365
* Salesforce
* 存储在任何云文件提供程序中的 Microsoft Excel 文件
* 云中和本地的 Microsoft SQL 数据库
* 为了连接你自己的系统而定义的自定义连接器

目前，如果使用 Microsoft Flow 导入或导出数据，无法获得完全同步服务。 向一个服务添加某对象时，它也会导入另一系统。 但是，这意味着如果将对象从某个系统删除，其他系统不会同时删除该对象。

如何设置导入取决于要导入对象是否已有模板。 如果模板存在，则可以将其设置为将数据从一个系统复制到另一个系统。 有关详细信息，请参阅[创建使用 Microsoft Common Data Service 的流](https://flow.microsoft.com/documentation/common-data-model-intro/)。 不过，如果没有此类模板，则需要创建可以使用数据库的流。 如需了解更多详情，请参阅[如何从头开始创建流](https://flow.microsoft.com/documentation/get-started-logic-flow/)。

