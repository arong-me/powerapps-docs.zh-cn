---
title: TrackContainerResize |Microsoft Docs
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
ms.assetid: c5f482c2-dde2-460b-89a7-39e0efcc5704
ms.openlocfilehash: 8f9bc1ef17bdcb762e992d9f77dcdcd7ba1e8c50
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2019
ms.locfileid: "72342544"
---
# <a name="trackcontainerresize"></a>trackContainerResize

[!INCLUDE [trackcontainerresize-description](includes/trackcontainerresize-description.md)]。

如果承载组件的父上下文在模型驱动的应用中提供了高度限制，则将相同的应用于子组件。 但在大多数情况下，父上下文不会限制组件的高度，因此它会收到 "-1" 以指示它可能会进一步增长。

在画布应用中，父上下文始终按拖放编辑器的性质向组件提供高度和宽度。

## <a name="available-for"></a>适用于 

模型驱动应用

## <a name="syntax"></a>语法

`context.mode.trackContainerResize(value)`

## <a name="parameters"></a>参数

| 参数名称|类型|需要|描述|
| ------------- |----|--------|-----------|
|值|`Boolean`|是|`True` 如果控件需要跟踪容器大小，则组件将获取 allocatedWidth 或 allocatedHeight。|


### <a name="related-topics"></a>相关主题

[Mode](../mode.md)<br/>
[PowerApps 组件框架 API 参考](../../reference/index.md)<br/>
[PowerApps 组件框架概述](../../overview.md)
