---
title: PowerApps 组件框架清单架构参考 |Microsoft Docs
description: ''
keywords: ''
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 06/4/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 045a395b-4475-48dd-8f67-6bc2b33cd89c
ms.openlocfilehash: 8f58f10f6a3695615ddc3b58b540c59240af9641
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2019
ms.locfileid: "72346362"
---
# <a name="manifest-schema-reference"></a>清单架构参考

本部分包含使用 PowerApps CLI 生成的清单架构的参考文档。

> [!IMPORTANT]
> "**可用**" 选项卡显示模型驱动应用和画布应用支持哪些元素（实验性预览）。 建议为每个单独的属性检查**可用的**部分（无论它是否受支持）。 例如，**代码**元素支持模型驱动应用和画布应用，但**代码**元素中的**html**和**img**属性不支持画布应用。 

|元素|描述|适用于|
|----|-----------|-----|
|[code](code.md)|[!INCLUDE [code-description](includes/code-description.md)]|模型驱动应用和画布应用（实验性预览）|
|[control](control.md)|[!INCLUDE [control-description](includes/control-description.md)]|模型驱动应用和画布应用（实验性预览）|
|[css](css.md)|[!INCLUDE [css-description](includes/css-description.md)]|模型驱动应用和画布应用（实验性预览）|
|[data-set](data-set.md)|[!INCLUDE [data-set-description](includes/data-set-description.md)]|模型驱动应用|
|[html](html.md)|[!INCLUDE [html-description](includes/html-description.md)]|模型驱动应用|
|[img](img.md)|[!INCLUDE [img-description](includes/img-description.md)]|模型驱动应用|
|[manifest](manifest.md)|manifest 是定义组件的元数据文件。 它是描述以下内容的 XML 文档<br/> - 组件的命名空间。<br/> - 它可以配置的数据种类，包括字段或数据集。<br/> - 在添加组件时，在应用程序中可以配置的任何属性。<br/> - 组件所需的资源文件列表。<br/> - 其中一个必须是 JavaScript Web 资源。 此 JavaScript 必须包含实例化对象的函数。 它可以实现一个接口，用于公开组件运行所需的方法。 这称为组件实现库。<br/> - 组件实现库中 JavaScript 函数的名称，该函数将返回应用所需接口的对象。<br/> 当有人在应用程序中配置了组件时，清单中的数据会筛选出可用组件，以便仅提供上下文的有效组件进行配置。 组件清单中定义的属性以配置字段的形式呈现，以便配置该控件的人员可以指定值。 然后，这些属性值在运行时可用于组件函数。|模型驱动应用和画布应用（实验性预览）|
|[property](property.md)|[!INCLUDE [property-description](includes/property-description.md)]|模型驱动应用和画布应用（实验性预览）|
|[property-set](property-set.md)|[!INCLUDE [property-set-description](includes/property-set-description.md)]|模型驱动应用|
|[resources](resources.md)|[!INCLUDE [resources-description](includes/resources-description.md)]|模型驱动应用和画布应用（实验性预览）|
|[resx](resx.md)|[!INCLUDE [resx-description](includes/resx-description.md)]|模型驱动应用和画布应用（实验性预览）|
|[type-group](type-group.md)|[!INCLUDE [type-group-description](includes/type-group-description.md)]|模型驱动应用和画布应用（实验性预览）|
|[功能用法](feature-usage.md)|功能使用情况元素用作围绕 `uses-feature` 元素的包装，它们本身允许开发人员声明其组件要使用哪些功能。 如果未定义任何使用-功能元素，则不需要使用此功能元素。|模型驱动应用|

### <a name="related-topics"></a>相关主题

[PowerApps 组件框架清单架构参考](index.md)<br/>
[PowerApps 组件框架 API 参考](../reference/index.md)<br/>
[PowerApps 组件框架概述](../overview.md)