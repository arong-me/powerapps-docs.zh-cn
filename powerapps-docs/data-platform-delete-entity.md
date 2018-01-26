---
title: "删除自定义实体并清除数据 | Microsoft 文档"
description: "删除自定义实体，并清除所有数据。"
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
ms.openlocfilehash: d3e83ad17fcafcfd65aab47b065413c5b72b4f35
ms.sourcegitcommit: 6afca7cb4234d3a60111c5950e7855106ff97e56
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2018
---
# <a name="delete-a-custom-entity"></a>删除自定义实体
可以删除自定义实体，但无法删除标准实体。

1. 在 [powerapps.com](https://web.powerapps.com) 上，展开“Common Data Service”部分，然后单击或点击左侧导航窗格中的“实体”。 在列表上方的搜索栏中键入一个或多个字符即可筛选该实体列表。
2. 在实体列表中，单击或点击要删除的实体，然后单击或点击右上角的回收站图标。
3. 在显示的对话框中，单击或点击“**删除**”来删除该实体。

>[!NOTE]
>删除某个实体时，将删除实体的定义及其包含的所有数据。

>[!NOTE]
>如果删除某个应用中所使用的实体，则可能会中断该应用。

>[!NOTE]
>如果实体 A 具有到实体 B 的 [查找字段](data-platform-entity-lookup.md)，则可能需要删除实体 B，然后才能删除实体 A。

