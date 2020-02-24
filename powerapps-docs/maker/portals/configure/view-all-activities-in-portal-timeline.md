---
title: 查看门户时间线中的活动 | MicrosoftDocs
description: 有关查看门户时间线中的所有活动的说明。
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 12/12/2019
ms.author: dileeps
ms.reviewer: tapanm
ms.openlocfilehash: b1e98d7233967345f3629fa99f41e406204243c4
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2020
ms.locfileid: "2980275"
---
# <a name="view-activities-in-a-portal-timeline"></a>查看门户时间线中的活动

处理服务案例或与客户交互时，可以创建活动，如约会、电子邮件或电话联络。 在支持门户中导航至时间线时，可能无法找到此活动，因为默认情况下，门户时间线中不显示所有活动。 

若要查看门户时间线中的所有活动： 

1. 将 **CustomerSupport/DisplayAllUserActivitiesOnTimeline** 站点设置设置为 true。  
    
    > [!NOTE]
    > 如果不存在 **DisplayAllUserActivitiesOnTimeline** 站点设置，则可以创建此名称的新设置。

2. 如果不存在，请添加要包含在视图筛选器中的活动类型：  
    1. 转到[**设置**](https://docs.microsoft.com/power-platform/admin/admin-settings#app-settings) > **自定义** > **自定义系统**。
    2. 选择**活动**实体，然后展开**视图**。
    3. 编辑**门户时间线视图**。
    4. 更新**编辑筛选条件**，然后添加所需活动类型，如**约会、电子邮件或电话联络**。
    5. **保存**并**发布**自定义设置。 

    > [!IMPORTANT]
    > 准备自定义项可能需要花费一些时间。 如果看到一条消息说明浏览器页面不响应，请等待页面响应，请勿将其关闭。

3. 由于这是门户元数据更改，所以请[清除服务器端缓存](../admin/clear-server-side-cache.md)以确保门户中显示更新后的数据。
