---
title: PowerApps 组件框架的限制 |MicrosoftDocs
description: 使用 PowerApps 组件框架的限制
author: nkrb
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.topic: index-page
ms.assetid: 18e88d702-3349-4022-a7d8-a9adf52cd34f
ms.author: nabuthuk
ms.openlocfilehash: aabcf4518e71648797c795a006c2d842f3e5ff01
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2019
ms.locfileid: "72346730"
---
# <a name="limitations"></a>限制 

随着 PowerApps 组件框架的发布，现在可以创建自己的代码组件，以改善模型驱动应用和画布应用中的用户体验。 即使您可以创建自己的组件，但有一些限制会限制开发人员在代码组件中实现某些功能。 下面是一些限制：

1. 在画布应用的实验预览中，仅支持组件的*字段*类型，而不支持*数据集*类型组件。 
2. 此实验性预览中不提供 Common Data Service 从属 Api，包括 WebAPI 和其他一些 Api。 有关此试验性预览版本的各个 API 可用性，请参阅[PowerApps 组件框架 API 参考](reference/index.md)。
3. 代码组件应将所有代码（包括外部库内容）捆绑到主代码捆绑。 若要查看 PowerApps 命令行界面如何帮助将外部库内容绑定到特定于组件的绑定的示例，请参阅[角度反转组件](sample-controls/angular-flip-control.md)示例。

   > [!NOTE]
   > 目前尚不支持在组件清单中使用库节点跨组件使用共享库。 我们正在查看此功能，并将在将来的版本中添加此功能。
4. 目前尚不支持在单个清单文件中定义多个组件。
5. 尚不支持调用进程和操作。 只能使用[导航](reference/navigation.md)方法调用对话框。
6. 尚不支持从另一个代码组件调用一个组件。
7. 目前还不支持字体资源（. tff）。

## <a name="related-topics"></a>相关主题

[PowerApps 组件框架 API 参考](reference/index.md)<br/>
[PowerApps 组件框架概述](overview.md)
