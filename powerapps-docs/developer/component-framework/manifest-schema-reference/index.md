---
title: PowerApps 组件框架清单架构参考 | Microsoft Docs
description: ''
keywords: ''
ms.author: nabuthuk
manager: ''
ms.date: 06/4/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 045a395b-4475-48dd-8f67-6bc2b33cd89c
ms.openlocfilehash: 7cf5f46fedc5708f4e2f30dc30140b8a8d9f3529
ms.sourcegitcommit: 4ed29d83e90a2ecbb2f5e9ec5578e47a293a55ab
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "63393845"
---
# <a name="manifest-schema-reference"></a>清单架构参考

[!INCLUDE[cc-beta-prerelease-disclaimer](../../../includes/cc-beta-prerelease-disclaimer.md)]

本部分包含使用 PowerApps CLI 生成的清单架构的参考文档。

> [!IMPORTANT]
> - PowerApps 组件框架为预览功能。
> - [!INCLUDE[cc_preview_features_definition](../../../includes/cc-preview-features-definition.md)] 
> - [!INCLUDE[cc_preview_features_no_MS_support](../../../includes/cc-preview-features-no-ms-support.md)]

|元素|描述|
|----|-----------|
|[code](code.md)|[!INCLUDE [code-description](includes/code-description.md)]|
|[control](control.md)|[!INCLUDE [control-description](includes/control-description.md)]|
|[css](css.md)|[!INCLUDE [css-description](includes/css-description.md)]|
|[data-set](data-set.md)|[!INCLUDE [data-set-description](includes/data-set-description.md)]|
|[html](html.md)|[!INCLUDE [html-description](includes/html-description.md)]|
|[img](img.md)|[!INCLUDE [img-description](includes/img-description.md)]|
|[manifest](manifest.md)|manifest 是定义组件的元数据文件。 它是描述以下内容的 XML 文档<br/> - 组件的命名空间。<br/> - 它可以配置的数据种类，包括字段或数据集。<br/> - 在添加组件时，在应用程序中可以配置的任何属性。<br/> - 组件所需的资源文件列表。<br/> - 其中一个必须是 JavaScript Web 资源。 此 JavaScript 必须包含实例化对象的函数。 它可以实现一个接口，用于公开组件运行所需的方法。 这称为组件实现库。<br/> - 组件实现库中 JavaScript 函数的名称，该函数将返回应用所需接口的对象。<br/> 当有人在应用程序中配置了组件时，清单中的数据会筛选出可用组件，以便仅提供上下文的有效组件进行配置。 组件清单中定义的属性以配置字段的形式呈现，以便配置该控件的人员可以指定值。 然后，这些属性值在运行时可用于组件函数。|
|[property](property.md)|[!INCLUDE [property-description](includes/property-description.md)]|
|[property-set](property-set.md)|[!INCLUDE [property-set-description](includes/property-set-description.md)]|
|[resources](resources.md)|[!INCLUDE [resources-description](includes/resources-description.md)]|
|[resx](resx.md)|[!INCLUDE [resx-description](includes/resx-description.md)]|
|[type-group](type-group.md)|[!INCLUDE [type-group-description](includes/type-group-description.md)]|


### <a name="related-topics"></a>相关主题

[PowerApps 组件框架清单架构参考](index.md)<br/>
[PowerApps 组件框架 API 参考](../reference/index.md)<br/>
[PowerApps 组件框架概述](../overview.md)