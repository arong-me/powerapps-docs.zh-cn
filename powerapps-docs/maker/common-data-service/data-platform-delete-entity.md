---
title: 删除自定义实体并清除数据的快速入门 | Microsoft Docs
description: 删除自定义实体并清除所有数据的快速入门
services: powerapps
documentationcenter: na
author: clwesene
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 3/21/2018
ms.author: clwesene
ms.openlocfilehash: 399d3e8bac215df7612ac12d922dfe644dc59f96
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2018
---
# <a name="quickstart-delete-a-custom-entity"></a>快速入门：删除自定义实体
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

