---
title: 删除自定义实体 | Microsoft Docs
description: 有关如何删除自定义实体并清除 PowerApp 中的所有数据的分步说明
author: clwesene
manager: kfile
ms.service: powerapps
ms.component: cds
ms.topic: conceptual
ms.date: 03/21/2018
ms.author: clwesene
ms.openlocfilehash: 6ef9dc3a1c82fdee9927ffd533ed41386345eaf7
ms.sourcegitcommit: b3b6118790d6b7b4285dbcb5736e55f6e450125c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2018
---
# <a name="delete-a-custom-entity"></a>删除自定义实体
可以删除自定义实体，但无法删除标准实体。

1. 在 [powerapps.com](https://web.powerapps.com) 上，展开“数据”部分，然后单击或点击左侧导航窗格中的“实体”。

    ![实体详细信息](./media/data-platform-cds-create-entity/entitylist.png "实体列表")

2. 在实体列表中，单击或点击要删除的实体，然后单击或点击命令栏中的“删除实体”选项。

3. 在显示的对话框中，单击或点击“**删除**”来删除该实体。

>[!NOTE]
>删除某个实体时，将删除实体的定义及其包含的所有数据。 删除实体和其中的数据后，无法恢复。

>[!NOTE]
>如果删除某个应用中所使用的实体，则可能会中断该应用或流。

>[!NOTE]
>如果实体 A 具有到实体 B 的 [查找字段](data-platform-entity-lookup.md)，则可能需要删除实体 B，然后才能删除实体 A。

