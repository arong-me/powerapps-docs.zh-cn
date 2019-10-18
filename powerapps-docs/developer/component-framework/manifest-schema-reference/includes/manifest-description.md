---
title: 清单 |Microsoft Docs
description: ''
keywords: ''
ms.author: nabuthuk
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
ms.assetid: 31af2963-b4ca-4347-98f6-4a3f6277f43a
ms.openlocfilehash: 22750956cea12e1ed17bbc1ee8d4f015cf0ce2c1
ms.sourcegitcommit: 63ea15e2f861d43333aacda19230cd8922d7bdfd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/01/2019
ms.locfileid: "72338910"
---
manifest 是定义组件的元数据文件。 它是一个 `XML` 文件，用于描述：

- 组件的命名空间。
- 可以配置的数据类型，可以是字段或数据集。
- 添加组件时可以在应用程序中配置的任何属性。
- 组件需要的资源文件的列表。 
  - 其中一个必须是 JavaScript web 资源。 此 JavaScript 必须包含实例化对象的函数。 它可以实现一个接口，用于公开组件运行所需的方法。 这称为组件实现库。
- 组件实现库中的 JavaScript 函数的名称，该函数将返回应用所需组件接口的对象。

当用户在画布应用程序或模型驱动的应用程序中配置自定义组件时，清单中的数据将筛选出可用组件，以便只有上下文的有效组件可用于配置。 组件清单中定义的属性将呈现为配置字段，以便配置组件的用户可以指定值。 然后，在运行时组件函数可以使用这些属性值。
