---
title: 调试代码组件 |MicrosoftDocs
description: 如何使用 Fiddler 和本机调试调试代码组件
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.topic: article
ms.assetid: 18e88d702-3349-4022-a7d8-a9adf52cd34f
ms.author: nabuthuk
author: Nkrb
ms.openlocfilehash: 088792a32f401ddaf7d3a3cd4fd4d5aa9fa472ff
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2019
ms.locfileid: "72346914"
---
# <a name="debug-code-components"></a>调试代码组件

实现代码组件逻辑后，可以使用 `npm start` 命令开始测试和调试代码组件。 这会生成代码组件，并在本地测试工具中将其打开。

> [!div class="mx-imgBorder"]
> ![测试工具 1](media/test-harness-1.png "测试工具 1")

如上图所示，浏览器窗口打开，其中包含四个部分。 代码组件显示在左窗格中，而右窗格中包含**上下文输入**、**数据输入**和**输出**部分。

- **上下文输入**提供了一种方法，用于指定外形规格并使用每个外形规格（web、平板电脑、手机）测试代码组件。 当代码组件依赖于特定的外形规格功能时，此功能很有用。
- **数据输入**是一个交互式 UI，用于显示在[清单](manifest-schema-reference/manifest.md)文件中定义的所有属性及其[类型](manifest-schema-reference/types.md)或[类型组](manifest-schema-reference/type-group.md)。 它允许您对每个属性的模拟数据进行关键。 
- 只要调用组件的[getOutputs](reference/control/getoutputs.md)方法 **，输出就会呈现输出**。  

     > [!div class="mx-imgBorder"]
     > ![测试工具 2](media/test-harness-2.png "测试工具 2")

> [!NOTE]
> 如果要修改 `ControlManifest.Input.xml` 文件或创建其他属性，则需要在调试过程出现在 "输入" 部分之前重新启动调试进程。

## <a name="test-code-components-with-mock-data"></a>测试带有模拟数据的代码组件

- 对于*字段*类型组件，可以输入**ControlManifest**中定义的每个属性的值和类型，如下所示：

   > [!div class="mx-imgBorder"]
   > ![测试工具 2.5](media/test-harness-2.5.png "测试工具 2.5")

- 对于*数据集*类型组件，可以加载包含测试数据的 CSV 文件。 直接从环境中手动创建或导出 .csv 格式。 有效的 CSV 文件可用后，可以按如下所示加载它：

   > [!div class="mx-imgBorder"]
   > ![测试工具 3](media/test-harness-3.png "测试工具 3")

- 加载 CSV 文件后，将**ControlManifest**中定义的每个属性绑定到 CSV 文件中的列。 这是通过为每个属性选取列来实现的，如下所示：

    > [!div class="mx-imgBorder"]
    > ![测试工具 4](media/test-harness-4.png "测试工具 4")

- 如果未在**ControlManifest**文件中定义任何属性，则所有列都将自动加载到测试工具中。

   > [!div class="mx-imgBorder"]
   > ![测试工具 5](media/test-harness-5.png "测试工具 5")


## <a name="watch-mode-in-test-harness"></a>测试工具中的监视模式

测试工具支持 `watch` 模式，你可以将其用于 PowerApps 组件框架项目。 若要启用 `watch` 模式，请使用命令 `npm start watch` 启动测试工具。 在 `watch` 模式下，对下列任何组件资产所做的更改将自动反映在测试工具中，而无需重新启动：

1.  `index.ts` 文件。
2.  `ControlManifest.Input.xml` 文件。
3.  @No__t_0 导入的库。
4.  清单文件中列出的所有资源。

## <a name="debug-code-components-using-native-browsers"></a>使用本机浏览器调试代码组件

您可以使用浏览器的调试功能来观察组件行为。 每个浏览器提供一个调试工具，可帮助你在浏览器中本机调试你的代码。 通常，您可以在浏览器中激活调试，只需要按**F12**键即可显示用于调试的本机开发人员工具。

例如，在**Microsoft Edge**上：

- 按**F12**打开检查器。
- 选择组件。
- 在顶部栏上，中转到 "**调试器**"，然后在搜索栏中搜索清单文件中所述的组件名称。 例如，键入组件名称，如 `Hello World component`。

     > [!div class="mx-imgBorder"]
     > ![调试组件](media/debug-control.png "调试组件")

> [!NOTE]
> 最好在组件的生命周期方法（如[init](reference/control/init.md)和[updateView](reference/control/updateview.md)）上设置断点。

你还可以通过在 "*源*" 选项卡中设置断点来实时与组件进行交互，并在 DOM 中查看元素，如下所示：

> [!div class="mx-imgBorder"]
> ![调试组件](media/debug-control-1.png "调试组件 1")

## <a name="fiddler-autoresponder"></a>Fiddler AutoResponder

使用 Fiddler AutoResponder 快速调试代码组件。 安装[Fiddler](https://www.telerik.com/download/fiddler) ，然后按照步骤配置[AutoResponder](https://docs.microsoft.com/dynamics365/customer-engagement/developer/streamline-javascript-development-fiddler-autoresponder)。

### <a name="related-topics"></a>相关主题

[PowerApps 组件框架 API 参考](reference/index.md)<br/>
[PowerApps 组件框架概述](overview.md)
