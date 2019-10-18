---
title: openUrl |Microsoft Docs
description: ''
keywords: ''
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 590078f3-c604-4bd0-ac74-9cf6d8806802
ms.openlocfilehash: 21e097c739364b6cdb3935654ae9bf2b61143a06
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2019
ms.locfileid: "72342268"
---
# <a name="openurl"></a>openUrl

[!INCLUDE [openurl-description](includes/openurl-description.md)]

## <a name="available-for"></a>适用于 

模型驱动应用

## <a name="syntax"></a>语法

`context.navigation.openUrl(url, options)`

## <a name="parameters"></a>参数

| 参数名称|类型|需要|描述|
| ------------- |----|--------|-----------|
|链接|`string`|是|要打开的 Url。|
|选项|`OpenUrlOptions`|否|用于打开 URL 的选项。 OpenUrlOptions 具有以下参数： <br/>- **高度**： `Number`。 窗口的高度，以像素为单位显示结果页。<br/>- **width**： `Number`。 要以像素为单位显示结果页的窗口宽度。|


### <a name="related-topics"></a>相关主题

[导航](../navigation.md)<br/>
[PowerApps 组件框架 API 参考](../../reference/index.md)<br/>
[PowerApps 组件框架概述](../../overview.md)