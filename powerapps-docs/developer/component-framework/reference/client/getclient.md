---
title: getClient |Microsoft Docs
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
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
ms.assetid: 4b7c18f8-cd00-4f39-8f88-ed9306d6a055
ms.openlocfilehash: 503d24d97061548132f912351a58fbce68082d18
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2019
ms.locfileid: "72345741"
---
# <a name="getclient"></a>getClient

[!INCLUDE [getclient-description](includes/getclient-description.md)]

## <a name="syntax"></a>语法

`context.client.getClient()`

## <a name="available-for"></a>适用于 

模型驱动应用和画布应用（实验性预览） 



## <a name="return-value"></a>返回值

类型： `String`

返回一个值，该值指示脚本正在执行的客户端。

|||
|-----|-----|
|站点| Web 应用程序或统一的接口|
|Outlook| Outlook|
|便携式| 移动应用|



### <a name="related-topics"></a>相关主题

[客户端](../client.md)<br/>
[PowerApps 组件框架 API 参考](../../reference/index.md)<br/>
[PowerApps 组件框架概述](../../overview.md)