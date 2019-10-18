---
title: PowerApps 组件框架概述 |Microsoft Docs
description: 使用 PowerApps 组件框架创建代码组件，为用户提供在窗体、视图和仪表板中查看和处理数据的增强体验。
keywords: 组件框架，代码组件，PowerApps 控件
author: nkrb
manager: kvivek
ms.date: 09/05/2019
ms.service: powerapps
ms.custom:
- dyn365-a11y
- dyn365-developer
ms.topic: article
ms.assetid: 7923e36d-3640-49f7-9f2f-c97358a632db
ms.author: nabuthuk
ms.openlocfilehash: dede052df8e760748da3dae6cfab645b071b21d7
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2019
ms.locfileid: "72345787"
---
# <a name="powerapps-component-framework-overview"></a>PowerApps 组件框架概述

使用 PowerApps 组件框架为模型驱动的应用程序和画布应用程序创建代码组件（实验性预览），以便为用户提供查看和处理窗体、视图和仪表板中的数据的增强的用户体验。 例如：

- 使用 `dial` 或 `slider` 组件替换显示数值文本值的字段。
- 将列表转换为绑定到数据集的完全不同的视觉体验，如 `Calendar` 或 `Map`。

> [!IMPORTANT]
> - PowerApps 组件框架处于适用于画布应用的实验性预览中，并在 GA 中用于模型驱动应用。 这意味着在画布应用上可能不支持模型驱动应用支持的所有 Api。
> - 默认情况下，对模型驱动应用启用 PowerApps 组件框架。 若要为画布应用启用此功能，请参阅[画布应用的可用性](component-framework-for-canvas-apps.md)。
> - [!INCLUDE[cc_preview_features_definition](../../includes/cc-preview-features-definition.md)]
> - 画布应用仅支持代码组件的*字段*类型，而不支持*数据集*类型。


PowerApps 组件框架使专业开发人员和应用程序开发人员能够创建可跨 PowerApps 功能的全部广泛使用的代码组件。 与 HTML web 资源不同，代码组件呈现为同一上下文的一部分，与任何其他组件同时加载，为用户提供无缝体验。 开发人员可以将所有 HTML、CSS 和 TypeScript 或 JavaScript 文件捆绑到一个解决方案包文件中。 可以在不同的实体和窗体中多次重复使用代码组件。

代码组件可以访问一组丰富的框架 Api，这些 Api 公开组件生命周期管理、上下文数据和元数据访问等功能、通过 Web API 实现的无缝服务器访问、实用程序和数据格式设置方法、相机等设备功能位置和麦克风，以及易于调用的 UX 元素，如对话框、查找和整页呈现。  


开发人员和应用程序开发人员可以使用新式 web 实践，还可以利用外部库的强大功能来创建高级用户交互。 框架自动处理组件生命周期，保留应用程序业务逻辑，并针对性能进行优化（不再有异步 Iframe）。 组件定义、依赖关系和配置可全部打包到一个[解决方案](https://docs.microsoft.com/dynamics365/customer-engagement/customize/solutions-overview)中并跨环境移动，并可通过[AppSource](https://appsource.microsoft.com/en-us/marketplace/apps?page=1&product=dynamics-365)发运。  

## <a name="related-topics"></a>相关主题

[什么是代码组件](custom-controls-overview.md)<br/>
[画布应用的可用性](component-framework-for-canvas-apps.md)<br/>
[创建并生成代码组件](create-custom-controls-using-pcf.md)<br/>
[面向开发人员的 PowerApps](https://docs.microsoft.com/powerapps/#pivot=home&panel=developer)

