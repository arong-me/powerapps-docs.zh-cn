---
title: 删除自定义实体 | Microsoft Docs
description: 如何在 PowerApps 中删除自定义实体和清除所有数据的分步说明
author: lancedMicrosoft
manager: kfile
ms.service: powerapps
ms.component: cds
ms.topic: conceptual
ms.date: 03/21/2018
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 8b4b9fb7942a7977bf6795ca21985b93c5469d26
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2019
ms.locfileid: "2754903"
---
# <a name="delete-a-custom-entity"></a>删除自定义实体
您可以删除自定义实体，但无法删除标准实体。

1. 在 [powerapps.com](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) 上，展开**数据**部分并单击或点按左侧导航窗格中的**实体**。

    ![实体详细信息](./media/data-platform-cds-create-entity/entitylist.png "实体列表")

2. 在实体列表中，单击或点按要删除的实体，然后单击或点按命令栏中的**删除实体**选项。

3. 在显示的对话框中，单击或点按**删除**删除实体。

>[!NOTE]
>在删除实体时，将删除实体定义和实体包含的所有数据。 实体和实体中的数据如果删除将无法恢复。

>[!NOTE]
>如果删除该应用程序中使用的实体，则可能中断应用程序或流。

>[!NOTE]
>如果实体 A 有实体 B 的[查找字段](data-platform-entity-lookup.md)，您可能必须删除实体 B，然后才能删除实体 A。

